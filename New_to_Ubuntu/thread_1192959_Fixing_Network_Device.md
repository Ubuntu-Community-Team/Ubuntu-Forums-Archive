---
title: "Fixing Network Device"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by faintscrawl on 2009-06-20
Yesterday I was having some trouble setting up my modem with ubuntu. I wanted to take my router out of the set-up to see if it was the cause of some recent problems. In the end I was able to set up the modem and I did discover that my problem was my router. However, when I was fooling around I had the terminal open and was trying to do some configuring suggested somewhere on a support page. It did't appear to do anything. Today, though, when I turned my computer off and then later back on something was very wrong. The computer would not connect to the modem or the router (I tried both setups) and when I click on the network manager it says "device not managed", which is something I've never seen before. I think I must have turned something off when I was fooling around yesterday but I have no idea what or how to turn it back on. Any help would be much appreciated. (I'm obviously sending this from another computer because mine has no access to internet.) THanks.

---

### Post by faintscrawl on 2009-06-20
I've been reading and I think I need to edit the nm-system-settings.conf file in etc/NetworkManager but it won't let me resave it. How can I modify this file?

---

### Post by nandemonai on 2009-06-20
You'll need to edit the file as root in order to be able to save.

Press F2 to bring up a run dialogue then type:

```
gksu gedit /full/path/to/file
```

For example /etc/NetworkManager/nm-system-settings.conf

The one time I've seen NM say that is when I manually setup networking in /etc/network/interfaces (Jaunty) so you may want to look there also if your issue isn't with the nm-system-settings.conf file.

---

### Post by faintscrawl on 2009-06-21
THanks! I decided to look at the interfaces first. Here is what it says:


auto lo
iface lo inet loopback

iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual
--

Is there anything there that looks like it might disturb Network Manager, turning it off, etc? If I had to guess I'd say it might be the last line.

Thanks.

---

### Post by faintscrawl on 2009-06-21
JUst to try something until someone can tell if there's any problem with what I found in interfaces, I made the change to nm-system-settings.conf. 

It used to say:
managed=false

But I changed it to "true".

Maybe I shouldn't have? Anyhow it didn't help.

---

### Post by LewRockwell on 2009-06-21
this post is more for future readers of this thread that those currently posting

that being said, I routinely caution others against continuing on with a compromised system where UNKNOWN alterations may have inadvertedly occurred

save/back-up/clone what you want to keep and re-install after wiping the drive and/or partition

this will save you from the uncertainty of an unknown deficiency which may very well cause you further difficulties in the future

as always, buyer be aware, beware, and your mileage may vary

---

### Post by faintscrawl on 2009-06-21
Update:

Network Manager stopped running altogher. It doesn't appear at the top of the screen nor under System-->admin.

So I tried using pppoeconf and finally got a connection. Yay!

However, I'd like to get network manager working. Any advice?

---

### Post by faintscrawl on 2009-06-21
I got a connection working through using pppoe, working around network manager.

I uninstalled and reinstalled Network Manager and rebooted. It once again appeared on my desktop. (It had disappeared before.) But it still says "device not managed". So even though I have a connection I would still like to get Network Manager working.

---

### Post by nandemonai on 2009-06-21
The NM settings conf file on my machine is false for the managed section, not sure what that actually does.

If you want NM managing the connection you need to remove the /etc/network/interfaces file altogether.

Remove / backup the file:

```
sudo mv /etc/network/interfaces /etc/network/interfaces.bak
```

Restart networking:

```
sudo /etc/init.d/networking restart
```

Relog to reset network manager? Maybe reboot. Logging out and in again should do it though.

---

### Post by faintscrawl on 2009-06-21
Thanks. I tried it. This is what I got:


tom@Franz:~$ sudo mv /etc/network/interfaces /etc/network/interfaces.bak
[sudo] password for tom: 
tom@Franz:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          ifdown: couldn't read interfaces file "/etc/network/interfaces"
ifup: couldn't read interfaces file "/etc/network/interfaces"
                                                                         [fail]
tom@Franz:~$

---

### Post by faintscrawl on 2009-06-21
--deleted--

---

### Post by faintscrawl on 2009-06-21
So I put "interfaces" back and then tried networking restart. This is what I got:


tom@Franz:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
 * if-up.d/mountnfs[dsl-provider]: waiting for interface eth0 before doing NFS mounts
                                                                         [ OK ]
tom@Franz:~$

Network Manager stills says "device not managed"

---

### Post by faintscrawl on 2009-06-21
Just to explain for others who stumble onto this thread how it all got resolved:

My etc/network/interfaces  looked like:

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual


After doing Google searches, I tried this:

gksu gedit etc/network/interfaces

Then I was able to edit the file. I deleted all but the first two lines, which are:
auto lo
iface lo inet loopback

Then I hit save. I closed everything and rebooted. After that Network Manager was working again. I did have to add my dls connection by right-clicking on the applet.

Whew.

---

