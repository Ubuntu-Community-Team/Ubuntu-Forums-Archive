---
title: "Compaq Armada 7400 installation stuck before I can choose anything"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by Whusmaname on 2011-01-11
Hi, I'm new to Linux in general, and thought I'd try out Ubuntu. I downloaded the ISO for Ubuntu 10.10, and wrote it to a cd using Nero BurnLite on Windows 7 Desktop, so I could install it to my Compaq Armada 7400, but when it boots up, the installation freezes at "kernel_thread_helper+0x6/0x10, and the cursor blinks after that line.

Am I supposed to type a command in, or is it a 'wait it out' situation?

I've also tried uninstalling Windows XP from the machine, because I've only got a 6gig harddrive in it... does that make a difference?

---

### Post by Hippytaff on 2011-01-11
You might have a corrupt ISO or the disc might be corrupt. I recommend downloading the iso again and burning it at the slowest possible speed.

---

### Post by Whusmaname on 2011-01-12
Is there a way I can check if the ISO is corrupt? 'cos I always write discs at the lowest speed.

---

### Post by garyhibdon on 2011-01-12
personally i have to say 2 words.

thumb drive.


4Gib flash drive is more then enough space to run ubuntu 10.10 32 bit and less issue with burn speed, etc


EDIT: why are you trading from windows 7, a 64 bit os, to ubuntu 10.10 32 bit? just a random question

---

### Post by Whusmaname on 2011-01-12
> **garyhibdon said:**
> why are you trading from windows 7, a 64 bit os, to ubuntu 10.10 32 bit? just a random question
I'm not trading... my desktop is keeping Windows 7 on it, the laptop I have (Compaq Armada 7400) is getting Linux on it, so I can try Linux out.

Edit: Besides, my Desktop's a 32-bit too.

---

### Post by Hippytaff on 2011-01-12
should have said you can check the iso by doing a md5sum check  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Whusmaname on 2011-01-12
I found out that the disc works by testing it on the machine I didn't want Ubuntu on, 'cos I've already got Windows 7 on it... Great, so it's the laptop that's the problem. Maybe I'll try using the flashdrive way to load it... anyone got a spare flashdrive? Mine was stolen.

---

### Post by Hippytaff on 2011-01-12
What graphics card do you have on the laptop?

---

### Post by Whusmaname on 2011-01-12
According to "Device Manager" in Windows XP Pro, my display adapter is an "S3 ViRGE MX" and there's 2 "Default Monitor"'s in "Monitors". Does that help?

---

### Post by Hippytaff on 2011-01-12
Are you able to boot from liveCD? or does it hang?

If the disc works on a different pc then it could be a hardware issue, in which case you idea to use a usb pen would be the best idea.

Also your disc drive on your laptop might not like the brand of disc your using...I know sounds bonkers but I've experienced this

---

### Post by garyhibdon on 2011-01-12
also, one problem ive had recently had, is the oem cd rom drive doesnt have any drivers built into the os, so upon trying to install the os, it forgets how to use the drive. i had this issue on a gateway laptop, so im not sure if this could be a relevant issue. Just throwing ideas out there

---

### Post by Whusmaname on 2011-01-12
What I've done is open the cd in Windows XP Pro, got the Ubuntu Menu window with the three buttons, IE: Demo and full installation, Install inside Windows, and Learn more. (LiveCD)

When I select the first option (Demo and full installation), I choose the first option (get the Laptop to reboot immediately) and it hangs on the screen with this list showing:
[      21.992253]    [<c081bf>] do_copy+0xca
[      etc...] 
up to...
[      21.994537]   [<c01363e>] kernel_thread_helper+0x6/0x10

And that's where it hangs.

When I tried uninstalling Windows XP, I used the windows installation disc to use the format function, then quit before installing Windows, restarted the machine with the Ubuntu disc I wrote from the .iso file in, and got to the same frozen screen.

So I've reloaded Windows XP to try the LiveCD again, from a different angle, so to speak.

When I tried the second option in the LiveCD menu (Install inside Windows) it brought up a Windows Error Message, saying 
"256MG of memory are required for installation. 
Only 63MB are available.
The installation may fail in such circumstances.
Do you wish to continue anyway?"
and there's a choice of "Yes" or "No"

When I click "Yes', it sends me to the username and password segment, and gives me 3 options: Accessibility, Install, and Cancel. Since Accessibility is not a problem, I click on "Install", and it starts the process. Once it gets past the point where it's extracting files from the disc, and begins installing, it brings up another Windows Error Message, saying 
"An error occurred:
Permission denied
For more information, please see the log file: c:\docume~1\*****\locals~1\temp\wubi-10.10-rev197.log" and gives me only the 1 option: "OK"

(I keep wanting to scream at the computer, telling it "it's not okay!!!" )

Should I send you the log file?

Edit: Sorry this reply took so long, I went through the processes again to get the details right. Hope that much detail helps.

---

### Post by Hippytaff on 2011-01-12
That sounds like a corrupt disc, eventhough we know its not. I'd get a usb stick and try it that way, and for the time being install the wubi.exe if you want to use ubuntu before you manage to get a usb stick. If you decide to do the wubi install, if you upgrade, deselect any upgrades with grub in the title - there are issues :-)

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by Whusmaname on 2011-01-12
I've just checked the last few lines in the log... I think it might be because there's no internet connection on the laptop... could that be a problem?

---

### Post by garyhibdon on 2011-01-12
> **Whusmaname said:**
> I've just checked the last few lines in the log... I think it might be because there's no internet connection on the laptop... could that be a problem?

only if you set it up to install the updatess automatically while install os

---

### Post by Whusmaname on 2011-01-12
Okay. How do I change it to no updates during install in LiveCD?

Meh, scratch that, I'm just going to use this PC's connection. I'll let you know if it works.

---

### Post by garyhibdon on 2011-01-12
it should be a little button you can click on if i remember correctly.  it will be towards the bottom of the screen.  and it sounds like windows is still present on the hard drive if its giving you a windows error.and  256 Mib is not enough to run ubuntu OR windows xp, so you may want to tackle the bios and make sure that its reading the hard drive correctly and also, make sure that ubuntu is trying to allocate the entire disk space, IF that what you're wanting to do

---

### Post by Sylslay on 2011-01-12
Well s3 cards works ok in Ubuntu.
Try pull out hard dive (if laptop had simple case),
Or swap CD-Drive.

You can use 1gb thumb-drive and an *iso file and any PC with Windows,
and make it.
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

PS. In emergency I like use ploop boot manager, for boot from older laptops and thumb dirves.

---

### Post by Whusmaname on 2011-01-12
I'm trying to replace the Windows XP with Linux, and Ubuntu seemed like the good choice, because of my history with Windows, because I want to use my laptop for a PDF reader only, and I've heard that Linux is more stable, and I'm guessing it will be faster for the laptop. I'm going to try running the windows install disc, to get to the formatting of my hard-drive, and this time I'm going to use the FAT32 format rather than the NTFS format, to see if that makes a difference.

Edit: I don't have a flash-drive, which is why I'm trying so hard with the disc.

---

### Post by Sylslay on 2011-01-12
Just run Windows installer,
than manage partion with 

delete every patition, 
do not format,


just 
ctrl+alt+dell,

and swap for ubuntu installer,
and use all harddive  , when installin ubuntu.

---

### Post by Whusmaname on 2011-01-12
Thanks, Sylslay. I'll try that now.

---

### Post by Sylslay on 2011-01-12
Burn ISO on DVD-R instead ordinary CD-R,

Sometimes broken DVD/CD-Reader works ok on diffrent length of wave.

---

### Post by Whusmaname on 2011-01-12
I don't have a DVD-rom, only CD.

Besides, the CD worked on my Desktop pc when I dual-booted.

---

### Post by Sylslay on 2011-01-12
Well [http://www.dealtime.com/Compaq-Armada-7400-387071-002/prices](http://www.dealtime.com/Compaq-Armada-7400-387071-002/prices), 
Could be some diffrents.

Whan startinig Ubuntu installer, before booting to liveCD,

Press F6 and turn off all opiton:

like ACPI, etec, 


turn off - hilight the option and press spacebar.

ctrl+e for editing booting option, delete words "quiet, splash"
than ctrl+x or ctrl+b for boot

If that laptop had only 64 MB, and You want only for pdf file,
use 

Lubuntu : A Pentium II or Celeron system with 128 MiB of RAM is probably a bottom-line 

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

or Puppy with Ubuntu packeages :[http://distrowatch.com/?newsid=06447](http://distrowatch.com/?newsid=06447)

[http://distrowatch.com/table.php?distribution=puppy](http://distrowatch.com/table.php?distribution=puppy)

Ubuntu needs at least 256MB ram, it's modern OS.

---

### Post by Whusmaname on 2011-01-12
Like so?

x acpi=off
x noapic
x nolapic
x edd=on
x nodmraid
x nomodeset
x Free software only

Is that what you meant?

[COLOR=Red]Looks like it's working!!! Yay!!![/COLOR]

Scratch that. It's stuck at the same place again.

Thanks... I'll try Lubuntu instead...

---

### Post by Sylslay on 2011-01-12
No Problem

x acpi=off
x noapic
x nolapic
x edd=on
x nodmraid
x nomodeset

---

### Post by garyhibdon on 2011-01-13
if the cd is working on your other computer then you will just have to either try several other brands of cd's (possibly costly), just go buy a flash drive( you can get them pretty cheap now. i think i paid $15 for my 4 gig at wally world),OR drop a lan line to your laptop and install from the internet. id recomend the last just because its cheapest way to go, BUT its all up to you. i honestly cant think of any other ideas. really wish i was of more use

---

### Post by garyhibdon on 2011-01-14
i just finally looked at sylslay's link and, HOLY CRAP BATMAN!! windows NT?!

---

### Post by elgordodude on 2011-01-14
> **Hippytaff said:**
> That sounds like a corrupt disc, eventhough we know its not. 

Have you tried the dvd? It's been my experience that repeated failed installations are usually due to a corrupt disc.

---

### Post by Whusmaname on 2011-01-14
elgordodude, I only have a cd-rom on the laptop, and since it's such an old model, no chance of finding a dvd-rom that'll fit it without spending more than what a new laptop costs.

---

### Post by Sylslay on 2011-01-14
You can use 1gb thumb-drive and an *iso file and any PC with Windows,
and make it usb-installer

[http://www.pendrivelinux.com/univers...easy-as-1-2-3/](http://www.pendrivelinux.com/univers...easy-as-1-2-3/)

but with such BIOS, with not supported usb-legacy (or say booting from removeble device),

need burn cd with PLOOPMANAGER - an boot manager

and boot first from cd 

and that boot manager allow You to boot from usb-key. 95% it will works,

Did You tried that Lubuntu?

---

### Post by Sylslay on 2011-01-14
You can use 1gb thumb-drive and an *iso file and any PC with Windows,
and make it usb-installer

[http://www.pendrivelinux.com/univers...easy-as-1-2-3/](http://www.pendrivelinux.com/univers...easy-as-1-2-3/)

but with such BIOS, with not supported usb-legacy (or say booting from removeble device),

need burn cd with PLOOPMANAGER - an boot manager

and boot first from cd 

and that boot manager allow You to boot from usb-key. 95% it will works,

Did You tried that Lubuntu?

---

### Post by Sylslay on 2011-01-14
You can use 1gb thumb-drive and an *iso file and any PC with Windows,
and make it usb-installer

[http://www.pendrivelinux.com/univers...easy-as-1-2-3/](http://www.pendrivelinux.com/univers...easy-as-1-2-3/)

but with such BIOS, with not supported usb-legacy (or say booting from removeble device),

need burn cd with PLOOPMANAGER - an boot manager

and boot first from cd 

and that boot manager allow You to boot from usb-key. 95% it will works,

Did You tried that Lubuntu?

---

### Post by Whusmaname on 2011-01-14
I've tried Ubuntu 10.10, 8.something-or-other, Lubuntu, DSL, and mini.iso, all on cd-r discs, written by Nero BurnLite... Each time I tried LiveCD through Windows XP SP2, and then deleted Windows using the Windows install disc to get to the partition delete function, then swapped discs and restarted the laptop. I'm now gonna borrow my friend's 4gig pendrive, and try it that way.

---

### Post by Whusmaname on 2011-01-14
Double-post... how do I delete it?

---

### Post by Sylslay on 2011-01-14
The Alternate Install CD only requires you to have 64 MB RAM at install time.
I am not sure what minimum ram is needed for others.(exept puppy) I had pc with at least 256MB ram

You may try this,
[http://releases.ubuntu.com/maverick/ubuntu-10.10-alternate-i386.iso.torrent](http://releases.ubuntu.com/maverick/ubuntu-10.10-alternate-i386.iso.torrent)

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

But need for easy setup LAN cable and internet form BOX. or internet shared from other pc.

and manual install desktop gui

sudo apt-get install xubuntu-desktop


XUbuntu vs LUbuntu, 

[http://crunchbanglinux.org/forums/topic/4547/ubuntu-xubuntu-lubuntu-comparison/]](http://crunchbanglinux.org/forums/topic/4547/ubuntu-xubuntu-lubuntu-comparison/])
(*,)](*,)]

What about Android OS for x86 ?

[http://code.google.com/p/android-x86/downloads/detail?name=android-x86-2.2-generic.iso&can=2&q=](http://code.google.com/p/android-x86/downloads/detail?name=android-x86-2.2-generic.iso&can=2&q=)

---

