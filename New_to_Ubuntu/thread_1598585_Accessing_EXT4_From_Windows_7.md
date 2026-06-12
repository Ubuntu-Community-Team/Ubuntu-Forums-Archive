---
title: "Accessing EXT4 From Windows 7"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by Joshwaa on 2010-10-16
I was wondering if there was any way of me accessing my Ubuntu filesystem from my Windows 7 OS.
I need read/write capabilities aswell, not just read.

Cheers :)

---

### Post by Hippytaff on 2010-10-16
was going to say samba, but not sure  about write permissions

---

### Post by BrockStrongo on 2010-10-16
If you are referring to accessing your windows partition on a dual boot machine. Ext2read does the trick. I use it on my computer and have had no problems. The newest version is available at [http://sourceforge.net/projects/ext2read/files/](http://sourceforge.net/projects/ext2read/files/)
there are a bunch of similar programs but I haven't tries many of them. I stopped looking when I found one that worked.
Hope this helps

---

### Post by anewguy on 2010-10-16
I always just make sure I have a NTFS partition (don't know Windows 7, so don't know what it uses).  Placing files there they can be read/write from Linux, Windows, etc..

Dave ;)

---

### Post by Joshwaa on 2010-10-16
> **BrockStrongo said:**
> If you are referring to accessing your windows partition on a dual boot machine. Ext2read does the trick. I use it on my computer and have had no problems. The newest version is available at [http://sourceforge.net/projects/ext2read/files/](http://sourceforge.net/projects/ext2read/files/)
there are a bunch of similar programs but I haven't tries many of them. I stopped looking when I found one that worked.
Hope this helps

I'll check this out :)
Oh and I was talking about accessing Ubuntu from Windows, I can easily access Windows from Ubuntu.
I need to keep Windows because of proprietary software.

---

### Post by bob-linux-user on 2010-10-16
Be careful. I once found a download that was supposedly EXT4 drivers for Windows and it was some piece of malware.

---

### Post by BrockStrongo on 2010-10-16
> **Joshwaa said:**
> I'll check this out :)
Oh and I was talking about accessing Ubuntu from Windows, I can easily access Windows from Ubuntu.
I need to keep Windows because of proprietary software.

Sorry thats what I meant accessing ubuntu partition from windows side. Thats what I get for not reading my posts before submitting them

---

### Post by HermanAB on 2010-10-16
Howdy,

I just make sure that the schtuff that I have to access from Windows are in fact on the Windows partition and access it that way from Linux.

---

### Post by anewguy on 2010-10-17
Also, like I said, if you have a NTFS partition you can go either way from either operating system.

Dave ;)

---

