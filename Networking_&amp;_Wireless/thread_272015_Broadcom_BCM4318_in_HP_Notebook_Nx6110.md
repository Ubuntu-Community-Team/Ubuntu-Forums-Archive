---
title: "Broadcom BCM4318 in HP Notebook Nx6110"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by applecookie on 2006-10-05
Hi there...

I bought today this fine little notebook for a good price. Dapper install worked perfectly and all seems to work "out of the box". But not...

the wireless card...

broadcom bcm4318 Airforce One 802g Rev. 02

I've read a lot the last hours and tried a lot and this workaround helped me, that even the control led is now on (before it was off...)
But I can't connect. I do not even got a signal from my wlan which is in the same room! Other notebooks work.

iwconfig says:

eth0      IEEE 802.11b/g  ESSID:"<mywebname>"  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.412 GHz  Access Point: <adress>
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Can anyone please help me? I am a very new user in linux and ubuntu and I do not have experience with ndiswrapper. Also I do not have any drivers for windows, because I bought this notebook "barebone" (without system and drivers and do not have a windows system to extract drivers in exe-files!)

Regards

Frank

---

### Post by Jagot on 2006-10-05
I have the same card in a Dell Inspiron 1300.  Ndiwrapper is the only way I've managed to get it to work.  So, firstly install ndiswrapper:

```
sudo aptitude update && sudo aptitude install ndiswrapper-utils
```

Now you will need to get the Windows drivers.  I know you say you don't have the Windows installation, but you should be able to download the drivers from the support section on the HP website.  The drivers that came with my Windows installation oddly didn't work and I ended up downloading the driver from Acer's website.

Anyway, now to installing the drivers with ndiswrapper.  The following assumes of course that the driver is  in a folder on your desktop:

```
sudo ndiswrapper -i ~/Desktop/bcmwl5/bcmwl5.inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

The first section actually installs the driver.  The second section blacklists the built-in Broadcom drivers in Ubuntu (which don't work for me).

Then it's just a matter of configuring the network settings.

---

### Post by applecookie on 2006-10-06
Hi.

That did not work. Before, I did have a wireless card in my iwconfig information, now I do not have any wireless extensions anymore.
The blue led for the card also is not lit anymore. And in the network information I also do not have any wireless extensions anymore :( :( 

Frank

---

### Post by Tom^ on 2006-10-08
applecookie, it's a bit struggle to get it working - I'm having hard time with Edgy and bcm4318 right now. But when I used Dapper, [http://www.ubuntuforums.org/showthread.php?t=185174](http://www.ubuntuforums.org/showthread.php?t=185174) did the trick for me with nx6110. Just follow the instructions.

---

### Post by applecookie on 2006-10-16
Thanks. :) 

I've worked it out now (without ndiswrapper, but bcm4318-fwcutter instead...) and it works... :eek: 

...but only a few hours. Then the wireless network disappears (not the card in the network). It seems, that the broadcom bcm4318 has a powersave function, which causes it to loose connection.
If I start again (reboot), the network works again. :???: 

Strange... :-k 

Regards
Frank

---

### Post by jsnelgrove on 2006-10-18
I have the dreaded Broadcom 4318 Rev02 card integrated in my Compaq V5000. The only distro that has succesfully run this card is "FREESPIRE" and I'm not a big fan. I refuse to use NDISWRAPPER, So I run natively with a USB WLAN stick for now.

However, I see today on Distrowatch that a developmental version of VINE has been released which supports the BCM4318xx cards. 

It looks like there are cracks in the ice and we're getting close. I hope someone can take a look at what they've done and see if they can figure it out. Freespire and Vine have managed to get this card going. The question is what have they done and how.

---

### Post by blackest_knight on 2006-11-06
Interesting Card this, 
I have had it up and running in breezy dapper and edgy 
and with both Ndiswrapper mode and native driver. 

The Ndiswrapper mode works best. 

With BCM4318 driver it doesnt want to work better than 11Mbs and a TX Power of 18DBm

However with NDISWrapper 
It runs at 54Mbs and a TX power of 25Dbm 

what is interesting too is the result of 
sudo ndiswrapper -i /home/Broadcom/bcmwl5.inf
when it sets up the Wireless it says it is forcing from mode0 to mode2

so I am guessing that the bcm43xx driver doesnt impliment this mode change
and thats why its set at a maximum of 18dbm and 11 Mbs

---

### Post by jml on 2006-11-06
I also have an HP nx6610 notebook.  Great piece of hardware.  My experience with the Broadcom wireless card is the same as everyone elses.  You have two choices.  You can use NDIS Wrapper plus the windows driver, or you can do what I did.  Give up and buy a PC card wireless adaptor with better Linux support.  Two that work for me are the Cisco Aironet 802.11 a/b/g card, ( a bit pricy, but it works well.)  and the Netgear WG511T.  These cards have the Atheros chip set and have good Linux drivers and support.

Joe

---

