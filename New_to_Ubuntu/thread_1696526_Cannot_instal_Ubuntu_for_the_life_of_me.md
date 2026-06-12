---
title: "Cannot instal Ubuntu for the life of me"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by GregMc on 2011-02-27
I have been trying to install Ubuntu for about a week now with almost no luck at all.  I have tried to install 10.10, 10.04 and about three other distros based on Ubuntu.  The only Linux OS I've been able to install and boot into (that I've tried) was PCLinuxOS.  I have actually had this problem on two different computers.  Both computers have 512 MB of RAM, one has an AMD XP 2000 1.66 Ghz and the other has an AMD Sempron 1.8 Ghz.  The problem I keep having is that after the cd loads I get the Ubuntu menu but when I hit Install Ubuntu it switches to a black screen with the flashing cursor and then the monitor just switches off like its not receiving a signal.  I have also been able to successfully install Ubuntu using the alternate boot cd but I have the same problem when it tries to boot into it.  Ive tried booting by removing the quiet and splash, and adding nomodeset boot parameters, the cds that have a safe video boot I've tried those, Ive tried everything I've come across but nothing seems to be working.  The video card on the Sempron machine is an onboard Radeon XPress 200 and I'm not sure what video card is in the other one because installing ubuntu wiped the hard drive so it has nothing that I can get to.  Not even a command line.  Both computers are this way now.  I would really appreciate any help.  I should also mention that I have used the boot cd to install Ubuntu on a virtual machine on this computer so I know the cd is good.

---

### Post by davidmohammed on 2011-02-27
you might have to use a combination of boot options  such as

nomodeset acpi=off

try nomodeset + one of the common boot options described [here]("https://help.ubuntu.com/community/BootOptions").

---

### Post by GregMc on 2011-03-25
Thanks for the answer.  Sorry I haven't replied but I took a break from trying as I was getting incredibly frustrated.
Back at it now though. :o

I finally got Ubuntu 10.04.2 installed and I can boot into and login but only by hitting ctrl+alt+F2, so I have a command line but nothing else.  I'm fairly certain it's a driver issue but I'm not totally sure.

The things I've tried to date are every boot paramater on the live cd both separately and in every combination possible as I have no idea what any of them mean.  I've purged and reinstalled xorg.  ATI no longer provides drivers for my card so I tried the generic ATI driver after checking the card was compatible.  I just got done going through all 13 pages in this thread: [http://ubuntuforums.org/showthread.php?t=1463294](http://ubuntuforums.org/showthread.php?t=1463294)  trying everything there with no luck.  

I've installed and removed fslrx(I think it is) with no luck.  

Honestly I've tried so many things I'm not even sure that I haven't deleted or changed something crucial. 

If this helps: lspci | grep VGA outputs "VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress G Series]"
and glxinfo | grep vendor gives the Error message "unable to open display" 
startx outputs:
"Fatal server error:
Server is already active for display 0 if this server is no longer running, remove /tmp/.X0-lock and start again (I did this too)

Please consult the X.Org......for help
Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit: Resource temporarily unavailable (errno 11): unable to connect to X server
xinit: No such process (errno 3): Server error."

I will try anything at this point.  I am going to try 9.10 on the other computer that is still blank and see if that installs.

Again I really do appreciate the help and I have been searching forums for what seems like forever now and have tried just about everything I've found that seems like it could remotely work.  

I'm even willing to start with a fresh install if I have made things worse in the course of my searching.

Thanks Again

---

