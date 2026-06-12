---
title: "Help with an Acer Aspire 5720"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by Rolaulten on 2008-06-02
Good Evening(or morning, or day, or afternoon, or night).

Havening finally gotten pissed off at vista, I've just installed Ubuntu 8.04 on the D partition of my Acer laptop's hard drive(the PC came pre formatted with a C and D drives). The install from the live CD went without a hitch...

That said, when I loaded Ubuntu up after the install, lo and behold    it is not seeing, or able to use, or some such the driver's for my wireless card (please note, it is a built in wireless card). wandering if I just needed to turn on a box, I found my way to the Hardware Drivers wizard(sorry if its called something different, all I've used is windows up until now. There I see a window saying that the privet drives installed pose a risk ext. Under that there are two drivers, a "Atheros Hardware access layer (HAL)" and "Support for atheros 802.11 wireless LAN cards". Both have the little check box checked for being enabled, and both have there status as "in use". 

So then, I've played around with trying to disable and re enable them to no success, so now I'm outa ideas, and wondering...How do I get my Laptop to see the wireless network? 

Side notes: I am running a Dell desktop alongside the acer, so downloading any software will not be too big a hassle(the biggest will be finding my jump drive), and our household is all wireless (IE not a cat-5 cable to be found)

If you would like the hardware specs, they are [http://us.acer.com/public/page9.do?sp=page4&dau34.oid=24362&UserCtxParam=0&GroupCtxParam=0&dctx1=25&CountryISOCtxParam=US&LanguageISOCtxParam=en&ctx3=150&ctx4=United+States&crc=1795802524]("http://us.acer.com/public/page9.do?sp=page4&dau34.oid=24362&UserCtxParam=0&GroupCtxParam=0&dctx1=25&CountryISOCtxParam=US&LanguageISOCtxParam=en&ctx3=150&ctx4=United+States&crc=1795802524")

Lastly, like I said before, I have used windows my whole life, so I know how to do some things, but well, just looking at it I can see XP/Vista and Ubuntu are  different so go slow on me please. 

SO then, thank you in advance and I look forward to being able to fully switch over
-Rol

PS: if you wish to talk to me in outside these forums, my skype is the same name, and I never remember to change the status so if I don't pick up...

---

### Post by isparkes on 2008-06-03
Hi Rol,

I'm a 5720Z user, and and getting to be something of an expert with the teething troubles that there are with the Acer kit.

Here is a list of the things that don't appear to work right out of the box (I've got them all working, and it's pretty quick once you've worked out what to do):

1) Wireless LAN just does not work

2) Thermal management does not work after resume from standby or hibernate

3) Flash doesn't work

OK, solutions:

**_1) Wireless LAN - Use ndiswrapper._**

The problem seems to come from the misdetection of the network card. Do

```
lspci
```

and you should see the network card in there:

```
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Which the hardware isn't. There is a lot of talk about compiling madwifi, but that's for hard core guys. Apparently things are working better on the madwifi side now, but I'm just a coward at heart (and earn my bread with this PC, so I tend not to fiddle).

(This is taken from post [http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686))

Go to System / Administration / hardware drivers and disable all referring to your network card (Screenshot below) 

HAL and support for Atheros Card

Ensure you have your kernel headers and build the essential package. Use Synaptic or:

```
sudo aptitude update 

sudo aptitude install linux-headers-$ (uname-r) build-essential

```
Install ndisgtk. Use Synaptic or:

```
sudo apt-get install ndisgtk
```

Get XP drivers from the Atheros site. I've attached the ones that are working for me below:

```
unzip xp3264-7.4.2.75-whql.zip

```
Blacklist the default driver

```
echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist
```

Load Ndiswrapper and XP driver:

```
sudo ndiswrapper -i netathw.inf
```

Load up ndiswrapper every time Linux is loaded

```
sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules

```
Restart your system using the following command Restart your system using the following command

```
sudo reboot
```


**_2) Thermal management - You can follow the thread at:_**

Edited: Update: BIOS 1.34 or above will fix this problem. Because the BIOS update works only on DOS, I have prepared a FreeDOS boot CD which has the BIOS update 1.40 built in. You can download it from:

[http://www.openrate.de/Downloads/FlashBIOSV140.ISO.bz2](http://www.openrate.de/Downloads/FlashBIOSV140.ISO.bz2) 

[COLOR="Silver"]Alternatively you could use the old method here:

[http://ubuntuforums.org/showpost.php?p=4702613](http://ubuntuforums.org/showpost.php?p=4702613)

and specifically post 117, which has a pretty detailed workaround.
[/COLOR]

**_3) Flash - Install the flash driver by hand_**

Taken from post [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Install the Flash plugin manually by downloading the tar archive of Adobe Flash v10 beta from [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html). Make sure that you get the ".tar.gz" one and not the RPM one. Open the tar archive, then find the file named "libflashplayer.so and place it on your desktop. Next, execute this command in the terminal:

```
sudo apt-get purge flashplugin-nonfree
sudo mkdir /usr/lib/flashplugin-nonfree
sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/
sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /etc/alternatives/firefox-flashplugin
sudo ln -sf /etc/alternatives/firefox-flashplugin /usr/lib/firefox-addons/plugins/flashplugin-alternative.so

```

You can now restart Firefox and use the plugin.

---

### Post by isparkes on 2008-06-03
Sorry, would have replied sooner, but the forum went down last night while I was typing...

---

### Post by Rolaulten on 2008-06-03
Cool man, thanks for taking the time...I'll go and load up ubuntu and try it (so hope it works). And no worries about the long response time, last week of school and they are trying to load us down with a ton of work.
-Rol

---

### Post by isparkes on 2008-06-03
Sure. Get back to me if something doesn't add up. I did it mostly from memory...

---

### Post by kleugers84 on 2008-06-03
Awesome. I too have an Aspire 5720, going to give this a try when I get home. Just installed 8.10 last night and was getting ready to try the madwifi trick but it looked a little messy. Thanks for the help!

---

### Post by kleugers84 on 2008-06-04
Good news! While your guide did not work initially, I followed the link to another post you mentioned, and tried those steps. After doing so I still found I could not connect in Network-Manager, however using wired connection I downloaded WICD from synaptics, loaded it up and was able to connect fine!

So in the end your steps may have worked as well had I used WICD in the first place. Either way, thanks so much for the help!

---

### Post by Rolaulten on 2008-06-04
So I think I'm blind because...
seems like acer has removed all the win xp drivers from there site with regards to the network drivers (or I should say all wired and wireless drivers)...at lest that is what I am seeing in the PDF for the 5720z drivers ([http://www.acerpanam.com/synapse/forms/AcerDrivers/Aspire%205720Z.pdf?CFID=1321853&CFTOKEN=35137892]("http://www.acerpanam.com/synapse/forms/AcerDrivers/Aspire%205720Z.pdf?CFID=1321853&CFTOKEN=35137892")
Then when you go to the normal aspire 5620 pdf([http://www.acerpanam.com/synapse/forms/AcerDrivers/Aspire%205720.pdf?CFID=1321853&CFTOKEN=35137892]("http://www.acerpanam.com/synapse/forms/AcerDrivers/Aspire%205720.pdf?CFID=1321853&CFTOKEN=35137892"), )
they seem to have removed all traces of a win xp network driver.
If you know another spot to get it for download...or if the vista drivers work...
-Rol

---

### Post by isparkes on 2008-06-08
I got the driver from the Atheros site directly:

[http://www.atheros.cz/download.php?atheros=AR5007G&system=1](http://www.atheros.cz/download.php?atheros=AR5007G&system=1)

---

### Post by isparkes on 2008-06-14
Another issue that I had, was that the sound didn't work after resuming from hibernate.

I followed this guide:

[http://ubuntuforums.org/showpost.php?p=5017453&postcount=2](http://ubuntuforums.org/showpost.php?p=5017453&postcount=2)

To get it going.

It boils down to adding the following line:

```
options snd-hda-intel model=acer
```

at the end of the file

/etc/modprobe.d/alsa-base

Hope that helps any other Acer users out there...

---

### Post by v3xation on 2008-08-31
Hi.

I've tried this method for the Acer 7520 to fix the wifi issue and it didn't work for me.  I followed the code in terminal and it went fine until the last step when I ran "sudo modprobe ndiswrapper" and it returned "WARNING: /etc/modprobe.d/blacklist line 40: ignoring bad line starting with '&#8220;blacklist' "

I believe it's ndiswrapper not starting when linux loads that is the issue. I've check the blacklist file and the line: &#8220;blacklist ath_pci&#8221; is there.

Anyone got a pointer for an ubuntu noob?

---

### Post by meditatingfrog on 2010-07-15
> **v3xation said:**
> Hi.

I've tried this method for the Acer 7520 to fix the wifi issue and it didn't work for me.  I followed the code in terminal and it went fine until the last step when I ran "sudo modprobe ndiswrapper" and it returned "WARNING: /etc/modprobe.d/blacklist line 40: ignoring bad line starting with '“blacklist' "

I believe it's ndiswrapper not starting when linux loads that is the issue. I've check the blacklist file and the line: “blacklist ath_pci” is there.

Anyone got a pointer for an ubuntu noob?

Did you get your problem fixed?  This site talks about setting up Atheros AR242x on an Aspire One:  [https://sites.google.com/a/mg8.org/ubuntu-aa1/hw/wifi](https://sites.google.com/a/mg8.org/ubuntu-aa1/hw/wifi)

I have an AR242x wireless chipset but not an Acer.

---

