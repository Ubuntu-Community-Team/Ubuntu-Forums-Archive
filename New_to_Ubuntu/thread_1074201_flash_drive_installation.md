---
title: "flash drive installation"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by sthrnpagan on 2009-02-17
Ok I selected my distro and where i want it to go, however, when the download was finished it asked to reboot and to choose Unetboot from a menu, said menu did not appear and I am still on XP. Please help. I know im probably a pain and I apologize.

---

### Post by Dr Small on 2009-02-17
Just downloading the ISO file does not install it to your system. You have to burn the ISO as an image to the disc and then boot from the disc.

---

### Post by halitech on 2009-02-17
did you get the download and installing bootloader info as per the website?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by halitech on 2009-02-17
> **Dr Small said:**
> Just downloading the ISO file does not install it to your system. You have to burn the ISO as an image to the disc and then boot from the disc.

actually, using Unetbootin eliminates the need to burn the iso to cd as it uses some 'magic' to create a temp partition in the windows side to mount the info, adding a boot loader and allowing you to install any distro from windows without booting from a cd or dvd

---

### Post by Dr Small on 2009-02-17
> **halitech said:**
> actually, using Unetbootin eliminates the need to burn the iso to cd as it uses some 'magic' to create a temp partition in the windows side to mount the info, adding a boot loader and allowing you to install any distro from windows without booting from a cd or dvd
Oh. I've never heard of that. My mistake!

---

### Post by sthrnpagan on 2009-02-17
> **halitech said:**
> did you get the download and installing bootloader info as per the website?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I got the Download and when I restarted I did not see an Unetbootin option while booting. I have the ISO file downloaded. CAn i just use that with Unetbootin?

---

### Post by halitech on 2009-02-17
try restarting again, something doesn't sound right cause unless you have a T1 line, it should have taken a bit of time to download the ISO

---

### Post by sthrnpagan on 2009-02-17
> **halitech said:**
> try restarting again, something doesn't sound right cause unless you have a T1 line, it should have taken a bit of time to download the ISO

i downloaded the ISO from the website last night. it is saved on my desktop. That is why I got DAEMON Tools Lite. I am about to restart again. be back soon

---

### Post by halitech on 2009-02-17
ok, when you ran the Unetbootin, did you tell it to use that iso file?

---

### Post by sthrnpagan on 2009-02-17
> **halitech said:**
> ok, when you ran the Unetbootin, did you tell it to use that iso file?

was just about to do that.

---

### Post by halitech on 2009-02-17
try that and it should run properly and set up the bootloader and hopefully work

---

### Post by sthrnpagan on 2009-02-17
> **halitech said:**
> try that and it should run properly and set up the bootloader and hopefully work

thank you. it is extracting files from ISO now. I will let you know how things go when I am done.

---

### Post by sthrnpagan on 2009-02-17
ok nothing new. there must be something that I am missing. I restart like Unetbootin is asking. The only prob is that i do not see a menu like it said i would to choose from. Thanks for your help and patience. I know we can get this to work.

---

### Post by halitech on 2009-02-17
scroll down the page to where it says

Installing Other Distributions Using UNetbootin

for the type and drive options, what are you selecting there?

---

### Post by sthrnpagan on 2009-02-17
> **halitech said:**
> scroll down the page to where it says

Installing Other Distributions Using UNetbootin

for the type and drive options, what are you selecting there?

i have chosen, Hard Disk for the type and C:\ for the drive.

---

### Post by halitech on 2009-02-17
ok, it should be installing it right ....

windows 2000? XP? Vista?

---

### Post by sthrnpagan on 2009-02-17
> **halitech said:**
> ok, it should be installing it right ....

Windows 2000? Xp? Vista?

xp

---

### Post by sthrnpagan on 2009-02-18
Bump

---

### Post by sthrnpagan on 2009-02-18
I am using Unetbootin to install ubuntu with out a cd or flash drive. I have been having trouble with installation because when i restart after unerbootin finishes, i expect the bootloader to showup and it doesn't, which just boots me straight into windows. i think that the bootloader is not properly installing on my comp. How is this problem correted?

---

### Post by sthrnpagan on 2009-02-18
Is there a place to get just the bootloader?

---

### Post by sthrnpagan on 2009-02-18
I am trying to install Ubuntu 8.10 without a CD because i have no CD reader. I have tried using UNetbootin, but when i restart and im supposed to see the boot loader asking me which OS to use, it is not there. I boot straight into XP. Please Help, I have been trying for 2 days to get this to work.

---

### Post by sthrnpagan on 2009-02-18
Please I need some help. my problem is that, I am trying to install Ubuntu 8.10 without a CD because i have no CD reader. I have tried using UNetbootin, but when i restart and im supposed to see the boot loader asking me which OS to use, it is not there. I boot straight into XP. Please Help, I have been trying for 2 days to get this to work.

---

### Post by sonu 1807 on 2009-02-18
Try Wubi

---

### Post by x33a on 2009-02-18
you have to change the bios settings of your motherboard to boot from usb first.

when you start the computer, keep pressing f2 continuously till you get to the configuration screen. then go to the boot settings, and change the order of booting 

1. usb
2. hard drive
3. anything else (if available)

---

### Post by halitech on 2009-02-18
not sure, I've only used it on win2000 and it worked great for me. I wonder if XP is preventing the bootloader from being modified so you don't get the option

---

### Post by sthrnpagan on 2009-02-18
I now have a flash drive. How would I go about using it to install Ubuntu and wiping out windows?

---

### Post by sthrnpagan on 2009-02-18
i now have a flash drive. How would i go about using it to install ubuntu and getting rid of windows?

---

### Post by kk0sse54 on 2009-02-18
> **sthrnpagan said:**
> I now have a flash drive. How would I go about using it to install Ubuntu and wiping out windows?

What do you exactly plan on doing with this flash drive? Are you going to use it to install Ubuntu on it?

---

### Post by iaculallad on 2009-02-18
> **sthrnpagan said:**
> I now have a flash drive. How would I go about using it to install Ubuntu and wiping out windows?

You can now try to install Ubuntu Live ISO files on your flash drive using [unetbootin]("http://unetbootin.sourceforge.net/").

---

### Post by sthrnpagan on 2009-02-18
> **C!oud said:**
> What do you exactly plan on doing with this flash drive? Are you going to use it to install Ubuntu on it?

i was under the impression that it could take the place of the CD drive so i can install ubuntu and wipe windows.

---

### Post by smo0th on 2009-02-18
store your backup files in your flash drive and make a clean ubuntu install :D

I recommend 8.04 =)

---

### Post by sthrnpagan on 2009-02-18
> **smo0th said:**
> store your backup files in your flash drive and make a clean ubuntu install :D

I recommend 8.04 =)


that would work if i had a CD drive but I do not. was under the impression that flash drive could take the place of the CD drive and allow me to install Ubuntu and wipe windows.

---

### Post by staf0048 on 2009-02-19
In Windows get a program called "unetbootin" - google search.  

Once you have that on your windows box, fire it up and tell the program to put the .iso image on the usb stick.  It's pretty straight forward from what I remember.

Then, restart your computer.  At the BIOS startup hit F2 or F12 (or whatever it tells you to) to enter into the boot device menu.  

If your computer can boot from USB you should have a selection specifying that, along with CD-ROM, Floppy, HDD, etc.  Choose USB and let the computer boot from the device.  

You'll get a grey screen, choose "default" and that should get you to the Ubuntu livecd image.  From there you can run ubuntu off the usb forever (or until it's full) or install it onto your hard drive.

Hope this helps!!

---

### Post by sthrnpagan on 2009-02-19
> **staf0048 said:**
> In Windows get a program called "unetbootin" - google search.  

Once you have that on your windows box, fire it up and tell the program to put the .iso image on the usb stick.  It's pretty straight forward from what I remember.

Then, restart your computer.  At the BIOS startup hit F2 or F12 (or whatever it tells you to) to enter into the boot device menu.  

If your computer can boot from USB you should have a selection specifying that, along with CD-ROM, Floppy, HDD, etc.  Choose USB and let the computer boot from the device.  

You'll get a grey screen, choose "default" and that should get you to the Ubuntu livecd image.  From there you can run ubuntu off the usb forever (or until it's full) or install it onto your hard drive.

Hope this helps!!


thanks   my Bios has the option to boot from Removable. would that be the setting i choose?

---

### Post by staf0048 on 2009-02-19
Yes that sounds right.  

If it doesn't work the BIOS will just go to the next item on the list and see if an OS (operating system) is there, so you wont break anything by choosing it.

---

### Post by sthrnpagan on 2009-02-19
> **staf0048 said:**
> Yes that sounds right.  

If it doesn't work the BIOS will just go to the next item on the list and see if an OS (operating system) is there, so you wont break anything by choosing it.

thanks trying now.  will post when im done

---

### Post by sthrnpagan on 2009-02-19
i have put the Ubuntu ISO file on my flash drive using Unetbootin. once that is done i reboot like it asks. now at this point im expecting it to boot off my flash drive because of the way i set up my BIOS. all that happens is that it boots right back into windows. 

Need help, thanks

---

### Post by sthrnpagan on 2009-02-19
i have put the Ubuntu ISO file on my flash drive using Unetbootin. once that is done i reboot like it asks. now at this point im expecting it to boot off my flash drive because of the way i set up my BIOS. all that happens is that it boots right back into windows. 

Need help, thanks

---

### Post by dabomb1022 on 2009-02-19
So what are your problems anyway?

---

### Post by jocheem67 on 2009-02-19
Don't blame ubuntu just yet, this really sounds like a bios-issue.
Try to google the maker's brand on the issue...

If it was ubuntu, then you should have had the notorious message like
" no system disk, press enter to retry" or something similar.

---

### Post by bilalakhtar on 2009-02-19
try connecting the flash to another port.

---

### Post by sthrnpagan on 2009-02-19
> **dabomb1022 said:**
> So what are your problems anyway?

i have the ubuntu ISO file on my flash drive. I put it there with UNetbootin. when that program was finished it aske me to reboot and I did. Now, i have already set my BIOS to boot removable first (have 6 USB ports) after a few seconds of a blinking underscore it proceeds to boot straight into XP. what could be causing this.

---

### Post by mc4man on 2009-02-19
There are 2 different things
bios setup (many times F2) where you can change your boot order. This is a stored setting that works with some bios's, with others it doesn't.
Then there can be a boot menu screen (many times F12) where you choose what to boot off of. This is not a stored setting, basically a one time deal.

So try inserting the usb, power up, and tap on F12

Many times it's displayed quickly when you boot in top left corner what's available and what key does what

---

### Post by benmoran on 2009-02-19
> **sthrnpagan said:**
> i have the ubuntu ISO file on my flash drive. I put it there with UNetbootin. when that program was finished it aske me to reboot and I did. Now, i have already set my BIOS to boot removable first (have 6 USB ports) after a few seconds of a blinking underscore it proceeds to boot straight into XP. what could be causing this.


So I take it you have no CD-rom, and you want to use a live-usb? Unetbootin usually works flawlessly for me, so the problem may be your USB drive. Some older ones were a little finickly trying to boot from. 

At this point your next best step is to try it on another computer. Then you will know whether or not the USB stick is bootable.

---

### Post by gackt on 2009-02-19
Your thread is closed. Well i dont know what is wrong but have you tried to put something else in the drive and boot? we need to isolate the problem. if the computer managed to boot from your flash drive then certainly the iso or the configuration made by unetbootin is the problem.

---

### Post by sthrnpagan on 2009-02-19
> **benmoran said:**
> So I take it you have no CD-rom, and you want to use a live-usb? Unetbootin usually works flawlessly for me, so the problem may be your USB drive. Some older ones were a little finickly trying to boot from. 

At this point your next best step is to try it on another computer. Then you will know whether or not the USB stick is bootable.


i tried it on another computer and it worked. all i had to do was play with that comps boot sequence. Tried that on this comp but still not working. Going to try tapping F12 while it boots.

---

### Post by Mercury_Alpha on 2009-02-19
> **sthrnpagan said:**
> i have the ubuntu ISO file on my flash drive. I put it there with UNetbootin. when that program was finished it aske me to reboot and I did. Now, i have already set my BIOS to boot removable first (have 6 USB ports) after a few seconds of a blinking underscore it proceeds to boot straight into XP. what could be causing this.

Some motherboards require you to hold down some keys during the POST (power on self-test) to trigger a boot from a USB device. And with other motherboards, "boot removable" only refers to an external hard drive or optical drive.

If there's no message during the POST that your BIOS is checking specific drives for booting (usually right before the grub menu appears), then there's probably a key combo you need to hit. I'd recommend checking the manual.

---

### Post by sthrnpagan on 2009-02-19
> **Mercury_Alpha said:**
> Some motherboards require you to hold down some keys during the POST (power on self-test) to trigger a boot from a USB device. And with other motherboards, "boot removable" only refers to an external hard drive or optical drive.

If there's no message during the POST that your BIOS is checking specific drives for booting (usually right before the grub menu appears), then there's probably a key combo you need to hit. I'd recommend checking the manual.



ok got it to boot off of flash. YAY!!!:popcorn:   but when the screen goes all tan when its about to get going with install. the screen goes black and all I see is my cursor in the middle of the screen. is there a fix?

---

### Post by Mercury_Alpha on 2009-02-19
> **sthrnpagan said:**
> ok got it to boot off of flash. YAY!!!:popcorn:   but when the screen goes all tan when its about to get going with install. the screen goes black and all I see is my cursor in the middle of the screen. is there a fix?

It's possible that there's just low through-put. Sometimes the USB ports on the front of the computer are slow, while the ones coming out the backplane are high-speed. If you're feeling patient, you may just want to let it sit for a few minutes and see what happens.

Edit: Low USB through-put can also be caused by plugging in multiple active USB devices into an external hub. Your best bet is to plug this thumb drive right into one of the ports on the backplane (where the mouse and keyboard get attached), assuming you haven't already.

---

### Post by sthrnpagan on 2009-02-19
> **Mercury_Alpha said:**
> It's possible that there's just low through-put. Sometimes the USB ports on the front of the computer are slow, while the ones coming out the backplane are high-speed. If you're feeling patient, you may just want to let it sit for a few minutes and see what happens.

Edit: Low USB through-put can also be caused by plugging in multiple active USB devices into an external hub. Your best bet is to plug this thumb drive right into one of the ports on the backplane (where the mouse and keyboard get attached), assuming you haven't already.

it did the same thing with the Wubi install at first. too bad i forgot how i fixed it  :(

---

### Post by sthrnpagan on 2009-02-19
ok i got my comp to boot from my flash drive (had to fool with BIOS settings) but as the installer starts and the screen first goes all tan just before it gets ready to start the install, my screen will go all black and all i see is my mounse in the middle of the screen.  Is there a fix to this.

---

### Post by theozzlives on 2009-02-19
> **sthrnpagan said:**
> ok i got my comp to boot from my flash drive (had to fool with BIOS settings) but as the installer starts and the screen first goes all tan just before it gets ready to start the install, my screen will go all black and all i see is my mounse in the middle of the screen.  Is there a fix to this.

That's normal.

---

### Post by sthrnpagan on 2009-02-19
> **theozzlives said:**
> That's normal.

really???  OK  how long does it last usually?

---

### Post by halovivek on 2009-02-19
system always set the mouse cursor in the middle of the screen while starting and it quite normal.

---

### Post by overdrank on 2009-02-19
Please do not create multiple threads on the same issue. Threads merged

---

### Post by mdsmedia on 2009-02-19
Seriously, good luck with installing from USB.

I thought, when I first saw the idea, that it would be easy.

I haven't tried it yet, but I want to, simply because USB is more usual now than a CD drive. I also have an external USB HDD that has more space than both my internal hard drives combined.

Stick with it, but it's probably not as simple as your regular "burn a CD then boot the CD". Not as many have tried it so getting responses is probably harder than for a lot of things.

---

### Post by cherva on 2009-02-19
> **sthrnpagan said:**
> ok got it to boot off of flash. YAY!!!:popcorn:   but when the screen goes all tan when its about to get going with install. the screen goes black and all I see is my cursor in the middle of the screen. is there a fix?

Why don't you try to install Ubuntu from the alternate cd?

---

### Post by solwic on 2009-02-19
> **mdsmedia said:**
> Seriously, good luck with installing from USB.

I thought, when I first saw the idea, that it would be easy.

I haven't tried it yet, but I want to, simply because USB is more usual now than a CD drive. I also have an external USB HDD that has more space than both my internal hard drives combined.

Stick with it, but it's probably not as simple as your regular "burn a CD then boot the CD". Not as many have tried it so getting responses is probably harder than for a lot of things.

The USB worked great for me...it was easily three times faster than CD on my machine.  

I had to press F10 and select the flashstick...after that it worked like a charm.  I was posting on these forums while the installer ran beside the firefox window...

As for the cursor in the middle of a black screen...mine does that, too.  Usually if you just wait it out it goes away.  If your USB is extraordinarily slow, you may have to wait a while.  It took 20 minutes for me to boot from LiveCD...maybe you're having similar issues here.

Good luck.  Hope you get it installed.  :)

> **cherva said:**
> Why don't you try to install Ubuntu from the alternate cd?

I don't think he has a CD Rom.......

---

### Post by staf0048 on 2009-02-19
> **sthrnpagan said:**
> really???  OK  how long does it last usually?

It usually only takes a split second for me and is easily fixable once you get the system installed.  If you're waiting more than say 10 seconds, then I'd venture to say that your computer is hanging somewhere during the process.

It's been a while since I was last on here, were you able to get everything going?  You were obviously having lots of trouble.  It might help to know exactly what make/model of computer you have if you're still experiencing issues.

---

### Post by sthrnpagan on 2009-02-19
> **staf0048 said:**
> It usually only takes a split second for me and is easily fixable once you get the system installed.  If you're waiting more than say 10 seconds, then I'd venture to say that your computer is hanging somewhere during the process.

It's been a while since I was last on here, were you able to get everything going?  You were obviously having lots of trouble.  It might help to know exactly what make/model of computer you have if you're still experiencing issues.


i have let it sit for over an hour hoping it would come out of the black screen. It has not. Anyone know a way to fix this?

---

### Post by sthrnpagan on 2009-02-19
bumpity bump   :D

---

### Post by staf0048 on 2009-02-19
Ok, I was going over some of your posts from the other day and noticed that at one point you had Ubuntu installed and were posting from within it.  Is this correct?  Is what you're doing now a complete re-install or did you go through the system recovery options?  

I'm a bit confused about what's happening since it looks like you had it working once.  One possibility is that you somehow broke X.  

Try this:

Restart the computer.  After the BIOS screen the system starts Grub.  Hit escape before it gets to 0.  You'll be given a couple of kernel options.  Choose the first one from the top that has Recovery Mode after it.  

There will be a bunch of text flashing across the screen that will probably be too fast to read.  After a while you'll be prompted with a MS-DOS style interface.  Arrow down to "Try to Fix X-server."  That will go through the process of restalling X to it's original configuration and *hopefully* get you back up and running.

---

### Post by staf0048 on 2009-02-19
FYI - I should note that I only use Hardy so things may be a little different under Intrepid.  I don't know though 'cause I've never tried it.

---

### Post by sthrnpagan on 2009-02-19
> **staf0048 said:**
> Ok, I was going over some of your posts from the other day and noticed that at one point you had Ubuntu installed and were posting from within it.  Is this correct?  Is what you're doing now a complete re-install or did you go through the system recovery options?  

I'm a bit confused about what's happening since it looks like you had it working once.  One possibility is that you somehow broke X.  

Try this:

Restart the computer.  After the BIOS screen the system starts Grub.  Hit escape before it gets to 0.  You'll be given a couple of kernel options.  Choose the first one from the top that has Recovery Mode after it.  

There will be a bunch of text flashing across the screen that will probably be too fast to read.  After a while you'll be prompted with a MS-DOS style interface.  Arrow down to "Try to Fix X-server."  That will go through the process of restalling X to it's original configuration and *hopefully* get you back up and running.

when i had it up before, i found that i had installed inside windows. will try your suggestion. thanks

---

