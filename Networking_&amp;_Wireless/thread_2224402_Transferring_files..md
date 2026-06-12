---
title: "Transferring files."
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by LastDino on 2014-05-16
I've never tried this before with anything, but I was just wondering, is it possible to exchange files between my Pc and mobile through wifi? Mobile is connected to WI-fi internet through my TP-link and my PC is directly connected trough LAN wire. Mobile is java based not android or windows.

Is there any way to achieve this?

---

### Post by brantcgardner on 2014-05-16
Should be possible, but we'd need rather a lot more detail about your mobile device to offer specific solutions.

By and large if your IP addresses can see each other there will be a way to exchange files; the specific method will pretty much be your own choice for how you want to implement it.

---

### Post by LastDino on 2014-05-16
Well, it is Nokia asha 502. It belongs to my father so I prefer it stays away from my PC :p

Is there anything specific you would like to know? I don't know how to check  IP address of it or whether it can be seen or not for sure but it should be as it connected through router. 

You know of any commands/tools to get IP of both that mobile and my PC?

---

### Post by brantcgardner on 2014-05-16
The Nokia Asha looks to be running the "Nokia Asha" operating system.  I'm afraid I don't know anything about that OS at all, but depending on your needs you could at least pass files TO the mobile by hosting them on your Trusty box with Apache.  For that to work this "Asha" OS just needs a browser, and according to the specs it has one.

Not sure what all you are trying to accomplish, could you tell us a little about what it is you want to do as far as file exchanging?

---

### Post by LastDino on 2014-05-16
My goal is to gain ability to transfer files (mostly music and documents) between my PC and that mobile without needing it to connect directly (with data cable) to my PC or taking  out its MicroSD card and attaching it to my card reader. You see, nokia allows me to download music for free for first few months and I would like to get that downloaded music to my PC without me needing to manually taking out that SD card or keeping that mobile itself busy by attaching it to my PC. As I said, it belongs to my father and he does not appreciate either of those methods. >.>

It does have a browser, that is how he browses net using our TP-link router. 
So, what to do next?

---

### Post by brantcgardner on 2014-05-16
Well, if I were in your shoes I'd set up an FTP server on your Trusty box and try pushing files to it from the Nokia.  FTP is a well-established service that the Nokia is likely to understand and cooperate with.  There are other alternatives but this is probably where I would start.

I can't really suggest a method going in the other direction as it would require more knowledge about the Asha OS than I've got, but perhaps others can chime in.

To get your Trusty box's IP address so you can start experimenting with this notion, open a terminal and type "ifconfig".

---

### Post by brantcgardner on 2014-05-16
Here's the Trusty [link]("https://help.ubuntu.com/14.04/serverguide/ftp-server.html") for FTP server, I forgot to add that.

---

### Post by LastDino on 2014-05-16
> **brantcgardner said:**
> Well, if I were in your shoes I'd set up an FTP server on your Trusty box and try pushing files to it from the Nokia.  FTP is a well-established service that the Nokia is likely to understand and cooperate with.  There are other alternatives but this is probably where I would start.

I can't really suggest a method going in the other direction as it would require more knowledge about the Asha OS than I've got, but perhaps others can chime in.

To get your Trusty box's IP address so you can start experimenting with this notion, open a terminal and type "ifconfig".

> lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 16  bytes 1176 (1.1 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16  bytes 1176 (1.1 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

p33p1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.100  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::8e89:a5ff:fe62:4227  prefixlen 64  scopeid 0x20<link>
        ether 8c:89:a5:62:42:27  txqueuelen 1000  (Ethernet)
        RX packets 19818  bytes 19931124 (19.0 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20428  bytes 2098404 (2.0 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 1  collisions 0

I see lot of numbers which looks like IP.lol
Which is suppose to be my IP to be exact? 

Also, does setting up FTP require me to install anything on that mobile? From what google tells me; I need to install vsftp on my PC, which I've did it already. 
Does this type of file sharing consume internet data? 
 
Sorry, my knowledge in this area is worse than a newborn :P

---

### Post by brantcgardner on 2014-05-16
The line you want is the one that starts with "inet", so your Trusty box has IP address 192.168.1.100.  That's subject to change when you reboot, so don't be afraid to run ifconfig again if you need to.

So once you set up an FTP server, on the Nokia you could navigate to [ftp://192.168.1.100](ftp://192.168.1.100).  Make sense?

---

### Post by brantcgardner on 2014-05-16
Hmm.  I've read up some more on your Nokia and it sounds like the native browser is Xpress, which again I am not familiar with so I don't know how to guide you with that.

However, the [specifications document]("http://www.nokia.com/global/products/phone/asha502-dual-sim/specifications/") over at Nokia indicates that it implements FTP natively.  That might be limited to Bluetooth, but it may be worth researching the Nokia docs to see if there is a native Asha FTP application that you could use.

---

### Post by LastDino on 2014-05-16
> **brantcgardner said:**
> The line you want is the one that starts with "inet", so your Trusty box has IP address 192.168.1.100.  That's subject to change when you reboot, so don't be afraid to run ifconfig again if you need to.

So once you set up an FTP server, on the Nokia you could navigate to [ftp://192.168.1.100](ftp://192.168.1.100).  Make sense?

Yes, yes! I would try that and get back here as soon as I get my hands on that mobile to experiment. 

But just in case and out of my curiosity, which were those other methods you mentioned?

---

### Post by brantcgardner on 2014-05-16
Incidentally, this also represents another possible file transfer path.  If you can't get FTP working to your satisfaction, you could try interacting with the Nokia using [Bluetooth]("https://help.ubuntu.com/community/BluetoothSetup").  That will require Bluetooth hardware on the Trusty box and physical proximity to the Nokia but it's another option to keep in mind.

---

### Post by LastDino on 2014-05-16
> **brantcgardner said:**
> Hmm.  I've read up some more on your Nokia and it sounds like the native browser is Xpress, which again I am not familiar with so I don't know how to guide you with that.

However, the [specifications document]("http://www.nokia.com/global/products/phone/asha502-dual-sim/specifications/") over at Nokia indicates that it implements FTP natively.  That might be limited to Bluetooth, but it may be worth researching the Nokia docs to see if there is a native Asha FTP application that you could use.

I've installed opera mini browser on it as well. I'll search for FTP application if it is available or not right away :3

Thank you for your help, I'll post here as soon as I make some progress either-way :P

Edit: I don't have Bluetooth hardware anymore, sadly. I was extensive user of Bluetooth dongle when I didn't have proper net connection. I used to use mobile net service to connect my PC to internet in emergency through that. Good old days. :P

---

### Post by LastDino on 2014-05-16
Well, good news is that it support some client called Web Share which allows sharing over Wi-fi or internet. 

After installing it I see following things>

> Local IP
192.168.1.101

Internet IP
Connected to WLAN

start the server and enter [http://LOCAL_IP](http://LOCAL_IP) or [http://INTERNET_IP](http://INTERNET_IP) on your PC

There there is ''start server'' button

I did enter that in my browser addressed bar and pressed start server on phone. It shows me this

[ATTACH=CONFIG]253207[/ATTACH]

I have to go out so I can't really check if this is working beyond this right now, but I'm bit curious as it asked me to put ''http:'' instread of ''ftp'' in address bar, is it wedging on my internet data? Does using http make difference?

Thank you for your help again, I appreciate it ^^

---

### Post by brantcgardner on 2014-05-16
Looks to me like you found your goal.  I offered FTP because it's simple and well-known, but this (while not well-known) looks to be an http implementation of exactly what we were trying to accomplish.

You're on the right path, just open that page on your Trusty box and start experimenting with transferring files from the Nokia to Ubuntu.

Good luck! :cool:

---

### Post by LastDino on 2014-05-16
I checked it and downloading is certainly possible. At least from phone to PC. However, I would like to know how to go other way around? ;D

There doesn't seen to be option to do that with the software I used on phone, are there any other ways to send file to phone from PC?

---

### Post by brantcgardner on 2014-05-17
It's not likely that y****ou will find an existing method to **push** files to the phone, but you have lots of ways you can **pull** files to the phone from the Trusty box.

Going back to where we started, using a browser on the phone to reach either Apache or FTP on the Trusty box is probably the easiest way to accomplish that.

---

### Post by Morbius1 on 2014-05-17
There's an easy way to test the http mehod and it doesn't require you to install or configure anything.

_ In linux:_

** Open your terminal
**Change directories to the folder that contains the files you want to download on the phone, for example:
```
cd Music
```
** Then issue this command to create a temporary "baby" http server:
```
python -m SimpleHTTPServer
```

_On the phone:_

Open your browser and point it to the linux machine, for example:
```
http://192.168.0.100:8000
```

When you are done with the transfer kill the http server on the Linux machine with a Ctrl+Z

---

### Post by brantcgardner on 2014-05-17
Nice!  Thanks Morbius1, I would not have thought of that approach.

---

### Post by LastDino on 2014-05-18
> **Morbius1 said:**
> There's an easy way to test the http mehod and it doesn't require you to install or configure anything.

_ In linux:_

** Open your terminal
**Change directories to the folder that contains the files you want to download on the phone, for example:
```
cd Music
```
** Then issue this command to create a temporary "baby" http server:
```
python -m SimpleHTTPServer
```

_On the phone:_

Open your browser and point it to the linux machine, for example:
```
http://192.168.0.100:8000
```

When you are done with the transfer kill the http server on the Linux machine with a Ctrl+Z

For some reason it isn't working for me, please tell me if I'm doing anything wrong.

ifconfig output
```
[glen@localhost ~]$ ifconfig
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 14  bytes 880 (880.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 14  bytes 880 (880.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

p33p1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.100  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::8e89:a5ff:fe62:4227  prefixlen 64  scopeid 0x20<link>
        ether 8c:89:a5:62:42:27  txqueuelen 1000  (Ethernet)
        RX packets 141695  bytes 199685882 (190.4 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 134376  bytes 11486345 (10.9 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 1  collisions 0


```

I've tried both 
[http://192.168.1.100:8000](http://192.168.1.100:8000)
and
[http://192.168.0.100:8000](http://192.168.0.100:8000)

I get this error on phone browser:

> Can't reach.
-whatever the address I entered-
Please try again.

Just in case you're interested; this is what I see when I enter command to make mini server.
```
[glen@localhost ~]$ python -m SimpleHTTPServer
Serving HTTP on 0.0.0.0 port 8000 ...



```
Any ideas?

---

### Post by LastDino on 2014-05-18
And yes, I've allowed HTTP connections from all network zones temporarily.

---

### Post by Morbius1 on 2014-05-18
Don't know what to tell you.

As it happens I have Android 4.3 in a VBox guest ( don't ask ) and it appears to work under these conditions so I know it's possible:
[ATTACH=CONFIG]253274[/ATTACH]
I did the python thingy from my home directory.

Open your web browser within Ubuntu and try to access [http://192.168.1.100:8000](http://192.168.1.100:8000). If it doesn't work within Ubuntu itself then something local is a problem.

---

### Post by LastDino on 2014-05-18
> **Morbius1 said:**
> Don't know what to tell you.

As it happens I have Android 4.3 in a VBox guest ( don't ask ) and it appears to work under these conditions so I know it's possible:
[ATTACH=CONFIG]253274[/ATTACH]
I did the python thingy from my home directory.

Open your web browser within Ubuntu and try to access [http://192.168.1.100:8000](http://192.168.1.100:8000). If it doesn't work within Ubuntu itself then something local is a problem.

 Just noting this down: Unfortunately, I'm in the process of checking out Fedora 20 XFCE and I'm waiting for 14.04.1 of Xubuntu to come out before I settle for it, so I'm doing this on fedora.

And yes, something local seems to be the problem as I get this error.
[ATTACH=CONFIG]253279[/ATTACH] 

I've no clue about how to correct this though, any ideas?

---

### Post by brantcgardner on 2014-05-19
Looks like you've installed the NoScript plugin and then accidentally triggered it by clicking on the [http://192.168.1.100:8000](http://192.168.1.100:8000) link here in the forums.  Instead of doing that, type it directly into your browser address bar in a new tab.

---

### Post by LastDino on 2014-05-19
> **brantcgardner said:**
> Looks like you've installed the NoScript plugin and then accidentally triggered it by clicking on the [http://192.168.1.100:8000](http://192.168.1.100:8000) link here in the forums.  Instead of doing that, type it directly into your browser address bar in a new tab.

Now I can certainly see the contents of my Ubuntu file system in browser on PC but phone browser is not able to see it and I get the same error as before. I've tried this on 3 different OS, result is same. 

Any ideas?
Is there any other method?

---

### Post by brantcgardner on 2014-05-19
> **LastDino said:**
> Now I can certainly see the contents of my Ubuntu file system in browser on PC but phone browser is not able to see it and I get the same error as before. I've tried this on 3 different OS, result is same. 

Any ideas?
Is there any other method?

You said earlier that:

> **LastDino said:**
> I see lot of numbers which looks like IP.lol
Which is suppose to be my IP to be exact? 

Also, does setting up FTP require me to install anything on that mobile?  From what google tells me; I need to install vsftp on my PC, which I've  did it already. 
Does this type of file sharing consume internet data? 
 
Sorry, my knowledge in this area is worse than a newborn :razz:

...so you have vsftp already running.  Can you reach that FTP server from your Nokia?

---

### Post by LastDino on 2014-05-20
> **brantcgardner said:**
> You said earlier that:



...so you have vsftp already running.  Can you reach that FTP server from your Nokia?

I do, but I've no clue about as to how to check what you're asking >.>

---

### Post by LastDino on 2014-05-20
I forgot to add this to last post, I get this error

> [glen@localhost ~]$ sudo systemctl start vsftpd.service
[sudo] password for glen: 
Job for vsftpd.service failed. See 'systemctl status vsftpd.service' and 'journalctl -xn' for details.

I used this guide to configure the vsftpd
[http://www.server-world.info/en/note?os=Fedora_20&p=ftp&f=1](http://www.server-world.info/en/note?os=Fedora_20&p=ftp&f=1)

---

### Post by brantcgardner on 2014-05-20
Oh, I took your comment that you had installed vsftp to mean "installed it and confirmed it was working".  For Ubuntu, you should probably use the Ubuntu [install instructions]("https://help.ubuntu.com/14.04/serverguide/ftp-server.html"), not the Fedora steps.

Try that guide, and after you get your FTP server running I think you could put [ftp://192.168.1.100](ftp://192.168.1.100) in your Xpress browser and see/download whatever files you have configured access to on the Trusty box.

---

### Post by LastDino on 2014-05-20
> **brantcgardner said:**
> Oh, I took your comment that you had installed vsftp to mean "installed it and confirmed it was working".  For Ubuntu, you should probably use the Ubuntu [install instructions]("https://help.ubuntu.com/14.04/serverguide/ftp-server.html"), not the Fedora steps.

Try that guide, and after you get your FTP server running I think you could put [ftp://192.168.1.100](ftp://192.168.1.100) in your Xpress browser and see/download whatever files you have configured access to on the Trusty box.

No, that was setup on fedora as I heard vsftpd may have some issues with 14.04 x64, but I do have it installed on Xubuntu as well.
Using this guide
[http://www.server-world.info/en/note?os=Ubuntu_14.04&p=ftp](http://www.server-world.info/en/note?os=Ubuntu_14.04&p=ftp)

I get errors when  I run the last lines
```
[root@maxwell glen]# initctl restart vsftpd
initctl: Unknown job: vsftpd

```

```
[root@maxwell glen]#  vsftpd start/running, process 1284
500 OOPS: cannot read config file: start/running,
```

And this is what happens when I simply type vsftpd in terminal.
> [root@maxwell glen]# vsftpd
500 OOPS: could not bind listening IPv4 socket
[root@maxwell glen]# 


Oh, boy, networking doesn't seem to be my forte  :P

I'll also provide copy of what I've in my config.

```
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
ascii_upload_enable=YES
ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
#chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
chroot_local_user=YES
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
ls_recurse_enable=YES
#
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=public_html
seccomp_sandbox=NO
```

---

### Post by LastDino on 2014-05-20
I've also tried this config

```
# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
chown_uploads=YES
chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
ascii_upload_enable=YES
ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
#chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
chroot_local_user=YES
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
ls_recurse_enable=YES
#
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=public_html
seccomp_sandbox=NO
ssl_enable=Yes
```

---

### Post by brantcgardner on 2014-05-20
Based on the 'could not bind' message, it looks like your FTP server (or another FTP server) is already running.  Have you tried interactively logging into it?  Try "ftp localhost" from your Trusty box and see if you can get access.

---

### Post by LastDino on 2014-05-21
> **brantcgardner said:**
> Based on the 'could not bind' message, it looks like your FTP server (or another FTP server) is already running.  Have you tried interactively logging into it?  Try "ftp localhost" from your Trusty box and see if you can get access.

```
glen @ maxwell  ~
&#9492;&#9472; $ &#9654; ftp localhost
Connected to localhost.
500 OOPS: vsftpd: cannot locate user specified in 'chown_username':whoever
ftp> 

```

?

---

### Post by brantcgardner on 2014-05-21
[FONT=arial]There is a stanza in your vsftpd config file that looks like this:[/FONT]

```
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
chown_uploads=YES
chown_username=**whoever**

```[FONT=arial]

Could you replace 'whoever' with your own username for testing and then restart vsftpd?

[/FONT]

---

### Post by LastDino on 2014-05-21
> **brantcgardner said:**
> [FONT=arial]There is a stanza in your vsftpd config file that looks like this:[/FONT]

```
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
chown_uploads=YES
chown_username=**whoever**

```[FONT=arial]

Could you replace 'whoever' with your own username for testing and then restart vsftpd?

[/FONT]

Is this what I'm suppose to see?
```
glen @ maxwell  ~
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; $ &#65533;&#65533;&#65533; ftp localhost
Connected to localhost.
220 (vsFTPd 3.0.2)
Name (localhost:glen): 

```

---

### Post by brantcgardner on 2014-05-21
Yes, that's right.  Assuming your configuration is set up for it, you can now use your Trusty login at that point.  The last line of your prompt indicates that the ftp client wants to know who you want to log in as, with the understanding that if you just hit enter it will try to provide the username "glen".

You can also try your Nokia at this point, either without credentials so it can try to anonymously log in, or with a URL like this for passing credentials:  [ftp://username:yourpassword@192.168.1.100](ftp://username:yourpassword@192.168.1.100), or possibly just [ftp://username@192.168.1.100](ftp://username@192.168.1.100) (in the hope that your browser will prompt you for the password).

---

### Post by LastDino on 2014-05-22
> **brantcgardner said:**
> Yes, that's right.  Assuming your configuration is set up for it, you can now use your Trusty login at that point.  The last line of your prompt indicates that the ftp client wants to know who you want to log in as, with the understanding that if you just hit enter it will try to provide the username "glen".

You can also try your Nokia at this point, either without credentials so it can try to anonymously log in, or with a URL like this for passing credentials:  [ftp://username:yourpassword@192.168.1.100](ftp://username:yourpassword@192.168.1.100), or possibly just [ftp://username@192.168.1.100](ftp://username@192.168.1.100) (in the hope that your browser will prompt you for the password).

I tried and it needs to ask my password or something, any ideas?
```
glen @ maxwell  ~
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; $ &#65533;&#65533;&#65533; ftp localhost
Connected to localhost.
220 (vsFTPd 3.0.2)
Name (localhost:glen): 
530 Non-anonymous sessions must use encryption.
Login failed.
421 Service not available, remote server has closed connection
ftp> ^Z
[1]+  Stopped                 ftp localhost
glen @ maxwell  ~
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; $ &#65533;&#65533;&#65533; ftp localhost
Connected to localhost.
220 (vsFTPd 3.0.2)
Name (localhost:glen): glen
530 Non-anonymous sessions must use encryption.
Login failed.
421 Service not available, remote server has closed connection
ftp> ^Z
[2]+  Stopped                 ftp localhost
glen @ maxwell  ~
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; $ &#65533;&#65533;&#65533; ftp localhost
Connected to localhost.
220 (vsFTPd 3.0.2)
Name (localhost:glen): localhost
530 Non-anonymous sessions must use encryption.
Login failed.
421 Service not available, remote server has closed connection
ftp> ^Z
[3]+  Stopped                 ftp localhost
glen @ maxwell  ~
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; $ &#65533;&#65533;&#65533; 

```

---

### Post by brantcgardner on 2014-05-22
Well, I think you're in danger of going down a road you don't need to at this point.  This is vsftpd trying to secure your communications and prevent your password from being stolen.  However, if I understand your project and your configuration, you are only running this to transfer files inside your LAN, and only between two known devices.  So I would suggest you log in anonymously and place only those files you are trying to transfer in the location that anonymous logins can reach.

To login anonymously, you should give the username "anonymous".  If prompted for a password, give your email address.

I believe you can also add:

```
no_anon_password=YES
```

to the config file to skip the password prompt.

---

### Post by LastDino on 2014-05-22
> **brantcgardner said:**
> Well, I think you're in danger of going down a road you don't need to at this point.  This is vsftpd trying to secure your communications and prevent your password from being stolen.  However, if I understand your project and your configuration, you are only running this to transfer files inside your LAN, and only between two known devices.  So I would suggest you log in anonymously and place only those files you are trying to transfer in the location that anonymous logins can reach.

To login anonymously, you should give the username "anonymous".  If prompted for a password, give your email address.

I believe you can also add:

```
no_anon_password=YES
```

to the config file to skip the password prompt.

Will do that, but from where is mail address as password coming into the picture? o-o

---

### Post by brantcgardner on 2014-05-22
That's just customarily how FTP servers have always handled anonymous access.  It's not really the password, it's a way for the FTP server to know who is accessing it (although obviously it's an honor system).

---

### Post by LastDino on 2014-05-23
I think this is going to frustrate you some more, this time when I booted in it started showing me new error. ''connection refused''

I'm not getting the thing I posted last time to see if the changes you suggested work or not ;-;

I've tried playing with other options in that script after that and nothing seems to be working. Maybe right time to throw in towel? hahaha

---

### Post by brantcgardner on 2014-05-23
"Connection refused" sounds to me like vsftpd isn't running now.  It's possible that you don't actually have it set to auto-start on boot.  Try starting it manually and then try logging into it anonymously.

I'd give you the instructions for how to start vsftpd, but I'm not certain how you installed it; if you used the Fedora install instructions, then I have no idea what the proper method is.  For a regular Ubuntu install, I *think* it should be 'sudo service vsftpd start'.

---

### Post by LastDino on 2014-05-23
> **brantcgardner said:**
> "Connection refused" sounds to me like vsftpd isn't running now.  It's possible that you don't actually have it set to auto-start on boot.  Try starting it manually and then try logging into it anonymously.

I'd give you the instructions for how to start vsftpd, but I'm not certain how you installed it; if you used the Fedora install instructions, then I have no idea what the proper method is.  For a regular Ubuntu install, I *think* it should be 'sudo service vsftpd start'.

I installed it using software center. 
```
glen @ maxwell  ~
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; $ &#65533;&#65533;&#65533; sudo ftp localhost
Connected to localhost.
220 (vsFTPd 3.0.2)
Name (localhost:glen): anonymous
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 

```

This is what I see now, I'm assuming it is functioning how it should be now. 
I don't have access to that phone atm but when I do I'll post back to see if it is working ^^

Your patience are commendable ;)

---

### Post by brantcgardner on 2014-05-23
That's a successful login, you should be all set.

Now you just need to put the files you want exposed for access by anonymous FTP clients into the appropriate folder and you should be good to go.  Briefly reading the vsftpd docs, this appears to be /var/ftp.

---

### Post by LastDino on 2014-05-24
> **brantcgardner said:**
> That's a successful login, you should be all set.

Now you just need to put the files you want exposed for access by anonymous FTP clients into the appropriate folder and you should be good to go.  Briefly reading the vsftpd docs, this appears to be /var/ftp.

I don't see any ftp folder in my var. :(

[ATTACH=CONFIG]253409[/ATTACH]

---

### Post by brantcgardner on 2014-05-24
Okay, then in your config file for vsftpd, add (or edit, if already present) this line:

```
anon_root=/some/folder
```

This tells vsftp where to switch to for an anonymous login. So for your purposes you may want:

```
anon_root=/home/glen/anon
```

Or similar.  Make sure the directory you indicate here exists and that the anon user (you, according to your config file) owns it.  In the case of the sample value I just gave you, you would need to do this before restarting vsftpd:

```
mkdir /home/glen/anon
```

Just be careful with this because you can easily expose your whole box to anonymous access if you aren't paying attention.

---

### Post by LastDino on 2014-05-27
Sorry for late reply, but I didn't have access to that phone through out this weekend.
I did the changes you mentioned, but now I get new error
```
glen @ maxwell  ~
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; $ &#65533;&#65533;&#65533; ftp localhost
Connected to localhost.
500 OOPS: vsftpd: cannot locate user specified in 'chown_username':anonymous
ftp> 

```

My config file looks like this if you're interested;
```

# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
chown_uploads=YES
chown_username=anonymous
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
ascii_upload_enable=YES
ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
#chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
chroot_local_user=YES
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
ls_recurse_enable=YES
#
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
local_root=public_html
seccomp_sandbox=NO
ssl_enable=Yes
no_anon_password=YES
anon_root=/home/glen/anon

```

---

### Post by brantcgardner on 2014-05-27
You changed your config file to this:

```
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
chown_uploads=YES
chown_username=anonymous

```

Just undo that change and put your own username for chown_username.  You're getting an error because you told vsftp to change ownership to user 'anonymous', but there is no such user on your system.

---

### Post by LastDino on 2014-05-27
> **brantcgardner said:**
> You changed your config file to this:

```
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
chown_uploads=YES
chown_username=anonymous

```

Just undo that change and put your own username for chown_username.  You're getting an error because you told vsftp to change ownership to user 'anonymous', but there is no such user on your system.

I did try that out and it showed the error message I previously posted 

```

glen @ maxwell  ~
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; $ &#65533;&#65533;&#65533; ftp localhost
Connected to localhost.
220 (vsFTPd 3.0.2)
Name (localhost:glen): glen
530 Non-anonymous sessions must use encryption.
Login failed.
421 Service not available, remote server has closed connection
ftp>

```

Or do I need to type anonymous here without doing any change in config? 
I'll try that and get back to you :3

---

### Post by LastDino on 2014-05-27
Tried by using my username in place of ''anonymous'' in config file and I tried logging in but I got following errors.

```

&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; $ &#65533;&#65533;&#65533; ftp localhost
Connected to localhost.
220 (vsFTPd 3.0.2)
Name (localhost:glen): anonymous
500 OOPS: vsftpd: refusing to run with writable root inside chroot()
Login failed.
421 Service not available, remote server has closed connection
ftp> 

```

And when tried my user name

```

&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; $ &#65533;&#65533;&#65533; ftp localhost
Connected to localhost.
220 (vsFTPd 3.0.2)
Name (localhost:glen): glen
530 Non-anonymous sessions must use encryption.
Login failed.
421 Service not available, remote server has closed connection
ftp> 

```

---

### Post by brantcgardner on 2014-05-27
These are all messages caused by different changes you have been making in the config file.  Going forward, **always** login as "anonymous" and **leave** the chown_username as glen.  This most current error is unrelated to either of those two items.

To fix the 'writable root in chroot' issue, I *think* this command will fix you up:

```
chmod ugo-w /home/glen/anon
```

This is going to complicate things for you later when it comes time to put files in this folder, but we'll cross that bridge when we come to it.

---

### Post by LastDino on 2014-05-27
That worked out.

Here is screen-shot of my browser on PC opening that link

[ATTACH=CONFIG]253498[/ATTACH]

However, when I try to open that link by phone browser, it is giving me error, which is;

```
The server times out
```

Exact address I tried;
```
ftp://anonymous@192.168.1.100
```

Firewall is switched off. Any ideas?

---

### Post by brantcgardner on 2014-05-27
Not really, I would expect that to work.  Do you have any other machines on your local network that you can test with to rule out the server configuration?

If not, does just ```
ftp://192.168.1.100
``` work from the Nokia?

If not, can you see if ufw is running on your Trusty box?  Use this command:  ```
sudo ufw status
```

Hmm... :-s

---

