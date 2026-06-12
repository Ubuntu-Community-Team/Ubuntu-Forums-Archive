---
title: "startx unrecognised command"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by Janeleaper on 2010-01-04
I seem to have lost my OS, and I don't even know how to reinstall

Karmic (recently upgraded) on Dell Inspiron 530 Desktop

After upgrading to 9.10 endless problems with Firefox.  Yesterday Firefox crashing.  Reported bug.  Told to use apport.  Tried to use apport, got message to upgrade tzdata and try again.  

Uninstalled and reinstalled tzdata.  This was not a good idea.  When uninstalled a number of files uninstalled with it and not replaced when I reinstalled.  PC worked fine until I shut down and tried to boot up.

Won't boot.  Error 15: file not found.  Error repeated when try to use different versions of kernel.  Can get to grub screen. 
 
grub> startx
Error 27: Unrecognized command

Although a noob, I'm getting the idea I've lost my OS.  

Is there anything I can do, and if necessary how do I reinstall it?

---

### Post by charlier653 on 2010-01-04
Do you have a live CD of 9.10 or 9.04?


Failing that, do you have the ability to download and burn a copy?

---

### Post by Janeleaper on 2010-01-04
No, I don't have a cd.  Theoretically I could download and burn, but previous attempts to do this have always failed.

However, I have two other pcs and am not going to be using this one for 5 months after today (because I'm traveling), so I could acquire a cd.

I've tried a cd of 8.04 and could not find a way of booting from it.  Will it be different with 9.04 or 9.10?

---

### Post by Methuselah on 2010-01-04
It should be possible to reinstall the missing packages through the recovery mode.
The problem is, I don't know what to tell you to reinstall.
There might be a metapackage that could pull in everything you'd need to repair the system.
I am hoping for some input from someone else who can help you with this.

---

### Post by Janeleaper on 2010-01-04
Thanks Methusalah.  It's good to have a ray of hope at least.

---

### Post by Methuselah on 2010-01-04
> **Janeleaper said:**
> No, I don't have a cd.  Theoretically I could download and burn, but previous attempts to do this have always failed.

However, I have two other pcs and am not going to be using this one for 5 months after today (because I'm traveling), so I could acquire a cd.

I've tried a cd of 8.04 and could not find a way of booting from it.  Will it be different with 9.04 or 9.10?

If your hard drive is first in the boot order your computer will not boot from the CD.
Usually, there is an option to select another boot device if you press F12 while it is showing the very first screen (before any operating system comes up)

---

### Post by K.J. on 2010-01-04
The easiest way to fix this is with an Ubuntu CD (the same version you have installed). Simply "sudo apt-get install firefox".

The problem is that firefox is part of the "base install." By removing it, synaptic automagically removed everything that is part of the "base" install, including Gnome and X.

Reinstalling firefox will automatically want to install the base. As long as you haven't removed the CD-ROM from your repository list, it should grab the needed files from there.

---

### Post by Janeleaper on 2010-01-04
Thank-you.  I'll put this on hold for now.  Order the cd, and when I'm back in May I'll use the cd and see what happens.

Very grateful to both of you.

---

### Post by USB_NL on 2010-01-04
you can make a usb or sdcard install boot too if you have a bootmenu at startup or an option for booting like that in bios it uses the same iso

startx did not work because your boot wasn't completted

---

### Post by K.J. on 2010-01-04
You can also plug in with a network cable to a network that uses dhcp (otherwise you have to configure the network manually via command line) and remove the CD-ROM from the list of repositories.

Then you run "sudo apt-get update" and then "sudo apt-get install firefox" and that will download the packages from the net.

---

### Post by Janeleaper on 2010-05-25
I've now tried using the 9.10 CD without success.  sudo apt-get comes up as an unrecognised command, and attempting to boot in any of the recovery modes just gets error 15 file not found.  Does anyone have any other ideas?

I appear to have not only lost all my files (or at least those that weren't backed up), but also got a useless computer that I can't even rehabilitate by doing a fresh install of the operating system.

---

### Post by Norava on 2010-05-25
What I did when i had issues with a net install for 10.04 was set it to boot from a usb drive and plugged it in to LAN to get it to install and it worked right, not sure if it will work for any 9.0 releases but you could try.

---

### Post by Janeleaper on 2010-05-25
Sorry Norava, this is too technical for me.  I'm a noob.  I don't know what a net install is.   I don't know how to set "it" to boot from a usb ( and I don't know what you mean by "it"), and I don't know what a LAN is.

---

### Post by Norava on 2010-05-25
I'm sorry I'm awful at explaining things >.<. Basically what I'm saying is that when I was having issues with my install when it broke I used the instructions in the guide here [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) to boot the computer by plugging it in to a usb port and selecting the option to USB boot in the BIOS (The screen that you get to by pressing the key it says to in the startup screen that lets you change a lot of hardware settings) and keeping the computer plugged into the router when running the install, I'm sure there would be someway to do this without plugging it into the router but it worked for me when it was plugged in to the router during the installs. Sorry >.<

---

### Post by Janeleaper on 2010-05-25
I think you mean the boot menu by "that screen".  When I press F12 for the boot menu, I get "error 15 - file not found".  **That is **the problem.

---

### Post by mk1w86 on 2010-05-25
When you boot from the Ubuntu 9.10 LiveCD does it boot to the desktop? :-s

> I appear to have not only lost all my files (or at least those that weren't backed up)

Your files should still be there as long as you have not deleted any partitions or formatted them, if the files are important make sure to back them up **before** reinstalling Ubuntu.  I'm sure we can help you do that if necessary.

---

### Post by Janeleaper on 2010-05-25
I'm sorry I'm obviously not making myself clear.  **I cannot boot**.

When I turn on the computer I get a black screen with the message:

 Error 15 file not found.  Press any key to continue.

If I press a key I get the list of Kernels, but if I select any of them I get the Error 15 screen again.  

Exactly the same thing happens if I have the 9.10 cd in when I start the computer, or if I press F2 or F12. In other words I cannot get the setup or boot menus.

---

### Post by Eisenwinter on 2010-05-25
> **Janeleaper said:**
> grub> startx
Error 27: Unrecognized command
You get this message because you can't start X from GRUB.

First, you need to boot the kernel you wish to use, log in, and only then you can startx.

Startx is a shell command, not a GRUB command.

EDIT:

Boot into a LiveCD environment.

Open a terminal, and mount the partition which is your root partition (for example, /dev/sdb1) into /mnt/, for example. (You can mount it anywhere you want).
```
sudo mount /dev/sdb1 /mnt/
```

If it says "No such directory: /mnt", you may have to create it:

```
sudo mkdir /mnt/
```

Try to mount the partition again.

Change the working root directory to /mnt:

```
sudo chroot /mnt/
```

Go into /boot:

```
cd /boot
```

Is there a "vmlinuz" file?
Is there a "kernelXXX.img" file?

You can view all the files in that directory with the "ls" command. Note that's a small L, not a large i or a 1.

Post results here.

---

### Post by Janeleaper on 2010-05-25
I'm sorry, but I'm not getting startx unrecognised command any longer.  Please read my last post.

---

### Post by JKyleOKC on 2010-05-25
> **Janeleaper said:**
> I'm sorry I'm obviously not making myself clear.  **I cannot boot**.

When I turn on the computer I get a black screen with the message:

 Error 15 file not found.  Press any key to continue.

If I press a key I get the list of Kernels, but if I select any of them I get the Error 15 screen again.  

Exactly the same thing happens if I have the 9.10 cd in when I start the computer, or if I press F2 or F12. In other words I cannot get the setup or boot menus.Apparently your machine is still trying to boot from the hard disk, not from the CD. When you first turn the machine on, you should see a message telling you to press some key to enter setup; that key might be DEL or one of the function keys, and the message may be there for only a second or two. On my laptop it flashed by so rapidly that I had to try several times to determine what it was saying. Anyhow, press that key as soon as the message appears, and you should get to a setup screen instead of the normal boot action.

EDIT--If you wait too long, the machine will ignore your key-press and continue its "normal" boot action. Again, the time window may be very brief; you may need to press and hold the key immediately after powering on. I've had to do that on several boxes.

From that setup screen you should see several menu choices; they may be across the top of the screen, or shown as a table. One of them should include the word "boot" and that is most likely to be the one you need. Select it, and on the screen that comes up, look for an option of "boot sequence" or "boot order." Selecting that one should show a table that lists several items; the top item will most probably be "HDD 0" which is the first (or only) hard disk. Somewhere below it will be "CD" and what you need to do is bring the "CD" entry to the top of the list. Different BIOS setup programs do this in different ways so I can't be more specific. Some of them require that you edit the top entry to change it while others let you use the arrow keys to move entries up or down. The goal is to get the list showing "CD" on top with "HDD 0" or whatever was on top moved to the position just below it. When you get there, find the "Save and exit" choice and use it to save your changed settings.

EDIT--Be careful not to make any other changes in the setup area; it's possible to make a system completely unbootable by changing the wrong thing. So long as you only modify the boot sequence, though, you'll be safe.

The system should then automatically reboot, and this time should go first to the CD although it may show you a message such as "Press any key to boot from CD..." If it does, press a key and the CD should become active. When it boots from the CD, select "run without changing my system" from the menu it displays and we can proceed from there!

There are so many different BIOS setup programs that it's not possible to give you clearer step-by-step instructions without knowing the make and model of your machine. I hope these generic instructions help...

---

### Post by Janeleaper on 2010-05-25
Sorry again, but no F2 for setup does not work, as I've already explained.  Perhaps describing myself as a noob wasn't a good idea.  I do know you have to be prompt in pressing F2 or F12, but it does not make any difference, I still get the error 15 page.

---

### Post by Janeleaper on 2010-05-25
Ok, correction, there must be about .1 of a second to choose F12 to get to boot menu, although I still can't get F2 setup to work.  On F12 I chose boot from cd and got the 9.10 cd to show up.  However, I can only find out how to reinstall it, not install files from it.  Have I lost all my documents? because if I reinstall I'll wipe the disc, won't I?

---

### Post by The Cog on 2010-05-25
When you boot from the installer cd, you have the choice to install or to try without touching the hard disk. Choose the latter option. It runs Ubuntu purely from CD. Note that the Desktop gives you the "try Ubuntu" option but the "alternative" installer CD doesn't.

Once you are running the "try" live Ubuntu, you should be able to find your hard disk in Places, open it and copy all your documents to a USB stick. 

Once you've rescued them, I think an install is probably the easiest fix. Normally I'd suggest **sudo fsck /dev/sd??** replacing ?? with the appropriate partition id, but it sounds like things might be beyond fsck's help.

I personally have suspicions that this kind of behaviour is due to the ext4 filesystem. Other people will say "I've had no problems with ext4", but I have had 7 out of 7 ext4 installs die horrible filesystem corruption deaths like this, so I would suggest avoiding ext4 next time. Try ext3, reiserfs or jfs. I use jfs myself.

---

### Post by Janeleaper on 2010-05-25
I've tried the "try Ubuntu" option and it does show my hard disc, but there is a further problem.  It will not give me access to my documents because I am not the "owner".  I guess that is because I am not logged in, but I can't log in because I'm using the "try Ubuntu". Is there any way round this?

---

### Post by JKyleOKC on 2010-05-25
> **Janeleaper said:**
> I've tried the "try Ubuntu" option and it does show my hard disc, but there is a further problem.  It will not give me access to my documents because I am not the "owner".  I guess that is because I am not logged in, but I can't log in because I'm using the "try Ubuntu". Is there any way round this?Yes. Open a terminal window, and type "gksudo nautilus" which should open up Nautilus with root privileges. Normally this command will ask for your password, but the default user on the live CD has no password. If it does ask anyway, just press Enter and it should work. From there you should be able to access your documents and copy them to a flash drive.

Running under sudo or gksudo gives you access to everything; it also will make "root" the owner of the copied documents, but once you have saved them off and re-installed the system, you can once again use the "gksudo nautilus" command to access them on the flash drive and copy them back to your home directory. This time you will probably be asked for your password, and it may not appear to be taken -- but it really will be going in so just keep typing it. You'll also need to select each file's "properties" in Nautilus, while still running as root, and change the owner and group back to yourself. Once that is done you should be back in good shape.

I use Xubuntu rather than Ubuntu itself, so have a different file manager and I may not have described the commands exactly as they appear in Ubuntu, but some of the other folk will jump in and help if I've missed anything significant here...

---

### Post by Janeleaper on 2010-05-25
ubuntu@ubuntu:~$ gksudo nautilus 
(nautilus:3485): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed 
Initializing nautilus-gdu extension 

** (nautilus:3485): WARNING **: No marshaller for signature of signal 'UploadFinished' 

** (nautilus:3485): WARNING **: No marshaller for signature of signal 'DownloadFinished' 

** (nautilus:3485): WARNING **: No marshaller for signature of signal 'ShareCreateError' 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory 
Please ask your system administrator to enable user sharing.

---

### Post by JKyleOKC on 2010-05-25
That's going to take a Nautilus expert to sort out!

There are other ways to get your files to safety but they're a bit more complicated. Hopefully some of the other forum members will chime in at this point and have some suggestions...

---

### Post by Janeleaper on 2010-05-26
Actually, my files were there.  I don't know what that message meant, but I was able to copy my documents onto a usb.

I have reinstalled 9.10 from disc, upgraded to 10.04 and reinstalled my other programmes, gnucash, gramps, and Skype. 

 Everything is working.  I've lost my bookmarks in Firefox.  Maybe I could have found them in Nautilus and copied them onto the usb, but I forgot.

I still have the original glitch that I had with 9.10, which is that I can't get BBC iplayer "listen again" programmes to play.  I know other 9.10 users don't have this problem, so it is a mystery, and disappointing that it still doesn't work in 10.04.

I am mega-relieved to have my files back.  My photos were backed up on Flickr, and I had a few documents on disc, but I was going to lose an awful lot of documents if I hadn't got this sorted.

So huge amounts of gratitude to you JKyleOKC, and everyone else who contributed to this thread.

---

### Post by JKyleOKC on 2010-05-26
That's good news! And you're quite welcome. Sometimes those of us who have used Linux for a while forget how many little steps we take to get things done, and "cut straight to the chase" in ways that just don't make sense to anyone who hasn't yet begun to take those steps automatically.

---

