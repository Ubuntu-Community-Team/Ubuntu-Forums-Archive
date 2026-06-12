---
title: "Wireless network has stopped working."
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by Eax.exe on 2008-02-15
Hello :)

I have a Atheros AR5007EG wireless network card, that after the Linux Kernel update (yesterday) stopped working, completely.
I'm using Feisty (7.04) as Gutsy (7.10) won't work on this laptop :(

I have used both this guide:
[http://ubuntuforums.org/showthread.php?t=662877&highlight=Atheros](http://ubuntuforums.org/showthread.php?t=662877&highlight=Atheros)

And this guide:
[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

To try making it work. Neither does.

I have reinstalled Network-manager and Network-manager gnome.

I'm 100% sure there is Wireless internet as I can see the router.

Another weird thing is that my network monitor sometimes (when I'm NOT on a wired network) shows some activity :S

Can anyone help me repairing this? Please?:)

Thanks a lot in advance :D

---

### Post by jeffus_il on 2008-02-15
Use the Restricted Driver Manager in the System Menu to see it the Atheros driver is enabled.

---

### Post by Eax.exe on 2008-02-15
It's not.

It has been though.

How do I make it appear again?

Thanks :)
And thanks for the quick answer :)

---

### Post by Eax.exe on 2008-02-15
Can anyone PLEASE help me? :)

---

### Post by Eax.exe on 2008-02-15
Please, anyone? I'm really desperate.
I seriously need to use this computers wireless internet :s

PLEASE help :)

---

### Post by Eax.exe on 2008-02-16
Please? Anyone? I really need help :) I'm desperate!
Someone must know what to do?

---

### Post by Eax.exe on 2008-02-16
Please anyone! I really have NO idea what to do. Can anyone help?

---

### Post by oellegaard on 2008-02-17
I can confirm the problem!

Maybe it's because of a recent update??

To ensure we have the same problem:

Suddenly i had no internet
I restarted
I can't see the the networkcard anymore
my ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:1A:92:AA:AD:93  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:feaa:ad93/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1299 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:942234 (920.1 KB)  TX bytes:221262 (216.0 KB)
          Interrupt:16 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5248 (5.1 KB)  TX bytes:5248 (5.1 KB)

vmnet2    Link encap:Ethernet  HWaddr 00:50:56:C0:00:02  
          inet addr:172.16.24.1  Bcast:172.16.24.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:172.16.125.1  Bcast:172.16.125.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


i tried to reinstall madwifi drivers, without any result

Regards
Kristian

---

### Post by oellegaard on 2008-02-17
I think i received this update yesterday:

Non-free Linux 2.6.22 modules on x86/x86_64 
This package provides restricted modules for Linux version 2.6.22 on
x86/x86_64.

Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
 - fcdsl, fcdslusba, fcusb, fwlanusb, fxusb (AVM ISDN x86 only)

These modules are "restricted" because they are not available under a
completely Free licence.

Can this have anything to do with it? The strange thing is, that it worked until something like an hour ago, where i restarted my computer (its possible that its the first time since i installed the update)

---

### Post by uberlube on 2008-02-17
Did you have to do any tweaking in the first place to get your driver working? If so you probably had to blacklist the restricted drivers and install them using ndiswrapper?  If so then the blacklisted ones were bypassed when you booted up and you were using the ones that you installed yourself. Just blacklist them and use ndiswrapper again to reinstall them. Im just speculating here, stop me if im wrong.

---

### Post by oellegaard on 2008-02-17
> **uberlube said:**
> Did you have to do any tweaking in the first place to get your driver working? If so you probably had to blacklist the restricted drivers and install them using ndiswrapper?  If so then the blacklisted ones were bypassed when you booted up and you were using the ones that you installed yourself. Just blacklist them and use ndiswrapper again to reinstall them. Im just speculating here, stop me if im wrong.

I didn't install ndiswrapper at first place, just updated using the newest wifidrivers from the website, and then just "make" and "make install", which i've done agian, without any result :(

---

### Post by littletinman on 2008-02-17
i'm having the same issue. I cans ee the modem but it wont connect. So i tried wicd and now i don't have lan. Uhhhhh, need help!!!!

---

### Post by Eax.exe on 2008-02-18
> **uberlube said:**
> Did you have to do any tweaking in the first place to get your driver working? If so you probably had to blacklist the restricted drivers and install them using ndiswrapper?  If so then the blacklisted ones were bypassed when you booted up and you were using the ones that you installed yourself. Just blacklist them and use ndiswrapper again to reinstall them. Im just speculating here, stop me if im wrong.

Yes I blacklisted ath_pci :( How do I unblacklist it? :)
Thanks in advance :D

---

### Post by Eax.exe on 2008-02-20
Somehow, it unblacklisted itself O.o

It's still not working though :(

Any help anyone?

---

### Post by oellegaard on 2008-02-20
Ok, i mangaged to get things runnning

I uninstalled this:

Non-free Linux 2.6.22 modules on x86/x86_64
This package provides restricted modules for Linux version 2.6.22 on
x86/x86_64.

Currently the following modules are included:
- madwifi (Atheros)
- fglrx (ATI)
- nvidia
- fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcpci (AVM ISDN)
- fcdsl, fcdslusba, fcusb, fwlanusb, fxusb (AVM ISDN x86 only)

These modules are "restricted" because they are not available under a
completely Free licence.

Afterwards, i removew madwifi-tools

Then i downloaded the newest source for madwifi, and compiled it with success, and after a restart it worked like a charm

Regards
Kristian

---

### Post by Eax.exe on 2008-02-20
Thanks a lot Kristian :)

I WILL do that NOW :D

But! With the guide I originally followed for MadWifi it had my drivers in it to. Do do I insert them in the new compile?

---

### Post by oellegaard on 2008-02-20
Np, i used this guide: [http://ubuntuforums.org/showthread.php?t=75451](http://ubuntuforums.org/showthread.php?t=75451)

Those simple steps got me running :-) I got an AR5007EG

Regards
Kristian

---

### Post by Eax.exe on 2008-02-20
Great :D Thanks a hell of a lot ^^

Nice to see a fellow dane :D

Regards
Eax

---

### Post by Eax.exe on 2008-02-20
I did as the guide told me but it's still not working :(

It can't even see that I have a wireless card anymore (when I try to click Networks it only shows wired/Manual Configuration). However it is on the Restricted Drivers List :confused:

Anyone got any ideas?

---

### Post by formol on 2008-02-20
hi, 

you may find your answer there:  [http://ubuntuforums.org/showthread.php?p=4364840](http://ubuntuforums.org/showthread.php?p=4364840)

whar did, and it work for him:

sudo modprobe ath_pci
sudo ifconfig wifi0 down
sudo ifconfig wifi0 up

---------------------------

for me, using, ndiswrapper, i don't know what to know.  i never be able to make it work with madwifi.  (i just didn't install the kernel update now because i did it 2 or 3 weeks ago and you know the result, no wifi at reboot...  i had no time to debug it, i just re-installed ubuntu, update and re-install tndiswrapper.  but i'm still searching for a futur solution...)

to install this wifi card with ndiswrapper : see last post on [http://ubuntuforums.org/showthread.php?t=527619&page=4](http://ubuntuforums.org/showthread.php?t=527619&page=4) , thx to bmartin.

---

### Post by Eax.exe on 2008-02-22
Didn't work :(

It can't even see the wireless interface :(

---

### Post by WastingBody on 2008-03-23
When you boot go into grub and pick the old kernel, not the updated one. My wireless quit working after the update too. I would like a fix, but I'm fine with using an older kernel for now.

---

