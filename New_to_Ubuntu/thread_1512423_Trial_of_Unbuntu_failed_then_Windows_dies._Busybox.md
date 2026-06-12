---
title: "Trial of Unbuntu failed then Windows dies. Busybox"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Chim Chim on 2010-06-18
First time trial of Ubuntu and after following the instructions on downloading and burning a CD I rebooted.
First Reboot got me a black screen with nothing happening
I went back into Windows (2k) and somehow got a message off the CD about adding something to help boot from the CD - tried this and rebooted and all went well till I got to a screen asking for a password.  After fiddling about with this I rebooted and tried to find a solution here but didn't understand anything!

After more random fiddling and running CCleaner nothing seemed to be getting better.

Then when rebooting back to W2K I got a Stop 0x0000007B Inaccessible Boot device error screen.  None of the suggested fixes worked on that.

I then went to reboot back to Ubuntu and got a busybox "Unable to find a medium containing a live file system" error message so I no longer have a PC that works. 

I'm now using a borrowed laptop.  I tried making a new CD using this and a slower burn speed but I get the same message.

I'm not good with PC stuff so I need really simple help!

thanks in advance

---

### Post by wilee-nilee on 2010-06-18
Post the script in my sig in code tags as described.

---

### Post by Chim Chim on 2010-06-18
I can't get the PC to boot to anything so I can't get to the internet.  However I'm downloading Mint (which is going to take over an hour here in Hi Tech Worcester) so I may be able to get somewhere with that???

---

### Post by wilee-nilee on 2010-06-18
> **Chim Chim said:**
> I can't get the PC to boot to anything so I can't get to the internet.  However I'm downloading Mint (which is going to take over an hour here in Hi Tech Worcester) so I may be able to get somewhere with that???

I doubt it will work, but do what you want. If you have a burned live cd and you use the key prompt to choose the boot it should run so you can post the script.

Many windows users rely on putting the cd as first to be read and it doesn't work, but the key prompt getting you to the choice outside of bios should. The prompt on my computer is f12. Look up what yours is on the web or post the computer model and I will try to find what it may be.

---

### Post by Chim Chim on 2010-06-18
When I switch on I get a choice of either Windows 2000 Pro or Ubuntu.
If I select Ubuntu it starts to load and if I then hit ESC I get the choices of Normal Mode, Safe Graphic Mode, ACPI workarounds, Verbose mode and Demo Mode in a box with GNU Grub version 1.98-1ubuntu5 above and instructions to use the up/down arrows, enter to boot to the selected OS, "e" to edit the commands before booting or "C" for a command line. underneath.

They all end in Busybox message...

---

### Post by wilee-nilee on 2010-06-18
I think your misunderstanding here. Boot a live cd of a Linux distro, run the script and post it in code tags. What I will say is that the more you peck at the system without the information in this script the more likely it will be that you lose all of whatever you have or a recovery will have to be run from accessing the windows setup from a live cd of Linux. 

Does this make sense to you? you have a broken setup that may be a fairly simple fix if the right information is shown through the script.

---

### Post by Chim Chim on 2010-06-18
OK I'm confused!  I thought I was booting from a Live CD as that is in the CD drive.  I haven't loaded Ubuntu on the PC at all.

---

### Post by wilee-nilee on 2010-06-18
Well I know I'm confused as to what has happened with your computer, that is why I want to see the script run from the booted live cd. The descriptions you have given have no relevant information to a fix for this. Can you post the script and we can go from there?

---

### Post by Chim Chim on 2010-06-18
But how can I show the script when I can't download the software?

I am right in that to show the script created by boot_info_script I have to download that onto the affected PC?  Or do I download it on to this laptop burn to a CD and then reboot the PC with the CD in?

---

### Post by wilee-nilee on 2010-06-18
> **Chim Chim said:**
> But how can I show the script when I can't download the software?

I am right in that to show the script created by boot_info_script I have to download that onto the affected PC?  Or do I download it on to this laptop burn to a CD and then reboot the PC with the CD in?

You can also run in the terminal ```
sudo fdisk -l
``` (l= a small case L) from the live cd this will at the least identify the partitions.
Since you have access to a computer that does download you mentioned down loading another distro go to that computer down load the script put it on a thumb. Then boot your computer with the live cd, plug the thumb in and drag the script to the live cd desktop and run this command.
```
sudo bash ~/Desktop/boot_info_script*.sh
```  
This will give you the read out from the script, then while still on the live cd come to the forums and copy and paste that script readout into a reply; and either put the code tags at the beginning and end as described in my sig. Or highlight the pasted script readout and click on the # in the reply window.

The script is very small and doesn't usually have anything to do with a burned cd other then the cd is used to get to a live desktop environment, to run the script from the desktop with the command given.

---

### Post by Chim Chim on 2010-06-18
You say run in the Terminal - How/What?  

I've now got the script on a USB stick but how do I drag this to the Live CD desktop when I don't get a desktop (either Ubuntu or Windows)

---

### Post by wilee-nilee on 2010-06-18
> **Chim Chim said:**
> You say run in the Terminal - How/What?  

I've now got the script on a USB stick but how do I drag this to the Live CD desktop when I don't get a desktop (either Ubuntu or Windows)

I was under the impression that you could boot the live cd. If you can, then plug the thumb into the usb port open it drag it to the desktop. Then go to menu-accessories-terminal, then run this in the terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```
copy and paste the file that appears on the desktop to a reply.

---

### Post by Chim Chim on 2010-06-18
Nope - can't boot the live CD!  (and my ISP went down for a while, things are going well!)

---

### Post by gandaran on 2010-06-18
> **Chim Chim said:**
> Nope - can't boot the live CD!  (and my ISP went down for a while, things are going well!)
I think there's some confusion here, on post #5 you said you can choose between windows 2000 and ubuntu, so then you must have installed ubuntu probably with wubi (inside windows)! but now you can not load any of the two systems, correct?
to run the Live Ubuntu CD you must setup the bios to load the cd/dvd drive in first place then reboot with the cd in the drive.

---

### Post by Chim Chim on 2010-06-18
You are correct - how do I change the BIOS to load the CD first?

Sorted the BIOS by googling the question, Ubuntu is now.......

---

### Post by Chim Chim on 2010-06-18
OK after changing the boot menu to CD Rom which I've double checked it still goes to the screen asking me to choose between W2K and Ubuntu.  When I choose Ubuntu it shows the screen with the changing coloured dots under the logo then goes to the busybox message.

---

### Post by eriktheblu on 2010-06-18
Doe you have a one time boot option? Is the optical drive built in or connected by USB? As a test, you might try removing your internal HDD from the boot priority to see if that makes it boot from CD.

This sounds like a Wubi install (ran wubi.exe from Win2K).

Try your Ubuntu disk on another machine, and run the build in test. If the test fails, or Ubuntu fails to boot, we can assume the disk was not burned correctly.

---

### Post by Chim Chim on 2010-06-18
> **eriktheblu said:**
> Doe you have a one time boot option? Is the optical drive built in or connected by USB? As a test, you might try removing your internal HDD from the boot priority to see if that makes it boot from CD.

This sounds like a Wubi install (ran wubi.exe from Win2K).

Try your Ubuntu disk on another machine, and run the build in test. If the test fails, or Ubuntu fails to boot, we can assume the disk was not burned correctly.

Can't see anything about One time boot

Changed BIOS to CDROM only and got "Disk Boot Failure, Insert system disk and press enter"  Tried with both Ubuntu disks I've made and the Mint one - nothing worked at all.  

TBH the only other computer is this borrowed laptop and I don't really want to try and load anything on this that I don't really have to.  Just put the disk in the laptop and it has 13 files on it - does that sound right?

---

### Post by eriktheblu on 2010-06-18
Unless you install it, nothing will be changed. Simply boot, select the diagnostic function, and see if it passes.

A lot of MS Windows programs have trouble burning ISOs. I once asked my wife to burn some disks for me on her Win7 machine; I ended up with an ISO file on a CD rom.

Have you burned many ISOs before?

---

### Post by Chim Chim on 2010-06-19
Just tried the CD on this (borrowed) laptop and it works - Ubuntu looks good!

Just wish it had been that easy on my PC!

---

### Post by eriktheblu on 2010-06-19
Well, that's both promising and disappointing. Promising because we have eliminated a potential problem, and disappointing because that would have been a really easy fix.

Since I'm not really sure what to do next, I'm going to recap for clarity.

1. Your machine does not boot from an Ubuntu CD. Similar problems with Mint.

2. You installed with Wubi, but Ubuntu fails to load.

3. You made some wort of change to try to correct the Wubi boot, and now Win2K does not boot.

For Windows, do you have an actual Win2K disk, or manufacturer's recovery disks?

---

### Post by varunendra on 2010-06-19
Just to avoid confusion, open your desktop's cabinet and disconnect the Hard-disk (remove power & data chords from its back).
Then power on the pc, put in the cd you've successfully tried on the laptop, & reboot the pc making sure that 'boot from cd' option is enabled in BIOS.

See if it lets you boot into Ubuntu. If it does, then most probably either there was some mistake in choosing CD drive as the first boot device, or your CD drive has difficulty reading the CD in appropriate time.

If even after removing the HDD & making cd drive the only boot device in BIOS doesn't help, then maybe your CD drive needs to be replaced.

PS: If you can successfully boot the laptop from the CD (as you said) but not the Desktop PC, then you should try creating a live USB stick (system>administration>Create Startup Disk) on the laptop and try booting the desktop off that USB stick (provided- your desktop's BIOS has the 'Boot From USB' option available.


PPS: Are [eriktheblu]("http://ubuntuforums.org/member.php?u=508854")'s points correct? If not, please correct them to make it more clear. :)

---

### Post by Chim Chim on 2010-06-19
I concur with your recap! 

Sadly when I loaded Win2K it was on the license from my work PC and for some reason I never did a recovery disk, although I do have my Win98 ones!!!

I have a mate who may be able to help so I'm going to see him Monday to try and get Win2K back, and then try Ubuntu again!

I have spoken to a local PC engineer who didn't have nice things to say about Ubuntu or Linux!  But then he was a MS Certified engineer!

Anyway, I thank everyone for their help so far, hopefully Monday will see my PC back working (with not much lost) and with Ubuntu working as well - I will move from the dark side!

---

