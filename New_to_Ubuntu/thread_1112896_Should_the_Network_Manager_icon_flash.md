---
title: "Should the Network Manager icon flash?"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by stig on 2009-04-01
On my two wire-networked Ubuntu PCs the Network Manager icons at the bottom of my screen behave differently, although I had never noticed this until now. One flashes, the other doesn't flash.

The PC with the non-flashing icon is working OK but the PC with a flashing icon has developed a network fault. Is the flashing an indication of the fault? The fault is that the PC cannot connect to the network or Internet after boot. After doing sudo /etc/init.d/networking restart it connects to the Internet but not the network. The icon flashes both before and after the restart.

I posted about the fault [here]("http://ubuntuforums.org/showthread.php?p=6987405") 24 hours ago but have not received any replies yet.

---

### Post by skymera on 2009-04-01
nm-applet sits in the top right corner of the screen, you can manage the network. It doesn't flash.

You can however, get a network app for the task bar via "Right click > Add to Panel". That doesn't flash.

I find configuring the connections manually is best
"System > Administration > Network"

You may need to install a package, network-admin? 
Sorry I'm at college on XP

---

### Post by stig on 2009-04-01
This is nm-applet 0.6.6 on the task bar, described as the Gnome Network Manager. I didn't install it separately, it came as default with Ubuntu. The flashing is not very obvious - the icon is an image two superimposed black screens and the flashing is a small area at the bottom of the image.

My network has been running fine for a couple of years. I don't understand what has suddenly changed.

---

### Post by clive littlewood on 2009-04-01
Hi

On my network icon the front "monitor" flashes when i have activity (change page etc.) and the rear "monitor" flashes at all times i am on the net.

Hope this helps.      :p

Clive

---

### Post by stig on 2009-04-01
Thanks, Clive. This gets stranger all the time! The icon never flashes on one of my PCs and is flashing all the time on the other!

---

### Post by stig on 2009-04-01
And I should add...this thread is not an April Fool's Day joke, honestly!

---

### Post by philinux on 2009-04-01
Network manager applet never flashes.

Network monitor, from add to panel, does flash when there is activity.

---

### Post by mcduck on 2009-04-01
I've seen all notification area icons flashing when using some animated wallpapers and such, but that's just a glitch in updating the display and doesn't have any effect in how things are actually working.

But since you mentioned that the whole icon doesn't flash but instead there's something flashing at the bottom of the image, I started thinking that perhaps this is because the connection is being enabled/disabled continuously (for some reason or other). If you disable network connections, or remove the cable (when using wired connection) you'll see a small icon appear at the bottom right corner of Network manager's icon..

You said that you are using wired connection, I'd check that the cable is OK and connected properly. Perhaps try with another cable.

---

### Post by stig on 2009-04-02
Thanks for the comments.
philinux, it's not the network monitor (on which the little screen flashes with network activity), but the network manager.

mcduck, the flashing is a spot at the base of the monitor on the image, Neither of my PCs has any fancy wallpaper, just a simple JPEG photo. the comment about it possibly being due to continuous enabling/disabling is interesting.

I hear what you say about the cabling. I checked it visually but I will see if I've got a spare cable to test as a bypass.

Thanks for the ideas! I've had no replies at all to my other post shown in the link above. :(

---

### Post by stig on 2009-04-02
Using a different network cable makes no difference. The icon still flashes. But that's not necessarily important, just a curiosity. The important thing is that I still can't get that PC to auto start the network at boot even though this one does auto start and they are on the same router and I've now changed network cards and cables.

---

