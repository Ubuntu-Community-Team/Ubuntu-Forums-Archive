---
title: "Who can help to me with network:ports, apache2 \\ wireless tp-link router"
date: 2020-04-23
forum: Networking &amp; Wireless
---

### Post by getting-power-or-powder on 2020-04-23
I have installed ufw
Typed:
sudo ufw allow 7777
  

after type:

 sudo ufw status -- 7777 is open ... 

i have tried to check the port 

[https://www.yougetsignal.com/tools/open-ports/](https://www.yougetsignal.com/tools/open-ports/)

this website showes it is not open.. how to fix problem and open the  port, then do the redirect from static [http://100.70.214.84:7777](http://100.70.214.84:7777) to  local server and show to visitors web-site from local server

How to do that?

I have static ip [http://100.70.214.84/](http://100.70.214.84/) 
I have opened port 7777 with ufw allow 7777
My  apache2 server is running -- i'm using server, web-site work correctly  with php+sql, all is ok --> localhost, 127.0.01 - work is ok. WebSite  is working inside localhost, it is show me all data but i can visit  website if i turn on vpn and try visit link [http://100.70.214.84:7777](http://100.70.214.84:7777)  outgoing link static my ipv4 from provider

how to sett up  correctly redirects with listening ip:port and get acces to localdata  from outgoing ip for visitor over the world, not only for local network  use under wi-fi router ?
I don't have commerce target only for personal use, paying for hosting it's expensive for me for not commerce little website. How to launch personal server ?

I have ubuntu 18.04 version

---

### Post by SeijiSensei on 2020-04-24
Opening the port is just the first step.  You need to set up a server of some sort to listen on that port.  You would need a "Listen 7777" directive in /etc/apache2/ports.conf, and virtual host configuration files that use
```

<VirtualHost *:7777>
stuff
</VirtualHost>

```

---

### Post by getting-power-or-powder on 2020-04-24
/etc/host
is
```

192.168.0.100    e1x1a1m1p1l1e.com
127.0.1.1    closedconnect
#below static ip which give to me the internet provider
100.70.214.84    e1x1a1m1p1l1e.com
#domain before this string is not registred
 
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
I decide to do in default mode with static 80 port...

Below etc/apache2/ports.conf
```
Listen 80

<IfModule ssl_module>
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

/etc/apache2/sites-available/e1x1a1m1p1l1e.com.conf
```
<VirtualHost *:80>
    #ServerName www.e1x1a1m1p1l1e.com
    ServerAdmin webmaster@e1x1a1m1p1l1e.com
    ServerName e1x1a1m1p1l1e.com
    ServerAlias www.e1x1a1m1p1l1e.com
    DocumentRoot /var/www/e1x1a1m1p1l1e.com/html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

etc/apache2/apache2.conf
```
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.4/ for detailed information about
# the directives and /usr/share/doc/apache2/README.Debian about Debian specific
# hints.
#
#
# Summary of how the Apache 2 configuration works in Debian:
# The Apache 2 web server configuration in Debian is quite different to
# upstream's suggested way to configure the web server. This is because Debian's
# default Apache2 installation attempts to make adding and removing modules,
# virtual hosts, and extra configuration directives as flexible as possible, in
# order to make automating the changes and administering the server as easy as
# possible.

# It is split into several files forming the configuration hierarchy outlined
# below, all located in the /etc/apache2/ directory:
#
#    /etc/apache2/
#    |-- apache2.conf
#    |    `--  ports.conf
#    |-- mods-enabled
#    |    |-- *.load
#    |    `-- *.conf
#    |-- conf-enabled
#    |    `-- *.conf
#     `-- sites-enabled
#         `-- *.conf
#
#
# * apache2.conf is the main configuration file (this file). It puts the pieces
#   together by including all remaining configuration files when starting up the
#   web server.
#
# * ports.conf is always included from the main configuration file. It is
#   supposed to determine listening ports for incoming connections which can be
#   customized anytime.
#
# * Configuration files in the mods-enabled/, conf-enabled/ and sites-enabled/
#   directories contain particular configuration snippets which manage modules,
#   global configuration fragments, or virtual host configurations,
#   respectively.
#
#   They are activated by symlinking available configuration files from their
#   respective *-available/ counterparts. These should be managed by using our
#   helpers a2enmod/a2dismod, a2ensite/a2dissite and a2enconf/a2disconf. See
#   their respective man pages for detailed information.
#
# * The binary is called apache2. Due to the use of environment variables, in
#   the default configuration, apache2 needs to be started/stopped with
#   /etc/init.d/apache2 or apache2ctl. Calling /usr/bin/apache2 directly will not
#   work with the default configuration.


# Global configuration
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the Mutex documentation (available
# at <URL:http://httpd.apache.org/docs/2.4/mod/core.html#mutex>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
#ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#Mutex file:${APACHE_LOCK_DIR} default

#
# The directory where shm and other runtime files will be stored.
#

DefaultRuntimeDir ${APACHE_RUN_DIR}

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 5


# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog ${APACHE_LOG_DIR}/error.log

#
# LogLevel: Control the severity of messages logged to the error_log.
# Available values: trace8, ..., trace1, debug, info, notice, warn,
# error, crit, alert, emerg.
# It is also possible to configure the log level for particular modules, e.g.
# "LogLevel info ssl:warn"
#
LogLevel warn

# Include module configuration:
IncludeOptional mods-enabled/*.load
IncludeOptional mods-enabled/*.conf

# Include list of ports to listen on
Include ports.conf


# Sets the default security model of the Apache2 HTTPD server. It does
# not allow access to the root filesystem outside of /usr/share and /var/www.
# The former is used by web applications packaged in Debian,
# the latter may be used for local directories served by the web server. If
# your system is serving content from a sub-directory in /srv you must allow
# access here, or in any related virtual host.
<Directory />
    Options FollowSymLinks
    AllowOverride None
    Require all denied
</Directory>

<Directory /usr/share>
    AllowOverride None
    Require all granted
</Directory>

<Directory /var/www/>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>

#<Directory /srv/>
#    Options Indexes FollowSymLinks
#    AllowOverride None
#    Require all granted
#</Directory>




# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#
AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being
# viewed by Web clients.
#
<FilesMatch "^\.ht">
    Require all denied
</FilesMatch>


#
# The following directives define some format nicknames for use with
# a CustomLog directive.
#
# These deviate from the Common Log Format definitions in that they use %O
# (the actual bytes sent including headers) instead of %b (the size of the
# requested file), because the latter makes it impossible to detect partial
# requests.
#
# Note that the use of %{X-Forwarded-For}i instead of %h is not recommended.
# Use mod_remoteip instead.
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
IncludeOptional conf-enabled/*.conf

# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
Include /etc/phpmyadmin/apache.conf
ServerName e1x1a1m1p1l1e.com
```

So i don't know what to do on the next steps... where and what listen to (ports) and how and what to direct/redirect/
Who know and can help to me?
> 
[http://localhost/](http://localhost/)
[http://e1x1a1m1p1l1e.com/](http://e1x1a1m1p1l1e.com/)
[http://100.70.214.84/](http://100.70.214.84/)
I can wee the index page of website which i have created on local apache server, but if i try turn on vpn and type in the browser [http://100.70.214.84]("http://100.70.214.84/"):80 - i have seen this 
> i am waiting for respond for > 1 min... and  **ERROR**

 **The requested URL could not be retrieved**

 
 [HR][/HR]   The following error was encountered while trying to retrieve the URL: [http://100.70.214.84/](http://100.70.214.84/)[INDENT] **Connection to 100.70.214.84 failed.**
 [/INDENT]
The system returned: *(110) Connection timed out*
  The remote host or network may be down. Please try the request again.
  Your cache administrator is webmaster.

  

  [HR][/HR]  Generated Fri, 24 Apr 2020 23:22:42 GMT by 54.37.73.126 (squid/3.5.12)

----> 54.37.73.126 - it's vpn ip adress

---

### Post by SeijiSensei on 2020-04-25
I'm guessing you have a routing problem on the apache server. Suppose you have a local network with address range 192.168.1.0/24, and a VPN tunnel with 10.0.0.1 at the server end and 10.0.0.2 on the machine running the VPN client.  The apache machine needs to have a static route like

```
sudo ip route add 192.168.1.0/24 via 10.0.0.2
```

telling the server to send packets for the 192.168 network over the VPN to 10.0.0.2.  Often people set up routing correctly at one end of the VPN tunnel, and forget to set up a route back at the other end.

---

### Post by TheFu on 2020-04-25
Should we assume there's a static IP on the system or did you just set the IP you hope to get in the /etc/hosts file? If something specific wasn't done to configure a static IP, then that didn't happen.

**ip addr** can prove the IPs on the box.
Then the router needs to open 1 port to the web server and point that port from the WAN side to the LAN server IP.  This assumes you don't want any security.  With a private website, you might want for that never to be accessed by all the bad-guys in the world.  They will find it. They always do.  If you would like to setup a tunnel into your LAN there are a few ways to accomplish that using ssh or openvpn or wireguard.  ssh is the easiest to get working and pretty easy to secure.  The VPN server that you'd run on your LAN is much harder to setup, but doesn't just handle website traffic.  

But ssh doesn't handle just website traffic either.  There's ssh, scp, sftp, rsync, sshfs, x2go, vim, and about 50 others that all leverage ssh connections to work. ssh is like a swiss army knife for connectivity, remote desktops, transferring files, remote editing, backups, cloning directories .... that's off the top of my head.   Once ssh-keys are setup between 2 systems, which is just 3 commands, and passwords from the internet are not allowed in the ssh configuration anymore (you'll want to change that), then ssh is perhaps 0.000001% less secure than those VPN tools.

---

