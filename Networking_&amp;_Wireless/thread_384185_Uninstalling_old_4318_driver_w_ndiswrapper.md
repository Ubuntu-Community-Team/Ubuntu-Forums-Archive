---
title: "Uninstalling old 4318 driver w/ ndiswrapper"
date: 2007-03-14
forum: Networking &amp; Wireless
---

### Post by HumbleGod on 2007-03-14
Hello,

I'll warn that I'm an absolute Ubuntu (and Linux in general) newbie here. I installed Edgy this evening and have been trying to get my Linksys WMP54GS (Broadcom 4318, 1737:0042) working all night. I've been following the directions [here]("http://www.ubuntuforums.org/showthread.php?t=378615"), but I get stuck at the line
```
ndiswrapper -e bcmwl5
```
which gives me no visible response. Then when I try to install the *new* bcmwl5.inf, it says that bcmwl5 is already installed--in other words, the old one obviously wasn't uninstalled.

Am I doing something wrong? Is there another way to uninstall the old bcmwl5 driver? Or am I going about this whole thing wrong?

Maybe I should also note that the wireless card doesn't even show up in my Networking options yet. This strikes me as odd, because it always showed up when I booted to the Live CD before installing.

Thanks for any help!

Edit: I should also mention that I have no wired Internet connection. I'm only able to connect via wireless through my XP installation; however, I set up a FAT32 partition to transfer files that I download to the Ubuntu system, so if I need anything else I can get it that way. But I can't connect to any repositories (to install Wine, e.g.).

---

### Post by pognonec on 2007-03-14
Hi there,
I had similar problem while trying to install wifi connection on a broadcom equiped HP Pavilion zd8000.
I solved my problem following this link:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset](http://ubuntuguide.org/wiki/Ubuntu:Edgy#Ndiswrapper_for_Broadcom_43xx_wireless_chipset)
Hope this help.

---

### Post by HumbleGod on 2007-03-14
Already tried that before doing the above, no dice. The 4318s need more effort, apparently.

Anybody else have input as to why ```
ndiswrapper -e bcmwl5
``` isn't working? Thanks!

---

### Post by blackhole82 on 2007-03-14
Try ```
sudo ndiswrapper -r bcmw15
```

---

### Post by HumbleGod on 2007-03-14
I just gave up and reinstalled Ubuntu over the old install. Which is actually working out pretty well now--the system at least recognizes that I have a wireless card, even if it's still not working. But that's related to another set of instructions, so I'll ask for help in the appropriate thread. Thanks for the input!

---

### Post by teaker1s on 2007-03-14
wireless in my sig good sound method

---

### Post by HumbleGod on 2007-03-14
That guide assumes wired connectivity; sadly I don't have that....

---

### Post by teaker1s on 2007-03-14
did you install with live cd or alternate.iso text install?

---

### Post by HumbleGod on 2007-03-14
The regular 386 live cd.

---

### Post by teaker1s on 2007-03-14
you can try the live cd as a source,but you may need alternate.iso
terminal
```
gksudo synaptic
```
search "ndiswrapper" select and completely remove all entries(at review check nothing but what you have ticked is going to be removed. APPLY

Hit reload tab-does synaptic ask for cd as source? no-then hit edit tab and select "add cdrom"


now you can access any packages that are on the cd source search "ndiswrapper" and reinstall everything that was uninstalled

---

### Post by HumbleGod on 2007-03-15
Thank you for the advice; unfortunately, those tips (though good to know how to do this) didn't really change the situation, and there are still plenty of other applications/packages requried by the thread in your sig that aren't available on the CD (as far as I can tell, though I might just be searching the wrong way).....

---

### Post by teaker1s on 2007-03-15
okay well the choices it would seem are:- 
1) in my sig is a link to ubuntu packages without internet access(you'll need packages and dependencies) not much fun:( 
2) download and burn iso of alternate.iso that has a fuller package list and add it as a cd source

---

### Post by HumbleGod on 2007-03-16
First of all, thank you for your help so far **teaker1s**.

Most of the packages I needed turned out to be on the i386 disc; the only one that wasn't was (obviously) the newest ndiswrapper 1.38, which I downloaded to my FAT32 partition. The first time I followed your guide my system crashed, probably due to some tweaks from following previous guides.

When following your guide from a fresh install, however, I've almost got it working! I can tell I'm closer than before because, after running [FONT="Courier New"]ifdown[/FONT] and [FONT="Courier New"]ifup[/FONT], [FONT="Courier New"]iwlist[/FONT] shows my wireless network with the actual strength. (Following other guides led to iwlist showing the network, but showing 0/100 for strength.)

```
brad@brad-ubuntu:~$ sudo iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:C0:49:CC:B1:40
                    ESSID:"Ringo"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

However, I'm still not connecting! And when running [FONT="Courier New"]iwconfig[/FONT] in Step 7 of your guide, it doesn't show the network in the ESSID:

```
brad@brad-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Everything's *seems* set up properly in Networking (correct ESSID, correct WEP key, set to DHCP). Any idea what I could be missing?

Again, thanks for the help so far!

EDIT: The only significant departure I made from the instructions in your guide was in Step 5; there was no 14E4:4324.5.conf, so I moved 14E4:4320.5.conf and turned that into .conf instead. Could that be part of the problem?

---

### Post by teaker1s on 2007-03-16
The guide is frodoB's I just added the bugs section and a few minor edits such as adding ndiswrapper to modules so it starts at boot.
Have you tried putting in an essid and network key in terminal?
or using network-manager-gnome as per guide?

Also be aware some features available on a native driven wireless card, are not avaliable with ndiswrapper.

---

### Post by HumbleGod on 2007-03-16
Well I'll be damned. I'm now submitting this using my Linksys WMP54GS wireless card on my Ubuntu system.

Though I shy away from anything labelled "optional," turns out network-manager and network-manager-gnome were what I needed. Well, that and a helluva lot of handholding by a patient guy with all the answers. Thanks for all your help! Wouldn't have been able to do it without you (and frodoB)!

---

### Post by teaker1s on 2007-03-16
bliss of wireless:guitar: :guitar: :guitar: 
if you go to your first post and edit it-you will see a tick box to mark it resolved.:popcorn:

---

### Post by HumbleGod on 2007-04-20
_UPDATE FOR FEISTY_

I'm including a few short words in case any other newbies upgrade from Edgy to Feisty after getting wireless to work following this method. I was afraid that upgrading might cause problems with this wireless setup, and it did, for about five minutes. Here's how I resolved it:

When installing the upgrade, I got a warning message saying that /etc/modprobe.d/blacklist would have to be altered, and that one of the lines being removed was "blacklist bcm43xx". After rebooting, I had no wireless connectivity (the keyring password dialog for Network Manager didn't even come up). So I typed:

```
sudo gedit /etc/modprobe.d/blacklist
```

and re-added the line

```
blacklist bcm43xx
```

Save, close, reboot, and all was back to normal! :)

---

