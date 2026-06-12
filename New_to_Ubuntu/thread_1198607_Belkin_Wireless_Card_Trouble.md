---
title: "Belkin Wireless Card Trouble"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by Teufel389 on 2009-06-27
Hi, not exactly sure if this is the exactly the right forum to post in, but I am pretty new (not exactly my first contact with Ubuntu, my grandparents had it when I was a kid) so I figured it works one way or the other.

I just installed Ubuntu 9.04 dual-booting with Windows Vista on my desktop and I can't get my wireless card ([Belkin Wireless G Plus]("http://www.belkin.com/support/product/?lid=en&pid=F5D7001&scid=221")) to work on Ubuntu and I have tried the wireless troubleshooting [guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#Device%20Drivers") and determined the problem is that it is disabled and as of now, I currently have no clue how to activate it.

Some screenshots (for your viewing pleasure)
[             [IMG]http://i560.photobucket.com/albums/ss44/Teufel389/Screenshot.png?t=1246139653[/IMG]         ]("http://javascript%3Cb%3E%3C/b%3E:void%280%29;")

Thanks in advance for help :grin:

---

### Post by Teufel389 on 2009-06-27
So I just found out that I need Ndiswrapper, which I've never installed before.

So far I've desperately been trying to install it and I need help. Anyone have any good guides on how to install Ndiswrapper (How to install it Offline, of course my desktop has no internet as we speak)?

Or maybe someone could talk me through.

---

### Post by reboot09 on 2009-06-28
Im kinda new myself had to use ndiswrapper  and Ndisgtk  
ndiswrapper should be on the live cd or installed so is ndisgtk ndisgtk is a graphical version of ndiswrapper 
open a terminal
type  sudo apt-get install ndiswrapper  
then type sudo apt-get install ndisgtk 
I had to do use both to get my card up hope this helps it took me days but once i got it it was easy.
let me know if this helps 
good luck
to run ndiswrapper    type ./ndiswrapper  
or ./ndisgtk to run it 
you may need to switch to that directory to run it

---

### Post by Toshubu on 2009-06-28
Hi Teufil,
You might want to do a:

**lspci** (from the command line)...So we know exactly which card you have...(if it shows up)..

---

### Post by Teufel389 on 2009-06-29
Toshubu:

Here are some screenshots, I did the lspci command and the lpsci -n.
[             [IMG]http://i560.photobucket.com/albums/ss44/Teufel389/Screenshot2.png?t=1246302503[/IMG] ]("javascript:void(0);")
lspci -n
[             [IMG]http://i560.photobucket.com/albums/ss44/Teufel389/Screenshot3.png?t=1246302542[/IMG]         ]("javascript:void(0);")
Reboot09: I can't seem to find ndisgtk or ndiswrapper in the Synpatic Package Manager, maybe it didn't come with the Live CD???

---

### Post by Teufel389 on 2009-06-29
Is Ndisctk supposed to come on the live cd? I dunno if it's supposed to be, but I could not find it.

---

### Post by Toshubu on 2009-06-29
Hi Teufel,
I have the Broadcom 4318 also, and was able to get it to work fine without the ndiswrapper or ndisgtk (I think). (I'm running 8.04, however)..I don't remember exactly how..but the thread **[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)** might shine some light on the problem..I would think this would still be applicable to versions newer than mine; according to the first post in that thread. But, I just don't know..Seems to me I suggested this to someone else...but, it was unclear as to whether it helped him, or not...Also, I seem to remember it has something to do with something called "fwcutter"..(whatever that is)..

---

### Post by Elep.Repu on 2009-06-30
I just do, Add/remove Programs, search for wireless;
install Windows Wireless Drivers,

Open it through System, 
You should have the cd with the drivers. If not, try to find the windows ones.
If x64, get xp x64. Same with 32 bit. Try 2000 ones if those don't work.

I *use* belkin, with no problem either...

After it's detected left click wireless indicator, click on connections detected.
Wireless configuration can be set to automatically connect within those preferences.

---

