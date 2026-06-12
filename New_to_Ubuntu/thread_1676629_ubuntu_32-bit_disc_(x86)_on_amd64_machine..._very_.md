---
title: "ubuntu 32-bit disc (x86) on amd64 machine... very bad for me!"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by ClaudeFleming on 2011-01-27
Hi, I am new to ubuntu and have the 32-bit version installed. The 64-bit version would lock up at the boot screen. I'm using 10.4 and need to download a driver for my network adapter.

I've tried sudo apt-cdrom add
sudo aptitude update
sudo aptitude build-essential

that didn't work. I don't have internet access and can't get it on my laptop without a wireless hookup.

I also tried sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential

It complains that it can't find anything. Then it says maybe there's an architecture conflict. Problem is, the x86 cd is the only one that works on my amd64 setup. 

I have my drivers downloaded and installed. The makefile and other things are on my usb stick. 

What do I need in order to load the drivers? 

The driver is for a Realtek rtl8188ce wireless lan pci-e nic. It's rtlxxxx now instead of 8188 but you get the drift I imagine. How can I link to my usb stick and run get the necessary tools to run the run the makefile and reboot and install my driver? Can I even do it with the x86 cd or do I need to download some linux programs onto my usb stick?

sorry for the rambling, but I'm tired of not knowing how to run command-line utililties and being a hard-core unix enthusiast like the rest of you.

Thanks,

Claude

---

### Post by Nickjpost on 2011-01-27
> **ClaudeFleming said:**
>  
sorry for the rambling, but I'm tired of not knowing how to run command-line utililties and being a hard-core unix enthusiast like the rest of you.

 
[PC (Intel x86) alternate install CD]("http://releases.ubuntu.com/10.10/ubuntu-10.10-alternate-i386.iso")  may be the way to go for you if you have no internet connection. See [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/) 
As for your claim above.......here:
[[COLOR=#444444]Free Ubuntu Pocket guide by Keir Thomas[/COLOR]]("http://www.ubuntupocketguide.com/")
[[COLOR=#444444]Ubuntu website (Canonical)[/COLOR]]("http://www.ubuntu.com/")
[[COLOR=#444444]Official Ubuntu documentation[/COLOR]]("https://help.ubuntu.com/")
[[COLOR=#444444]Community documentation (searchable)[/COLOR]]("https://help.ubuntu.com/community/")
[[COLOR=#444444]Psychocats Ubuntu guide[/COLOR]]("http://www.psychocats.net/ubuntu")
[[COLOR=#444444]ZabiGG's Newbie 101[/COLOR]]("http://ubuntuforums.org/showthread.php?t=790485")
[[COLOR=#444444]Comprehensive list of weblinks about Ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?t=232059")
[[COLOR=#444444]Ubuntu-centric Google Custom Search[/COLOR]]("http://www.google.com/coop/cse?cx=001461844748502826593:hh-ikmexth4")


[[COLOR=#444444]How to get and install Ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5004671#post5004671")
[[COLOR=#444444]Using Ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5004723#post5004723")
[[COLOR=#444444]Multimedia problems and Installing Codecs[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5004922#post5004922")
[[COLOR=#444444]Installing Programs & Applications in Ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5004960#post5004960")
[[COLOR=#444444]Specific Hardware How-tos[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5004976#post5004976")
[[COLOR=#444444]Doesn't work? Ask for help[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5005011#post5005011")
[[COLOR=#444444]Books about Ubuntu / Linux[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5005069#post5005069")
[[COLOR=#444444]User submitted links[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5006304#post5006304")
[[COLOR=#444444]Ubuntu News & Blog sites[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5008928#post5008928")

---

### Post by bodhi.zazen on 2011-01-27
> **ClaudeFleming said:**
> sorry for the rambling, but I'm tired of not knowing how to run command-line utililties and being a hard-core unix enthusiast like the rest of you.

Thanks,

Claude

Honestly, by far the easiest solution it to either :

1. Purchase a linux compatible wireless card. The are less the $30 tops.

2. If that is not possible, use a wired connection until you get your wireless up an running. I do not know of any home wireless router that does not allow you to do this.

Many wireless cards work out of the box. Getting one that does not work out of the box going can be an exercise in futility (just so you know, sometimes it works and sometimes not).

---

### Post by ClaudeFleming on 2011-01-27
Now I have a new problem. I'm reinstalling x86 version but permission is denied in wubi. And it tells me to read a log file for more information, but the log file disappeared. It is not to be found on my computer.

---

### Post by ClaudeFleming on 2011-01-27
> **Nickjpost said:**
> [PC (Intel x86) alternate install CD]("http://releases.ubuntu.com/10.10/ubuntu-10.10-alternate-i386.iso")  may be the way to go for you if you have no internet connection. See [http://releases.ubuntu.com/10.10/](http://releases.ubuntu.com/10.10/) 
As for your claim above.......here:
[[COLOR=#444444]Free Ubuntu Pocket guide by Keir Thomas[/COLOR]]("http://www.ubuntupocketguide.com/")
[[COLOR=#444444]Ubuntu website (Canonical)[/COLOR]]("http://www.ubuntu.com/")
[[COLOR=#444444]Official Ubuntu documentation[/COLOR]]("https://help.ubuntu.com/")
[[COLOR=#444444]Community documentation (searchable)[/COLOR]]("https://help.ubuntu.com/community/")
[[COLOR=#444444]Psychocats Ubuntu guide[/COLOR]]("http://www.psychocats.net/ubuntu")
[[COLOR=#444444]ZabiGG's Newbie 101[/COLOR]]("http://ubuntuforums.org/showthread.php?t=790485")
[[COLOR=#444444]Comprehensive list of weblinks about Ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?t=232059")
[[COLOR=#444444]Ubuntu-centric Google Custom Search[/COLOR]]("http://www.google.com/coop/cse?cx=001461844748502826593:hh-ikmexth4")


[[COLOR=#444444]How to get and install Ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5004671#post5004671")
[[COLOR=#444444]Using Ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5004723#post5004723")
[[COLOR=#444444]Multimedia problems and Installing Codecs[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5004922#post5004922")
[[COLOR=#444444]Installing Programs & Applications in Ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5004960#post5004960")
[[COLOR=#444444]Specific Hardware How-tos[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5004976#post5004976")
[[COLOR=#444444]Doesn't work? Ask for help[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5005011#post5005011")
[[COLOR=#444444]Books about Ubuntu / Linux[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5005069#post5005069")
[[COLOR=#444444]User submitted links[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5006304#post5006304")
[[COLOR=#444444]Ubuntu News & Blog sites[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5008928#post5008928")

I meant to say that I wanted to become a hard-core linux command-line user that knows how to get almost anything to work. I know that's probably an impossible goal, but it's worth aiming for it. :)

---

### Post by ClaudeFleming on 2011-01-27
OK,

I can't get make-essential to work.

Should this get the trick done? I found it on an ubuntu site:

sudo mv /etc/apt/sources.list  /etc/apt/sources/list.old
sudo touch /etc/apt/sources.list
sudo apt-cdrom add

... loading

sudo apt-get install build-essential

Or is that for an older version?

---

