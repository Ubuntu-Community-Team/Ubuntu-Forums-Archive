---
title: "Home Networking fails after reboot"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by OldGrey on 2009-12-10
Hi though I have been using Ubuntu for some time. I am no expert on newtworking.

Recently installed a wireless router, to which my Ubuntu PC is connected by ethernet and an iMac (Snow Leopard) is connected wirelessly. Things started well. I went to share a folder in Ubuntu, did the download, rebooted and hey presto I could see the iMac  on the Ubuntu PC and the iMac could see the Ubuntu PC. However when I later rebooted the Ubuntu PC The connection was broken and when I clicked on the Windows Network icon all I got was:

"Unable to mount location
Failed to retrieve share list from server"

and I cannot get beyond that. What went wrong?

---

### Post by cariboo on 2009-12-11
Can you pig the mac?

---

### Post by OldGrey on 2009-12-13
I am ashamed to show my ignorance, but how do I do that?

---

### Post by gaming_guy on 2009-12-13
> **OldGrey said:**
> I am ashamed to show my ignorance, but how do I do that?
open the terminal > type ping -c4 [IP or Hostname of the mac/computer/website] that you want to ping and then press enter to execute the command.

Example:
```

ping -c4 www.google.co.uk

```

---

### Post by Iowan on 2009-12-13
> **OldGrey said:**
> I am ashamed to show my ignorance, but how do I do that?
Don't be too ashamed - the missing "n" masks (obfuscates?) the actual question. ;)

---

