---
title: "USB fail to load unetbootin: could not find kernel image"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by jharvey24 on 2009-10-01
Hey guys,
I'm very new to linux but excited to try it.  I have an Acer aspire one d150 running an atom 1.6 with 160 gb hd, and 1gb ram.  When I installed ubuntu to my usb (sandisk cruzer 8gb) after formatting it then restart my computer I get a screen that only has the default option not the install or uninstall.  Any ideas on what is going on?

---

### Post by markbuntu on 2009-10-01
Did you use unetbootin to install the iso?
I think unetbootin needs to be on a fat formatted drive.

---

### Post by jharvey24 on 2009-10-01
unetbootin needs to be on the usb drive?  I'll try that thanks!

---

### Post by Mighty_Joe on 2009-10-02
> **markbuntu said:**
> I think unetbootin needs to be on a fat formatted drive.

Absolutely not.  unetbootin is just a tool to create a bootable USB drive.  Once it has copied the files to the USB drive, its served its purpose.

@jharvey24: "I get a screen that only has the default option not the install or uninstall."

What is this "default" option you speak of?  When I boot a Live CD or Live USB, I get a screen like this:
[IMG]http://ubuntunigeria.files.wordpress.com/2007/09/bootscreen.jpg[/IMG]
What are you seeing?
I haven't had much luck with unetbootin.  I've had much better luck with the Live CD's [Live USB Creator]("http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator").  
If you have an 8Gb drive, you may want to just do a [full install]("http://ubuntuforums.org/showpost.php?p=7497700&postcount=4").  
If your drive still has the [U3]("http://www.u3.com/") software on it, you'll probably want to [remove it]("http://kb.sandisk.com/app/answers/detail/a_id/2550/kw/usb%20flash%20drive%20remove%20u3/r_id/101834") before installing Ubuntu.

---

### Post by LewRockwell on 2009-10-02
@ Mighty Joe

+ 1

.

---

### Post by jharvey24 on 2009-10-02
When it loads from usb it says unetbootin at the top and the whole page is silver.  Default is the only option in a list that should include install and uninstall.  I'm looking now at the instructions on how to make the usb drive bootable.  I think that is the root problem

---

### Post by markbuntu on 2009-10-02
Well, that is what unetbootin does, it makes to usb stick bootable and then aims at the iso. I have had no problems using unetbootin to put bootable isos on usb sticks. Just start unetbootin and find the iso into the box and tell it to do it. I never formatted the usb sticks, just used them as they came from the store which is I think fat16 or fat32 format because they say filesystem msdos when I mount them.

---

### Post by xi0nic on 2009-10-03
I'm trying to get the Karmic x64 beta installed on a 2gb flash drive, using UNetBootin on Windows 7. The flash drive is formatted Fat32.

When I boot up, I get a message saying "Could not find kernel image: linux", and am dumped to a "boot:" prompt.

I haven't modified any config files or anything strange like that. Any ideas?

---

### Post by Mighty_Joe on 2009-10-05
> **xi0nic said:**
> Any ideas?

As I posted earlier, I've had better luck with the Live CD's Live USB Creator than with unetbootin.

---

### Post by Plumtreed on 2009-10-05
Your dead right ,Mightyjoe, but I wonder if these 'new' users realise that Ubuntu has a 'built -in', very simple, highly effective and persistent USB Creator.

---

### Post by xi0nic on 2009-10-05
> **Mighty_Joe said:**
> As I posted earlier, I've had better luck with the Live CD's Live USB Creator than with unetbootin.

> **Plumtreed said:**
> Your dead right ,Mightyjoe, but I wonder if these 'new' users realise that Ubuntu has a 'built -in', very simple, highly effective and persistent USB Creator.

You gentlemen failed to read my post in which I stated that I'm burning from a Windows OS. The goal of using a flash drive was to avoid wasting a CD-R. In order to accomplish your suggestion, I would need to burn the disc, and then boot from it, in order to create the flash image with the Live USB Creator, which I wanted to install from.

FWIW, I ended up doing exactly that, just to end the headache.

Thanks.

---

### Post by Mighty_Joe on 2009-10-06
> **xi0nic said:**
> You gentlemen failed to read my post in which I stated that I'm burning from a Windows OS. 

You are the one who asked for "any ideas".  My experience is that the USB Creator works better than unetbootin, and that's what I shared.  If you are that concerned about "wasting" CD-R's (they cost what, $0.10?), invest in a CD-RW! ;)

---

### Post by dan233 on 2009-10-06
> **jharvey24 said:**
> Hey guys,
I'm very new to linux but excited to try it.  I have an Acer aspire one d150 running an atom 1.6 with 160 gb hd, and 1gb ram.  When I installed ubuntu to my usb (sandisk cruzer 8gb) after formatting it then restart my computer I get a screen that only has the default option not the install or uninstall.  Any ideas on what is going on?
Do not use unetbootin use another program called
 "win32diskimager" on windows to mount the ISO image onto the USB drive.
There s a very good chance it will solve the problem

---

