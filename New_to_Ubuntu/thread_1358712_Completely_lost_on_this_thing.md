---
title: "Completely lost on this thing"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by cyndijw on 2009-12-18
Son was on his ubuntu and something happened, not sure what, he told me he was downloading his game and it froze, when we got it started back up, then found we had no internet connection, i've tried to find it but it keeps telling me that I don't have permission to access the terminal...and that HAL could not be initiated? Nor could I be authenticated? I don't know how that is possible, because I OWN it! How can it be reset to factory standards so that we can start all over again??? This is totally frustrating!!!!:confused::confused:

---

### Post by Extract_Here on 2009-12-18
Are you directly connected to the internet? and do you have any files that you dont want to lose? you can also use the root terminal that is located in system tools. got to (system>preferences>main menu) then click on system tools and check Root Terminal. Then go to (applications>system tools>root terminal. From there on use the SUDO command to get administrative privileges. if all else fails boot from your ubuntu live cd or get one from this link [www.ubuntu.com](www.ubuntu.com) and reinstal.

---

### Post by spiderbatdad on 2009-12-18
you could try booting into recovery and adding your user to admin.
```
# usermod -a -G admin username
``` username gets substituted with your actual username.

---

### Post by audiomick on 2009-12-18
Hi.
A quick look at Wikipedia tells me that HAL means Hardware Abstraction Layer, the bit that lets the software communicate with the  harware, as I understand it.

With errors like that, although I don't know what they mean, I would be taking steps to backup anything important asap.

To me it sounds like a seriously broken system, or maybe a hardware problem. You might be able to repair it, but a new install might be unavoidable...:(

---

### Post by cyndijw on 2009-12-18
I had it connected wireless to my router before it went haywire, now it doesn't even show a connection to the net. I don't know how to get it connected back to the net, that's why I asked about factory settings, I don't have any files that would be lost as the user is a minor. It just won't let me sign on at all and keeps telling me it can't authenticate me. I'm trying to use the path you wrote, but once I get to main menu, I don't see anything that says system tools etc. I'm a Mema here and you gotta step me slow :P like I said, no files I need to keep as the user is a minor. But any help would be appreciated. And yes, it keeps saying at startup failed to initilize HAL! I've got the red ubuntu disc..guess I need to put it in my tower and some how connect it to the ubuntu to restart it???

---

### Post by audiomick on 2009-12-18
Don't know what the "red CD" is, is that a live CD? One that you can boot from with the option "try Ubuntu without changing the computer"?
If so, try booting from that. If it works, you know your hardware is ok; if you get the same error messages, then it isn't software problem.

---

### Post by cyndijw on 2009-12-21
Still not able to get it going....any simple ideas for me to try to reset this thingy back to factory settings that are easy to follow directions? :confused:

---

### Post by CaptainMark on 2009-12-21
use the cd to do a clean install, put the disk in turn off the computer and turn it back on, it should boot into a menu which gives the option of installing the system, use the whole disk. Make yourself the admin and your son a system user, that way he cant accidently mess anything up, these thingscan happen when children have the sudo password.

---

### Post by ctdahle on 2009-12-21
I learned my way around Linux by building a computer for my kids too (They are seven and five, so there was no worry about losing their data either).

I found that as I was learning my way around the command line and figuring out the "lay of the land" so to speak, I managed to completely screw things up several times in ways that I didn't know how to fix. Since I had not yet made the total switch, I just went ahead and did a full reinstall.

By the third reinstall, I figured out that it would be smart to start a notebook...an old school, hand written one, in which I wrote down every setting, every change, and every message I got back as I was trying to troubleshoot. Of course it might have been better to do it new school, I should have started a blog, recording my Linux adventure from one of the other working computers in the house while I fiddled with the new Linux box.

Sounds to me like you are at the same point, that is, you need to reinstall, telling the installer to overwrite everything on the hard drive in order to put you back to the "factory" settings.

I'm sure there are ways to clear up your kid's system by fiddling at the command line, but I'm sure those involve lots of typing in of commands as a superuser (sudo). Out of my league for sure! So reinstalling seems like the logical choice for me.

Frustrating as all this is, the intellectual pay-off is great. Take it from a guy with an ageing brain, the mental exercise is healthy.

---

### Post by cyndijw on 2009-12-21
Thanks for all the info, totally needed I assure you, only thing is, this is the mini 9 and there is no space to reload the disk back on it, I have my computer which has a tower and I wonder if I can put the disk in my tower and connect to the mini 9 and reinstall everything? Or, could I put it on a scan disk and then transfer it to the mini 9? Any suggestions are totally and completely welcome!! :popcorn:

---

### Post by adam814 on 2009-12-21
I have done network installs, but wouldn't recommend it...

The simplest solution would be to either connect an external USB CD drive to the mini (had to do it once with an HP netbook myself) or use the USB Startup Disk Creator from the Ubuntu Desktop to make a USB drive version of the LiveCD.

On mine it's under System > Administration > USB Startup Disk Creator.  You'll need a USB (flash) drive you can use for this.  If you do this the USB drive will be formatted so save anything important on it to another drive first.

That should be able to boot the mini so you can reinstall.

---

### Post by cyndijw on 2009-12-21
Thanks Adam, gonna try it now....:P

---

