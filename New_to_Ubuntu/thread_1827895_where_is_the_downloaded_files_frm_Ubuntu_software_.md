---
title: "where is the downloaded files frm Ubuntu software center stored?"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by jeshrel on 2011-08-18
Hi

Where is the downloaded files from the Ubuntu software center stored after installation?

And can the downloaded files be deleted after installation?

Thank you

---

### Post by howefield on 2011-08-18
FIles are stored in

```
/var/cache/apt/archives
```

and can folder can be emptied by using the terminal command

```
sudo apt-get clean
```

---

### Post by jeshrel on 2011-08-18
thanks, and are there any others cleaning commands so that i can clean all the unwanted cache, thumbnails saved, and other stuff?

---

### Post by jerrrys on 2011-08-18
[BleachBit]("http://bleachbit.sourceforge.net/"), its in the software center

---

### Post by jeshrel on 2011-08-18
thanks for ur help, appreciate it..

---

### Post by adeklipse on 2011-08-18
> **jeshrel said:**
> thanks, and are there any others cleaning commands so that i can clean all the unwanted cache, thumbnails saved, and other stuff?

If you want a reliable cleaner, I suggest the one included in Ubuntu Tweak. Installation:

```
sudo add-apt-repository ppa:tualatrix/ppa && sudo apt-get update
sudo apt-get install ubuntu-tweak
```Open in Applications > System Tools > Ubuntu Tweak.

If you're quite familiar with Linux, you might also want to try BleachBit. It's very advanced and the interface and technical lingo might be confusing, but it's fully-featured.
Just a warning, though: not all of BleachBit cleaning options are safe. Most should be treated carefully and read thoroughly to avoid the possibility of unwanted file-deletion, as it will only prompt you once (or twice).
Installation: I believe BleachBit is already in the Ubuntu Software Center.

---

### Post by jerrrys on 2011-08-18
my setting for BB

[ATTACH]200275[/ATTACH]

---

