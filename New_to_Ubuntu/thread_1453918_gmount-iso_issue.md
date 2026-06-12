---
title: "gmount-iso issue"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by us11csalyer on 2010-04-13
An error occured
 wrong fs type, bad option, bad superblock on /dev/loop0,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

How the heck do I fix this?

---

### Post by NightwishFan on 2010-04-13
It is likely the image you are trying to mount is not a true .iso. Can you open it with the archive manager?

If you can open the .iso file, and it does not say "This is not an iso9660 image" then try making a new directory to mount isos with.
```
sudo mkdir /media/virtual
```

---

### Post by us11csalyer on 2010-04-13
error: CD-ROM is NOT in ISO 9660 format

So what can I do from here?

---

### Post by NightwishFan on 2010-04-13
I suppose if you made the image yourself, remake it. If you found it somewhere check your download.

---

### Post by us11csalyer on 2010-04-13
> **NightwishFan said:**
> I suppose if you made the image yourself, remake it. If you found it somewhere check your download.

I can't remember what program I used in win7 but this iso file is all my important files.

---

### Post by NightwishFan on 2010-04-13
I suppose you might want to open it using Windows if possible. It must not be standards compliant, or has had an error somewhere.

---

### Post by us11csalyer on 2010-04-13
I know I can mount it with deamon tools in windows. Can I install that emulator in wine?

---

### Post by NightwishFan on 2010-04-14
I doubt it, because it probably relies on installing a driver to work, which is not compatible with wine. It gets a "garbage" rating on the Wine App Database. You will likely need to open the .iso or try to burn it somehow. Give this a shot on Ubuntu in the terminal. Ensure you have a blank cd/dvd of a suitable size before you try. I do not think this will work though.
```
wodim /path/to/iso
```

You will probably need to use someone's Windows to open this. It is not that Ubuntu cannot open .iso files, just the program probably did not create it correctly.

---

### Post by us11csalyer on 2010-04-14
Thank you for your help.

---

### Post by NightwishFan on 2010-04-14
If you have any other questions about it, you know where to ask. I am not an expert on all things iso though.

---

### Post by new to linux help needed on 2011-12-12
i have the same issue when im trying to install an iso of civ V. but i cannot open with Archive manager or use the Archive Mounter.

---

### Post by coffeecat on 2011-12-14
Old thread. Closed.

---

