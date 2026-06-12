---
title: "Truemobile 1150 Configuration With WPA"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by danstever on 2007-01-12
Alright everyone.... I need help. I am completely new to Ubuntu. I have had minimal experience with other Linux distributions in the past, but never with this. I would consider myself an expert with Windows and mac formats, but I just am being driven crazy right here with my wireless.

I have setup a dual boot with XP home and Ubuntu 6.10. Everything is working great, except my wireless with Eft. I am trying to setup a Dell Truemobile 1150 on my Dell Inspiron 1100. I have searched and read every posting on here I can find with no luck. My research has shown me that the Truemobile 1150 uses the orinoco_cs driver. I have checked the Device manager and it does recognize and list "Dell Truemobile 1150" stating that the driver is the orinoco_cs.

A little info: the status light on my wireless card will flash every once in awhile, but will not stay on.  iwconfig outputs:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Wireless"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/92  Signal level=134/153  Noise level=134/153
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:1
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

My wired connection works fine. I have the network "monitors" next to the time and date, but only the "wired network" is present.

I feel like I am probably missing one small thing. Anyone have any suggestions? Any help would probably get me further than I am now. Thanks.
- dan

---

### Post by danstever on 2007-01-14
bump

---

### Post by danstever on 2007-01-16
Ok, an update...

After a few days of digging and trying different things, I have found out I have no problems with my drivers for my wireless card. It is working great. Now my next problem comes in getting it to connect.

First, because I have tried so many different configurations for my network, including installing different programs, I reinstalled ubuntu so I would have a clean slate... Not a big deal. I haven't done much with this yet because I want my hardware to work first.

After reinstall, I installed wifi radar to make scans and connects easier. My network appears and I attempt to connect. It ends up saying "Connected to Wireless ip (none)" 

In wifi radar, is there something I have to put in the "driver" box under No WPA/Use WPA?

I am using WPA-TKIP to secure my network. I have tried to follow the 'sticky' post on wireless security: but can not get any further than this.

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

iwconfig is still coming back as listed above. Looks good to me except the "Access Point: None"

I know the Dell Truemobile 1150 works with WPA-TKIP... That is how I have my XP setup.

Anyone have any suggestions? Please? Anyone? Just a post to say "nope." ?

 Thanks...

**Update**
I scratched wifi radar...  I was not moving forward in getting a connection. When the problem isn't fixed, and what you are doing isn't working... Go back to square one.

So, I have been trying to configure my setup using the tutorial listed here: [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

I did it the first time and my wireless would not show up in the network manager. I figured I would give it a shot after the reformat/reinstall. It Worked!  Sort of...  The network manager appeared in the gnome panel, and my wireless network appeared... the network I was trying to connect to appeared... When I clicked on it though, WPA was not an option. I have WEP as an option...

 So this leads me back to the driver. I know I have the orionoco_cs driver. I know it is working. I know that the windows driver supports WPA. But how do I get WPA with my wireless card in Edgy?

Does anyone know if there is an update available for the orionoco_cs driver that would support WPA?  Or another Linux ready driver that supports the Dell Truemobile 1150 with WPA? Or should I start trying to attempt to use the ndiswrapper with my "known to work" windows driver? 

I'm struggling guys... any help... any thing?

dan

---

### Post by danstever on 2007-01-17
bump.....

Can anyone confirm for me if you are using a dell truemobile 1150 with WPA encryption?

Or if you have tried and it really doesn't work, or what you did to get it to work?

I know also now that this card is considered an Orinoco Gold card.

I have the orinoco_cs driver running. It was loaded on install. I have not messed with it since my reinstall.

 Anyone using the orinoco_cs driver with WPA?

 Am I the only person with this card/driver/or something else problem?

dan

---

### Post by danstever on 2007-01-21
Well if anyone has been reading this thread.... I finally got my problems solved. I will just cross-reference where I got it, and hope that it helps someone. 

[http://www.ubuntuforums.org/showthread.php?t=304217&highlight=Lucent+IEEE](http://www.ubuntuforums.org/showthread.php?t=304217&highlight=Lucent+IEEE)

Big ups to IntuitiveNipple for the help.

- dan

---

