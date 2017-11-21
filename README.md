# intensepool
Scripts and Projects for intensepool

# Requirements
These scripts have been tested on _"Debian 4.9.30-2+deb9u5 (2017-09-19) x86_64 GNU/Linux"_ but should work on any linux distro running systemd. You should have both **xmrig** and **intensecoind** saved to your local machine along with a copy of your wallet address. You will also need root access to complete the setup

See [intensepool support](http://intensepool.net/support.html) if you do not have either xmrig or intensecoind

# Configuration
1. Clone project repo
2. Copy xmrig.service and intensed.service to _/etc/systemd/system/_ you will need **root** access for this, most likley
3. Edit the newly copied files

<h2> intensecoind.service </h2>

_Configure the systemd scripts replaing fileds "{}" with your own information_

1. WorkingDirectory - The location of intensecoind
2. User - The user who will run this service, usually your own user
3. ExecStart: {path_to_intensecoind} - Path to the intensecoind binary. {working_dir} - Same as WorkingDirectory. {log_file} - file which the service should log to. See "Logs" below for more details.

Start and (optionally) enable the service to start at boot
1. systemctl start intensecoind.service && systemctl enable intensecoind.service

<h2> xmrig.service </h2>

_Configure the systemd scripts replaing fileds "{}" with your own information_

1. WorkingDirectory - The location of xmrig
2. User - The user who will run this service, usually your own user
3. ExecStart: {path_to_xmrig} - Path to the xmrig binary. {wallet_address} - Your wallet address. {log_file} - file which the service should log to. See "Logs" below for more details. {donate_level %} - Donate level as a percentage eg 5%

Start and (optionally) enable the service to start at boot
1. systemctl start xmrig.service && systemctl enable xmrig.service

<h2> Logs </h2>

To keep things simple I created a directory "/var/log/intensecoin/" and set read/write permissions on that directory for the user listed in the services. Setting just "/var/log" may cause problems is running the service unless root.
