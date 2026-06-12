---
title: "Ubuntu 10.04 unistall nvidia drivers"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by servicetech on 2010-04-10
I can't uninstall the nvidia drivers through the "hardware drivers". It's stuck on 173, no option to uninstall, just says another version in use.

Other that that I'm liking the new 10.04 :)

---

### Post by servicetech on 2010-04-10
Here's some screen shots to explain better:

---

### Post by servicetech on 2010-04-10
Apparently it installed? even though I get an install failed message?
Newest version at that...

---

### Post by rtilson on 2010-04-10
Go into synaptic package manager...once in there search for nvidia...uninstall any packages that deal with the nvidia driver...the nvidia modaliases packages theses provide the pci ids that the driver will uses to detect ur graphic card.

For me I have nvidia-current installed look for that package uninstall...restart computer...one you log back in try to reinstall through the hardware drivers.

But you already have the drivers installed. Really there is no need to do anything because it seems that you are running compiz and nvidia-settings shows the most current driver.

---

### Post by servicetech on 2010-04-10
Suspend still not working. Works once then hangs the 2nd time I try to use it. Uninstalled nvidia drivers and still didn't fix. Oddly suspend did work before I installed the nvidia drivers the first time. Now I can't get the nvidia drivers back. No option to install hardware driver, just says no proprietary driver installed.

---

### Post by servicetech on 2010-04-10
Screenshot This is after searching for drivers.

---

### Post by rtilson on 2010-04-10
I had that some problem with no drivers found. Had to use synaptic to install the nvidia-current package. After that in a terminal run sudo nvidia-xconfig.

I have never had any problems with suspend. If it works and you try to resume and get a black screen try hitting ctrl + alt + f7. Could be that when resuming it cant determine which terminal to resume. I have experienced this before but not recently.

The other option is to install the nvidia binary driver from the nvidia website.

To make sure we are on the same page you want to install the drivers because suspend wasnt working and you are trying to get suspend working again.

---

### Post by clhsharky on 2010-04-10
HI

Lucid has its own section here

Lucid Lynx Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

Sharky

---

### Post by servicetech on 2010-04-10
Thanks for the link. It's not just a Lucid problem, I had it in 9.10 also. FWIW I reinstalled and still have the same problem before any drivers were changed. Apparently it's NOT and Nvidia driver issue. I was hoping that the suspend issue would have been fixed for this version but maybe next time...

---

