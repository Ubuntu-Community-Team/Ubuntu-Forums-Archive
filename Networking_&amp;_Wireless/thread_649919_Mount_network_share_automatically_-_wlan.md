---
title: "Mount network share automatically - wlan"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by fuchik1979 on 2007-12-25
Hi all,

I've found these forums a great help in getting my latest attempt to switch to ubuntu to be a painless one. Now I have a question.

I have a server running windows xp that shares to my media centre and desktop (ubuntu). I have managed mount a share from this server. Only 1 problem.

When I reset the computer the share mount isn't available. I need to remount before it comes up. I assume this is because of the time it takes the wlan (static settings) to negotiate its connection. If I run "sudo mount -a" immediately upon logging in then the mount pops up straight away.

There is a guide to using a method to automatically un/mount network shares but the server is never unavailable so this method seems a bit of overkill to me.

All I need is a way to run the mount -a command after the wlan has been activated.


Help me ubuntu-ones, you're my only hope.

PS. is wireless bridging something we can expect in the future? I can't even get it to work using ndiswrapper

---

### Post by danwood76 on 2007-12-25
you could try adding the line 'mount -a' to the /etc/rc.local file.
This script executes at the end of each runlevel init, so it may execute after your wireless is up.

regards,
Danny

---

### Post by fuchik1979 on 2007-12-25
Already tried that. Didn't work.

Also tried adding the line to the end of the /etc/network/interfaces that didn't work either. Mind you that was a complete stab in the dark.

---

### Post by danwood76 on 2007-12-26
you could setup a bash script that is run on startup that delays running mount -a for however long it takes for your wireless to get connected.

I have no clue about scripting im afraid so I cant really help, but im sure there are many guides online that can help.

good luck,
Danny

---

### Post by santosh_gr on 2007-12-26
Normally your /etc/network/interfaces file would be like.
-----------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
     address 192.168.0.2
     netmask 255.255.255.0
     gateway 192.168.0.1
-------------------------

Add another line to /etc/network/interfaces files as show below using the post-up command.  You need to replace <script-name> with a bash script which will execute "mount -a" command.  Make sure you give execute permissions to the script before running it.

Test using /etc/init.d/networking restart

--------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
# The primary network interface
auto eth0
iface eth0 inet static
     address 192.168.0.2
     netmask 255.255.255.0
     gateway 192.168.0.1
     post-up /etc/network/if-up.d/<scripts-name>

--------------------------

---

