---
title: "Can not find program but it is in Synaptic"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by L Campbell on 2011-06-12
I downloaded and installed a CAD program, 'Draftsight', which should show up in Applications > Graphics but it is not there, although it is listed in Synaptic.

I tried looking in 'Search for files' but did not find it.

I would appreciate any suggestions here.

TIA

---

### Post by SoFl W on 2011-06-12
What happens when you try starting it from the command line (terminal)?

Are you sure it is suppose to be in the menu?  You might have to enter it manually.
I googled the name and the 3gs.com website gives me a redirection error.


If you have Ubuntu 64bit see this [link]("http://courira.ca/en/2011/03/draftsight-for-linux-how-to-install-on-ubuntu-64-bit").

---

### Post by VOT Productions on 2011-06-12
**ALT+F2** then type **draftsight**

---

### Post by L Campbell on 2011-06-12
> **VOT Productions said:**
> **ALT+F2** then type **draftsight**

Thanks but, unfortunately, I get a message 'no such file or directory'.

---

### Post by raja.genupula on 2011-06-12
do this in terminal ```
 which program_name 
```

program_name nothing but your application name , this will gives you its installation location

---

### Post by VOT Productions on 2011-06-12
Try this: **Terminal **and [B]draftsight
[/B]If it doesn't work, try **ALT+F2**and **/opt/dassault-systemes/draftsight/bin/DraftSight**

---

### Post by L Campbell on 2011-06-12
> **VOT Productions said:**
> Try this: **Terminal **and [B]draftsight
[/B]If it doesn't work, try **ALT+F2**and **/opt/dassault-systemes/draftsight/bin/DraftSight**

Many thanks, this got it up and running:-

 ALT+F2and /opt/dassault-systemes/draftsight/bin/DraftSight


It still does not show up in Applications > Graphics but I can use it this way.

---

### Post by VOT Productions on 2011-06-12
Tip: Make a shortcut on your desktop to access it faster.

---

### Post by L Campbell on 2011-06-12
> **VOT Productions said:**
> Tip: Make a shortcut on your desktop to access it faster.

That worked perfectly, thanks.

---

### Post by VOT Productions on 2011-06-12
> **L Campbell said:**
> That worked perfectly, thanks.

Your welcome

---

