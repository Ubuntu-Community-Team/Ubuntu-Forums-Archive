---
title: "Wireless Issue"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by Aeroxin on 2010-01-27
Computer : Dell Inspiron 1525
Operating System : Ubuntu [latest]

I'm very, very new to Ubuntu and am having an issue with recognizing the wireless card.
I'm unsure of what my wireless card is or how to look for it in Window's Vista. 

So far I've tried : 
Connections - Configure VPN - Network Connections - Wireless
Add - SSID : larsons hardware - Apply

And it amounted to doing nothing, so I'm wondering what exactly I'm doing wrong?
I read on another forum about something such as " iwlist wlan0 scan " or " sudo iwlist scanning " but am unsure of how/where to put that in? 

Any type of help would be greatly appreciated.

**Edit : **
Wireless Card : Dell Wireless 1395 WLAN Mini-Card

---

### Post by J V on 2010-01-27
sorry, are you on vista or ubuntu? just to clear things up...

---

### Post by Aeroxin on 2010-01-27
Right now I'm using Vista to use the internet/wireless to ask for assistance. 

However, I'm having an issue with the wireless on Ubuntu.

I hope that clears things up? I'm horrid with explanations.

---

### Post by J V on 2010-01-27
right, ok :)

in ubuntu you should be able to right-click a little icon in the tray and select enable wireless, then left-click on it and choose the name of your network and input your password.

Tried that?

---

### Post by Aeroxin on 2010-01-27
> **J V said:**
> right, ok :)

in ubuntu you should be able to right-click a little icon in the tray and select enable wireless, then left-click on it and choose the name of your network and input your password.

Tried that?

I'll go try that right now. Shouldn't be more then a few minutes.

---

### Post by Aeroxin on 2010-01-27
Just tried that and it didn't seem to work either, unfortunately.

---

### Post by bkratz on 2010-01-27
> **Aeroxin said:**
> I'll go try that right now. Shouldn't be more then a few minutes.

If you want to find out what your wireless card is: Go to the terminal  (Applications>>Accessories>>Terminal) and type in

lspci  (that is LSPCI in lowercase) Copy/paste the output back here. It probably says something like BCM43xx.

sudo lshw -C network   " Shows interface and driver associated with each networking device"

and
sudo iwlist scan   " Will show what AP's you can "see""

sudo will require the entry of your password which will not be echoed to the terminal. Just hit enter when put in.

---

### Post by Kixtosh on 2010-01-27
> **J V said:**
> right, ok :)
 
in ubuntu you should be able to right-click a little icon in the tray and select enable wireless, then left-click on it and choose the name of your network and input your password.
 
Tried that?
 
This worked for me. It was a new installation too, with a Netgear wireless card. 
 
Look on the top right of the "panel" (the name for the "strips" on the top and bottom of your screen after a standard installation, if you're as new to Ubuntu as I am). You should see an icon that resembles a cell phone tower icon on a mobile phone, with no bars (because there's no connection yet).
 
I first clicked on that and immediately saw my network identified, along with a few others, and then clicked on the name of my network. It turned on the card and the "link" light came on instantly. A few moments later, it was working flawlessly, with all the bars displayed, just like on a cell phone (this card has a "power" light, which was alrealdy on with no working connection; and a "link" light, which was not on until the connection worked). 
 
I kept my card in the laptop during the installation process. I don't know if you did this when you were installing.

---

### Post by Aeroxin on 2010-01-27
> BCM4312 802.11 b/g

Is what came up when I went into the terminal - lspci

---

### Post by bkratz on 2010-01-27
> **Aeroxin said:**
> Is what came up when I went into the terminal - lspci

This thread should help you

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Aeroxin on 2010-01-27
So I followed the thread instructions up to :

> System Admin - Synoptic Package Mgr
Settings - Repositories - Unbuntu Software

But I get lost at :

> Check "Installable from CD-ROM/DVD" and close
Reload *(disregard connectivity errors)*

Because it doesn't give me the [Reload] Option.

---

### Post by Atzu on 2010-01-27
try sudo apt-get update (on terminal) and then continue with that :p i guess that should do it... (you need to close synaptic to run that command on terminal then open it again)

---

### Post by Aeroxin on 2010-01-27
Closed Synaptic and tried that out. The message I received was :

> Failed to fetch [http://security.unbuntu.com/unbuntu/dists/karmic-security/multiverse/il8n/Translation-en.US.bz2](http://security.unbuntu.com/unbuntu/dists/karmic-security/multiverse/il8n/Translation-en.US.bz2) Could not resolve 'security.unbuntu.com'

Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Atzu on 2010-01-27
That's because u don't have internet... did you enable using the ubuntu cd? if you did: 

try: sudo apt-get install b43-fwcutter 

You will need to have your ubuntu cd inside your comp...

EDIT!!: Oh wait u need the other driver... which i dunno how to install via apt-get >.>... if u installed this i guess u should remove it... : sudo apt-get remove b43-fwcutter

I think you should search on synaptics for bcmwl-kernel-source and install it from there

SORRY!!! >.>

---

### Post by bkratz on 2010-01-27
> **Aeroxin said:**
> Closed Synaptic and tried that out. The message I received was :

OK so you are following the no internet connectivity section

Check "Installable from CD-ROM/DVD" and close
Reload (disregard connectivity errors)
Search for "bcmwl-kernel-source"


Did you put a check mark in Installable from CD-ROM/DVD? and press the reload button? then use the search box for bcmwl-kernel-source?

That would have loaded the STA driver.

---

### Post by Aeroxin on 2010-01-27
Now just as a question before I switch over to Ubuntu to try it again, is the fact that I downloaded straight from the site rather then use the cd making a difference?

---

### Post by Aeroxin on 2010-01-27
Just went into Ubuntu and tried it. 
The only file that came up was **bcmwl-modaliases**. 
Tried it two more times and got the same thing. Hm...

---

### Post by synapsys on 2010-01-28
> **Aeroxin said:**
> Closed Synaptic and tried that out. The message I received was :Failed to fetch [http://security.unbuntu.com/unbuntu/...tion-en.US.bz2]("http://security.unbuntu.com/unbuntu/dists/karmic-security/multiverse/il8n/Translation-en.US.bz2") Could not resolve 'security.unbuntu.com'

Some index files failed to download, they have been ignored, or old ones used instead.                      

What's "u**n**buntu" ?

Usually if something is not detected, you should first check 
**System >> Administration >> Hardware Drivers**
to see if a driver is available.

---

### Post by Geezer60 on 2010-01-28
I had to do two things to get wireless to pay attention.  I had to install Ubuntu Restricted extras, and then install the NVidia drivers.  After that everything worked great.  When I crashed the whole thing and reinstalled, I had to do exactly the same thing again to get wireless.  I'm on an old HP notebook (Pavillion DV6000)

---

### Post by Aeroxin on 2010-01-28
So I got [http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source).
*(This is the package that I need, since it isn't on my ubuntu currently.)*
And decided to download both onto a flash drive, transfer them to my Ubuntu.
When I opened them up they both refused to install. 

**amd64** = Error : Dependency is not satisfiable : dkms
**i386deb** = Error : Wrong Architecture 'i386'

[U]@ synapsys
[/U]That would be a typo from fast typing in the forums.

---

### Post by synapsys on 2010-01-30
> **Aeroxin said:**
> So I got [http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source](http://packages.ubuntu.com/da/karmic/bcmwl-kernel-source).
*(This is the package that I need, since it isn't on my ubuntu currently.)*
And decided to download both onto a flash drive, transfer them to my Ubuntu.
When I opened them up they both refused to install. 

**amd64** = Error : Dependency is not satisfiable : dkms
**i386deb** = Error : Wrong Architecture 'i386'

[U]@ synapsys
[/U]That would be a typo from fast typing in the forums.



[LIST]
[*]            dep: 	[dkms]("http://packages.ubuntu.com/da/karmic/dkms") 	         Dynamic Kernel Module Support Framework
[*]            dep: 	[libc6-dev]("http://packages.ubuntu.com/da/karmic/libc6-dev") 	         GNU C bibliotek: Udviklingsbiblioteker og inkluderingsfiler
[*]            dep: 	[linux-headers-generic]("http://packages.ubuntu.com/da/karmic/linux-headers-generic") 	         Generic Linux kernel headers
[*]            dep: 	[linux-libc-dev]("http://packages.ubuntu.com/da/karmic/linux-libc-dev") 	         Linux Kernel Headers for development
[/LIST]

That package has these dependencies, so......
```
sudo apt-get install dkms libc6-dev linux-headers-generic linux-libc-dev
```
Then you can install your package. Hook up with an ethernet cable if you have to until you get the wireless working.

---

