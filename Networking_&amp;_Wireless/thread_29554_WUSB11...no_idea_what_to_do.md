---
title: "WUSB11...no idea what to do"
date: 2005-04-24
forum: Networking &amp; Wireless
---

### Post by asimon623 on 2005-04-24
Hi. My windows completely died due to spyware so I decided to go with linux and thought ubuntu would be a good selection....anways...I need to use my linkysy wusb11 to access the internet...running this 100 ft ethernet cable is just not gonna cut it....I've researched for about an hour now, and I've pretty much determined that I must be stupid.

Apparently a WUSB11 has "ATMEL" chip and so i must get a atmel driver..this i understand

There are 2 places that you can get this...one is from sourceforge and the other from this site that I got from the thread WUSB11...success!

Anyways, they have little instructions and from what I have pulled out, I need to do some compilations and do some kernel stuff....I need to figure out if I have matching kernels and some of that stuff

anyways, I downloaded ubunto today i think its called hoary 5.04...haven't done anything to it except install it. I figured out how to get to the network thing on this computer and it lists "modem" and "ethernet" no wireless thing...but under the device manager I can see something that says linksys wusb11 2.6

can any body gie me instructions that look like this?

1. download
2. click this
3. click this
4. bam your done

thanks.

---

### Post by Cal on 2005-04-25
I think the Amtel driver is built into the 2.6 kernal, but you need the firmware... 
English :  Its built in Unbuntu, you need to:
1: open a terminal (right click the desktop and select open terminal)
2: then type  - *sudo apt-get install amtel-firmware*  -

I think that will make it work.


P.S. Extracredit
while still in the terminal type

sudo apt-get install atmelwlandriver-tools
that should install extra usefull software for you wifi.

P.P.S
Good luck, I just used up all of my linux smarts...

---

### Post by asimon623 on 2005-04-25
alex@lounge:~$ sudo apt-get install amtel-firmware
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package amtel-firmware


This is what I am getting. I'm probably an idiot and am not in the right directory or some easy stuff like that but I don't know where to start.

Thanks for that information though.

---

### Post by poofyhairguy on 2005-04-26
[QUOTE=asimon623]alex@lounge:~$ sudo apt-get install amtel-firmware
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package amtel-firmware


This is what I am getting. I'm probably an idiot and am not in the right directory or some easy stuff like that but I don't know where to start.
[/QUOTE]

You are no idiot. Its just a small spelling mistake. do this instead:

sudo apt-get install atmel-firmware

Its in the Universe, so make sure you do what it takes to install stuff from there (its in the ubuntuguide).

---

### Post by Cal on 2005-04-26
[QUOTE=poofyhairguy]You are no idiot. Its just a small spelling mistake. do this instead:

sudo apt-get install atmel-firmware

Its in the Universe, so make sure you do what it takes to install stuff from there (its in the ubuntuguide).[/QUOTE]
 Thanks... my fingers type faster then my brain thinks sometimes.

---

### Post by asimon623 on 2005-04-26
[QUOTE=Cal]Thanks... my fingers type faster then my brain thinks sometimes.[/QUOTE]
 Hey Thanks For continuing to help. So I went in to "synaptic package manager" made sure that universe is on..which it now is...installed the atmel drivers...and went back to the terminal to install this and I'm still getting the same error message....and I have spelled it the correct way

---

### Post by asimon623 on 2005-04-27
up

---

### Post by Cal on 2005-04-27
Actully I think the package is in the multiverse repository.
```
sudo apt-get install atmel-firmware
``` should do it.

Are you getting a apt-get error, or a driver error?

---

### Post by asimon623 on 2005-04-27
[QUOTE=Cal]Actully I think the package is in the multiverse repository.
```
sudo apt-get install atmel-firmware
``` should do it.

Are you getting a apt-get error, or a driver error?[/QUOTE]
Package can not be found error.

---

### Post by Cal on 2005-04-28
Try searching for atmel in synaptic...  If it doesn't show up you don't have your repositories enabled.

---

### Post by asimon623 on 2005-04-29
[QUOTE=asimon623]Hey Thanks For continuing to help. So I went in to "synaptic package manager" made sure that universe is on..which it now is...**installed the atmel drivers**...and went back to the terminal to install this and I'm still getting the same error message....and I have spelled it the correct way[/QUOTE]
I found the atmel stuff in synaptic.

---

### Post by peejay on 2005-04-29
Here are the steps I used to get this card to work that I posted in a different thread:

I just installed the latest ubuntu and this card last night:

Go to [http://at76c503a.berlios.de/cvs.html](http://at76c503a.berlios.de/cvs.html)
Click the 'snapshot of the cvs repository link' and save to a disk, another partition, or by using a different method of internet access.

# sudo apt-get install build-essential linux-headers-`uname -r`

tar xzvf at76c503a-cvsroot.tar.gz
mv at76c503a CVS
cvs -d `pwd`/CVS co at76c503a

cd at76c503a
make
make install

Go to menu item System/Administration/Networking and enable and setup the device.

I think I restarted once just to be sure all of the settings "took".

---

### Post by asimon623 on 2005-04-29
Thanks pee jay...but still not working

downloaded your thing to the desktop (i have an ethernet cable in the computer now)

applications>system tools> root terminal

typed this 

sudo apt-get install build-essential linux-headers-`uname -r`

and it told me that nothing was updated  because it is already the newest version

then i did tar xzvf at76c503a-cvsroot.tar.gz

and I run into some problems: tar: at76c503a-cvsroot.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous erro

thank you

ps is anybody available for instant messaging (aim because I need to get this thing working pretty soon...aim handle...asimon623

thanks

---

### Post by asimon623 on 2005-04-29
okay...improving

i remembered reading somewhere about being in the right directories is important and you can change to the desktop by cd /home/alex/Desktop

but trudging along I get to the first CVS command and I get 

alex@lounge:~/Desktop$ cvs -d `pwd`/CVS co at76c503a
bash: cvs: command not found

I went to synaptic package manager and did a search for CVS and found one called CVS and tried to install it but it required the use of cds...

please help

---

### Post by asimon623 on 2005-04-29
hold on this may be working now

---

### Post by asimon623 on 2005-04-29
you're the man


posted without wires

maybe just add "cd <directory you downloaded to>" to your howto thingy

---

### Post by WhirlwindMonk on 2005-04-30
[QUOTE=peejay]Here are the steps I used to get this card to work that I posted in a different thread:

I just installed the latest ubuntu and this card last night:

Go to [http://at76c503a.berlios.de/cvs.html](http://at76c503a.berlios.de/cvs.html)
Click the 'snapshot of the cvs repository link' and save to a disk, another partition, or by using a different method of internet access.

# sudo apt-get install build-essential linux-headers-`uname -r`

tar xzvf at76c503a-cvsroot.tar.gz
mv at76c503a CVS
cvs -d `pwd`/CVS co at76c503a

cd at76c503a
make
make install

Go to menu item System/Administration/Networking and enable and setup the device.

I think I restarted once just to be sure all of the settings "took".[/QUOTE]

I tried this and have gotten as far as the "make" command, and it gives me the following output:

co  Makefile,v Makefile
make: co: Command not found
make: *** [Makefile] Error 127

Does anyone know what is wrong?

---

### Post by WhirlwindMonk on 2005-05-01
OK, I fixed the command not found problem. Now it's giving me file not found errors when it tries to access a directory called ".tmp_versions". Can anyone help me get passed this problem?

---

### Post by Reb on 2005-05-01
How did you fix the command not found problem with co?

---

### Post by WhirlwindMonk on 2005-05-01
[QUOTE=Reb]How did you fix the command not found problem with co?[/QUOTE]

I installed a package...but I can't remember which one. I think it was rms or rcs or something like that. If you can't find it, I'll reboot into linux and check so I can post it.

---

### Post by Reb on 2005-05-02
It was rcs, and now I'm stuck where you are/were.

---

### Post by Parkway on 2005-05-03
I get to 

cvs -d `pwd`/CVS co at76c503a

Then I get

bash: cvs: command not found

So...what next?

---

### Post by philipacamaniac on 2005-05-06
Peejay,

Did you get the ATMEL CVS drivers working with Kernel 2.6? As in, using Hoary?

---

### Post by peejay on 2005-05-08
Okay, I just got it working a second time, so here are some musings on going 
through the process again.

This was on:
Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005

To the ,v people, do:
 sudo apt-get install cvs
 mkdir ~/atmel
 cvs -d /home/USERNAME/at76c503a co at76c503a

(the path after -d should be wherever you unpacked the cvs file to)
after you've unpacked the cvs tar,gz file.

This will give you a directory called at76c503a inside your atmel directory.  CD into that directory and do the make / make install, and it should work.


Post-install:
-unplug/replug your card, to make sure the module gets loaded
-use the System/Administration/Networking option from the main menubar
-choose wireless, click properties, enter the settings
-click deactivate then activate to get the settings loaded

That's all of the steps I remember at this point.  I'll try to remember to check back here again sometime soon.

Also, I have a WUSB11v2.6, if that makes a difference, as well.

Edit (one more remembrance):
the make install command should be: sudo make install

---

### Post by philipacamaniac on 2005-05-09
I got it working in Kubuntu, and basically your instructions work. I didn't use them because I did this about a 4 days ago. But they look good.

Here's the one problem in Kubuntu: the KDE wireless configuration editor doesn't seem to affect the settings, and therefore you can't set a WEP key or SSID. You have to either do it manually with iwconfig, or download Wireless Assistant for KDE ([http://www.kde-apps.org/content/show.php?content=21832)](http://www.kde-apps.org/content/show.php?content=21832)). The Wireless Assistant works great, and even supports/scans multiple WiFi networks.

Peejay, you should put all this into a howto in the howto forum.

*Posted wirelessly from my WUSB v2.6*

---

### Post by deorca on 2005-05-19
OK, I posted this on another thread too.

Basically none of this works for me. Am using a 3Com OfficeConnect PCMCIA card which uses the atmel chipset, so it SHOULD work.

The thing that bothers me most is that iwconfig never shows the MAC address of my card, but confusingly, it seems to be able to find out the MAC address of the access point. Tried everything, or so it feels. I really have NO idea what to do short of buying a new wireless card.

Anyone know what the best-supported PCMCIA WLAN card is under Ubuntu?

---

### Post by sqwiggly on 2005-05-21
How did you fix the .tmp_versions error?

---

### Post by alive on 2005-05-23
I have a WUSB11 v2.8 and I'm having problems with getting this to work.

Install etc. works fine, I can use the network fine for a short while, but intermittently the network connection will suddenly die, and usually the keyboard locks up soon afterward (this cannot be fixed without a reboot). When it happens, running the "dmesg" command gives me something like this, at the end:

uhci_hcd 0000:00:10.0: host controller process error, something bad happened!
uhci_hcd 0000:00:10.0: host controller halted, very bad!

Earlier when I had Fedora Core 2 installed on that computer, using the same driver and the same USB adapter (except it was a different version, WUSB11 v2.4 or v2.6 I think), I had this same problem. The computer was brand new at the time; I have never gotten it connected successfully.

Any clues as to why this would happen? I don't have another way of getting on the Internet from that computer, so I would really appreciate a solution! Thanks.

Edit: By the way, I have an ASUS A7V8X MX SE motherboard if that makes a difference.

---

### Post by Reb on 2005-05-24
For the .tmp_versions problem, install linux-headers-`uname -r`.

---

### Post by joshchernoff on 2005-06-04
[QUOTE=peejay]Here are the steps I used to get this card to work that I posted in a different thread:

I just installed the latest ubuntu and this card last night:

Go to [http://at76c503a.berlios.de/cvs.html](http://at76c503a.berlios.de/cvs.html)
Click the 'snapshot of the cvs repository link' and save to a disk, another partition, or by using a different method of internet access.

# sudo apt-get install build-essential linux-headers-`uname -r`

tar xzvf at76c503a-cvsroot.tar.gz
mv at76c503a CVS
cvs -d `pwd`/CVS co at76c503a

cd at76c503a
make
make install

Go to menu item System/Administration/Networking and enable and setup the device.

I think I restarted once just to be sure all of the settings "took".[/QUOTE]
 can anyone tell me what this duz  I cant seem to get this line to work for me  ](*,) 
cvs -d `pwd`/CVS co at76c503a 

I get as far as this in the terminal 

# sudo apt-get install build-essential linux-headers-`uname -r`
this updated something with no problems 

I can un tar with :                                         tar xzvf at76c503a-cvsroot.tar.gz
I can do what ever this duz  with no erors:   mv at76c503a CVS
but when i put this in it stops  with a eror:   cvs -d `pwd`/CVS co at76c503a
I dont have the eror right off hand but i think it's some ting like cvs command not found or something like that 

I'm like 3 days new to linux and I'm winging it the best i can but I can't seem to get this right 
so a simple bitt of info on the commands will help a lott so I know what I'm doing 
should I be in root terminal or just  terminal

ps i allso have a dwl-g510 dlink 802.11g/b pci card witch duz not work right out of the box I have dun some reading and  i think it will be simpler to install the wusb11 v2.5 over insted of the  dwl-g510 
am i right for thinking this or sould i try to get the dlink up insted of the wusb
 all the info that you can give hard or not will help me thanks

---

### Post by Reb on 2005-06-05
You need to do "sudo apt-get install cvs rcs".

---

### Post by Dural on 2005-07-27
I burned the latest atmel drivers to CD since I couldn't get an Internet connection from my WUSB11 v. 2.8 network card, but I do not know how to get Ubuntu to install files from a copied directory. Is there a way to tell apt-get to install from files on a CD or the hard drive?

---

### Post by theinvictus on 2005-08-03
can I save the snapshot in windows partition, and will running those commands automatically be able to access it from there, or is there some step I will have to do to move the file to linux?

[QUOTE=peejay]Here are the steps I used to get this card to work that I posted in a different thread:

I just installed the latest ubuntu and this card last night:

Go to [http://at76c503a.berlios.de/cvs.html](http://at76c503a.berlios.de/cvs.html)
Click the 'snapshot of the cvs repository link' and save to a disk, _another partition_, or by using a different method of internet access.

# sudo apt-get install build-essential linux-headers-`uname -r`

tar xzvf at76c503a-cvsroot.tar.gz
mv at76c503a CVS
cvs -d `pwd`/CVS co at76c503a

cd at76c503a
make
make install

Go to menu item System/Administration/Networking and enable and setup the device.

I think I restarted once just to be sure all of the settings "took".[/QUOTE]

---

### Post by theinvictus on 2005-08-09
[QUOTE=peejay]
cvs -d `pwd`/CVS co at76c503a
[/QUOTE]

I get this far, but when I enter that in, it comes up with

bash: cvs: no such command

or something like that.....please help I really want to be able to use linux but without internet its worthless to me... I already tried and failed at using the windows drivers by using ndiswrapper, but that freezes my system when I try to modprove ndiswraper. HELP!

---

### Post by Reb on 2005-08-09
You need to install "cvs" in either synaptic or from the command line. This driver is in the kernel by default in breezy if waiting is an option.

---

### Post by Ivhassel on 2005-08-11
I'm also trying to set up a linksys wusb11 v 2.8 wlan card on my fresh Ubuntu install, but I can't get it working.
I have no working internet connection on that ubuntu machine whatsoever, so I downloaded the CVS snapshot on my other (windows) machine, and put it on the ubuntu machine via a USB stick.

Everything works fine up to extracting the CVS snapshot, but when i use the make command i get the 'Command not found' error.

Anyone able to help me out with this?
I'm a total linux newbie, so it's probably a very stupid mistake that I made.

I'm working on a Athlon 1GHz computer, logged in as root to do the make command, installed Ubuntu 5.04. That's all the extra info I can think of atm  ;-) 


Thanks in advance for your effort.

---

### Post by organdonersteve on 2005-08-18
I am a little lost, sorry if it has already been explained, but i burned the cvs file from that website, and put the cd in the ubuntu machine, do i just drag the files onto the desktop, or do i have to install them?  i i typed *sudo apt-get install build-essential linux-headers-`uname -r`* inot the terminal and nothing happened.
thanks for any help you can give me.
Ian

---

### Post by linux4Donkey on 2006-01-04
> Originally Posted by peejay

Go to [http://at76c503a.berlios.de/cvs.html](http://at76c503a.berlios.de/cvs.html)
Click the 'snapshot of the cvs repository link' and save to a disk, another partition, or by using a different method of internet access.

# sudo apt-get install build-essential linux-headers-`uname -r`

tar xzvf at76c503a-cvsroot.tar.gz
mv at76c503a CVS
cvs -d `pwd`/CVS co at76c503a

cd at76c503a
make
make install



I just installed the latest ubuntu and this card.

First i tryed the above and did not work so changed
"cvs -d `pwd`/CVS co at76c503a"

to

"sudo apt-get install cvs"

On the advice of a mate. This seemed to work but when i get to the 
"make"
command it fails with an error, code 127 (think some one else has had the same. Some thing to do with not finding the make file or something)

Any deas on how to solve it? (totally the first time on linux!)

---

### Post by yochanan.g on 2006-01-15
Hello everybody!
I have wusb11v4...
I have followed all the steps succesfully - until the make command...
When I run it I get several pages of errors and warnings...
The linux-headers-2.6.12-9-386 is installed
Any ideas?

---

### Post by personman on 2006-01-29
I was also getting pages and pages of warnings and syntax errors when I tried to make.  I did "sudo apt-get install gcc-3.4" and those seemed to clear up.  But I still don't see a wireless device in System > Administration > Networking.  

I unplugged my WUSB11v4 and plugged it back in, then did "tail /var/log/messages" and this is what it  said:
> Jan 29 20:27:30 computer kernel: [4295080.667000] usb 1-2 new full speed USB device using uhci_hcd and address 3
Any ideas on what I'm doing wrong?

---

### Post by personman on 2006-01-29
What's the story with ndiswrapper?  Is that what I need to try if this continues to not work?

---

