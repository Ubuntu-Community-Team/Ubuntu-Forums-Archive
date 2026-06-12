---
title: "Bootable ISO"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by theozzlives on 2009-01-10
I have a boot-able ISO that I created with remastersys. I want to burn that to a USB drive. What software do I use?

---

### Post by triFeral on 2009-01-10
What OS are you running at the moment?

---

### Post by Oak37 on 2009-01-10
[Unetbootin]("http://unetbootin.sourceforge.net/") is a good solution that is cross-platform. (Well almost, it doesn't work on Macs)

---

### Post by theozzlives on 2009-01-11
> **triFeral said:**
> What OS are you running at the moment?

Ubuntu, but my laptop has Winblows XP for uCertify, and Transcenders.

---

### Post by ugm6hr on 2009-01-11
> **Oak37 said:**
> [Unetbootin]("http://unetbootin.sourceforge.net/") is a good solution that is cross-platform. (Well almost, it doesn't work on Macs)

This should work

I'd recommend you use it from XP - it seems to work better than the Linux version (don't know why).

---

### Post by theozzlives on 2009-01-11
> **ugm6hr said:**
> This should work

I'd recommend you use it from XP - it seems to work better than the Linux version (don't know why).

That worked, Except it made a live USB. I wanted persistence.

I think I need something besides remastersys

---

### Post by theozzlives on 2009-01-11
bump, please

---

### Post by ugm6hr on 2009-01-11
You can just install to the USB as if it is a HD.  Just be careful of where Grub is installed.

---

### Post by blackened on 2009-01-11
So far all I've seen that can accomplish what you're asking is DSL's pendrive version. You might head over there and poke around: [http://damnsmalllinux.org/usb.html]("http://damnsmalllinux.org/usb.html")

or do a frugal install to minimize OS writes to the media.

---

### Post by Captain_tux on 2009-01-11
If you're using Intrepid click on **System > Administration > Create a USB start up disk**. To ensure persistence, make sure you select **Stored in reserved extra space** and slide the bar as far over as desire.

---

### Post by blackened on 2009-01-11
> **Captain_tux said:**
> If you're using Intrepid click on **System > Administration > Create a USB start up disk**. To ensure persistence, make sure you select **Stored in reserved extra space** and slide the bar as far over as desire.

Nice. I knew about this, but didn't realize it was so capable.

---

### Post by theozzlives on 2009-01-11
> **ugm6hr said:**
> You can just install to the USB as if it is a HD.  Just be careful of where Grub is installed.

That's a clean install, I want my setup on the USB.

---

### Post by theozzlives on 2009-01-11
> **blackened said:**
> So far all I've seen that can accomplish what you're asking is DSL's pendrive version. You might head over there and poke around: [http://damnsmalllinux.org/usb.html]("http://damnsmalllinux.org/usb.html")

or do a frugal install to minimize OS writes to the media.

Played with DSL don't like it.

---

### Post by blackened on 2009-01-11
Please multi-quote your posts.

> **theozzlives said:**
> That's a clean install, I want my setup on the USB.So wait, you're wanting a mirror image of your HD install on a USB drive? It's probably possible with something like acronis true image, but it seems like a waste of time. IMO it would be easier to do a clean install and then set it up as you like it.

> **theozzlives said:**
> Played with DSL don't like it.

What's not to like about it? It's the same as every other distro around, just a smaller base install, but completely extendable.

---

### Post by Frak on 2009-01-11
> **blackened said:**
> What's not to like about it? It's the same as every other distro around, just a smaller base install, but completely extendable.

Well, it's ok unless he needs multimedia capabilities. DSL is very old, and doesn't support anything much newer. I'd suggest more along the lines of Puppy or Slax.

---

### Post by blackened on 2009-01-11
> **Frak said:**
> Well, it's ok unless he needs multimedia capabilities. DSL is very old, and doesn't support anything much newer. I'd suggest more along the lines of Puppy or Slax.

Sorry, my main point in suggesting DSL was that it comes as a ready-made distro for installation on flash media and that, at its core, doesn't differ that much from most linux distros available. 

Looks like this is becoming an Oklahoma dominated thread.

---

### Post by Frak on 2009-01-11
> **blackened said:**
> Sorry, my main point in suggesting DSL was that it comes as a ready-made distro for installation on flash media and that, at its core, doesn't differ that much from most linux distros available. 

Looks like this is becoming an Oklahoma dominated thread.
Let the dustbowl begin!

---

### Post by theozzlives on 2009-01-12
I used pendrivelinux's script to do a clean install. Lots of configuring to do (mine is far from default).

---

### Post by theozzlives on 2009-01-12
> **theozzlives said:**
> I used pendrivelinux's script to do a clean install. Lots of configuring to do (mine is far from default).

I wonder what would happen if I ran Install from the Administration menu and specify my USB drive?

---

### Post by blackened on 2009-01-13
> **theozzlives said:**
> I wonder what would happen if I ran Install from the Administration menu and specify my USB drive?

Post #8:
> **ugm6hr said:**
> You can just install to the USB as if it is a HD.  Just be careful of where Grub is installed.

---

