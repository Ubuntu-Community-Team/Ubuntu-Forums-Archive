---
title: "vboxusers not available in VirtualBox"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by dredvard on 2010-12-21
There might be a simple solution to this but I'm missing it.
 
Like this thread:
[http://ubuntuforums.org/showthread.php?t=1344075](http://ubuntuforums.org/showthread.php?t=1344075)
 
I believe I have the PUEL version installed (v 3.2.12r68302) although I'm not sure how to confirm I have the PUEL vs the OSE.  I did just download the binary.
 
I have Ubuntu 10.10 installed and added virtual additions.  I'm using Windows 7.
 
I tried deleting VirtualBox and reinistalling it but I stilldon't have vboxusers available as a group.
 
Even if I typing
 
sudo usermod -aG vboxusers $USER 
 
and I get
 
usermod: group 'vboxusers' does not exist

When I ran VirtualBox I did notice my two VirtualBox drives being installed as USB devices on Windows so something was happening.
 
Any additional suggestions?

---

