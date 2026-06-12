---
title: "Noob in need!"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by eversilentone on 2011-08-21
Hi there :)

I managed to install Lubuntu on my laptop and am sufficiently impressed that I want to install Ubuntu on my desktop.  Caveats being a) when I boot from my USB HD (the same one and the same method for my laptop) it just freezes on a black screen with a white cursor blinking intermittently.

b) I tried loading it via Wubi but it wouldn't seem to allow me to update the driver on my graphics card (ati Radion HD 5800) and, for some reason, the mouse pointer was invisible...

c) and finally I use my current PC to game - I tried WINE/POL on my laptop to run WoW, and it was a bust - I could load the program but it took me nearly 10 mins just for the system to process my clicking through all the EULAs.  It's a low spec laptop (maybe 6 years old?) but I had WoW running on in (at low specs) as recently as six months ago.

Anyhow, if you can help I'd be much obliged.  I'm scared and nervous and excited about being able to make the switch to Ubuntu on my main box.  It's fine not being able to game on my laptop, but if I can't play WoW or my many Steam games then that's a road block for me :(

Thanks in anticipation :)

---

### Post by SavageWolf on 2011-08-21
You can dual boot, this means you can run both Windows and Ubuntu at the same time, switching at boot. Have you the facilities to burn the ISO to a disk (A disk burner and actual disks)? And have you checked the MD5 sum of the download? See here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Quackers on 2011-08-21
You may need to use the nomodeset boot option to boot the live cd/usb.
Read here
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by eversilentone on 2011-08-22
Hi Quackers, thanks for this - I suspect it's the answer.  But in my ignorance I'm not actually sure how to make the changes outlined in the link you sent: are these supposed to be options in the bios?  Or do I have to run something in the Windows terminal before I try to access the bios?

Sorry - as I said, noob indeed.  But I've been playing on my ubuntutop and loving it.  Gaming is the *only* reason I can think of to stay with Windows, and I think I'll probably just run Win7 on a virtual box with a main install of Ubuntu... if I can ever install it! :)

---

### Post by Mark Phelps on 2011-08-23
If your plan is to use Win7 in a virtualized mode ONLY to play Windows games -- that will most likely not turn out well.

Gaming is especially demanding on PC resources, and using it in a VM doesn't give it the access it needs to those resources.

You would do better keeping win7 in "native" mode and using Ubuntu in its own partitions.  That way, you will be able to experience the best of both worlds.

---

### Post by idoitprone on 2011-08-23
> **Mark Phelps said:**
> If your plan is to use Win7 in a virtualized mode ONLY to play Windows games -- that will most likely not turn out well.

Gaming is especially demanding on PC resources, and using it in a VM doesn't give it the access it needs to those resources.

You would do better keeping win7 in "native" mode and using Ubuntu in its own partitions.  That way, you will be able to experience the best of both worlds.

well it depends. He can run warcraft 3 just fine. I have to say running wow on a 6 year old computer is kidda though. Even if the computer is running natively, I wonder if it is able to handle wow.

If he wants to try to play wow on linux, then wine it is best bet. It does not have the same penalty as running in a virtual enviroment
Wine has been shown to handle wow well

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922)

---

### Post by eversilentone on 2011-08-30
Hi I've finally managed to install Ubuntu - I changed a bios setting for usb storage to force booting.  So I have 11.04 installed but my mouse cursor is invisible?  It still works, as I get tool tips when I mouse over things, and I was just about able to complete the install, but it's not a usable machine right now.  I've tried my really basic usb mouse (I don't have other ports on my computer, or non-usb mice to try) and it's still the same.  Can you help me?

EDIT:

So I found out that it was not installing the proprietary driver but when I clicked activate it came up with:

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.940-0ubuntu_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/restricted/f/fglrx-installer/fglrx-amdcccle_8.940-0ubuntu_i386.deb) Could not resolve gb.archive.ubuntu.com'

I have no idea what that means, but I'm guessing my invisible mouse cursor is related to my graphics card?

EDIT2:
I tried it again after disabling then re-enabling my graphics card and it downloaded.  It may have been that the server was busy or perhaps the disabling helped.  Either way, this particular issue is now closed for me, thanks all for your help.

---

