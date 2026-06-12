---
title: "MSI wind flicker (9.10)"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by pearldrums on 2009-11-06
Hi, I just installed Ubuntu 9.10 on my MSI wind and encounter the know issue talked about here: [http://www.ubuntu.com/getubuntu/releasenotes/910#Brightness%20flickering%20on%20MSI%20Wind%20netbooks%20with%20KMS](http://www.ubuntu.com/getubuntu/releasenotes/910#Brightness%20flickering%20on%20MSI%20Wind%20netbooks%20with%20KMS)
Unfortunately I've been unsuccessful in disabling KMS. Heres what my grub file looks like:
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=54268f7d-ba2f-45fb-b9e2-65b894f69286 ro

what i'm gathering is that I should change that last line to:
# kopt=root=UUID=54268f7d-ba2f-45fb-b9e2-65b894f69286 ro nomodeset
or perhaps even
# kopt=root=UUID=54268f7d-ba2f-45fb-b9e2-65b894f69286 ronomodeset

both of which have not worked for me. Am I doing something wrong, or is there something else I need to be doing?

---

### Post by ricojonah on 2009-11-06
Unfortunately, I've been having this same problem for a few weeks now on my U100 as well. I've tried the same modifications, but ultimately I just wound up restoring my Jaunty system backup.

Best of luck to you (and other MSI Wind owners) who are encountering this same issue. Karmic will be an amazing release once some of these small (but irritating) bugs are fixed.

---

### Post by saleminkb on 2010-03-25
Look around in other threads, this problem is everywhere, there are instructions on how to update your bios, which apparently solves the problem.

---

### Post by Gadgetech on 2010-03-25
I'm also running Jaunty on my U100 because of the flicker issue. I have tried Lucid Beta1 and the flicker issue is resolved. Unfortunately the webcam and Bluetooth don't work. These may have been resolved already. I've only run a LiveUSB so far, so I haven't gotten the latest updates.

---

### Post by ricojonah on 2010-03-25
FYI for anyone still having issuess with the flickering issue on the MSI Wind U100: 

I haven't tried this out yet, but an extremely helpful user from another forum provided the link to the download for the BIOS update:

[http://www.msi.com/index.php?func=do...5&prod_no=1474]("http://www.msi.com/index.php?func=do...5&prod_no=1474")

---

### Post by pearldrums on 2010-03-29
the last posted link did not work for me, but I believe this one is the one we are looking for:
[http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1474](http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1474)
I also have not tried it. I will install tonight, but I am going to run 9.04 untill 10.04 comes out, so I will only know if it totally bonks my sys.

[COLOR=DarkRed]EDIT: Hmmmmm oddly enough the link looks to be exactly the same, but it still does not work for me. If you have the same issue, go to MSI's site and search "U100 bios update" and click full text search. Hope that helps.[/COLOR]

---

### Post by Puzzled Guy on 2010-06-29
Good news guys!

I just tested a Ubuntu 10.04 LiveUSB session last night on my MSi Wind U100 and had no problems with wifi cards and encountered no screen flicker.  I posted my initial findings here: [http://ubuntuforums.org/showthread.php?t=1517589](http://ubuntuforums.org/showthread.php?t=1517589)

Although I think there is that problem where the computer hibernates if you start on AC power and then unplug it (the workaround can be found here: [http://ubuntuforums.org/showthread.php?p=9289047](http://ubuntuforums.org/showthread.php?p=9289047) in the first post).

---

