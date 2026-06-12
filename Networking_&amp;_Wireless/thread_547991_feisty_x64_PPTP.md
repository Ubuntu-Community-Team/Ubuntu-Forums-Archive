---
title: "feisty x64 PPTP"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by coloured on 2007-09-10
Hi, just wondering what is the right way to get PPTP VPN tunnels configured under Feisty x64?

I know there is a thread in tutorials and tips - but it has been there for a while, so may be out-dated.

I have installed the following packages through Synaptic:
network-manager-pptp
pptp-linux
pptpd
bcrelay

I have configured my VPN connections through the gui using network-manager (great program)
When I try to connect a VPN, I am presented with the Authentication box, where I type in the username and password and then click OK. 
After that the box disappears and nothing ever happens.

Whats going on? This worked great under opensuse.
I am running gnome.

Here is my sources.list

Please help if you can
Jurgen

> # Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb [http://seveas.theplayboymansion.net/seveas](http://seveas.theplayboymansion.net/seveas) feisty-seveas all 

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse 

# Upstream Wine
# GPG key: 387EE263
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main 

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

## Repos for avant window navigator
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator

## Repos for screenlets
deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets
deb-src [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets

---

### Post by coloured on 2007-09-10
I did a bit more poking around, this is what syslog has to say once I have tried to connect... no sure what it means though. Maybe someone could shed some light?

> jbaier@jbaier-fiesty:/$ sudo tail -f /var/log/syslog
Sep 11 10:30:49 jbaier-fiesty gconfd (root-28303): GConf server is not in use, shutting down.
Sep 11 10:30:49 jbaier-fiesty gconfd (root-28303): Exiting
Sep 11 10:35:16 jbaier-fiesty NetworkManager: <debug info>^I[1189463716.148294] nm_dbus_signal_filter (): NetworkManagerInfo triggered update of VPN connection 'First Mobile' 
Sep 11 10:35:16 jbaier-fiesty NetworkManager: <debug info>^I[1189463716.149188] nm_dbus_signal_filter (): NetworkManagerInfo triggered update of VPN connection 'First Mobile' 
Sep 11 10:35:23 jbaier-fiesty kernel: [ 9158.756731] nm-ppp-auth-dia[28511]: segfault at 0000000000000088 rip 00002b282322321b rsp 00007fff8d41cd20 error 4
Sep 11 10:35:56 jbaier-fiesty kernel: [ 9191.685942] nm-ppp-auth-dia[28525]: segfault at 0000000000000088 rip 00002b2c3f21421b rsp 00007fff7142bd30 error 4
Sep 11 11:01:42 jbaier-fiesty -- MARK --
Sep 11 11:10:32 jbaier-fiesty kernel: [11266.721860] nm-ppp-auth-dia[29497]: segfault at 0000000000000088 rip 00002af0e56b721b rsp 00007fffcaf87890 error 4
Sep 11 11:17:01 jbaier-fiesty /USR/SBIN/CRON[29689]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 11:17:16 jbaier-fiesty kernel: [11670.183264] nm-ppp-auth-dia[29697]: segfault at 0000000000000088 rip 00002b3bb738e21b rsp 00007ffff92b1bb0 error 4


---

### Post by coloured on 2007-09-10
just an update - found this bug report [=https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/125886](=https://bugs.launchpad.net/ubuntu/+source/network-manager-pptp/+bug/125886)

Is there anyway I can install the Gutsy package? VPN's are very important to my work - I connect to multiple VPN's and doing it the manual way just doesnt cut it.

looking here [=http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/](=http://ftp.gnome.org/pub/GNOME/sources/NetworkManager/0.6/) there appears to be a version of NM later than that which I am currently running (im using 0.6.4-6ubuntu7)
0.6.5

Can I install this? - even better is there a ubuntu package somewhere? (a development repo somewhere?)

I have found this [="http://packages.ubuntu.com/gutsy/net/network-manager-pptp"](="http://packages.ubuntu.com/gutsy/net/network-manager-pptp") - you will have to forgive me I am a new user to Ubuntu.

all of this may seem quite confusing to you - so I will put it simply. It looks to me that there are later versions of network manager and its friends, is there a repo I can add just to update this? (I know its going to want dependencies :) )

cheers
Jurgen

---

### Post by coloured on 2007-09-10
here [="http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](="http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/) is a repo I found - but the packages for 0.6.5 look to be for ubuntu10 (gutsy)

I really want to update :)

ooooh look what I found  - [="http://craig.dubculture.co.nz/blog/category/pptp/"](="http://craig.dubculture.co.nz/blog/category/pptp/")
Craig has built some packages that should fix the problem I am having. What do you guys think??? should I install these or build my own?

btw - I have never built my own ubuntu packages - should I follow craigs guide on that page I linked? or how do I go about it? - how do I find out where the svn/cvs is?

Jurgen

---

### Post by coloured on 2007-09-10
I can confirm that the package provided by Craig works 100%! good job Craig and thanks man!!

I think my next step is to learn how to build packages in ubuntu.
I want to be able to help out just the same way Craig has helped me.

The linux community rocks!

Jurgen

---

