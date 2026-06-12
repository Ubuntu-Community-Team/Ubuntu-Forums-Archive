---
title: "problem making install CD/installing ubuntu"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by MollFlounders on 2011-02-13
This thread is a branch off from a previous one here: [http://ubuntuforums.org/showthread.php?p=10453683#post10453683](http://ubuntuforums.org/showthread.php?p=10453683#post10453683).

I've been trying to install Ubuntu 10:10 on my new Toshiba Satelite laptop, with a partition to keep windows on one side. My first attempt didn't work, I think because of a problem with the ubuntu cd I created: it installed, but without a graphic interface so I had to remove it (see previous thread). My second attempt today has also not worked either. 

I downloaded the files from the ubuntu website using firefox, which took a few minuets. Having burned my new Ubuntu files onto a dvd using infrarecorder,  at a low burn speed as recommended, I tried to install Ubuntu from that  disk and wasn't successful. Here's what happened:

- hit F12 when prompted, and selected to boot from CD
- I got the purple Ubuntu screen that just has two small logos at the  bottom (a rectangle and a little stick figure in a circle) for a few  seconds.
- I got the purple screen with Ubuntu and a row of dots for a few seconds...
- then the screen went black with a flashing cursor, followed by the following message:

Busybox v1.15.3. (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands
(initramfs) mount:mounting/dev/loop0 on //filesystem.squashfs failed: Input/output error
Cannot mount /dev/loop0 (/cdrom/casper/filsystem.squashfs) on //filesystem.squashfs

I'm not sure if this is a problem in how I'm making the ubuntu cd, or in how its reacting with my laptop. I've used ubuntu before, but am pretty much a beginner in terms of fixing things on my own! Any help would be much appreciated!

---

### Post by Hippytaff on 2011-02-13
What graphics card do you have? and did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the iso? (I never do but it's a good to check if things don't work)

---

### Post by Hedgehog1 on 2011-02-13
The Toshiba web site lists this laptop as having:

```

PROCESSOR*
Intel® Pentium® Processor P6200
OPERATING SYSTEM*
Genuine Windows 7 Home Premium (64-bit)*
GRAPHICS ENGINE*
Mobile Intel® HD Graphics
GRAPHICS MEMORY*
64MB-1696MB dynamically allocated shared graphics memory
DISPLAY SIZE
15.6" widescreen
DISPLAY TYPE*
HD TruBrite® LED Backlit display
DISPLAY RESOLUTION
Supports 720p content, 16:9 aspect ratio, 1366x768 (HD)

```

I didn't see the specific on-board intel graphics model number.

---

### Post by oldfred on 2011-02-13
When you get the stick figure & keyboard, press any key. Then press f6 and try nomodeset or other parameters.

No, I did not even know that that was a stick figure & a keyboard until someone posted that. The old menu made more sense as at least it showed that you could have options.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by MollFlounders on 2011-02-13
Hi everyone, thanks for your replies. 

This is the info for my graphics card and laptop:

My laptop is a Toshiba Satelite L655-S5155 with a 64 bit operating system 
Graphics Card Intel GMA HD, driver version: 8.15.10.2189

I did the MD5SUM using [winMD5Sum]("http://www.nullriver.com/index/products/winmd5sum") on the file I had downloaded following the instructions from the links. It said the MD5 check sums are different. So presumably I need to download it again,  check I get a non-corrupted version, and then burn that?

---

### Post by Hedgehog1 on 2011-02-13
May I suggest doing a bit-torrent download for the ISO?

Micro torrent works fine in the windows space:

[http://www.utorrent.com/downloads](http://www.utorrent.com/downloads)

:KS

---

### Post by Hippytaff on 2011-02-13
> **MollFlounders said:**
> 

I did the MD5SUM using [winMD5Sum]("http://www.nullriver.com/index/products/winmd5sum") on the file I had downloaded following the instructions from the links. It said the MD5 check sums are different. So presumably I need to download it again,  check I get a non-corrupted version, and then burn that?

yip...looks like that is the problem. It's usually a corrupt iso when you get dumped into busybox

---

### Post by MollFlounders on 2011-02-13
ok I'm downloading it as a bittorrent, having just installed the one you suggested. It seems like its going to take a while to download, but when its done I guess should check it again with MD5Sum, burn it to a cd (presuming its ok), and then try again.

As long as I don't get chucked off this starbucks internet connection before its done, I'll let you know if it works!!

---

### Post by Hedgehog1 on 2011-02-13
Your installing Ubuntu at [SIZE="3"]Star Bucks?[/SIZE]

Now THAT is faith in an OS.  I am impressed.

A bit-torrent is checked against the check-sum for you, so you don't **need** to check it again - but you are welcome to if you want.

What time zone are you in that your are drinking coffee at this hour?

:KS

---

### Post by MollFlounders on 2011-02-13
lol yes... I guess there is something nicely amusing about that. Its not where I would usually hang out, honest! But I'm travelling in the US at the moment, so relying on a combination of coffee shops and libraries for my internet connection :) you're right, coffee is probably not the best idea, but I'm guessing I'm going to up late sorting this out (and then getting done the work I'm meant to have done this weekend once its all set up!)

---

### Post by Hedgehog1 on 2011-02-13
Well, that makes sense, then.

It sounds like your old laptop went out while you were on the road, and are now getting the replacement setup as you travel?

I think you may have hit on an ideal example of open source and free software working out well.  You can download whatever you need, where ever you are.

Of course, if I were on the road I would miss my very fast internet connection.  And my 55" TV that is also my monitor. Ans my fancy sound system that Rhythm Box plays too. And my comfy chair. Ohh - the fridge; Gotta have that...

I don't travel much - can you guess why? :KS

---

### Post by MollFlounders on 2011-02-13
Ok. So I downloaded the bittorrent, double checked it before burning it to a cd, and it was fine. I went through the installation process with no problems, but when I restarted I was stuck in the command line version, and couldn't get a graphic interface. (This was the same problem I had yesterday)

So now I have an installed version of ubuntu, but perhaps this is a problem with the graphics card?? I tried entering "startx", and this gave me a completely blank screen. Before I installed I tried the test version of ubuntu, and that worked fine.

---

### Post by Hedgehog1 on 2011-02-13
OK - we have gone full circle (but without the extra partitons this time)

This does appear to be a common issue.  Here is a post with what to try:

[http://ubuntuforums.org/showthread.php?t=1687201]("http://ubuntuforums.org/showthread.php?t=1687201")

Time for more coffee...

---

### Post by oldfred on 2011-02-14
I had to use nomodeset with liveCd and then on first boot.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by MollFlounders on 2011-02-14
Hi, sorry for disappearing - starbucks closed and I lost my internet connection :)

I just tried what you suggested, adding "nomodeset" after the "quiet splash", and then ctrl-x to reboot. It comes up with the command line again for me to log in, rather than graphics, and then if I enter "startx" it gives a blank screen with no cursor.

---

### Post by oldfred on 2011-02-14
Update:
Since it is a portable and not a full video card. Some have better success with generic settings:

* Generic: xforcevesa or nouveau.modeset=0

You can try this from command line to install the nVidia. If not full video card I do not think you should install the nVidia driver.

[COLOR=DarkRed]Do not do this:[/COLOR]
sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

You can do this:
You could also update system:

if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

