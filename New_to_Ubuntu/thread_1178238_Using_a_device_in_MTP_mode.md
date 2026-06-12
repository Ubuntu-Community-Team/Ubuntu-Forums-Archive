---
title: "Using a device in MTP mode"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by chacha_nehru on 2009-06-04
Hi, I've been trying to use my Sansa Fuze in MTP mode, so I can drag and drop files to its internal memory. That is, I want to use it as a memory stick too. So I set it to MTP mode and connected it to my system. I also installed the latest version of MTP-Tools. When I run MTP-Detect, it says that there are no Devices connected. Running 'lsusb' shows a device listed as 'Sandisk', but it does not show up under 'Places'. It does not show up in /media either.. What can I do ?

---

### Post by Hospadar on 2009-06-04
well for starters, don't confuse mtp with a real mounting or filesystem protocol, because it isn't.
It's possible to emulate a filesystem with mtpfs, but it just makes it look nice, and doesn't provide the same kind of disk access you'd expect with a usb drive or similar.  If you device has a "removable disk" mode (I know the creative players do) that's what you probably want to use (since dragging files in with mtpfs won't allow you to play them on the player anyways typically)

If you're trying to put music (or files) on the device, I'd strongly suggest gnomad2, it's simple and effective, and doesn't give the sometimes confusing illusion of folders that don't really exist (which mtpfs can do because of the nature of mtp).

Also, only one program can attempt to use an mtp device at once, so if you rythmbox running in the background, it's probably trying to connect and tying things up in the process.  Make absolutely sure nothing is attempting to access the device before you attempt.  I often have to force plug and unplug mine (A creative player) a couple times to make it work

---

### Post by chacha_nehru on 2009-06-04
Thanks for the reply.. Yes, I wanted to use my device in the removable disk mode..I only wanted to transfer other data such as text files, movies, etc which I had stored in the device in the removable disk mode. And I am not using any other applications in the background which may attempt to access the device. What could the problem be?

---

### Post by chacha_nehru on 2009-06-05
any suggestions, people?

---

