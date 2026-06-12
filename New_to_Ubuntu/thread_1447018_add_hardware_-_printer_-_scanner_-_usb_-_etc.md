---
title: "add hardware - printer - scanner - usb - etc"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by harry003 on 2010-04-04
I am a newbie testing Lucid in a VirtualBox under XP to test the waters before making a switch.

I am starting to think that the VirtualBox system may cripple EVERYTHING, because everybody in these forums acts like everything is peachy.

My 2 main tools in Windows are the Device Manager and Windows Explorer, which I use constantly. People in these forums refer to System/Administration and Nautilus, but I can't seem to get them to do anything I need.

Also, I have a fat 500-page book called "Beginning Ubuntu Linux" by Keir Thomas but it does not address any of my issues.

What is the Ubuntu equivalent for downloading and installing drivers to make my Epson printer and Microtek scanner work? According to Thomas they are just supposed to automatically work, but they don't.

How can I access a USB flash drive when I can't see anything outside the VirtualBox?

How can I see files on any of my other hard drives, or even on this drive outside of the VirtualBox?

Asus M2N-E, Athlon 64x2, 4GB ram, 500GB SATA, 8600GTS, ethernet DSL

---

### Post by anewguy on 2010-04-04
Not sure if I'm understanding your USB problem correctly, but if you can't see them in VirtualBox you need to download the free but not open source version from Sun (unless they are calling themselves Oracle now).  That version supports USB devices in VirtualBox, but you have to create filters to see/use them.

Also, when running in a virtual machine like VirtualBox, remember that the devices are those known to the host OS (in your case, Windows).  There really is no equivalent to downloading/installing drivers as per Windows, but the same idea applies.  You must find and install drivers for those devices that don't work out of the box, and then some may not work as very few of the manufacturers support Linux and hence the driver support normally found from the vendors it pretty much non-existant.

Nautilus really does "equate" to Windows explorer - if you are using regular Ubuntu it is what is used when you open "places".  Do keep in mind that Linux isn't Windows (and some of us say thank goodness!), so things aren't meant to look/feel like Windows.  If there is something specific you are trying to do and having problems with, post back the details for each one separately so we can get an idea of what you are looking for.

Not all scanners and printers will work with Linux - the best support is using HP devices (not an add for them, but rather the best support in Linux).


Dave ;)

---

### Post by harry003 on 2010-04-04
My VirtualBox is buried in a directory on one hard drive. I have 2 other hard drives, and also use a flash drive and an SD card regularly. 

I am trying to evaluate Ubuntu, but seem to be "trapped" in my VirtualBox. I need to  know whether I can use the OS to perform my day-to-day computing tasks.

How can I listen to an .mp3 on D: or move a photo from S: to E: when I cannot even find or see them from within Ubuntu?

---

### Post by tsp_2177 on 2010-04-04
> **harry003 said:**
> My VirtualBox is buried in a directory on one hard drive. I have 2 other hard drives, and also use a flash drive and an SD card regularly. 

I am trying to evaluate Ubuntu, but seem to be "trapped" in my VirtualBox. I need to  know whether I can use the OS to perform my day-to-day computing tasks.

How can I listen to an .mp3 on D: or move a photo from S: to E: when I cannot even find or see them from within Ubuntu?
i have had a few problems with ubuntu recognizing my sandisk drives but i haven't really played with that, that much it seems to load fine but then when it loads it just loads the thing to boot up the "OS" for that disk, at least thats what i called it, i tried that when i first started playing with ubuntu and haven't really touched my gaming laptop since lol. i have recently acquired an older laptop that i installed xubuntu on and have just been playing around with that. and i haven't needed to use a flash drive since then. my problem could easily be fixed if i played with it maybe or it could be a pain i don't know lol. but i do know that it will show that i have a usb device plugged in. heck it's even letting me use a usb wireless card without having to install anything it just worked! if i had to guess it's just the virtual box thats not letting you do anything with it. if i were you i would shrink a small volume of a hard drive and install unbuntu on there to "test it out" like i did, and if you don't love it just uninstall it. luckily i love it! and if i didn't have to use windows for school work i probably would never use it again! lol

---

### Post by bhmildy on 2010-04-04
I tried to run Ubuntu 9.10 in VB, and couldn't really get it to work.  It works much better installed directly on a machine than installed virtually.

Per the above poster, there are two versions of VB.  one is open source edition, VB OSE, the other is regular old VB.  You need to run the regular old VB, because it's the only one that has USB support.

You also need to have "Guest Additions" installed, which tightens the integration between the guest and host.

You also need to manually to up to the devices menu, USB sub menu, and put a check mark next to the USB device that you want the guest OS to use.  Only then will it work. (You'll see the USB icon, next to the virtual hard drive icon, start to flash when USB is connected and working.)

---

### Post by 3rdalbum on 2010-04-04
> **harry003 said:**
> My VirtualBox is buried in a directory on one hard drive. I have 2 other hard drives, and also use a flash drive and an SD card regularly. 

I am trying to evaluate Ubuntu, but seem to be "trapped" in my VirtualBox. I need to  know whether I can use the OS to perform my day-to-day computing tasks.

How can I listen to an .mp3 on D: or move a photo from S: to E: when I cannot even find or see them from within Ubuntu?

If you need to do these things in Ubuntu, then you must run Ubuntu on your hardware, not in a virtual machine (Virtualbox). Virtual machines have limits to what they can touch in your system; working directly with a real hard disk would be disastrous if the host OS decided to start working with the disk at the same time.

My advice would be to install Ubuntu using the Wubi tool on the Ubuntu CD. Use it this way for evaluation (there are still limits, but not as many as inside a virtual machine). If you decide you want to use Ubuntu full-time, then remove it using Windows' Add/Remove Programs and then boot up the Ubuntu CD to install the system.

---

### Post by tsp_2177 on 2010-04-04
> **bhmildy said:**
> I tried to run Ubuntu 9.10 in VB, and couldn't really get it to work.  It works much better installed directly on a machine than installed virtually.

Per the above poster, there are two versions of VB.  one is open source edition, VB OSE, the other is regular old VB.  You need to run the regular old VB, because it's the only one that has USB support.

You also need to have "Guest Additions" installed, which tightens the integration between the guest and host.

You also need to manually to up to the devices menu, USB sub menu, and put a check mark next to the USB device that you want the guest OS to use.  Only then will it work. (You'll see the USB icon, next to the virtual hard drive icon, start to flash when USB is connected and working.)
thanks! i'll try that next time i use it

---

