---
title: "Problem with Linksys WIreless USB"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by leenyx64 on 2009-01-29
Hello,
 
I am having trouble with my desktop running 8.10.  My desktop is no where near a hard line for the Internet so i had to install a USB wireless adapter.  The USB is a Linksys WUSB600N.  It has been working perfectly for awhile now.  Every time i start the computer i have to use the terminal to navigate to the directory containing the Linksys software and type:

sudo insmod rta2870sta.ko

this is a bit of a pain the *** every time but it usually gets the device turned on then everything is perfect. The problem is today i did that same code and i got:

insmod: error inserting 'rta2870sta.ko' : -1 Invalid module format

I don't know what happened.  Can someone please shed some light on what went wrong.  Thanks

---

### Post by leenyx64 on 2009-01-29
bump

---

### Post by leenyx64 on 2009-02-01
bump

---

### Post by mizunoX on 2009-02-03
> **leenyx64 said:**
> bump

I think you've probably compiled this driver against an older kernel, now you've updated and it's not working anymore.

Go back to the folder where you compiled the driver (or download it again) and "sudo make" again.

You can also automate loading the driver... follow my thread here:
[http://ubuntuforums.org/showthread.php?t=972060]("http://ubuntuforums.org/showthread.php?t=972060")  check post 10 for that.

---

### Post by leenyx64 on 2009-02-08
mizunoX,

you rule.  worked perfect.

---

### Post by netman74501 on 2009-02-14
I have the same problem. My driver has stopped working. I have stayed on an old kernel just to use my wireless card for a while now and am fed up with being behind because of the thing. I can compile against the new kernels just fine, but when I insert it, nothing seems to happen. The light on the card is always on too. It acts as if it is working but ifconfig shows nothing. I can go back to my old kernel without recompiling the driver and it still works! How's that!? Seems weird that it would still work on the old kernel even though I have recompiled it for the new kernel. Old kerenel is: 2.6.27-9 and the new kernel is: 2.6.27-11. I am running Ubuntu Itrepid 8.10. Thanks in advance...

EDIT: On second thought, it's not the *exact* same problem. I don't get an error message saying module invalid.

EDIT 2: Well. After struggling with this for quite a while now and finally working up the nerve to post, I just solved it on my own. Grrr. Hate it when that happens.... I did it by deciding to follow the link above, (meant for enabling it to load automatically), and the first post on the page has the link to where I found my solution. I had forgotten that I had to add the WUSB600N to the rt2870.h file.

---

