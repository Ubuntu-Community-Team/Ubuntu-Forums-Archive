---
title: "Dell truemobile 1150 not detected in gutsy?"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by bubba_169 on 2007-10-01
OK i've tried quite a few things but I just cant seem to get my wireless working using the new gutsy kernel.

Over the past year or so I have been using linux on my Dell C640 laptop and have installed edgy and feisty without any problems what-so-ever. I liked the fact that k/ubuntu just worked with all my hardware and only a few minor tweaks were needed in software (eg codecs) to get a fully functioning desktop that I saw as a true alternative to windows.

However, with this new gutsy kernel, my wireless card just seems to not work at all. Following bits of advice from different sites (looking using my M$ computer) i tried a few different things. In feisty (2.6.20-16 kernel) when i type lshw it shows that my wireless card is using the orinoco driver whereas the same action in gutsy (2.6.22-11 kernel) will show the card name but not much else and its physical ID is 0. Also on both kernels the card doesnt show up when i type lspci or lsusb.

I have read an article [here on launchpad]("http://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125832") that may be something to do with the problem im facing but I wondered if it is then how do I install the orinoco driver myself? I tried getting the source for the orinoco-0.15 driver but when I try "make" it complains that wireless extensions are not enabled? Im a bit of a noob when it comes to drivers and compiling kernels etc so please be gentle :)  I tried ndiswrapper but every time I install the windows driver (it seems to install OK) and then type ndiswrapper -l the output is "wldel48b: invalid driver!"

If anyone has any suggestion for me to try (please include instructions) then im willing...

Thankyou

---

### Post by bubba_169 on 2007-10-01
Maybe a little bit more success I have now managed to get ndiswrapper to accept a different driver from driverguide.com that claims it works with my wireless card. After ndiswrapper -l it now says 

```
wlluc48: driver installed
```

but how do I get the hardware to work using this driver?  When I do iwconfig it only shows me lo and eth0 (wired) both say "no wireless extensions"? If this road is going nowhere then please can someone nudge me in the right direction, otherwise any help appreciated :D.

---

### Post by cameronjcc on 2007-10-01
If your using Dell, I hope you don't have the infamous Broadcom Wireless Card.  If you do, then Ndiswrapper will probably not work with the drivers Dell provides.
I tried that once, no good for JoeJoe.
Try the bcm43xx.
Not the toys, but the actual driver (OEM.inf)  This worked for me.


1) Blacklist bcm43xx driver
Open a Terminal window
Type "sudo gedit /etc/modprobe.d/blacklist"
At the bottom add the lines

# get rid of the default kernel drivers
blacklist bcm43xx

2) Make sure network interfaces file is correct
Type "sudo gedit /etc/network/interfaces"

Remove all comments ('#') that you see so that all devices are handled by the default network manager.

I would reboot here and make sure the wireless light goes out  If it doesn't don't worry to much. once mine did, the next computer it didn't.

3) Install ndiswrapper

Put in Ubuntu CD. Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.

You could also type "sudo apt-get install ndiswrapper-utils 
(IF you are not using ubuntu (Why In The Great Heavens NOT!!!!!!) then make sure you have ndiswrapper-utils somhow installed)

4) Conigure ndiswrapper
Open terminal and navigate the folder where your drivers are."cd Desktop/bcm43xx"

Type       sudo ndiswrapper -i oem3.inf
Type       sudo ndiswrapper -m
Type       sudo gedit /etc/modprobe.d/ndiswrapper

Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit. 

If it worked, you should be able to click the Network Manager icon in the top right. 

It will probably show a disconnected connection because the computer is not plugged in.

Left click it and select eth1 from the drop down menu.

Click Configure

Click Wireless Connection, then Properties. 
Here just enter your network information. 
If you're using an unprotected network you should only have to type yout SSID.

Click OK and you should now be connected! 

If a green signal meter and connected network icon appear in the upper right you'll know it worked.

---

### Post by bubba_169 on 2007-10-02
Erm I tried what you said but ndiswrapper doesnt seem to want to take control of the card? I think its because Im using the wrong driver with the bcm43xx one as Im pretty sure its a lucent orinoco chip?

I think the problem is that the orinoco_cs thingy that my card needs is missing from the gutsy kernel so thats why Im looking at alternatives to get my wireless working. I know it will work with the orinoco_cs one because when Im in feisty and I blacklist orinoco and orinoco_cs the network refuses to start and iwconfig and ifconfig  show as if eth1 (my wireless) doesnt exist. As soon as i modprobe orinoco and orinoco_cs then my wireless is up and working!

I tried to insmod the orinoco_cs.ko from that was included with the previous kernel whilst using gutsy but it says invalid format? Would I be able to do something like this to get it to work?

Thank you again...

---

### Post by Lambert on 2007-10-02
Your problem does seem to be related to the orinoco.cs module and gutsy.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125832](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125832)

You can wait to see if this is fixed in the final release or find a valid driver and use ndiswrapper. Looking on the ndiswrapper site, I didn't see the truemobile 1150 listed. 

You will have to search and find a driver that can work.

---

### Post by bubba_169 on 2007-10-02
Ok thank you for your help :D 

Just one last question how will I know when I have found a working driver for my card using ndiswrapper? I get the impression from reading other sites that as well as saying driver installed on the ndiswrapper -l command, it should say device found or something along those lines?

---

### Post by Lambert on 2007-10-02
> **bubba_169 said:**
> Ok thank you for your help :D 

Just one last question how will I know when I have found a working driver for my card using ndiswrapper? I get the impression from reading other sites that as well as saying driver installed on the ndiswrapper -l command, it should say device found or something along those lines?

when you run ndiswrapper -l you should see output stating hardware present: driver present. When you run iwconfig, you should also see an interface wlan0 present.

---

### Post by mightysween on 2007-11-25
Realize this is an old thread, but I was just wondering if anyone has gotten a Truemobile 1150 working in 2.6.22-14-rt (the Ubuntu Studio kernel version).   Mine works fine in 2.6.22-14-generic where the orinoco_cs driver is still present.   For some reason it was removed from the rt version of the kernel and I can not find a driver to replace it.

I've tried a dozen or so drivers with ndiswrapper to no avail.  At this point, the wireless card is not recognized at all...in other words, the light does not even come on for the wireless (like it does in "generic" kernel). So it is not just a configuration problem.   

Any suggestions?

---

