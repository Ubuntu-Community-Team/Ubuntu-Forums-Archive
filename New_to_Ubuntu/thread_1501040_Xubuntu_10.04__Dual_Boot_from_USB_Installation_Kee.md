---
title: "Xubuntu 10.04 :: Dual Boot from USB Installation Keeps Failing"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by adamsiddhi on 2010-06-03
Hello,

I started attempting to install Xubuntu 10.04 on my older  laptop. I followed all the instructions from the tutorial:

[[COLOR="Purple"]http://www.pendrivelinux.com/put-xubuntu-10-04-on-a-flash-drive-with-windows/[/COLOR]]("http://www.pendrivelinux.com/put-xubuntu-10-04-on-a-flash-drive-with-windows/")

but it does not seem to work. Specifically I am using:

**LapTop**
[LIST=1]
[*]Acer TravelMate 2300
[*]MS Windows XP SP2
[*]Intel Celeron(R)M
[*]1500mhz processor
[*]504mb RAM
[/LIST]

**USB**
[LIST=1]
[*]Sans Disk 8gb USB flash drive)
[/LIST]

**Software**
[LIST=1]
[*]Universal USB Installer
[LIST]
[*]xubuntu-10.04-desktop-i386
[*]2GB persistent file (casper rw file)
[/LIST]
[/LIST]

So first I create the Xubuntu USB. I follow the straight forward instructions and Universal USB Installer says the creation of the Xubuntu USB drive is successful upon comlpetion. Then I restart my computer and switch to USB in BIOS, save and continue. My computer loads the Xubuntu boot screen successfully. On this screen I can see the Xubuntu logo at the top of the screen. Below that I see the "Installer Boot Menu". The boot menu consists of these items from top to bottom:

[LIST]
[*]Run Xubuntu from this USB
[*]Install Xubuntu from Hard Drive
[*]Test Memory
[*]Boot from 1st Hard Disk
[*]Advanced Options(there are none. only an option to go back to the menu)
[*]Help
[/LIST]

So to continue with describing what happens ... the same thing happens when I choose either:

[COLOR="Blue"]Run Xubuntu from this USB[/COLOR]

or

[COLOR="Blue"]Install Xubuntu from Hard Drive[/COLOR]

The first thing I see is some text at the top of the screen that reads:

**Loading /casper/vmlinuz..............**(2 lines of dots)
**Loading /casper/initrd.lz............**(3 to 4 lines of dots)

After this text I see a whole lot of text just shoot up the screen as if the installer is telling the user what its going through in the moment. Too fast to copy onto paper. 

Right after the rising text, I see the Xubuntu logo or a strange version of it. It is rendered with two colors: white(letter portion) & light gray(glow portion). It looks as if it could have been rendered on an 8bit NES. I found that a bit strange. Anyways, it hangs on this logo for about a minute. Keep in mind that the USB stick is blinking (that means its working/loading data) through this entire process. Then all of a sudden: the logo disappears in a glitchy way, screen turns blank black and then the USB light stops blinking. At this point it stays like this forever. 

So this will happen each time I try to install Xubuntu. I have no idea what is going on. Any help or guidance is very welcome. 

Sincerely,
Adam

---

### Post by oldfred on 2010-06-04
I have teh nvidia card but I think the nomodeset works for many different cards.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

---

### Post by adamsiddhi on 2010-06-04
Hey Oldfred,

I tried **Workaround: A From an installation** obviously since I have not been able to install Xubuntu yet. When I restart my computer and the USB starts loading up the Ubuntu boot option menu screen, I press and hold down **Shift** as it says. The following text appears on the screen:

[B]Booting from local disk...

SYSLINUX 3.85 2010-02-20 EBIOS Copyright (C) 1994-2010 H. Peter Anvin et al
Unknown keyword in configuration file: gfxboot
Boot:[/B](blinking cursor)

So holding down **Shift** did not take me to the GRUB menu where I would be able to:

[B]2) Press 'e' to edit.
3) Add "i915.modeset=1" after "quiet splash".
4) Ctrl+x to boot.[/B]

So I decide to look through the Help menu on the Xubuntu boot option menu screen and find some possible hope on the **F6** page. I realize I can type some commands at the original bootline that appears after pressing **SHIFT** as my computer starts to boot.

Here I can type in boot commands. I have tried the following:

[LIST]
[*]live-install noapic nolapic
[*]live-install vga=771
[*]live-install vga=771 noapic nolapic
[/LIST]

The first boot command **live-install noapic nolapic** produces the same failure the I have been experiencing. 

The second command **live-install vga=771** produces new results that also ends in failure but I get to see something new. 
What happens is that the same text displays:

**Loading /casper/vmlinuz..............**(2 lines of dots)
**Loading /casper/initrd.lz............**(3 to 4 lines of dots) 

Lots of text prints to the screen flying up the screen. Too fast to read. 

And then I see Ubuntu 10.04 written in basic white text appear on a black screen with 4 white periods below which change color to bright pink purple. These 4 dots appear to be emulating the Ubuntu 10.04 5 dot loader bar. Then all of a sudden some text appears really fast next to the loader (too fast to read). Then finally I see the following text appear permanently next to the 4  period load bar:

[B],,,,,,,,,,,,,,,*Speech-dispatcher configured for user sessionse to load
,,,,[/B]


The third boot command **live-install vga=771 noapic nolapic** produced the same result as the first (same Ubuntu 10.04 text logo with 4 dots underneath) except the end message was different slightly. It read:

[B],,,,,,,,,,,,,,,*Speech-dispatcher configured for user sessionsterface, unable to load
,,,,[/B]

I investigated **Workaround B** which recommends switching to **-vesa** by pasting a bunch of code into the file located:

**/etc/X11/xorg.conf**

So this is nice and all but where the heck is this **xorg.conf** file located? I checked my USB drive and HD but found nothing. Is this refering to people that already have Xubuntu installed? Sooo confusing!

I will investigate other options later. This is very time consuming. Any insight is appreciated. 

Thanks,
Adam

---

### Post by gerU on 2010-06-04
I'm having exactly  the same issue as you......I'm trying to install Ubuntu in my laptop from my USB. I follow exactly the same steps as you too and get the same errors.
Since my laptop do not support USB booting I installed PLop Boot manager to get my laptop boot from USB. I thought that was causing the problems....since when I set up different boot usb modes I get different results. 
The issue is that in a setting wich I do not remember!! I could get over this errors and start the ubuntu install till the part where I need to select the hd , but only the USB was appearing , it didn't detect my HD and SO , so I had to restart , and get to this errors again!!!!
I'll keep working on this issue!

---

### Post by gerU on 2010-06-04
sometimes the installer hangs here  too :
Starting Common Unix Printing System: cupsd

but i do not know how to reproduce it either

---

### Post by adamsiddhi on 2010-06-04
> **gerU said:**
> I'm having exactly  the same issue as you......I'm trying to install Ubuntu in my laptop from my USB. I follow exactly the same steps as you too and get the same errors.
Since my laptop do not support USB booting I installed PLop Boot manager to get my laptop boot from USB. I thought that was causing the problems....since when I set up different boot usb modes I get different results. 
The issue is that in a setting wich I do not remember!! I could get over this errors and start the ubuntu install till the part where I need to select the hd , but only the USB was appearing , it didn't detect my HD and SO , so I had to restart , and get to this errors again!!!!
I'll keep working on this issue!

I actually used PLop boot manager as an alternative to the BIOS (USB start up disk) option. Some questions.

[LIST]
[*]**What software did you use to create your USB boot drive? **
[*]**Can you list all the USB boot modes have you tried out? **
[*]**What errors were you getting when you restarted after the Ubuntu installer did not recognize your HD and SO?**
[/LIST]

I just want to say that it is very important to document each attempt you go through when trying to install Ubuntu. I know it is difficult since you would most likely have to write all these messages with a pen and paper but! with out the details you will never get real help. Communicating your problem in a highly detailed way is critical to eventually solve your problem. And yes, this is HARD time consuming work but, it is worth it.

So please go back through each technique you used to try installing Ubuntu and write down each step in detail. Write down every error message. Then come back and post all your information with your computer specs.

Thanks,
Adam

---

### Post by C.S.Cameron on 2010-06-04
Sounds like it might be a good idea to check the MD5SUM of your downloaded iso.

---

### Post by adamsiddhi on 2010-06-05
So it turns out all I had to do was:

1. Press **TAB** on the Xubuntu 10.04 Boot Options Menu screen. This will bring up a bunch of text at the bottom of the screen called the boot string.

2. I then type **i915.modeset=1** after the end of the boot string. For me, the boot string ends with **splash --**.

3. Press **ENTER** and bingo!!! Xubuntu 10.04 loads with a nice Xubuntu logo. The glow on the logo is smooth and well rendered. There must be 256 shades of color in that logo. *Remember before I was getting the 2 tone 16 bit NES style rendered logo?* 

So eventually I have success. Xubuntu 10.04 desktop loads up succesfully with the install icon on it. (or the installer loads up, depending on what option you have chosen in the menu i believe. not certain. regardless, either way you have the ability to install Xubuntu)

So that is it. I hope that helps anyone with this problem. Apparently there are multiple work arounds. I am glad I did not have to try them all. I figured out this solution by combining two suggestions I got from two different people. It kind of like magic. :-\":-\"

---

### Post by houldsworth1 on 2010-08-20
> **adamsiddhi said:**
> So it turns out all I had to do was:

1. Press **TAB** on the Xubuntu 10.04 Boot Options Menu screen. This will bring up a bunch of text at the bottom of the screen called the boot string.

2. I then type **i915.modeset=1** after the end of the boot string. For me, the boot string ends with **splash --**.

3. Press **ENTER** and bingo!!! Xubuntu 10.04 loads with a nice Xubuntu logo. The glow on the logo is smooth and well rendered. There must be 256 shades of color in that logo. *Remember before I was getting the 2 tone 16 bit NES style rendered logo?* 


"All I had to do..."?  
First - Thank you !  This worked for me.  But...it's hardly intuitive.  Just another reason why Linux has a long way to go before it is ready for Joe public (and I like Linux!)

---

### Post by RetchingRabbit on 2010-08-21
> **houldsworth1 said:**
> "All I had to do..."?  
First - Thank you !  This worked for me.  But...it's hardly intuitive.  Just another reason why Linux has a long way to go before it is ready for Joe public (and I like Linux!)

Truly, spoken as one who has never done a stock windows installation....
:lolflag:

---

### Post by houldsworth1 on 2010-08-22
> **RetchingRabbit said:**
> Truly, spoken as one who has never done a stock windows installation....
:lolflag:
That is funny.  

But, sadly, I have done stock windows installations on numerous occasions - far more than Ubuntu.  Ubuntu is MUCH faster to install, but Windows doesn't really ask you to do anything except hit the next key...a lot.

---

### Post by Metsuri Tossavainen on 2010-08-22
Hello, I am quite new to Linux, been using Ubuntu for several months and now trying to do some testing with Xubuntu on a flash drive.

I have exatcly same problems as adamsiddhi, exept his solution didn't work for me. I tried TAB and adding radeon.modeset=1 after splash--, but screen remains blank after the glitchy Xubuntu logo. (I have Radeon HD5770)

I also have tried Kubuntu and Lubuntu but I have similar problems with those distributions too.
So, any help? Is all hope lost or is there any other workarounds?

E: I also tried Damn Small Linux and well that worked flawlessly.

[COLOR=Red][B]EDIT: I got it working after all. If the workarounds that were suggested earlier don't work, try this:

Press TAB when you're at Xubuntu USB boot menu.
Add xforcevesa after splash--.
Press ENTER.
Xubuntu should now boot normally without problems. There is a small delay after Xubuntu logo disappeares but just be patient, the desktop should load up within a few seconds.
[/B][/COLOR]

---

