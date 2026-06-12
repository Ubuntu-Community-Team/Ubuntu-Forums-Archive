---
title: "Intel 3945 ABG wireless card - not working?"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Everywhere_at_Once on 2008-05-19
I would like to get some information from anybody here who knows what the issue is with this card/the iwl3945 driver, or any info on when to expect a fix, where to look. 

If you're having problems with it [COLOR="Red"]AFTER[/COLOR] upgrading to hardy, then feel free to sound off. I'd like to know that i'm not the only one without wireless around here. *Hopefully* i'm the only one without ethernet either...:mad:

---

### Post by chili555 on 2008-05-19
There is evidently a better iwl3945 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```After I installed this, mine works perfectly.

---

### Post by Tulsapoke on 2008-05-19
Yea, this backport fix was out the first week after Hardy was released.  I have been running my Intel PRO/Wireless 3945ABG trouble free since then.

---

### Post by putt1ck on 2008-05-20
Mine is still problematic (Samsung X60, Kubuntu 8.04). Symptoms are difficulty connecting and once connected very variable performance (pings of 6ms to 8000ms!). Signal strength seems constant as per KNetworkManager graphical view. 

Various other laptops in the household, including others running 8.04 perform fine, as did this laptop with 7.10 (clean built as 8.04, not an upgrade).

Another issue which may or may not be related but is really, really annoying given the problems with wireless is that the onboard Ethernet also does not work - it loads the e1000 driver but never creates a network interface. Get this in the log:

probe of 0000:02:00.0 failed with error -5

Any ideas for solving one or both of these problems fixed welcome. Is driving me mad...

---

### Post by kmads on 2008-05-20
It doesn't make any difference. Do I have to do something after installing linux-backports-modules-hardy-generic?

Best regards,
Mads
--
Fujitsu Siemens AmiloPro v3505 laptop

---

### Post by harryman01 on 2008-05-20
I got  Wireless intel pro 3945abg with Hardy, also, and so far as I can see, I'm unable to list the AP, or authenticate to them.

I also notice that mi wifi was called eth1, instead of wlan ( already fixed) but I see a wmaster0 interface, no idea why?

and the avahi keeps assigning an IP address.

any advise


Thanks

---

### Post by Everywhere_at_Once on 2008-05-21
Yeah, i have backports installed, but no wireless interface showing up in network manager.

is there something that has to be done after backports are installed? (even though backports have been installed since upgrade to hardy...)

---

### Post by chili555 on 2008-05-21
> is there something that has to be done after backports are installed?Nope. I actually think it's a Network Manager problem. Anyone game to uninstall Network Manager and dhcdbd? I use Wicd instead. [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

By the way, in order to get wireless working, you must detach the ethernet cable, if you have one, and let your wired interface down gently:```
sudo ifdown eth0
```

---

### Post by chili555 on 2008-05-23
@Everywhere-

You will not connect with the wired connected and with an IP address. Please detach the wire and do:```
sudo ifdown eth0
sudo modprobe iwl3945
sudo lshw -C network
```Does your wireless interface show up now?

---

