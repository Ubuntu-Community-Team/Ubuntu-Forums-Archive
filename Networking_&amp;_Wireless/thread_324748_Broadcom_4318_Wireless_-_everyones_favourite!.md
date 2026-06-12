---
title: "Broadcom 4318 Wireless - everyones favourite!"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by John Picton on 2006-12-24
Hi all,

I've just installed Ubuntu on an HP Pavilion DV 5000 laptop and I like it lots. Only thing is this wireless network problem that I and half the newbies in the Linux community have.

I've used ndiswrapper, the driver seems to be installed OK, the light on the laptop that indicates wireless is active is on, if I go into Wireless Assistant the connection I want to link to is there and at full strength but when I try to connect I get a "Connection Failed" error.

I'm sure my router settings are fine, can anyone offer some advice?

Thanks.

---

### Post by John Picton on 2006-12-27
I'm so nearly there! If someone can  help me with the last piece of the jigsaw I would be really grateful.

So far, the wireless lamp on the laptop is lit which leads to me to believe that the system has found this BCM 4318 card and knows it is there.

I think that the wireless card is configured to eth1, as eth0 is the wired network and works fine. I've filled in all the info that I think is correct in this configuration but no luck.

I've installed WiFi Radar, and it can see all the networks around, there are four in total and one of them is mine and the signal for it is full strength. But when I try to connect to it it tells me "Could not get IP address". This is in auto mode, I've tried manually configuring the connection, giving it an IP address (192.168.0.5) in the same subnet as the router and specifying the routers IP as the Gateway (192.168.0.2) but it still doesn't want to work. I know these settings are OK as they work in Windows.

I've no idea what to try next. Am I right in thinking that because the computer can see the networks the card must be configured correctly? I've followed many of the posts and tutorials as best as I can, but I've only been working with Linux for around a week and don't really understand what I am doing.

Thanks in advance

---

### Post by kelbizzle on 2006-12-27
type "iwconfig" into terminal. What does it say? I have the same card. In my Gateway mx6436.

---

### Post by John Picton on 2006-12-27
Hmmm! Not sure what all this means:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  Nickname:"DI-524"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:25 dBm   
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Make any sense to you?

Thanks for your help.

---

### Post by SeaSky on 2006-12-27
If you have ever updated the broadcom driver under windows many of these how to's will not work. Why? Because the OEM drivers also update your firmware on your handy dandy broadcom chipset, it will still say you have 4318 or 4319 or whatever, and you do, but it's been "updated" After sending over 300 correspondances to HP about this and threatening legal action they finally did add the words "and firmware" on their driver downloads pages.

If you updated your driver under windows with a driver from HP then it also 'updated' your firmware...

---

### Post by John Picton on 2006-12-27
Re: Firmware update:

Not sure if I have done this or not. The laptop did previously have XP Pro on it but I don't recall having ever updated the driver. This isn't to say that it hasn't been done I suppose, maybe by an HP Auto Update package or something?

Do you know how I could find this out? And will it stop my Wireless Network from operating under Ubuntu?

---

### Post by taurus on 2006-12-27
Try this one...

[http://www.ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318](http://www.ubuntuforums.org/showthread.php?t=285809&highlight=bcm4318)

---

### Post by John Picton on 2006-12-27
Thanks,

Took a look at the link, but in the file that I need to add the blacklist line to there was already a line that said:

#module below does not work with Broadcom 4318 wireless cards

So I guess that's a non starter? I may have tried the blacklist bit already whilst browsing through other "how to" guides, though as Linux is new to me I've no idea what I may have changed!

Tried it anyway and I got the following message when I tried the sudo rmmod bcm43xx command:

ERROR: Module bcm43xx does not exist in /proc/modules

This means nothing to me! Make any sense to anyone else?

---

### Post by John Picton on 2006-12-27
And if there is such a problem with Broadcom cards would it be worth me buying a different wireless card to plug in to the laptop? I'm guessing that the Broadcom is on the main board of the laptop (HP dv5000)?

Rather than go back to windows I would rather purchase a compatible card. Anyone know of any that work with Ubuntu - as easy as possible would be nice? Or should I not be giving up yet!

---

### Post by kelbizzle on 2006-12-27
If you would like when I get home. In an hour or so. I will give you the same exact driver and the same set of instructions that got my card working every time. I'll even help you over im or something. it's a thread from this forums. I remember saving the entire webpagee with the drivers, buring to a cd, and marking it "laptop' wireless drivers(linux)"

---

### Post by ibc on 2006-12-27
I was having similar symptoms.  Same card; tried the ndiswrapper fix, even though I could successfully scan for local SSIDs, etc...

Before you throw in the towel, if you can do everything but ping the gateway using the native BC4318 drivers, you may want to try what I did.  Get rid of ndiswrapper, clean out the /etc/network/interfaces file, and then try using the NetworkManager applet. (don't forget to remove ndiswrapper from /etc/modules, and remove bcm43xx from /etc/modules.d/blacklist!)

[http://www.ubuntuforums.org/showthread.php?t=326374](http://www.ubuntuforums.org/showthread.php?t=326374)

---

### Post by kelbizzle on 2006-12-27
heres the link [http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

the drivers are there too. I have this working with the same card and my network is using wpa. I wouldn't mind helping you over aim or something either.

---

### Post by Macgyver007 on 2007-11-03
Compaq Presario V2000 with Broadcom 4318 ver 02 card worked GREAT after completing the long version of installing ndiswrapper. I also had to blacklist the "included" bcmxx driver that came with ubuntu. For anyone else with this card, follow his guide it worked finally for me.

---

