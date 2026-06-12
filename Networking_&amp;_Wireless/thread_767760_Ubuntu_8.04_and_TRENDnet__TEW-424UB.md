---
title: "Ubuntu 8.04 and TRENDnet  TEW-424UB"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by EnigmaStrain on 2008-04-25
So I have just installed Ubuntu 8.04, admittedly I am new to Linux GUI or otherwise. Anyhow my problem is this I have followed all possible instructions for getting my wireless usb dongle to work with Ubuntu 8.04. Problem is the ndiswrapper won't install no matter what I do I even downloaded the ndiswrapper from sourceforge on the windows side of my system; I am pulling my hair out I am at a complete loss and I would really love to get into Ubuntu and learn it...because I hate windows, and well I won't even get into my issues with Apple. If there is anything anyone can recommend; possibly even a Wireless USB Dongle that would work out of box with Ubuntu 8.04 :confused:

---

### Post by ElJefeRocks on 2008-04-26
I also am having a problem with this card, although I already have ndiswrapper installed.  What is going wrong with the installation exactly?  are you sure that you have the correct ndiswrapper in your sources?


You'll have to plug into the wall to do this.
```

apt-get update
apt-get install ndiswrapper-common ndiswrapper-utils-1.9

```

Hope this helps a little.

---

### Post by EnigmaStrain on 2008-04-26
> **ElJefeRocks said:**
> I also am having a problem with this card, although I already have ndiswrapper installed.  What is going wrong with the installation exactly?  are you sure that you have the correct ndiswrapper in your sources?


You'll have to plug into the wall to do this.
```

apt-get update
apt-get install ndiswrapper-common ndiswrapper-utils-1.9

```

Hope this helps a little.


Yea I'll have to give that a shot

---

### Post by schiette on 2008-04-26
I played around with Ubuntu 8.04 trying to connect my computer to my TEW-432BRP wireless router using this TrendNet TEW-424UB usb adapter and finally succeeded tonight :) In case this is useful for someone 
else, here is how I did. (I assume that everything else works properly, that you do have an internet connection if you connect directly into the router, etc.)


[LIST]
[*]Setup the router security to WEP hex 64-bit key (10 hexadecimal digits)
[*]Download the rtl8187b driver from Realtek web site and unzip it somewhere.
[*]Install ndiswrapper as mentioned in the previous post or using Synaptic.
[/LIST]
From the terminal, make the following incantations:
```
cd ~/where/driver/unziped/RTL8187B/WinXP 
sudo ndiswrapper -i net8187b.inf
sudo ndiswrapper -l
sudo modprobe ndiswrapper
```
the "sudo ndiswrapper -l" command should output: 
 net8187b : driver installed
 device (0BDA:8189) present

The driver is now installed, and you should see the adapter (wlan0) by typing iwconfig or ifconfig. If you don't see it, reboot, you should see it afterwards. (There is probably another way but I'm not geek enough ;) )

We still need to connect and get an IP adress:
```
sudo iwconfig wlan0 key NNNNNNNNNN
sudo dhclient wlan0
```
where NNNNNNNNNN is your 10 digit WEP hex key

You will need to do these two incantations everytime you boot. You may put them in a script file, make it executable, then add a link on the desktop to launch it more quickly.

BEWARE: all this time, the little network icon at the top right of your screen indicates that there is no connexion. Just don't bother with it and especially don't try to make it work using the different menu related to it, **it will mess up everything** and you won't be able to connect again even with the incantations. Actually, it will see the router, but it can't get an IP address from it. I tried alot, but found no solution. AND you can't even make the script work! If you still do the bad thing, this is the way out: remove all ndiswrapper related packages, reboot, make sure wlan0 is not there anymore (ifconfg & iwconfig), and restart the process.

Hope it helps!

---

### Post by ElJefeRocks on 2008-04-27
What version of the 424ub do you have?  I have V.2 which uses a SiS chipset, and the SiS163.inf driver.  Also, I would like to have my network manager work, it's capable, I believe it should be utilized.

Also, my computer freezes while connecting to the network, using a WPA-PSK(tkip), requiring a hard-reboot.

---

### Post by schiette on 2008-04-27
> **ElJefeRocks said:**
> What version of the 424ub do you have?  I have V.2 which uses a SiS chipset, and the SiS163.inf driver. 
Your right, mine is V. 3.1R. Try downloading the sis163 driver and tell us if it works.

> **ElJefeRocks said:**
> Also, I would like to have my network manager work, it's capable, I believe it should be utilized.

Also, my computer freezes while connecting to the network, using a WPA-PSK(tkip), requiring a hard-reboot.
I tried several hours getting the network manager to work, with all possible advices from the internet, but found no way to do it. 

This morning I tested other security keys types. I could not get the WAP to work, it gives the same kind of problem as with the user interface  (can't get a IP address from the router DHCP). Same symptoms , perhaps its related.

WEP 128-bit works, though. You can even enter an ascii key in the router config, but you have to enter the hexadecimal correspondent in the *iwconfig wlan0 key NNN...NNN* command. (My router displays both versions when I switch from ascii to hex in its settings.) I've not been able to enter the ascii key directly in the iwconfig command, but there is probably a way to do it.

---

### Post by ElJefeRocks on 2008-04-28
I still have had no luck in configuring the TEW-424UB V.2 (SiS163) with hardy yet.  I have tried to configure manually and through network manager, but it always locks the system up.  I have not had the chance to try WEP because a few too many people use the router here to be messing around with that.

I had a WG111T I bought off woot a while back that I tried in the system as well, same configuration, using ndiswrapper still, but it has an atheros chipset instead of the sis.  The computer doesn't freeze when trying to connect to the network, but it doesn't connect either, it just sits trying to obtain the WPA key from the router.

It is a little frustrating when two different hardware pieces don't work.  I think hardy and ndiswrapper need a little alone time to work things out, wpa-supplicant probably needs to come too...

---

### Post by sexcopter on 2008-05-11
> **ElJefeRocks said:**
> I still have had no luck in configuring the TEW-424UB V.2 (SiS163) with hardy yet.  I have tried to configure manually and through network manager, but it always locks the system up.  I have not had the chance to try WEP because a few too many people use the router here to be messing around with that.

I would like to make a more insightful post, but all I can say is I'm having exactly the same trouble on Hardy with the same Trendnet device and using the same driver. I'm disinclined to try using WEP, because from what I hear it's pretty ineffective for security.

I will be on the look-out for a solution and report back if I find one!


James

---

### Post by sexcopter on 2008-05-11
I haven't found anything that works yet, but I'm wondering, does anyone know how we can diagnose these lock-ups any further? Are there any relevant logs that can tell us more about what's going wrong?

Cheers, James.

---

### Post by bigdee973 on 2008-05-17
yeah i have the same problem with the tew 424ub locking up my Ubuntu 8.04 hardy heron system.  the screen just freezes and always requires me to give it a hard reboot... it only happens when i have WEP encryption on my router but when i disable it it works like a charm...this sucks major *** because i hate having an unsecured network around. u never know when someone will try to prank on me or use up a large amount of my internet bandwidth...well u should get a hold of the administer and tell him to disable wireless encryption... i hate having to go thru the problem of pinpointing the problem all by myself so could somebody tell me if they have the same setup as us with some kind of encryption and kindly tell us about it...if not than ima try to find out whats causing the problem or if theres a work around to allow encryption..id have to try hex and/or 64/128 for both hex and asci..i know ascii 128 causes a lock on my system... id have to keep on experimenting

---

