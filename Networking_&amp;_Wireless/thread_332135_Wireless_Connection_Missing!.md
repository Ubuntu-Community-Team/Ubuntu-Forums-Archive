---
title: "Wireless Connection Missing!"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by boilermaker on 2007-01-05
When I tried something to make my wireless connection work (ndiswrapper stuff) I am shocked to see that when i go to 
System->Administration->Networking 
I dont see any wireless connection (which was there before) ](*,) 

Can someone help me with this?:(

---

### Post by teaker1s on 2007-01-05
terminal 
sudo modprobe ndiswrapper

sudo ndiswrapper -l

what does it say?

---

### Post by boilermaker on 2007-01-05
Hi: 


this is what i got!


For 
sudo modprobe ndiswrapper

nothing happened!


$ sudo ndiswrapper -l

Installed drivers:
bcmwl5.sys      invalid driver!


I am still not able to see the wireless connection when i go to 
System->Administration-> Networking

---

### Post by teaker1s on 2007-01-05
ok well modprobe ndiswrapper just starts kernel module, from what i can see the driver that ndiswrapper installs by default isn't suitable.

remove it by 
**sudo ndiswrapper -r bcmwl5**

what wireless brand and model do you have terminal

[B]lspci
[/B]

---

### Post by agirlnameddanni on 2007-01-05
My computer is doing the exact same thing, the wireless connection was gone after i rebooted the computer after updating. i can't cpy/pste anything from the terminal since the internet wont work on there.....

any help?

---

### Post by teaker1s on 2007-01-05
we have had a private message session and sorted it as it was invalid driver in ndiswrapper for his broadcom chipset. I was about to call it a night,would you like some quick help if I can?

---

### Post by teaker1s on 2007-01-06
**okay we are getting there, look below and read the bold comments**
Installed drivers:
bcmwl5 driver installed, hardware present

**above shows that we have both hardware and software correctly installed -good news**

$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11b/g ESSIDff/any Nickname:"Broadcom 4318"
Mode:Managed Access Point: Invalid
RTS thrff Fragment thrff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.
**your ubuntu system is seeing your wireless as ethernet port 1, we can easily sort this by**
[COLOR="Red"]sudo gedit /etc/iftab[/COLOR]

**the file will open and you will see, note your mac will be different**

eth0 mac 00:16:36:86:a7:08 arp 1
eth1 mac 00:14:a5:e8:4f:8f arp 1

**change ethernet1 by commenting it out like this**

eth0 mac 00:16:36:86:a7:08 arp 1
[COLOR="Red"]#[/COLOR]eth1 mac 00:14:a5:e8:4f:8f arp 1

**REBOOT**

When i tried to install Network Manager
**your making this hard for yourself as this package is in the repositories, first "cd" into folder containing source code now if you managed to sudo make install you will need example**
[COLOR="Red"]cd /home/teaker1s/hpfax[/COLOR]
**now if you managed to sudo make install you will need**
[COLOR="Red"]sudo make uninstall[/COLOR]

**if on the other hand you never managed make install-just delete folder with source in it**




When i tried double clicking network manager it says
" Failed to execute child process nm-applet"

ok also the i am able to load the network connection and signal meter at startup but it says not connected

[COLOR="Red"]gksudo synaptic[/COLOR]
[B]click settings tab-preferences-general,tick recommended packages as dependencies. next search and install with synaptic
[/B]
[COLOR="Red"]Network-manager-gnome[/COLOR]
I would be really happy if you someone can help me out.....


CAn you also tell me what this is suppose to mean

Blacklist native bcm43xx drivers
**ubuntu has a driver for wireless cards-it doesn't work with our hardware so we need to stop it loading at boot time**
* Type:
Code:

sudo gedit /etc/modprobe.d/blacklist

* Add the line:
Code:

blacklist bcm43xx

* After saving type at the terminal:
Code:

sudo rmmod bcm43xx
**while we are at it the native module isn't needed so we'll remove unused garbage from the kernel**


Sorry for such a long thread![/quote]
__________________

---

