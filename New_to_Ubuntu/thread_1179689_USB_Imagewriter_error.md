---
title: "USB Imagewriter error"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by Famicommander on 2009-06-05
I'm attempting to install Netbook Remix on my Asus EEE 901.

So, I downloaded the .img file and installed imagewriter. But when I run it, it this is what comes up in the details:
```
Image: /home/jason/ubuntu-9.04-netbook-remix-i386.img
Target Device: Unknown Unknown (/dev/sdb)
Unmounting all partitions of /dev/sdb:
Trying to unmount /dev/sdb...
/dev/sdb successfully unmounted
Executing: dd if=/home/jason/ubuntu-9.04-netbook-remix-i386.img of=/dev/sdb
```

Then it says to check the details for the error message, but there doesn't seem to be one there. The program just closes when I click "OK" on the pop up window.

I also tried doing it in Windows, but for some reason Windows XP reads my flash drive as 931 MB, while Ubuntu reads it as 976 MB. Windows thinks my drive is smaller than the .img file, so it just quits.

A solution befitting either operating system would be nice. The sooner I get Xandros Linux off my EEE PC, the better.

---

### Post by Famicommander on 2009-06-05
Question-- What special advantages would there be to installing Netbook Remix in the first place, aside from conserving screen space?

Are there any special optimizations for the Atom processor, or would I be just as well off installing standard Ubuntu or Xubuntu?

Because my only real concern is whether or not my OS will detect my wireless card, bluetooth device, webcam, and microphone.

If basic Jaunty will do all of that by default, then I'll just skip Netbook Remix and install Xubuntu.

---

### Post by Famicommander on 2009-06-06
Well, since I didn't get a reply, I'm just going to wing it and dig out my old external CD ROM drive and install Xubuntu.

---

### Post by mikechant on 2009-06-08
> Question-- What special advantages would there be to installing Netbook Remix in the first place, aside from conserving screen space?

Are there any special optimizations for the Atom processor, or would I be just as well off installing standard Ubuntu or Xubuntu?

I've got UNR running on my eeePC 1000 and I'm happy with it. I think the problem with installing standard Ubuntu is that some dialogue boxes will be partly offscreen, which can be a pain, whereas with UNR they're usually resized to fit the screen.

From what I've read, UNR is not optimized for the Atom or other low power processors. I understand that you need to install a special kernel (LPIA kernel?) if you want Atom optimization. I'm considering this but I've also read that the optimization doesn't make a big difference.

Incidentally, did you actually try booting from your flash drive after using imagewriter in Ubuntu? Maybe the error message was an error...

---

