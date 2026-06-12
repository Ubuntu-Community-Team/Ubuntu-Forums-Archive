---
title: "humbly asking wificonnect help (have read up on related threads)"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by gr00 on 2007-07-24
Im clearly new to linux. I really wish to break away from windows. After building my first machine just last week, i vowed not to ruin everything by bogging it down with XP or Vista (gulps). 

installing is clearly a breeze, ive got feisty installed just fine, and one of the first topics i obviously wanted to try to get working was wireless connection. my apt layout makes wired connections impossible without rediculous 50ft wiring rig.

Mobo has built in wifi chip, identified as Realtek 8187 usb interface (0dba:8187), and have a linksys wireless g router with WPA-PSK security. Upon booting up Ubuntu, one of the first things i noticed was the net connection icon with the  dreaded <!> icon, and then began my painful research on the subject matter, referencing dozens of previous posts. 

Ive read up about ndiswrapper and loading windows drivers, specifically for rtl8187 chipsets, (using the debian files for easy installation, as well as the GUI-based 'wizard' app. ive been able to successfully load the windows drivers, (or at least i believe). running the ndiswapper -l command, i get the following output. 

```
 netrtuw : driver installed
        device (0BDA:8187) present (alternate driver: rtl8187)
```

So ive read several different threads about where to go from here, but keep running into two fundamental problems. 

A. the steps are explained but the reasoning or explanation of what each command means very little to me at best, 
B. I cant even get NetworkManager to recognize my unsecured wireless network, which is a very basic thing that the other folks posting similar threads seemed not to have any problems with. 

Ive tried in the past to run commands to disable (stop) network manager and manually configure wlan0 values as outlined by weiman (pinned thread) which were relevant to my router settings (making sure that all the 'prereqs' were fulfilled as described in his post) with no luck. Ive tried to disable/uninst NetworkManager to run Wicd (1.3.1) to try to connect to my open network with no success after tinkering with several preferences options. ive tried setting up a wpa-supplicant.conf file with some "network{...}" method as described in other posts. Ive followed step-by-step instructions on how to disable the rtl8187 native drivers with rmmod and blacklisting, but this is not well described enough to me to know if im doing something wrong here. Ive uninstalled and reinstalled ubuntu more times than i can count over the past 90 hours of constant frustration, and ive finally broken down to asking flat out for some guided help to get me at least on track to finding my way to wireless wpa connectivity. 

I really do not want to quit on this and copout and get so frustrated i run back to windows. I suppose my first step question is, "Why is my open, unsecured network not detected by NetworkManager"?

---

### Post by imdano on 2007-07-24
Did you remember to blacklist the rtl8187 driver?

---

### Post by kevdog on 2007-07-24
I think you need to use the Windows 98 drivers rather than the WinXP drivers for this chipset.  Also this post may help:

[http://ubuntuforums.org/showthread.php?t=493958&highlight=rtl8187+ndiswrapper](http://ubuntuforums.org/showthread.php?t=493958&highlight=rtl8187+ndiswrapper)

---

### Post by swampdweller on 2007-07-24
I'd swear you were me last year.

Got an RJ port?    :)

[http://ubuntuforums.org/showthread.php?t=508137](http://ubuntuforums.org/showthread.php?t=508137)

---

### Post by gr00 on 2007-07-24
i appreciate you guys sounding eager to help! 

Kevdog, ive seen panurge77's post previously, and i think followed it step by step on three different occasions to try to get my similar hardware working with absolutely no luck at all. After reading through the rest of the post, i noticed that the solution (or at least the part posted about configuring the interfaces file) would only work with WEP encryption, not WPA. 

It was after this i decided to try to open up all security on my network to see if i could then find a wireless signal. The first couple times i booted feisty i could see that i was receiving a signal from my router with the correct ssid. However, even with no encryption i could not get any pages to load. after reading more howtos and mucking with files i hadnt quite understood (and several reinstalls in the process as well i might add), i can no longer detect the same wireless signal at all, and it is a strong signal, after about the past 5 reformats (lol yes that is a lot). 

what processes ive confirmed so far to be helpful is installing the ndiswrapper utils and yes im using the win98 drivers, and using ndiswrapper -l command, i can see that the driver is loaded (and also says it has alternate driver rtl8187 loaded, despite the blacklisting)

im not sure how to proceed if i cant even get my open wireless signal to be recognized on a consistent (or even a rare) basis at this point. 

it kindof feels like the router is just plugging its ears and sticking its tongue out at me with closed eyes. 

swampdweller: i read through the post and i have to say i dont really understand what the problem is or fully understand how the solution works, but if i wanted to invest more money in my system id probably be getting a second, hassle free wireless card :P. 

am i doing something quite fundamentally wrong?



EDIT* [I]So Ive begun the process again, and upon a fresh reformat with 7.04 feisty installed, my wireless open network (linksys wireless g router) could not be even detected. 
I could only assumed that perhaps removing the native rtl8187 drivers might be helpful, and as such installed ndiswrapper-common 1.3.1 and ndiswrapper-tools v1.9, as well as the GUI plugin to help with the process (until i familiarize myself more with linux). Before loading the window drivers, ive entered the following commands
```
 sudo rmmod rtl8187 
```
and added 'rtl8187' and 'rtl' to blacklist.
```
 sudo gedit /etc/modprobe.d/blacklist
```
After this i used the GUI tool to load up Netrtuw.inf using the wind98 versions of the drivers (downloaded off the net, not from the manufacturer cd). this is what ndiswrapper -l reads out
```
sudo ndiswrapper -l
netrtuw : driver installed
        device (0DBA:8187) present (alternate driver: rtl8187)
```
After this short process, i rebooted to see if this would at all help detect my wireless connection. upon boot, the network icon is still showing the ugly orange exclamation point of wlan death, with no access points being detected (windows xp can detect at least 10 in my apt at any given time).

So i have a new question i suppose, is it pretty much the case that i cannot trust NetworkManager? [/I]

---

### Post by gr00 on 2007-07-25
Update: PROGRESS! running off of the live cd for feisty (rather than just reformatting each time which takes 20 minutes a pop). so heres my usual process at this point.

First off, a hardware recap. Using an Asus M2N32 SLI deluxe mobo with integrated WiFi (realtek 8187) and have a Linksys Wireless G router. I plugged in my WiFi antenna (hadnt thought i needed it, my laptops can pick up the 10+ signals around my apt). with the antenna, voila, i can now see several networks through NetworkManager! (of course, initially, trying to connect to any of these WPA secure networks will give me an error message saying that my hardware isnt capable to handle secured networks or something to that degree)  

```
 sudo rmmod rtl8187 
```
adding 'blacklist rtl8187' to the following file
```
 sudo gedit /etc/modprobe.d/blacklist 
```

from here, installing ndiswrapper (via deb packages from here [http://packages.ubuntu.com/feisty/net/](http://packages.ubuntu.com/feisty/net/)), using the gui interface plugin to load Netrtuw.inf from some folder (win98 drivers from the net, not the CD

double checking to see my driver is loaded properly with 
```
sudo ndiswrapper -l
```

(im not disabling networkmanager at this point btw)

then i am modding my interface file as outlined by weiman's stickied WPA settings guide for WPA1 w/essid and DHCP, also tried the mixed mode setup as well ) using this command
```
 sudo gedit /etc/network/interfaces 
```
adding the following text to wlan0

```

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid MySSID
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk XXX....XXX

```

this often times does nothing to mod the output of "iwconfig" however :(

im then typing the following commands

```
 sudo depmod -a 
```
```
 sudo modprobe ndiswrapper 
```

i have no idea what those commands do but ive been reading it constantly in steps in other similar threads. 

then adding 'ndiswrapper' to the following file
```
 sudo gedit /etc/modules  
```


Now, i go back up to networkManager to try to connect to my network, and for the first time ever, i am prompted for a WPA password! i was soooo ecstatic i almost cried. I typed it in (chose the 'show password' option to make sure i wasnt mistyping anything) and hit connect button. a minute later without a single breath, the connection failed. i tried again, only this time there is a dropbox at the bottom labeled as "type") using the TKIP option and tried to connect. After another minute of no breathing, there was no connection. 
hovering over the icon, i get the following popup descript.

```
 Waiting for Network Key for the wireless network 'MySSID'... 
```

ive done this many times with my network and no connect success. in addition, there was a different open network i tried to jump on with no success.

So now im really stuck, why wouldnt i be able to succeed from here on out!?

---

### Post by imdano on 2007-07-25
Is your network key between 8 and 63 characters using only letters and numbers?  If not, change it so that it is and try again.

---

### Post by swampdweller on 2007-07-25
I've never owned a desktop motherboard with built-in wifi,
I was wondering what it used for an antenna (unlike laptops,
desktop motherboards typically live completely inside a metal box).

I thought you were trying it open first (as in no security)?
If not, it's probably a good idea, to try the simplest case first,
before compounding the issue with WPA.

---

### Post by gr00 on 2007-07-25
Yes, my ASCII network key is in that range, and consists solely of alphanumeric characters. 

Another update, last night i finally logged on to an unsecured network 'out of the box' using the rtl8187 native drivers. as soon as i blacklist and remove that using rmmod, and install the window drivers via ndiswrapper properly, i can no longer connect to any open networks at that point. I can, however, at least get a prompt (via NetworkManager) to enter in a network key for secure connections, however that never resolves any ip address and i fundamentally seem to have even less functionality once im utilizing ndiswrapper. 

Thanks for any and all direction. Every night i feel like breaking down and booting up XP from utter frustration :( Stickin it out though as long as i can manage

---

### Post by swampdweller on 2007-07-25
So... are you still certain that you must in fact abandon the
rtl8187 drivers and resort to ndiswrapper?  Might the missing
antenna simply have started you down a long dark blind alley?

---

### Post by kevdog on 2007-07-25
Take a look at this post:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/)

Im not saying this is a long term solution, but by doing it in the way they recommend, it will give a lot of debugging output that may help to isolate the source of the problem.  Once figuring out the problem, there are ways to automate the connection process.

---

### Post by gr00 on 2007-07-25
i have this info burried in there previously but i dont at all mind reiterating, 

the original rtl8187 drivers work out of box for open, unsecured networks in feisty. however, try to connect to a network with wpa (or wep i believe, i have wpa 1 set up on router), and youll get an error message telling you that security encryption is not supported by your hardware. 

Plugging in an external antenna helped me receive signals that i wasnt previously getting (through the metal box as you put it :)  ). As such, i was able to connect to an open, unsecured network in my area and load up pages in FFox. Reiterating again, out of box, you arent even prompted for a net key if you attempt to connect to a secure network. 

KevDog: Im reading up on that post now, thank you. I have gone step by step through someone elses wpa-supplicant configs (paired up with wicd) to no avail, but that was using wicd afterall, and i cant claim that i know enough to say i didnt goof somewhere. Ill try this method tonight. thanks

---

### Post by fredj on 2007-07-26
Open a terminal and type sudo ndiswrapper -v
This will show the version of ndiswrapper utils and the required version. If these two are different then
you have the faulty version of ndiswrapper and it won't install your drivers properly.
.

---

### Post by gr00 on 2007-07-26
oyy... this news could be something very basic to fix. here is my output from ndiswrapper -v

```

utils Error: no version specified!
driver version: 1.38
vermagic: 2.6.20-15-generic SMP mod_unload 586

```

i dont know what relevance any of that means other than the driver version line, but it doesnt appear to look good :(.  I grabbed my version of ndiswrapper-common and ndiswrapper-utils off of packages.ubuntu site, (.deb versions, i havent yet learned how to compile something). 

Ill do some research as to the latest version that works correctly.

---

### Post by kevdog on 2007-07-26
You dont need the utils package to work -- the user space modules are ok.  For us to help you, you are going to have to print some error messages or something or things you have tried.  Right now you are not helping us!

---

### Post by swampdweller on 2007-07-27
Sorry I was slow to comprehend.
So, you've got wifi right out of the box.
Security is what you're working on.
Right?
You need ndiswrapper in order
for the WPA supplicant to work?
Is that it?
Security's a double-edged sword.
We lock ourselves out more often
than anyone else.
How much security do you need?
Are people really going to intercept
wifi signals in your apartment, or are
you merely trying to prevent unauthorized
connections to your access point?
If it's just the latter, you could simply
enable MAC filtering, which is completely
transparent from your end.
Then that would be that.
On the other hand, if you've got the patience,
I'm sure someone will be able to talk you
through setting up WPA, if you feel you need it.

---

