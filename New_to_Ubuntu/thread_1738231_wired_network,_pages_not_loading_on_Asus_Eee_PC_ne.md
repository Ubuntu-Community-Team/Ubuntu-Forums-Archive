---
title: "wired network, pages not loading on Asus Eee PC netbook"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by agnisflugen on 2011-04-24
okay, so this is a two part question. first of all, i'm using an Asus Eee PC 1215T. i  installed the ubuntu desktop version 10.10 last night. everything seems to be okay, but every now and then the internet stops working. i'm using a wired connection. when i click on the little up and down arrows at the top left of my screen it says, "wired network connection active" and the internet is still working on my other laptop so it's gotta be this netbook.  i check the error console and i get the following message: "unknown property border-radius declaration droped" so i try to google the problem and someones suggests it's a problem with firefox,  i thought i'd try downloading Google chrome for linux, but here's my question: how can i tell if my netbook is 32 bit or 64 bit? and my second question: anybody else experiencing this issue and if so how did they remedy it? 

netbook: Asus Eee PC 1215T
OS: ubuntu desktop version 10.10
error message: unknown property border-radius declaration droped
browser: firefox
internet connection: wired

---

### Post by agnisflugen on 2011-04-24
i also wanted to add, the only way i can get the netbook to connect back to the internet is to turn it off and restart it, and then the pages come back up. i don't know why.

---

### Post by agnisflugen on 2011-04-24
anybody there? please help! i don't know how to tell if i'm 32 or 64 bit :(

---

### Post by gandaran on 2011-04-24
type in terminal
```
uname -a
```
this will show what ubuntu version 32-bits or 64-bits (not computer)

---

### Post by josephmills on 2011-04-24
hi there could you press ctrl_alt+t  then type in ```
sudo lshw -c network
``` [b]it take a min to load
[/b] and then paste that here thanks this will take a look at you networking tool the

---

### Post by agnisflugen on 2011-04-24
it's 64 bit! thanks so much!!!!! i hope switching to google chrome with solve my internet connection issues...

---

### Post by josephmills on 2011-04-24
if you go to ubuntu software center  and in the search bar type in chromium you can get chromium its the open source version of google chrome

---

### Post by agnisflugen on 2011-04-24
i tried to download  google chrome but i got the following error message:

Wrong architecture 'amd64' 

dang it!

---

### Post by agnisflugen on 2011-04-24
> **agnisflugen said:**
> i tried to download  google chrome but i got the following error message:

Wrong architecture 'amd64' 

dang it!

UPDATE:

okay. now it's working. i don't know why, but i'm glad. thank you for the all the help! i gotta figure out how to use the ubuntu software system. i didn't think about just downloading chrome directly from there. i'm so use to windows and having to download stuff from websites. i've got ALOT TO LEARN!

---

### Post by agnisflugen on 2011-04-24
okay, after spending all day on this, i hope i have solved my firefox problem. i downloaded flash aid also a firefox firefly expansion thing a ma jig, so i hope i'm able to start using it again. i mean, i'm okay with chrome, it's just that i don't like how difficult it is to get to my bookmarks. thanks again for helping me figure stuff out :)

---

### Post by josephmills on 2011-04-24
please take a look at the pic for bookmark help. Also have you tried Opera?

---

### Post by agnisflugen on 2011-04-24
> **josephmills said:**
> please take a look at the pic for bookmark help. Also have you tried Opera?

whoa! that helped alot, thank you! maybe i could start to get use to chrome....i've never tried opera, i wonder if it's very user friendy as i'm not computer suavey...

---

### Post by agnisflugen on 2011-04-24
unfortunately, downloading chrome did not solve my internet woes. neither did adding firefox upgrades. randomly for no reason my netbook will stop connecting and the pages won't load. i'm using a wired connection and it shows that it's connected and other computers in the house are connected. the only way to resolve it is to turn the netbook off and restart it, which is getting really cumbersome. i wish i understood why it was doing this. i hope my netbook doesn't have something wrong with it :( 


 
 _**netbook**_: Asus Eee PC 1215T
 _**OS**_: ubuntu desktop version 10.10
 _**error messages in firefox**_:
- unknown property border-radius declaration dropped
-Warning: Error in parsing value for 'text-decoration'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-eeef40f9-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-eeef40f9-00098.css)
Line: 68
_**error message in google chrome**_: 
-error 105 (net: ERR_NAME_NOT_RESOLVED): The server could not be found
 _**internet connection**_: wired

---

### Post by josephmills on 2011-04-24
hi again could we see ```
lspci -nn
``` and ```
sudo lshw -C network
```thanks

---

### Post by agnisflugen on 2011-04-24
**lspci -nn**


agnis@agnis-1215T:~$ lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate [1022:9601]
00:01.0 PCI bridge [0604]: ASUSTeK Computer Inc. RS880 PCI to PCI bridge (int gfx) [1043:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f]
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g LP-PHY [14e4:4727] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
agnis@agnis-1215T:~$ 


**sudo lshw -C network**

agnis@agnis-1215T:~$ sudo lshw -C network
[sudo] password for agnis: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4313 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbefc000-fbefffff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c1
       serial: 20:cf:30:72:78:47
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI duplex=full firmware=N/A ip=192.168.1.70 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:42 memory:fbfc0000-fbffffff ioport:ec00(size=128) 
agnis@agnis-1215T:~$

---

### Post by josephmills on 2011-04-24
ok how about a ```
dmesg | grep b43
``` and a ```
lsmod | grep b43
``` thanks

---

### Post by agnisflugen on 2011-04-24
i typed both in, but it didn't do anything....no codes came up or nuthin'...

it came up like this:


agnis@agnis-1215T:~$ dmesg | grep b43
agnis@agnis-1215T:~$

---

### Post by josephmills on 2011-04-24
you do not have your driver installed? you need the 
Broadcom brcmsmac (mac80211-based softmac PCIe) and brcmfmac (SDIO) drivers
it comes with the kernel out of the box have you updated and upgraded ?
please see this 
[http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211)

but lets see a ```
rfkill list 
``` first your wifi might be blocked

---

### Post by agnisflugen on 2011-04-24
i just installed this OS yesterday. i had installed the ubuntu netbook version like a month ago, but i didn't like it and it wouldn't stay connected to the internet (like now but even worse) so last night i stayed up and reinstalled the desktop verion and afterwards i clicked on the update screen that popped up after installation, but i noticed i was still missing some stuff, like i couldn't view any videos until i downloaded Adobe, and Gimp wasn't on there so i added that...

nothing came up either when i just entered the code: rfkill list

---

### Post by josephmills on 2011-04-24
Please make sure that you are plugged into your router then please go to **system-->addmin-->synaptic package manager** then go to **settings-->repositories **then make sure all is ticked see pics then close the "software source" and go back to synaptic and press the **reload** button then **close synaptic **then go back to your terminal and type in ```
sudo apt-get update 
``` then ```
sudo apt-get upgrade
``` then ```
sudo reboot
```after rebooting tell us if you get the wifi

---

### Post by agnisflugen on 2011-04-24
i'm not very good at this :( thank you so much for being kind to me! i clicked on the link you gave me but i became overwhelmed, which do i choose? there alot on that page! i'm trying to make heads and tails of it...

---

### Post by josephmills on 2011-04-24
> **agnisflugen said:**
> i'm not very good at this :( thank you so much for being kind to me! i clicked on the link you gave me but i became overwhelmed, which do i choose? there alot on that page! i'm trying to make heads and tails of it...

please see post #20

---

### Post by agnisflugen on 2011-04-24
okay, i did as instructed and then rebooted.

i've never tried using wifi on this netbook, i'm hooked up directly to the modem, but for some reason periodically my pages will not load and i get error messages, yet the other computers in the house are picking up the wireless signal..do you think i should download some driver from [http://linuxwireless.org/en/users/Drivers/brcm80211](http://linuxwireless.org/en/users/Drivers/brcm80211) ? maybe that will help me not to loose the server...i don't know....when it starts acting up i restart it and then it's okay for a while....lulling me into a false sense of security...

---

### Post by josephmills on 2011-04-24
try going to system-->addmin-->additional  drivers after that loads is there a driver there that you can activate?

---

### Post by agnisflugen on 2011-04-24
> **josephmills said:**
> try going to system-->addmin-->additional  drivers after that loads is there a driver there that you can activate?

yes, i just activated the broadcom STA wireless driver, now i can see my wireless network name, that's cool! my wired connection is faltering, but maybe i can just plug the internet wire into my daugther's laptop and just start using this one wirelessly.

---

### Post by josephmills on 2011-04-24
ok now that wireless is working if you would like we could look into you eth0 troubles make sre that you are still pluged in to your router and then lets see a ```
lsmod | grep atl1c
``` also do you know if you are using  a pppoe or a static account?

---

### Post by agnisflugen on 2011-04-24
i get the following:


agnis@agnis-1215T:~$ lsmod | grep atl1c
atl1c                  29949  0 
agnis@agnis-1215T:~$ 


and the "atl1c" is in red

---

### Post by josephmills on 2011-04-25
ok unplug the cat5 cable(ethernet) and go to your wireless and connect to you wireless go and open firefox do you still get the error? go too two or three sites and report back

---

### Post by agnisflugen on 2011-04-25
the wireless connection is working good thus far! unfortunately the wired connection would stop working periodically, so i don't know how long this will last, hopefully forever...knock on wood....

---

### Post by josephmills on 2011-04-25
ok if you do a ```
sudo apt-get update
``` then ```
sudo apt-get upgrade 
``` then reboot and try your wifi again

---

### Post by agnisflugen on 2011-04-25
i did as instructed and rebooted, the wireless network came up lickety split. and is working as it should for now, i am happy :) the only thing is video's don't load as fast now that it's a wireless connection rather than a wired one, but whatever. the wired connection was flackey and kept getting messing up so i can live with this!

---

### Post by josephmills on 2011-04-25
if you want we can get it working I have three more questions 
one do you know if your isp is pppoe or not?
two could I please see a ```
dmesg | grep -e atl -e eth0
```
three could you please open up synaptic and type in compat-wireless in the search bar is there anything that is in green?

---

### Post by agnisflugen on 2011-04-25
> **josephmills said:**
> if you want we can get it working I have three more questions 
one do you know if your isp is pppoe or not?
two could I please see a ```
dmesg | grep -e atl -e eth0
```
three could you please open up synaptic and type in compat-wireless in the search bar is there anything that is in green?

i'm sorry, i don't know what that means..but the code yeilded the following results:

agnis@agnis-1215T:~$ dmesg | grep -e atl -e eth0
[    2.051416] atl1c 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.051434] atl1c 0000:03:00.0: setting latency timer to 64
[    2.220868] atl1c 0000:03:00.0: version 1.0.0.2-NAPI
[   17.226087] atl1c 0000:03:00.0: irq 42 for MSI/MSI-X
[   17.226583] ADDRCONF(NETDEV_UP): eth0: link is not ready
agnis@agnis-1215T:~$

---

### Post by agnisflugen on 2011-04-25
when i search for "compat-wireless" a bunch of 
"linux-backports-modules-compact-wireless" came up, they have boxes next to them that are all unchecked, none of them are in green.

---

### Post by josephmills on 2011-04-25
ok there might be an easy way to find out if you are pppoe or not but this is the only way that I know how. first go to your network connections icon(top right) then right click on it then go to connection info do you see your default route write this down. Then open up foxfire and type in your defult route where you would put ww w.whatever.com you will get a window that is your router it will ask for a password or to log in it is admin or password the username is either admin or nothing enter the password to get into your router. then start looking around for some thing like isp connection. there it will tell you what you internet service provider provides it will say that you are pppoe or static. hope that this helps wireless should work fine for a long time though. what kind of router do you have?

---

### Post by agnisflugen on 2011-04-25
when i click on my network connection it shows my wireless connection name, and then other available signals (that are my neighbors). when i right click on my wireless connection it doesn't show any info but rather it disconnects me from internet. if i click it again then i'm reconnected. i got my router from AT&T. it's the 2wire Gateway kind. one a side note, my wireless connection has been doing well. i wonder if my wired cord is junky?

---

### Post by josephmills on 2011-04-25
> **agnisflugen said:**
> when i click on my network connection it shows my wireless connection name, and then other available signals (that are my neighbors). when i right click on my wireless connection it doesn't show any info but rather it disconnects me from internet. if i click it again then i'm reconnected. i got my router from AT&T. it's the 2wire Gateway kind. one a side note, my wireless connection has been doing well. i wonder if my wired cord is junky?
if you have more then one port on your router take one end of your cable and plug it into say port 1 and on the other end putit into port#2 watch it it should lite up for port 1 and 2 watch it for a coulpe of min does the light flicker?

---

### Post by agnisflugen on 2011-04-25
okay, i did it, and the lights blinked the entire time

---

### Post by josephmills on 2011-04-25
> **agnisflugen said:**
> okay, i did it, and the lights blinked the entire time
never went to a solid green huh might be the cable try a new one

---

### Post by agnisflugen on 2011-04-25
yeah, i think you might be right. i don't know, the other laptop always stays connected when using that cord, but this netbook has trouble with it. by visual inspection the cord is kinda worn. i will feel so nerdy if that's what the trouble was all the time, but relieved at the same time that it isn't something more menacing. also, i was able to figure out how to turn on the wireless internet feature, which i never could have done without you. THANK YOU SO MUCH!!!!

---

### Post by agnisflugen on 2012-05-16
well...i never was able to get my netbook to connect to the internet directly, even after buying a new ethernet cord so i've just been using the wireless connection all this time, and then i stumbled across this today:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219662](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/219662)

so i'm wondering if that was the problem all along.....

---

