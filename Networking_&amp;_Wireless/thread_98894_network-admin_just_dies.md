---
title: "network-admin just dies"
date: 2005-12-04
forum: Networking &amp; Wireless
---

### Post by xenmax on 2005-12-04
Hello there,
I am new here. I know my way around linux (or can find it with some help :) ). I just installed breezy yesterday. I am trying to connect to the internet, but with little success. I have a DSL connection through a router.

I picked up a few instructions from some forum and did the foll:
1. Logged in as root: su root
 a. ifconfig -a eth0 192.168.1.2 netmask 255.255.255.0
 b. route add default gw 192.168.1.1(addr of my router)

2. I pinged the gw - ping 192.168.1.1 and it worked fine. Overjoyed, i tried the next step - specifying IP addrs for DNS, since when i am stuck. The instructions read "type netconf" - i did that and discover unbuntu has no tool called netconf.  I went back to net via my Windoze and did some searching to find out I can use "System -> Administration -> Networking" in Ubuntu

So, i click on "System -> Administration -> Networking" and it asks me for a password - I enter the root password and it growls. So, i click again and try my user password - no growling this time, but no NOTHING. I wait and wait, and nothing happens.

I did more searching and tried BOOT option "acpi=off" in /boot/grub/menu.lst, but no good.

I love this OS, but am so frustrated not being able to log onto the net. I could be totally wrong on this, but I figure this is not related to  detecting my eth card or having proper driver for it  since i can ping my router and i see leds on router switching while i do that. It must be related to configuring the internet settings?

So, can someone plz help me how i can setup my internet connection?

---

### Post by xenmax on 2005-12-05
To answer my own question, I looked for the file /etc/resolv.conf - which did not exist. So, i created one and entered "nameserver dnsAddr" and it worked!!

I am replying to this post from Ubuntu. I notice that the ifconfig setting i set were not stored from last time i re-booted. Is there any file I can edit for that too??

---

### Post by mpvano on 2005-12-05
Apparently the network control panel in Gnome (it's apparently not really part of the OS, or of Ubuntu) doesn't always interact properly with the underlying network and hotplugging script system that's part of Debian.

If you're having trouble, one thing you can do is what you've already started to do - ignore the Gnome applets and interact directly with the OS.

The overall networking configuration is controlled by the ifup and ifdown scripting system. It's principal configuration file is "/etc/network/interfaces". Try reading the man pages (by using the "man interfaces" and "man ifup" commands).

Using sudo, you can directly edit "/etc/network/interfaces" to control start up of each interface, including it's address setting, wireless options, dns configuration, etc. You can even directly issue shell commands to copy custom hosts files, etc.

The "interfaces" file operation is a little confusing, so don't try to do anything too complicated with it. Remember its contents are not read until the next time something triggers ifup or ifdown on the interface in question.

The only precaution is to not run any other configuration system (like the Gnome network applets) once you start editing "interfaces" directly, because they might clobber your changes. It's a good idea to back up your "interfaces" file, once you've got it the way you like it.

If you look around in this forum you'll find several examples of solving problems this way.

hope this helps,

Mario

---

### Post by xenmax on 2006-01-10
thanks for the reply!
sorry for the delay... i have been busy lately and did not log into forums for weeks....

actually the problem was solved when i was able to launch network-admin for a terminal and configure the settings. From then on, it remembers all the settings and i can just boot and log onto the net.

The only problem is that i cant invoke any of "Administration" tools from GUI - using mouse click. I always need to invoke them from cmd-line logged in as root - but that is another problem... :)

---

### Post by xenmax on 2006-03-20
Just updating this thread incase anyone comes across this. The problems regarding launching Administration apps is now gone - refer to this thread: [http://www.ubuntuforums.org/showthread.php?t=146859](http://www.ubuntuforums.org/showthread.php?t=146859)

---

