---
title: "Howto: Use DWL-650 D-Link PCMCIA card w/ Ubuntu Edgy"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by SirKillalot on 2006-11-09
Hello,
I've been working on getting my wireless card to work on Ubuntu. That's how I made it:

Fist of all: Ubuntu uses the Orinoco drivers for DWL-650 D-Link cards. That's the wrong driver actually. Maybe you can get it work (well it did SOMETIMES for me, but you won't have all features your card is actually providing).
So all we have basically to do is changing the driver from Orinoco to Hostap driver which work fine for me.

So first of all let's install hostap.
```
sudo apt-get install hostapd hostap-utils
```

Then let us ban the evil Orinoco drivers:
open the file /etc/modprobe.d/blacklist-hostap-utils and add at the end:
```
blacklist orinoco_plx
blacklist orinoco_cs
blacklist orinoco_pci
blacklist orinoco
```

also don't forget to unload the evil drivers:
> sudo rmmod orinoco orinoco_cs orinoco_pci orinoco_plx
(don't forget to remove your card from your notebook before doing that!)

Now we have to change ubuntus config files because they will still load the bad drivers and not the good ones when you insert your card.
I recommend using gedit because you can easily 'replace all' with it.
> sudo cp /etc/pcmcia/config /etc/pcmcia/config_bak
sudo gedit /etc/pcmcia/config
Now go to "replace" and replace all the 'orinoco' stuff with 'hostap', save the file, insert your card and be happy.

Hostap also allows you to use the gnome network manager, which I recommend to you because its pretty cool.
Just do a apt-cache search on "network manager".

Hope that helps
sirk

---

### Post by tturrisi on 2006-11-09
To clarify the above card mentioned:
The DWL-650 was manufactured by D-Link at different times, using 4 different chipsets.  The above howto is for dwl650's that have a Prism 2-2.5 chipset.  Some dwl650's have a ralink chipset, some dwl650g's have an atheros chipset, etc etc.

---

### Post by SirKillalot on 2006-11-09
> **tturrisi said:**
> To clarify the above card mentioned:
The DWL-650 was manufactured by D-Link at different times, using 4 different chipsets.  The above howto is for dwl650's that have a Prism 2-2.5 chipset.  Some dwl650's have a ralink chipset, some dwl650g's have an atheros chipset, etc etc.

exactly, thanks!

---

### Post by K.B. on 2006-12-03
Would love to get my wireless card to easily work with Ubuntu, thanks.


I tried this and got some errors and since I'm rather new to Linux can't figure it out. here's what happens:
[I][INDENT]~$ sudo apt-get install hostapd hostap-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package hostapd
kb@kb-laptop:~$ sudo rmmod orinoco orinoco_cs orinoco_pci orinoco_plx
ERROR: Module orinoco does not exist in /proc/modules
ERROR: Module orinoco_cs does not exist in /proc/modules
ERROR: Module orinoco_pci does not exist in /proc/modules
ERROR: Module orinoco_plx does not exist in /proc/modules
[/INDENT][/I]

any help or suggestions on this would be greatly appreciated!

---

### Post by K.B. on 2006-12-04
I think that perhaps the first error I got was because I needed to update the apt-get. I was looking at something else and they said to be sure and update it before I did this and told me to :
*[INDENT]sudo apt-get update[/INDENT]*

And to also go under system>administration>synaptic package manager and add the 'universal' option.  

Does anyone else think this is why it now works?? (newbie making sure he understands what happened)


The good news is that I get way further... till I get to the point of backing up the PCMCIA config, there is none.

this is what I get:
[I][INDENT]sudo cp /etc/pcmcia/config /etc/pcmcia/config_bak
cp: cannot stat `/etc/pcmcia/config': No such file or directory
kb@kb-laptop:~$ sudo gedit /etc/pcmcia/config
[/INDENT][/I]

any ideas??

--- update ---

don't know if this is new or just never did it before but now when I have my D-Link PCMCIA card inserted when I restart Ubuntu won't get past the initial loading screen.

---

### Post by SirKillalot on 2006-12-04
Well, this looks like your PCMCIA might not be working. This should also be the reason why you can't edit (tne not existing) file...
Maybe you should start from getting your pcmcia fixed.
Best wishes 
sirk

---

### Post by K.B. on 2006-12-04
The PCMCIA slot and card both work fine under windows xp. Tried a PCMCIA ethernet card in the slot under windows as well and it worked. 

Is that what you meant or should I be looking at the Ubuntu software side of the laptop?

Thanks

---

### Post by K.B. on 2006-12-06
In the etc/pcmcia folder there are only two files:

config.osbt 
hostap_cs.conf
( I believe that is correct, writing this from different computer)

When I go in and do a status of the PCMCIA it shows the card in slot 2 and says that it is bound to hostap_cs

Is there a way to test the card and see if it's getting any signal or work on it without the config file?

---

### Post by K.B. on 2006-12-07
sorry to bump this but I've been searching for an answer to this all over the web and can't find anything. All I keep finding is articles and mentions that are several years old if anything.

---

### Post by K.B. on 2006-12-14
Well,  I've tried a lot of things lately and I'm not sure which it was but I am now able to access my wireless network with the DWL-650 card in my laptop. 

I'm also able to access it with full WEP thanks to the How-To [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo]("https://help.ubuntu.com/community/WifiDocs/WiFiHowTo")

Finally I don't have to boot into m$ when I want to use my laptop in another part of the house.

---

### Post by konungursvia on 2007-01-23
Thanks, I tried all that and the thing still never works, probably because I use encryption. 

my iwconfig output is currently:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"Samarkand"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Tx-Power=18 dBm   Sensitivity=176/255
          Retry min limit:7   RTS thr:off
          Encryption key:DC36-C668-1B   Security mode:open
          Power Management:off
          Link Quality:44/100  Signal level:39/100  Noise level:6/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and it does give a valid access point when I activate the wlan, it just never allows any apps to send and receive data. Any more ideas guys? I need help, or I can't roam around with the wi-fi.

---

### Post by webist on 2007-04-14
My DWL 650 revision m worked great with a fresh install of 6.06 ubuntu. Wouldn't work with a fresh install of 6.1 kubuntu (the light came on but I couldn't get it to log on to the network). Wouldn't work with a fresh install of 7.04 ubuntu (the lights never even went on). Upgrading from 6.06 to 6.1 everything worked fine. Upgrading to 7.04 everything seemed to be fine until I rebooted. The lights stayed off on the card. I'm back to a fresh install of 6.06 and will just stay there.

---

