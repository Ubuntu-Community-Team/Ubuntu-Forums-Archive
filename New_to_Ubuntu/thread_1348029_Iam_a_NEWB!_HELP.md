---
title: "Iam a NEWB! HELP"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by Swindlerz on 2009-12-06
ok i decided to hit from Windows Xp to Ubuntu...
before i actually install it on my master computer, i've decided test it on my old computer so i dont care if it goes wrong...

system specifications 
20GB hdd (contains work and windows xp os)
9200SE Radeon 
Amd Athlon 1ghz
and i forgot the ram but system monitor states its 749.9 MiB 

First problem:
installing ubuntu- i chose **"***guided partitioning*", i suppose it was meant to resize windows xp which took the whole hdd and install ubuntu... i had an error (ive forgot what it said, iam sorry i should have made some notes before asking but assuming you know what error came up... it lead me to the partition table with the whole partition as ntfs, i had no idea how to resize it as it kept popping the error. So i gave up and deleted the partition install ubuntu 10GB as ext3 and i had no idea that it needed a root which happens to be "/"
and i done 1GB of everything else e.g. 1 GB of swap,  vars,windows, home.etc (had no idea whats important i relise what's what after reading this forum (noobie section).

but anyway problem is that i couldnt dual boot windows xp + ubuntu (at that time, yesterday), due to some unexpected error.

Second problem: **SOLVED**
Gaining access to IDE with os installed
ok i got 3 hdds IDE- 
1st is Ubuntu (which i failed to dual boot but its working, so far so good)
2nd is Windows Xp with my programs (this one better not die)
3rd is NO OS just bunch of docs + media

I've managed to boot the 1st and 3rd hdd no problem and gained accessed by mounting it managed to play and open files flawlessly.

Heres the problem now 1st and 2nd hdd if both are plugged in and computer turns on computer freezes on the bios just before grub loads...
My second attempt was to boot ubuntu first and just plug the ide cable and power... ubuntu freezes but mouse movable, ive unplugged the ide cable and ubuntu screen turns red and stops from there.

Third Problem:** SOLVED**
how the #### do i delete the folders under application>wine>Programs>PSP ISO Compressor 
yes ive managed to get wine working but psp iso compressor doesnt work so i uninstalled it and couldnt work out how to delete the folder

4th Problem: **SOLVED**
System >Admin...>Software sources 
Error 
"Failed to run /usr/bin/software-properties-gtk as user root. Unable to copy the user's Xauthorization file."

5th Problem: **SOLVED**
tried to do this in terminal but...

master@master-desktop:~$ sudo apt-get update
[sudo] password for master: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB
Get: 1 [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release.gpg [197B]  
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release
Get: 2 [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release [4033B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources
Ign [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources          
Hit [http://repository.cairo-dock.org](http://repository.cairo-dock.org) intrepid/cairo-dock Packages   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 198B in 0s (460B/s)
Reading package lists... Done
W: GPG error: [http://repositok](http://repositok) i decided to hit from Windows Xp to Ubuntu...

6th problem: **ANSWERED**
Windows Xp run youtube smoothly whereas Ubuntu doesnt given i installed the plugins...
Ubuntu runs it slower than Windows xp and its choppy. What could be the problem?

7th Problem: **ANSWERED **(Wine is not fully compatible)
Why does wine run window xp games slower than windows xp?
game tested: Warcraft 3 since youtube users had sucess...

General Question: 

Qu 1:** SOLVED **( Keyboard Shortcuts +Custom Shortcut using "gnome-system-monitor"  )
Is there any way to open system monitor (task manager) without having to click with mouse
 e.g. alt+ctrl+del  
programs crash in full screen no idea how to fix it, i just restarted the comp

Qu 2: 
Is there a way to start the vgui via the terminal?
(on windows if explorer doesnt start i tend to alt+ctr+del run "explorer.exe" to start the desktop if it crash.

Qu 3:
Is it possible to boot liveusb (ubuntu) from a livecd (ubuntu)?
(or another method to bootlive usb but it must support all other hardware computers)

I apologise if there's anything that doesnt make sense, i will re-type and try my best to inform you the problem i am getting... 

Many thanks to any user that participated to help me answer or solve my problems,
yes i agree there i have a lot of problems but if i can solve these problems i can try help others solve if they have the same problem.

---

### Post by sandyd on 2009-12-06
THird Problem.
go into /home/username/.wine/drive_c/
that is the equilivent of a C: drive
if you want to delete the menu items, go into /home/username/.local/share/applications/Wine.

fifth problem
```

wget -q http://repository.cairo-dock.org/cairo-dock.gpg -O- | sudo apt-key add -  

```6th problem
whats your video card. and installed drivers for them yet?

7th problem
wine is work in progress.


general question
full screen games: everyone has problems with these. 
instead of crashing your computer,
press ctrl+print screen
hold them down, then hold each of these keys for one second R E I S U B.

or is it alt printscreen?

---

### Post by BDNiner on 2009-12-06
2nd problem

You should never unplug and replug IDE devices while the computer is on. The is a very good chance that you will damage the hard drive and lose the data.

What error message displays when the computer freezes if any? Are there any system warning beeps? How do you have the devices arranged on your IDE cables?

---

### Post by Swindlerz on 2009-12-06
thanks [carlee]("http://ubuntuforums.org/member.php?u=717412"): 
you solved problem 3 and 5 which i have no idea how you know the code (straight off)
"wget -q [http://repository.cairo-dock.org/cairo-dock.gpg](http://repository.cairo-dock.org/cairo-dock.gpg) -O- | sudo apt-key add -"
for the 6th problem i've no idea but my visual effects work. 
as for general qu: it was alt + print screen and i held R down... it crashed the comp and rebooted.. i just wanted it to close the program or window like alt+ F4 in windows or something that gets the task manager up so i can end task.

thanks [BDNiner]("http://ubuntuforums.org/member.php?u=302617") for contributing and your quick response...
there are no error messages it just freezes but mouse is movable. No warning beeps, at all but i can see the comp processing. One as Primary and other as secondary well it should be i forgot how the pins were layed out. How is it meant to be layed out so when i have time i have a good look at it since i dont want to wake the house up late night.

---

### Post by Swindlerz on 2009-12-07
Attempt to install ati driver but have an error? **SOLVED**

Problem: 
master@master-desktop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
master@master-desktop:~$ sudo apt-get install xorg-driver-fglrx
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
master@master-desktop:~$

---

### Post by nothingspecial on 2009-12-07
Have you got software centre or synaptic package manger open?

You can only run one instance of apt at a time

---

### Post by Swindlerz on 2009-12-08
Thank for your help, nothingspecial.

Question:
Is it possible to Boot usb drives via the ubuntu live cd?
since if I press other options F6 it leads me to a command prompt "boot..."

I would like to know because I've decided to put ubuntu as live usb but not all motherboard (or their bios) can boot via usb. There is other ways like using a cd/ floppy/ internal hdd     but it is specifically one drive letter; if I try using a cd/floppy/internal hdd it wouldnt work since the drive letter would be different.

---

### Post by nothingspecial on 2009-12-08
I am unsure what you asking. Do you want to split your computer in 2 and have ubuntu and windows?

In that case, yes :D

Or do you want to run ubuntu from a cd?

Yes again, although in my opinion there are distributions better suited to that.

In short, what exactly do you need instructions on how to do.

---

### Post by ukripper on 2009-12-08
Second problem- If nothing else works try changing jumper (obviously afetr turning your computer off and taking out power cable) from back of your HDD to Cable Select(CS) . this would avoid any confusion BIOS is getting about your drive.

---

### Post by Swindlerz on 2009-12-08
thanks [ukripper + ]("http://ubuntuforums.org/member.php?u=229569")[BDNiner]("http://ubuntuforums.org/member.php?u=302617") 
Problem 2 is now solved... I removed the jumper and used another jumper from another hdd. It is now working. No idea why but if i use the jumper (or should i say the faulty one), problem occurs.

reply to nothingspecial
I want to boot the liveusb but the some systemhardware doesnt support this.
I do not want to boot the livecd as i would not be able to save changes e.g. installing wine, dock, drivers.etc
I was wondering if the livecd (ubuntu) can boot the liveusb as one of the options F7 lets you type the command (boot:)

In short i need a method to boot a liveusb that supports all computer hardwares given i can at least boot a cd.

---

### Post by ukripper on 2009-12-08
> **Swindlerz said:**
> thanks [ukripper + ]("http://ubuntuforums.org/member.php?u=229569")[BDNiner]("http://ubuntuforums.org/member.php?u=302617") 
Problem 2 is now solved... I removed the jumper and used another jumper from another hdd. It is now working. No idea why but if i use the jumper (or should i say the faulty one), problem occurs.



Jumpers connectors may be worn out or connection between metal pins maybe blocked inside (jumpers are suppose to supply connection between HDD pins) - it can happen. Use torch to see inside of the faulty jumper and see if the metal pins are not obstructed by plastic inside.

---

### Post by zkriesse on 2009-12-08
> **BDNiner said:**
> 2nd problem

You should never unplug and replug IDE devices while the computer is on. The is a very good chance that you will damage the hard drive and lose the data.

What error message displays when the computer freezes if any? Are there any system warning beeps? How do you have the devices arranged on your IDE cables?
Agreed....never ever ever unplug IDE devices while you're using on the pc.

---

### Post by ukripper on 2009-12-08
> **ZachK_ said:**
> Agreed....never ever ever unplug IDE devices while you're using on the pc.

Some people want to learn it hard way I guess.

---

### Post by zkriesse on 2009-12-08
> **ukripper said:**
> Some people want to learn it hard way I guess.
I guess...sad...let's fix that shall we? :)

---

### Post by ukripper on 2009-12-08
> **ZachK_ said:**
> I guess...sad...let's fix that shall we? :)

:) always in!

---

### Post by heyho on 2009-12-08
Regarding your choppy flash playback, there have been some problems with recent versions of flash/ubuntu.  Worth trying on as many flash sites as you can to see if it always happens.

Also, you appear to have a 1Ghz processor, which I would say is right on the edge of coping with flash playback.  On the official flashplayer site, a 450Mhz processor is listed for windows, but 800Mhz for linux.  I have an old 1Ghz AMD tower, and it struggles to play flash.

---

### Post by Swindlerz on 2009-12-08
> **heyho said:**
> Regarding your choppy flash playback, there have been some problems with recent versions of flash/ubuntu.  Worth trying on as many flash sites as you can to see if it always happens.

Also, you appear to have a 1Ghz processor, which I would say is right on the edge of coping with flash playback.  On the official flashplayer site, a 450Mhz processor is listed for windows, but 800Mhz for linux.  I have an old 1Ghz AMD tower, and it struggles to play flash.

yes your right just checked "http://www.adobe.com/products/flashplayer/systemreqs/"
i thought linux will require less resource but yeah this should be the reasoning.
I always thought its my graphics card not installed (i find it too complicated to install)

thanks heyho

---

### Post by BDNiner on 2009-12-08
Nice to hear that you have some of your issues resolved. I attempted to install an ATI card (on board card on my MB) but gave up after a weekend. I took the Nvidia card out of my 2nd computer and bought a replacement for the 2nd machine.

---

