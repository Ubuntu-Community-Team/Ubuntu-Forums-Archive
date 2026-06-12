---
title: "USB 'mounted' image on my desktop with nothing associated to it"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-05
Hi,
I've been messing around with mounting boots to a USB stick. Now this USB stick appears in my Places, even though it's not plugged in. I'm guessing Ubuntu is seeing it as a virtual drive or something but it's also on my desktop. How do I get rid of it? 

Thanks

---

### Post by tkoco on 2010-11-05
> **demonboy said:**
> Hi,
I've been messing around with mounting boots to a USB stick. Now this USB stick appears in my Places, even though it's not plugged in. I'm guessing Ubuntu is seeing it as a virtual drive or something but it's also on my desktop. How do I get rid of it? 

Thanks

Which version of Ubuntu are you using?

---

### Post by JustinR on 2010-11-05
Hi,

press 'ALT + F2' and type 'gksudo nautilus'

Then navigate to '/media' and simply delete the flash drive folder from there (as long as the drive in unmounted - it's fine). It should disappear. If not, open up nautilus (eg. double click your home folder) and go to Bookmarks > click on the USB drive name > 'Remove Item'.

---

### Post by tkoco on 2010-11-05
> **JustinR said:**
> Hi,

press 'ALT + F2' and type 'gksudo nautilus'

Then navigate to '/media' and simply delete the flash drive folder from there (as long as the drive in unmounted - it's fine). It should disappear. If not, open up nautilus (eg. double click your home folder) and go to Bookmarks > click on the USB drive name > 'Remove Item'.

Thanks. I was thinking that if he was running a bleeding edge version of Ubuntu, the problem might need reporting to launchpad.

---

### Post by demonboy on 2010-11-06
Good morning,

Well since yesterday I rebooted Ubuntu and found that I had lost my Applications drop-down menu (see other thread - my Apps doc was empty), but so too had the shortcuts to this drive. It did not appear in my Bookmarks drop-down.

I am running 10.10 and am new to Linux so I can't really help but if there is any diagnostic test I can run to help with dev then please let me know.

For the time being, problem gone. :P

---

