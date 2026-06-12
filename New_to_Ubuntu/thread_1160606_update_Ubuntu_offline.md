---
title: "update Ubuntu offline"
date: 2009-05-15
forum: New to Ubuntu
---

### Post by realmoonstruck on 2009-05-15
is there a way to download the updates from one computer and then install them on another without too much hassles?
actually my friend has a very slow dial-up connection so he can't install the updates.

---

### Post by sundar_ima on 2009-05-15
there are few methods. but aptoncd is the graphical way to do that. install aptoncd in the computer which has good Internet connection (Synoptic--> aptoncd). update your system (**sudo apt-get update**). then open aptoncd (system-->> administrator) and create image. by default this .iso image will be saved in your home folder (places-->> home folder). take this image to your friend's computer and extract the .iso image (right click-->> extract here). you can find packages folder inside extracted folder (which contain .deb packages). just copy and paste this packages folder to desktop. Now open terminal and give this following command...

**sudo dpkg -i ~/Desktop/packages/*.deb**

now your friend's system should be up to date....

---

### Post by nhasian on 2009-05-15
+1 for aptoncd

my friend is stationed in Iraq and they dont let him use an internet connection anymore so we use aptoncd to keep his ubuntu updated and to install programs that he doesnt have access to.

---

### Post by realmoonstruck on 2009-05-16
**Thanks a lot.** :KS

---

### Post by k3lt01 on 2009-05-16
There is another option that is, I think, much better. [Check this out]("http://ubuntuforums.org/showthread.php?t=352460"). This way your friend can have EVERY available package not just the ones you choose to use.

---

### Post by ugm6hr on 2009-05-16
Synaptic has an option of creating a download script (using wget).

If your friend has an identical installation to you, then aptoncd is fine (although I would recommend installing updates using Synaptic or apt-get rather than dpkg).

If they have additional software (but use the same version of Ubuntu), try this:
Copy your /var/cache/apt/archives/ directory (except the lock file) and copy to their computer (same directory) - this just ensures you dont download the same updates twice
On their computer:
First install all your updates that you have just copied
```
sudo apt-get upgrade
```
Open Synaptic
Connect to internet
Click *Reload*
Click *Mark all upgrades*
File -> Generate Package Download list

This will generate a script with a list of wget commands for the necessary downloads.  Take this script back to somewhere with a fast connection (or email it to a friend!), and run it.

These can then be installed by using the "Add downloaded packages" option in Synaptic.

Repeat as necessary.

---

### Post by mac9416 on 2009-05-16
[Keryx]("http://keryxproject.org") can help you.

---

### Post by Cheesemill on 2009-05-16
+1 for Keryx

---

### Post by EXCiD3 on 2009-05-16
+2 for keryx :D

---

### Post by bimbot on 2009-12-16
+3 Keryx.  I just downloaded VLC for my laptop I can't hook up to my work network.

---

