---
title: "Networking woes (can't reconnect without restart)"
date: 2005-09-11
forum: Networking &amp; Wireless
---

### Post by Strife on 2005-09-11
I have a Dell Inspiron 6000, and I've been having very strange networking issues for quite some time. I've posted previously about not being able to switch from the wireless interface to the wired interface without restarting, but this was never resolved.

I recently got a wireless router of my own, which means I have been connecting to a secured wireless network for the first time since I got this laptop. Now I have weird issues where it refuses to connect to a network (whether mine or an open one) at seemingly random intervals. This seems to occur most often when I try to use a wifi managing app, such as WiFi Radar (which doesn't work at all for me), gtkwifi (hardly works) or netapplet (works some of the time).

Most recently, I went from my home network to the campus non-WEPed network. Since I hadn't changed /etc/network/interfaces to reflect that I don't want to connect to my local network, it obviously didn't connect to any network. But then when I tried ot set the ESSID to 'utexas,' it would not connect until I restarted. Running /etc/init.d/networking restart didn't work, nor did manually running ifup eth1 or dhclient eth1, etc.

I'm completely stumped, and this is getting very frusterating, because I don't want to have to manually change things AND restart every time I change networks. Any ideas as to what the problem is?

---

### Post by Strife on 2005-09-14
No ideas?

---

### Post by heimo on 2005-09-14
Well, not much ideas here, but maybe you could try this next time: dhclient -r (release dhcp lease) and restart networking. :-/ I'm not too hopeful, maybe others with more experience with wireless could suggest something?

---

### Post by rob.fender on 2005-09-14
Hi - was a solution for this ever found ? I have what I think is the same problem..:

I use two wireless networks, one at home and one at the office, and have a network profiles set up for each. When I've been using the machine at home and then go to the office, I simply have  to bring up networking, switch the profile to office, wait a couple of min and bingo. However, when going the other way I have to switch the profile and then reboot the machine. Also, sometimes the network drops out at home and again I need to reboot the machine. I have tried 'netrestart' plus all the ifdown etc stuff and can not get past this... ridiculous that I have to reboot to restart network services. Not a disaster, but annoying and presumably simple to solve.... ? hopefully ... ?

thanks in advance,
R

---

### Post by Strife on 2005-09-14
I've tried releasing the IP address. Also, I had basically this same problem earlier when trying to switch from the wireless to wired interface (or vice versa). It seems that there's something rotten in the state of how networking is handled... I'm just not sure what...

---

### Post by mlomker on 2005-09-15
Hmm.  I've never had these issues but none of the access points that I use have WEP/WPA enabled...I wonder if that's a part of the equation?  I also don't use any graphical tools to change my configuration (they send commands in a hidden manner and who knows what they are doing).

I use a combination of wpasupplicant, ifplugd, and resolvconf.  The whole setup works quite well but it's all command-line.

What network driver are you using?  Ndiswrapper or a native driver?  Are you booting/shutting down your machines at each location or are you trying to use suspend/hiberate?

---

### Post by Strife on 2005-09-15
As for the driver, it's the ipw2200 (or whatever it's called... The latest generation of Centrino, basically). I am not suspending/hibernating, mainly because I never got these to work (and also, I tend to not be the type of person that only opens his laptop to check email then close it again, so I don't really have much use for suspend, really).

Also, the encryption/no encryption problem is relatively irrelevent, considering that I can't even change interfaces without rebooting. I tend to be able to switch which wireless network I am using without any problems (regardless of encryption or lack thereof), but every once in a while, it refuses to actually do anything unless I restart.

I can try to do everything on the command line, or I can do it via graphical tools, but the result is always the same.

---

### Post by rob.fender on 2005-09-15
Hi - both networks currently have WEP enabled, but in fact I had the same problem when my home network was unprotected. The machine is shut off between sites, not suspended (which doesn't work properly on my little VAIO T2, but not important), but as I say it also happens if my wireless signal temporarily drops out at home. I have also tried a combination of dhcp -r and then network restart, plus a load of command line stuff, and it doesn't work. Its very odd that it causes a problem going work -> home but not the other way round..! all I want to be able to do is completely shut down wireless/all networking and then restart.

As an aside, I do find it bad design that the networking GUI splits up the bits of your profiles across several different files, instead of having a single file for each profile which you could tweak like ifcfg files.

ta!
Rob

---

### Post by firecat53 on 2005-09-15
Another suggestion: try using rmmod or modprobe -r to remove your wireless driver modules, and then reload them. I've had to do this with my sound card at times to restart sound, and occasionally I have to unplug my PCMCIA wireless card and plug it back it (basically accomplishes the same thing, I think) to keep things working. 

Good luck!  Scott

---

### Post by Strife on 2005-09-16
While that should work, that's really a pain in the ass. There has to be some explanation to why this is happening to begin with.

If I can't find a solution any time soon, I'm probably going to have to either try completely reinstalling Ubuntu, or, heaven forbid, use another distro in hopes that that will fix the problem.

Does no one else have this problem or know how to solve it???

---

### Post by flyingman on 2005-09-18
I am having the exact same issue with my Intel PRO/Wireless 2200 on my Dell Inspiron 9300. After a while, I am disconnected and I have to go in the Network tool under System Administration to deactivate it an activate it. As long as I keep this network window open I am connected. But once I hit OK to make the window go away, I am disconnected from the net.

Once in a while (rarely), I have to do a whole reboot just to get my wireless to work at all!

Perhaps there is a bug with the implementation of IPW2200 or perhaps the firmware that was automatically installed when I installed Ubuntu??

---

### Post by mlomker on 2005-09-18
[QUOTE=flyingman]Perhaps there is a bug with the implementation of IPW2200 or perhaps the firmware that was automatically installed when I installed Ubuntu??[/QUOTE]

There are bugs even in the latest version of the firmware.  If you do a **dmesg | tail** when you're having trouble you might see some error messages about the firmware restarting.

I'd recommend [installing](http://www.ubuntuforums.org/showpost.php?p=338666&postcount=16)  the latest versions, though, if you haven't already.

---

### Post by foxy123 on 2005-09-30
I've got a similar problem with my broadcom chip card. I use it ndiswrapper. The thing is that I have no problem at home, but it takes 10-15 min to hook up on the wireless network at work. Firstly I have to change the profile, which takes several minutes. Then I have to reboot. I wonder why it is not possible to change to do it on fly...

Neither of wifi managers works for me. KWiFiManager and GTKWiFi say that my card does not support scanning, while WiFi Radar shows networks but does not do anything to connect. Recently I have spent half a hour trying to configure it...

---

### Post by mlomker on 2005-09-30
>  I wonder why it is not possible to change to do it on fly...
Neither of wifi managers works for me.

I've never used the graphical tools for anything other than a signal strength indicator.  If your links are encrypted then you should configure wpa_supplicant.  If your connections are not then you could automate things using whereami.

[URL="http://www.ubuntuforums.org/showpost.php?p=368604&postcount=4"]
A post[/URL] I made about a part of my config.

Here's one that touches on [wpa_supplicant]("http://www.ubuntuforums.org/showthread.php?t=26623") (ignore the ipw2200 stuff).

[Whereami.]("http://www.ubuntuforums.org/showthread.php?t=44219")

---

### Post by foxy123 on 2005-10-01
[QUOTE=mlomker]I've never used the graphical tools for anything other than a signal strength indicator.  If your links are encrypted then you should configure wpa_supplicant.  If your connections are not then you could automate things using whereami.
[URL="http://www.ubuntuforums.org/showpost.php?p=368604&postcount=4"]
A post[/URL] I made about a part of my config.
Here's one that touches on [wpa_supplicant]("http://www.ubuntuforums.org/showthread.php?t=26623") (ignore the ipw2200 stuff).
[Whereami.]("http://www.ubuntuforums.org/showthread.php?t=44219")[/QUOTE]
thanks for the links. Something I do not understand though.

As I've already said I've got a laptop with wireless Belkin PCMCIA card, based on Broadcom chip. The laptop also has a Ethernet network port. At home I've got a wireless ADSL router and a desktop with wireless access point. The router uses encryption to make the network secure. So to commect to the network and Internet I use either Ethernet cable (if I'm upstairs) or wireless card (if I'm downstairs). I have no problem with switching between wired and wireless at home (though I have to reboot if I want to change from wired to wireless).

The problem occurs somewhere else. I can be at client site and want to use its wireless network. What I want is to boot up my laptop, choose the network and connect to it without using the Gnome Networking, since it takes ages to change anything there. COmmand line solution is ok for me as it takes usually less time than GUI, though GUI is sometimes more convenient.

Sorry for the prolonged explanation, but I just want to make sure that I will be doing the right thing following the links... I mean I do not understand whereami thing. What is it for? I mean I have no problem with booting up my laptop at home with cable or wireless card, it hooks up on the network. If I do not know anything about external network, which can be nw every time, should I bother about whereami? And so on... I am still a complete newbie in networking, sorry...

---

### Post by mlomker on 2005-10-01
>  (though I have to reboot if I want to change from wired to wireless).

That shouldn't be necessary unless there is something wrong with your machine or setup.  Although I don't have to use ndiswrapper, so that could be a factor for you.

> The problem occurs somewhere else. I can be at client site and want to use its wireless network. What I want is to boot up my laptop, choose the network and connect to it without using the Gnome Networking, since it takes ages to change anything there. COmmand line solution is ok for me as it takes usually less time than GUI, though GUI is sometimes more convenient.

If varies depending upon encryption and whatnot.  If the LAN uses WPA then you have pretty much have to use wpa_supplicant.  wpa_supplicant is just a deamon that looks at a configuration file and watches for access point names...when it finds one that it is configured for then it does the first three lines (below) and a few others for you.

```

sudo iwlist wlan0 scan #lists access point essid's within range
sudo iwconfig wlan0 essid *myAP* #set access point name
sudo iwconfig wlan0 key xxxxxxxxxx #if it uses WEP
sudo dhclient wlan0 #grab a tcp/ip address from dhcp

```

**iwconfig** will tell you what access point the system automatically connected to.  Your machine will automatically attach to the strongest signal.  If it's the correct one then just do the **dhclient** command and you're done.

> If I do not know anything about external network, which can be nw every time, should I bother about whereami? 

Whereami is just a way to script things.  You create rules like: if I don't recognize this network then it's probably an open access point and you should execute this set of commands.  If you want to manually type them in then that's the same thing.

---

### Post by foxy123 on 2005-10-01
[QUOTE=mlomker]That shouldn't be necessary unless there is something wrong with your machine or setup.  Although I don't have to use ndiswrapper, so that could be a factor for you.



If varies depending upon encryption and whatnot.  If the LAN uses WPA then you have pretty much have to use wpa_supplicant.  wpa_supplicant is just a deamon that looks at a configuration file and watches for access point names...when it finds one that it is configured for then it does the first three lines (below) and a few others for you.

```

sudo iwlist wlan0 scan #lists access point essid's within range
sudo iwconfig wlan0 essid #access point name
sudo iwconfig wlan0 key xxxxxxxxxx #if it uses WEP
sudho dhclient wlan0 #grab a tcp/ip address from dhcp

```

**iwconfig** will tell you what access point the system automatically connected to.  Your machine will automatically attach to the strongest signal.  If it's the correct one then just to the **dhclient** command and you're done.



Whereami is just a way to script things.  You create rules like: if I don't recognize this network then it's probably an open access point and you should execute this set of commands.  If you want to manually type them in then that's the same thing.[/QUOTE]
thanks a lot for the explanation. It makes it easier for me now.

---

