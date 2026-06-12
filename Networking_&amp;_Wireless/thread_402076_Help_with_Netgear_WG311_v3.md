---
title: "Help with Netgear WG311 v3"
date: 2007-04-05
forum: Networking &amp; Wireless
---

### Post by windrider621 on 2007-04-05
This week I decided to try out a linux OS, and found ubuntu. I was able to get it running on my computer, but can't for the life of me get my internet to work with it. I only have wireless connection up here, and it's a pain to switch back to Windows when what I try doesn't work, and I'm also not sure what all I should be trying.

I've tried using ndiswrapper with the driver, although it has two SYS (I belive, may be the INF that has two) file, so I just grabbed one, since it says to only use one. I managed to get it loaded with ndiswrapper, but than when I use the ndiswrapper -l to check the list, it lists it as invalid. Also, I'm not sure if its recognizing the card properly or not. When I used lspci to find it, it was listed under communications, but said something about it being not in use (don't remember the exact wording, inavtive perhaps?).

I figured I'd post here and see if anyone has used WG311 v3 succesfully, and if so, if they could walk me through how to set it up in Ubuntu. I was really hoping to give it a try, but if I can't get the internet working...

Any help is greatly appreciated.

(Note: Sorry if this is already answered somewhere in the forums, I've looked but haven't found anything)

---

### Post by Floppyjoe on 2007-04-05
Your card is listed several times on the ndiswrapper list site at:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#N)
> # Card: Netgear WG311v3 54Mbps PCI adapter

    * pciid: 11ab:1faa (rev 03)
    * ndiswrapper 1.5 using driver wg311v3, stock 2.6.14 kernel
    * Tested with 11mbps and 128-bit WEP only, all other features untested.
    * Tested with Gentoo linux-2.6.14-gentoo-r4 kernel, ndiswrapper 1.5, wg311v3 driver. 54mbps (.11g) with no WEP works. Note: CB55N51 driver did *not* work. Couldn't set essid. 

# Card:Netgear WG311v3

    * Distro: Slackware 10.2 + 2.6 kernel (optimised for below without 4Kblock size)
    * Mobo: VIA MS10000
          o Worked no worries. Windows XP driver caused horrible kernel panic and seize-up. Windows 98 Driver works fully. 

# Card: Netgear WG311 v3 (54Mbps wireless G PCI adapter)

    * pciid: 11ab:1faa
    * Distro: Suse 10.0
    * Ndiswrapper: standard with suse 10: 1.2
    * Driver: latest XP drivers on netgear site at 3 jan. 2006: 02/22/2005,3.1.1.7 (so reads the .INF file)
    * Mode: 54g with WPA TKIP
    * Comments: I used the suse configuration center YAST to configure my WLAN card 


> # Netgear WG311 v3 (Marvell 88w8335 Libertas)

    * Chipset: Marvell 88w8335 Libertas 54Mbps Wireless Interface
    * pciid: 11ab:1faa
    * Driver: Copied WG311v3.INF and WG311v3XP.sys from Netgear CD to local ad hoc directory and ran ndiswrapper 1.2 there. Please see hint at [209]
    * Other: Running SuSE 10.0 - needed some tweeking in YaST - threw out old card from Network Devices / Network Card configuration and installed new card with Module Name as "ndiswrapper" in Manual Network Card Configuration. Runs 128 bit WEP at 54Mbps.
    * Other: Driver WG311v3.inf (XP) from Netgear-HP or CD (date: 2005-03-10) with ndiswrapper-1.33 on gentoo-2.6.18-r6. WPA/PSK with wpa_supplicant-0.5.4 runs without problems! 


> Netgear WG311 v3 (Marvell 88w8335 Libertas)

    * Chipset: Marvell 88w8335 Libertas 54Mbps Wireless Interface
    * pciid: 11ab:1faa
    * Driver copied from [208]
    * From Initial Release 6.20 MB May 16,
    * Running Mandriva Free 2007 DVD
    * Program Computer Configuration - Network and Internet-Cofiguration New Device
    * Works Great
    * Trabaja muy bien 


My guess is you should be able to get it working with ndiswrpper.
Make sure to delete the invalid drivers with:
```
sudo ndiswrapper -e drivername
```

---

### Post by windrider621 on 2007-04-05
I think I figured out the problem...it's not reading the memory on the card. When I stry sudo pccardctl ident, I don't get any output. Oddly enough, that seems to be the one thing in the Trouble Shooting Guide that doesn't have a 'if this happens, try this...', it just if it happens the memory isn't being read. Is that something not fixable? I'd really appreciate any suggestions, I want to give this a try, but don't plan on buying anything to make it work, since I'm getting a new laptop in a few months, and will be buying new things then.

Thanks in advance.

---

### Post by Floppyjoe on 2007-04-05
Do you get anything from:
```
lspci
```

---

### Post by windrider621 on 2007-04-06
Nope...at least I don't think so. Nothing that's obviously the device, adn when I check with iwconfig I get three 'no wireless extensions'. I'm thinking the problem is that it isn't even recognizing the card. Unfortunately, I tried sudo pccardctl ident, and got nothing. Any other suggestions? Or maybe someone who has a working internet set-up with Netgear WG311 v3 (or a similar card)?

---

### Post by windrider621 on 2007-04-07
Okay, so I found my card under lspci and lspci -n (though its listed as Network 1: UNLISTED, is that bad?). However, When I use ndswrapper and install the driver or whatever, I get that the wg311 v3 driver is an 'invalid driver!'. Help?

---

### Post by Floppyjoe on 2007-04-07
> **windrider621 said:**
> Okay, so I found my card under lspci and lspci -n (though its listed as Network 1: UNLISTED, is that bad?). However, When I use ndswrapper and install the driver or whatever, I get that the wg311 v3 driver is an 'invalid driver!'. Help?
Did you have the .sys file in the same directory as the .inf file when you installed the .inf file?
The spelling of the drivers is case sensitive.(eg. UPPER/lower Case)
You have to delete invalid drivers with the:
```
sudo ndiswrapper -e drivername
```

---

### Post by windrider621 on 2007-04-07
Yeah, both files were there, and yup I had deleted invalid drivers, but kept getting another invalid one. The one wierd thing was that it's case sensitive, but I typed in Upercase and got a driver installed (according to ndiswrapper -l) in lowercase. Is that supposed to happen?

Thanks for all the help, especially if any of this should be obvious. Like I mentioned in the first post its my first try at a Linux System. It doesn't help that I only have a wireless conection up here, so I have to switch to windows to get the help (which is why I haven't been able to provide copy/pastes from the Terminal.

---

### Post by Floppyjoe on 2007-04-07
> **windrider621 said:**
> Yeah, both files were there, and yup I had deleted invalid drivers, but kept getting another invalid one. The one wierd thing was that it's case sensitive, but I typed in Upercase and got a driver installed (according to ndiswrapper -l) in lowercase. Is that supposed to happen?

Thanks for all the help, especially if any of this should be obvious. Like I mentioned in the first post its my first try at a Linux System. It doesn't help that I only have a wireless conection up here, so I have to switch to windows to get the help (which is why I haven't been able to provide copy/pastes from the Terminal.
As long as you enter the drivername.inf file in the right case(s) you should get a valid driver if you installed it correctly. I don't know about your drivers but sometimes there is also a .bin file that needs to be in the same directory.

---

### Post by windrider621 on 2007-04-07
Hm...I don't think there was, but I can check. I know there was a third file with the .sys and the .inf, but I can't remember the extension. Would anything besides a .bin need to be there?

Also, there's a couple versions, depending on what windows version you're using (XP, 98, ect.) any idea if it matters which one I use? Some of those have files that have XP at the end of the name and a same file type that doesn't, I was going with the windows 98 since that didn't have any file with XP, but maybe I should use a more reccent version? Dunno if I'd want the file with XP (it was either .sys or .inf) or not.

Thanks again.

---

### Post by Floppyjoe on 2007-04-07
> **windrider621 said:**
> Hm...I don't think there was, but I can check. I know there was a third file with the .sys and the .inf, but I can't remember the extension. Would anything besides a .bin need to be there?

Also, there's a couple versions, depending on what windows version you're using (XP, 98, ect.) any idea if it matters which one I use? Some of those have files that have XP at the end of the name and a same file type that doesn't, I was going with the windows 98 since that didn't have any file with XP, but maybe I should use a more reccent version? Dunno if I'd want the file with XP (it was either .sys or .inf) or not.

Thanks again.
It couldn't hurt to try the other files. Sometimes that works. I don't think you need any other file besides possibly .bin if there even is one.

---

### Post by windrider621 on 2007-04-09
I think I figured part of it out, the .INF was in caps, and I was putting .inf in lowercase. I fixed that, the driver loaded and I got wg311v3 driver present, hardware present. However, then when I checked for errors with tail /var/log/messages, and there were two errors about ndiswrapper being unable to load properly. Also the one thing I had been wondering about, but didn't remember the wording was that the Network 1 is 'UNCLAIMED', that makes me think that the card isn't being seen, but at the same time all the info is correct (32 bits, wireless, ect.)

Thanks again for the continued help.

---

### Post by windrider621 on 2007-04-09
Okay, so I tried using modprobe to get the driver installed (sudo modprobe ndswrapper) and a get a message saying something along the lines of 'FATAL: Error cannot load ndswrapper (filelocation) invalid argument.' However, after that the errors in the system log ???. Any idea how to properly load the driver? 

My only guess was that the problem is originating (at least now) with the actual card, since it doesn't always show up (sudo pccardctl ident gives me nothing). Maybe once I get the OS to recognize the device, the driver will work? I don't really know. Every wireless set-up I've ever had to use has been PnP, so it's hard for me to know exactally what the problem is.

Any help is much appreciated.

---

### Post by windrider621 on 2007-04-10
Anyone have any ideas? I've tried everything I found in the couple tutorials I found on setting up a Wi-Fi connection. Thanks.

---

### Post by sh0elace on 2007-04-10
I have no clue, man. I'm going through the same kinda thing as you right now, and I can't get anything to work. The weird part about my issue is that everything *seems* like it's working, but then when I try to iwconfig nothing shows up. This is crazy... it looks okay. My .inf installed fine, modprobe'd fine, tied PCIID (11ab:1faa) to driver - all of that went through with no catch. And then it just kinda crapped out with the issue of no wireless extensions in iwconfig. I'm clueless.

---

### Post by windrider621 on 2007-04-11
Does anyone know how to get modprobe to work with ndiswrapper? I don't get why it won't work for me.  :confused:

---

### Post by windrider621 on 2007-04-15
*BUMP*

Help please!

---

### Post by Floppyjoe on 2007-04-15
Maybe you need a newer version of ndiswrapper than is available in the repositories.
[http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3](http://floppyjoes.homeip.net/phpBB2/viewtopic.php?t=3)

---

### Post by flotoonie on 2007-05-13
when I try to delete/unistall the mrv8335.inf file  with the ´ndiswrapper -e mrv8335.inf´ command I get the following msg.

couldn´t delete /etc/ndiswrapper/mrv8335.inf : no such file or directory

When I navigate there in file browser there is no file there at all.

But the ´ndiswrapper -l´ command tells me the driver is invalid

But ´ndiswrapper -i mrv8335.inf´ tells me that the driver is already installed.

I have the drivers for win2000, win98, winme, and winxp all lined up ready to try but I can´t uninstall my first attempt.

Any ideas?

---

### Post by flotoonie on 2007-05-13
Somehow I got it to work.
I tried to delete the folder rather than the driver
´ndiswrapper -e mrv8335´ instead of ´ndiswrapper -e mrv8335.inf´
That worked

Then I started again and tried the win98 driver instead of the XP_2K one.  Bingo everything worked from there.

I followed the instructions on this site

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

but this one helped me a bit too

[http://www.jimbo7.com/wiki/index.php?title=WG311v3](http://www.jimbo7.com/wiki/index.php?title=WG311v3)

Then i clicked on the networking symbol top right of the Ubuntu desktop and fumbled my way through there.

Cheers:)

---

