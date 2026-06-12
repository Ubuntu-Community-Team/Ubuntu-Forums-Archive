---
title: "Starting Out"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by fuse_Man91 on 2010-10-01
Hi there,

I've always wanted linux on my computer, but 1) I don't know how to burn the iso image I download from the site and 2) I don't know how to partition my hd (yes I want to leave windows on my computer until I get comfortable with linux). Also, my friend tried to install it once and my wireless card (PCIe GBE Family Controller) failed to work. How do I ensure this won't happen again?

Thanks a bunch

---

### Post by Quackers on 2010-10-01
Which Windows version do you have? If you have Vista or W7 you can resize your Windows partition from within Windows.
The .iso file needs to be burned to a cd (Imgburn will do it). You MUST select "burn image" though, don't just burn the files.

---

### Post by Daniel0108 on 2010-10-01
If you don't get the cd burned and the hard-drive partitioned, try WUBI :)
It's easy ;) and when you get comfortable with linux, you can install the REAL Ubuntu ;)
Yours,
Daniel

---

### Post by fuse_Man91 on 2010-10-01
I have windows 7... I did try wubi, but once again my wireless adapter didn't work. Then it says to get the driver for the adapter that ends in .inf and install ndisgtk. I don't know how to do either....

---

### Post by sikander3786 on 2010-10-01
*.inf driver files can be installed on Ubuntu by using ndiswrapper. You card might be natively supported, before going for ndiswrapper, which wireless card have you got?

---

### Post by Megaptera on 2010-10-01
Useful general guide here [http://kernelnews.com/articles/2010/ubuntu_for_winusers.html](http://kernelnews.com/articles/2010/ubuntu_for_winusers.html)

---

### Post by fuse_Man91 on 2010-10-01
I have the Realtek PCIe GBE Family Controller. Should I just put the ndiswrapper on a flash drive and use that to install it on Ubuntu?

---

### Post by oldos2er on 2010-10-01
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[https://help.ubuntu.com/10.04/switching/C/index.html](https://help.ubuntu.com/10.04/switching/C/index.html)

---

### Post by themusicalduck on 2010-10-01
Once you have booted in, go to System > Administration > Hardware drivers to see if you can install a driver for your wireless card. You'll need a wired connection to the internet to download the driver though.

---

### Post by fuse_Man91 on 2010-10-01
Perfect! Thanks musicalduck that worked perfectly. I didn't even think to use a wired connection. Everything is good to go now I think. Any recommendations on things I should do as a first time linux user?

---

### Post by Daniel0108 on 2010-10-02
> **fuse_Man91 said:**
> Any recommendations on things I should do as a first time linux user?
Change the Appearance, make the Panel so, that you like it ;) Configure the chat accounts and email account(i recommend to download Thunderbird). Look into the Software Center for programs, you may like. 
PS: Click on Thread Tools(in the Ubuntu Forums) and click on "Mark this thread as solved".
Yours,
Daniel

---

### Post by themusicalduck on 2010-10-04
> **fuse_Man91 said:**
> Perfect! Thanks musicalduck that worked perfectly. I didn't even think to use a wired connection. Everything is good to go now I think. Any recommendations on things I should do as a first time linux user?

Glad it worked! :)

For a first time user, I'd recommend taking a look at [http://ubuntu-manual.org](http://ubuntu-manual.org) It provides a no-nonsense easy beginners guide to Ubuntu and tells you about a lot of what you can do with Ubuntu.

Good luck!

---

