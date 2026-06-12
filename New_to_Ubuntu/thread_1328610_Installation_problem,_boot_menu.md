---
title: "Installation problem, boot menu"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by lolwot92 on 2009-11-16
Ok so i decided to install Ubuntu again after not having used it for a while. Downloaded 9.10 and the hash matches. I used Wubi to install it to a second hard drive to boot from, once its installed i reboot. Though it goes straight into Windows, theres no boot menu.
Any idea on how to fix this? Am i surpose to install it on the same HDD as windows?

Cheers

---

### Post by Jon Monreal on 2009-11-16
Is it a USB drive? What format is it in?

Thanks.

---

### Post by kansasnoob on 2009-11-16
> **lolwot92 said:**
> Ok so i decided to install Ubuntu again after not having used it for a while. Downloaded 9.10 and the hash matches. I used Wubi to install it to a second hard drive to boot from, once its installed i reboot. Though it goes straight into Windows, theres no boot menu.
Any idea on how to fix this? Am i surpose to install it on the same HDD as windows?

Cheers

This makes absolutely no sense! You can't possibly use Wubi to install Ubuntu to a different drive than Windows is on!

Wubi installs Ubuntu within Windows in a sort of virtual machine.

Look here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Post the results of that script.

---

### Post by Jon Monreal on 2009-11-16
> **kansasnoob said:**
> This makes absolutely no sense! You can't possibly use Wubi to install Ubuntu to a different drive than Windows is on!

Wubi installs Ubuntu within Windows in a sort of virtual machine.

Look here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Post the results of that script.

I've heard of people getting it to work, but it takes some working. I was thinking we could help him in doing this.

At any rate, simply installing to the Windows partition is probably the easiest solution.

---

### Post by kansasnoob on 2009-11-16
> **Jon Monreal said:**
> I've heard of people getting it to work, but it takes some working. I was thinking we could help him in doing this.

At any rate, simply installing to the Windows partition is probably the easiest solution.

The first thing is to see what went wrong.

That Boot Info Script will generally tell us.

---

### Post by lolwot92 on 2009-11-17
Ok i just installed it onto the primary drive with windows on it, rebooted...and it still skipped straight to windows. Ill post the script results in minute.
@ kansasnoob, its a 250g IDE HDD im installing it onto, which is in NTFS format. And no, not a usb drive.
Ahh i cant use the script as it wont let me boot off cd, everytime i hit the "try" instead of installing, it just makes a black screen and sits there.
So i tried to install it from booting off it, and got this error.

Stdin: 0
Mount: Mounting/Dev/Sr0 On/cdrom Failed: Invalid argument
^^^^ all over the screen, then it says

(initramfs) unable to find a medium containing a live file system.

---

### Post by kansasnoob on 2009-11-17
Just to clarify this is a typical Wubi install:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

This is a fairly typical dual boot:

[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

As far as not being able to boot the Live CD, it sounds like you checked the md5sum, so you might look here:

[http://www.psychocats.net/ubuntu/burn](http://www.psychocats.net/ubuntu/burn)

---

### Post by lolwot92 on 2009-11-17
Ahh thanks for that. Appears everything was fine, it was the settings that were wrong.
In "Start up recovery" "Time to display a list of operating systems" was set to 1 second..no wonder it wasnt showing =x

Found that from the link u posted..[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)
Thanks for the help, much appreciated.

EDIT: Ok so it appears on the boot menu, i hit enter and it goes to the loading screen. Once thats over it just sits at a black screen. Any idea as to why it does this?
EDIT2: Tried to "Check cd for errors" or whatever its called, it goes to a loading screen, then a black screen. Then gives this error
"
Stdin: 0
Mount: Mounting/Dev/Sr0 On/cdrom Failed: Invalid argument
^^^^ all over the screen, then it says

(initramfs) unable to find a medium containing a live file system."

The same as when i try install when booting off it...maybe the CD was dodgey? I've made 4 copies and they all do the same, im beggining to think maybe is my DVD/CD drive, though that wouldnt explain why the WUBI installation isnt working.

---

### Post by kansasnoob on 2009-11-18
If you're burning that in Windows what program are you using?

---

### Post by lolwot92 on 2009-11-18
> **kansasnoob said:**
> If you're burning that in Windows what program are you using?

InfraRecorder, made 2 copies of Ubuntu both at 4x speed, and 1 copy of Kubuntu at 4x speed. Both give the same mounting error and such...im thinking maybe its the drive.

---

### Post by arnab_das on 2009-11-18
download startupmanager and you can edit the menu options there.

sudo apt-get install startupmanager

---

### Post by lolwot92 on 2009-11-19
> **arnab_das said:**
> download startupmanager and you can edit the menu options there.

sudo apt-get install startupmanager

Thanks for trying to help, but it doesnt really have anything to do with my problem. The menu not showing was solved, i stated in a later post. Now its just figuring out why linux wont install properly off the cd.

---

### Post by wrgb2 on 2009-11-19
You could download the iso for the alternate install cd -- there's an option on it to do a text mode install.  It looks like the gui installation program has a problem with your video card.

---

### Post by lolwot92 on 2009-11-20
> **wrgb2 said:**
> You could download the iso for the alternate install cd -- there's an option on it to do a text mode install.  It looks like the gui installation program has a problem with your video card.

Mm just wondering, why have you come to that conclusion? Are the errors i showed something to do with the video card?

---

### Post by wrgb2 on 2009-11-20
Sorry, I meant to say it looks like you're having a problem when the boot program is going into gui mode - this could be because of a problem with the video card.

---

