---
title: "Did I kill it?"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Lilibeta on 2010-10-25
[SOLVED] (kinda)
Hi, I'm very green with Linux and am having trouble getting it to boot. 
 
I run an Acer Aspire One ZG5. It came with Windows XP Home but I was sick of Windows so I downloaded and installed Linux4One (Ubuntu 10.04.1) to run along side Windows. My intention was to switch solely to Linux once I felt comfortable with it. 
 
Well, Windows crapped out several days ago, files became corrupt, I got the BSOD and went into a rebooting loop so I decided to only boot up in Linux and once I was comfortable, remove Windows. 
 
The other night I was tired and didn't remove my flash drive (for storing .doc files and images) before I shut the machine down. When I tried to boot up this morning Ubuntu displays the splash screen but does nothing else. I tried ctrl/alt/del, got several pages of codes with final note that something was being fixed but I needed to reboot. I rebooted, same outcome, this time at the end of the code there was the words "Kernel Panic, not syncing - attempted to kill init". 
 
Any idea what is going on and what I do to fix this? I did google the issue and searched this forum first but I am very new with Linux and most answers that I found might as well be in Latin. 
 
Much appreciated, Lilibeta

---

### Post by robsoles on 2010-10-25
Welcome to UF.

I reboot with memory sticks inserted regularly, it pretty much can't harm files on the hard drive(s) without at least a little work.

It sounds as if your hard drive is failing. May I know the age of the hard drive and do you have the installer CD for Ubuntu 10.04? - It can be used for a live desktop session that can assist checking out your hard drive among other things.

Can you boot the machine with the LiveCD?

---

### Post by Lilibeta on 2010-10-25
Thank you for the welcome. 
 
The netbook is about 1.5 years old and the hard drive has already been replaced once.  The current drive is only 10 months old (no warranty anymore).  
 
I don't have the installer CD as the netbook doesn't have a CD drive.  I downloaded Linux4One but I have it stored on another computer and can made a CD or put it on a flash drive.  
 
Is it difficult to make a flash drive bootable and reinstall ubuntu from that?  
 
Much appreciated, Lilibeta

---

### Post by trikster_x on 2010-10-25
As long as you have access to another computer, it is easy to make a bootable usb drive.  [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") just download this, and it will make a bootable usb from the .iso file you downloaded.

[http://ubuntuforums.org/showthread.php?t=811397]("http://ubuntuforums.org/showthread.php?t=811397") is a guide on how to use the program.  

A little forewarning, the program will seem to hang when it gets to 9 or 10%, that is normal.  At that point it is copying the largest file to the usb drive and it takes a few minutes to complete.  Just start running it and walk away for about 10 minutes.

Once you have your bootable usb, start the computer, press f12 to get into the boot device menu, and set the usb to boot first.

---

### Post by macem29 on 2010-10-25
a little reading revealed that the message: "Kernel Panic, not syncing - attempted to kill init"
is almost always hardware failure related...the line or lines preceding that message may
shine some light on what is causing the kernel crash, can you post'm up?

---

### Post by Lilibeta on 2010-10-26
Lots of fast moving code.  Here's what I caught:
/dev/loop0 contains a file system with errors, check forced. 
/dev/loop0: Inodes that were part of a corrupted orphan linked list found. 

/dev/loop0: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. 
     (i.e., without -a or -p options)
mountall: fsck / [705] terminated with status 4 
mountall; Filesystem has errors: /

ESC and DEL repeat this error.    

I didn't get the "kill init" error again even when my cat walked across the keyboard.  

I have a three day weekend coming up so I will create a bootable USB stick from the links provided.  

Thanks again, Lilibeta

---

### Post by robsoles on 2010-10-26
When you get around to booting this machine using a USB stick set up with 10.04 on it go to "System"->"Administration"->"Disk Utility" and see if you can find your main HDD and have the disk utility check the drive for errors from the LiveCD environment.


I fear you will end up reinstalling and may find hardware issues remain in your way. I hope you have opportunity to enjoy the freedom Ubuntu can bring regardless :)

---

### Post by rado1 on 2010-10-26
If you do not want to use windows anymore, may i suggest to download ubuntu 10.10 ( maverick meerkat ) and do a fresh install ? I think this will solve your problem with grub.

---

### Post by migs73 on 2010-10-26
> **Lilibeta said:**
>    

I didn't get the "kill init" error again even when my cat walked across the keyboard.  



Was it chasing your mouse!! :P

Welcome to the forums, I hope you get your problem solved soon.

---

### Post by ikt on 2010-10-26
> **Lilibeta said:**
> /dev/loop0: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. 
     (i.e., without -a or -p options)
mountall: fsck / [705] terminated with status 4 
mountall; Filesystem has errors: /


If you get the command prompt, then run 

```
sudo fsck
```

this will try and fix your file system and *may* get you back into windows.

---

### Post by Lilibeta on 2010-10-26
@migs73: LOL, no, I suspect he was just exerting his authority over my lap!  

It seems that I do have a Linux CD!  My copy of Ubuntu Linux for Dummies arrived yesterday and it includes Linux on CD.  It may be outdated though so I'll create my own CD or stick anyway.  

I will try all of these suggestions this weekend when it's quiet and let you know how I made out. 

Thanks again!  
Lilibeta

---

### Post by robsoles on 2010-10-26
> **rado1 said:**
> If you do not want to use windows anymore, may i  suggest to download ubuntu 10.10 ( maverick meerkat ) and do a fresh  install ? I think this will solve your problem with grub.

10.04 is Long Term Support and 10.10 isn't (that I've heard). There seem  to have been a lot of posts about 10.10 not supporting plenty of hardware that  apparently worked in 10.04 (and often enough 9.10, 9.04 and 8.04).

I think Ubuntu beginners will be better off with 10.04 LTS - is just my 2 cents on that! 

> **ikt said:**
> If you get the command prompt, then run 

```
sudo fsck
```this will try and fix your file system and *may* get you back into windows.

@ikt: Lilibeta mentions trying to escape from Windows #-o

---

### Post by rado1 on 2010-10-27
i'm using 10.10 almost for a month and didn't encounter any problems with hardware. even nvidia drivers works properly. 
yes maverick is not a LTS, support expire in 2012, but with new version of ubuntu every six months it doesn't matter.

---

### Post by Lilibeta on 2010-10-27
Ok, I made a bootable USB using UNetbootin and Ubuntu 10.04.1 iso.  My netbook boots up using this but the cursor won't work (tried it twice). 

I can move around using the direction keys, but no cursor action.  

Any ideas? 
 
Lilibeta

---

### Post by macem29 on 2010-10-27
so the touchpad doesn't respond? do you have a USB mouse to try?

---

### Post by Lilibeta on 2010-10-27
No, I don't have a USB mouse unfortunately. 

The cursor just sits there, no response.  I can move about with the arrow keys, the touchpad left and right buttons respond, as does the keyboard.  So I can open applications and such, just no cursor. 

PS - I've already tried disabling/re-enabling the cursor with fn & F7.

---

### Post by ikt on 2010-10-28
> **Lilibeta said:**
> No, I don't have a USB mouse unfortunately. 

The cursor just sits there, no response.  I can move about with the arrow keys, the touchpad left and right buttons respond, as does the keyboard.  So I can open applications and such, just no cursor. 

PS - I've already tried disabling/re-enabling the cursor with fn & F7.

Have you tried something like this:

[http://ubuntuforums.org/showthread.php?t=1577700](http://ubuntuforums.org/showthread.php?t=1577700)

> Here's the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
2. Run: sudo update-grub
3. Reboot.

---

### Post by phr0ze on 2010-10-28
It really sounds like failing hardware. Windows failed, then ubuntu failed. Odds are it's all hardware and reinstalling is only going to work for so long.

You can:

Take a gamble that the failure is the hard drive (which really could just be another symptom) and replace the drive immediately.

Or run right off a bootable thumbdrive for a few weeks and ensure you have no more problems.

---

### Post by phr0ze on 2010-10-28
Dupe

---

### Post by Perseverance on 2010-10-28
> **rado1 said:**
> i'm using 10.10 almost for a month and didn't encounter any problems with hardware. even nvidia drivers works properly. 
yes maverick is not a LTS, support expire in 2012, but with new version of ubuntu every six months it doesn't matter.
Exactly !

---

### Post by Lilibeta on 2010-10-28
The cursor fails to work regardless of how I run Ubuntu (flash drive or hard drive). 
Is it worth the price to replace the hard drive?  Now that the beast is no longer under warranty, Acer doesn't want anything to do with me.  I can take it back to Best Buy for servicing but since the unit was only $250.00....  Any ideas as to what a new hard drive will cost?  I know someone who can replace it and save me the labour cost. 

As to IKT's fix, I'm willing to give it a try but again, I'm a noob.  I have no idea how to type this code in: Here's the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
2. Run: sudo update-grub
3. Reboot.

Where is Edit?  The only menu items that I have at the top are Applications Places System.  And how to I open any of these without the touchpad?  ie. for applications I've tried alt A but that doesn't work.    

Seems I just kill computers...

---

### Post by Lilibeta on 2010-10-28
[QUOTE]
As to IKT's fix, I'm willing to give it a try but again, I'm a noob.  I have no idea how to type this code in: Here's the fix:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX="i8042.nopnp"
2. Run: sudo update-grub
3. Reboot.

Where is Edit?  The only menu items that I have at the top are Applications Places System.  And how to I open any of these without the touchpad?  ie. for applications I've tried alt A but that doesn't work.    [QUOTE]

Ok, I found keyboard shortcuts to open the terminal window and locate Edit but the drop down from Edit is Copy, Paste, Select All, Profiles, Keyboard Shortucts, Profile Preferences.  Where am I entering the text?  Or am I entering the whole text including Edit into the terminal window?  The rest of the instructions I understand, just stuck on 1.

---

### Post by robsoles on 2010-10-28
Not sure that advice will work on a LiveCD but you are using a flash/USB stick as the boot medium and that's writable so maybe it will.

```
gksudo gedit /etc/default/grub
```will open the file in gedit, mine looks like this:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```The advice given means add this line (bottom ought be fine, just a line of it's own in the file)
```
GRUB_CMDLINE_LINUX="i8042.nopnp"
```Mind you, I haven't tried it so forgive me if it doesn't work.

---

### Post by robsoles on 2010-10-28
On second thoughts, look for the line that starts the same;
```
GRUB_CMDLINE_LINUX=
```
and replace that line.

---

### Post by RJ12 on 2010-10-28
If I am correct, you should probably use that as a boot parameter. When you load the Live USB, do you see a purple screen with a rectangle and circle? Push any key then and you should get to another Ubuntu screen. I can't remember the next step (I believe its press F6 then type that code i8042.nopnp in then press enter), someone should be able to guide you to entering that as a boot parameter.


By the way, Welcome to Ubuntu!

:)

---

### Post by Lilibeta on 2010-10-28
I have no idea what happened but suddenly my cursor is working.  I did nothing, entered no code because I wasn't sure what I was doing (yet). 
 
All I did was take the beast out to work in subzero weather with the intention of fussing with it during breaktime (which I am doing).  I have a USB mouse at work so I figured I'd give that a try.  I powered the little bugger up and suddenly the cursor is working!  USB mouse works too.  
 
To me it's a mystery.  Let's see how long it works for.  For now, I'm greatful for all the help (especially you robsoles) and thanks for the welcomes and patience with my noobiness.  \m/

---

### Post by robsoles on 2010-10-28
> **Lilibeta said:**
> I have no idea what happened but suddenly my cursor is working.  I did nothing, entered no code because I wasn't sure what I was doing (yet). 
 
All I did was take the beast out to work in **subzero weather** with the intention of fussing with it during breaktime (which I am doing).  I have a USB mouse at work so I figured I'd give that a try.  I powered the little bugger up and **suddenly the cursor is working**!  USB mouse works too.  
 
To me it's a mystery.  Let's see how long it works for.  For now, I'm greatful for all the help (especially you robsoles) and thanks for the welcomes and patience with my noobiness.  \m/

Sounds even more like a hardware issue. I won't mind one bit finding out I'm wrong about that. Maybe if/when it gives you trouble again a couple of minutes in the fridge (:)) will help.

---

### Post by Lilibeta on 2010-11-06
Update:  still working so far.  No idea what happened.  I hope it's not the hard drive.  My first thought was that I needed to reinstall the driver but I didn't do that either.  I know that there is code to deactive/reactivate the touchpad but I entered it.   

For now, I'm calling this SOLVED and if it gets petulant again, I'll take Rob's suggestion and toss it in the fridge or on the balcony.:P  Cold right now.  

Thanks to all, 
Lilibeta

---

