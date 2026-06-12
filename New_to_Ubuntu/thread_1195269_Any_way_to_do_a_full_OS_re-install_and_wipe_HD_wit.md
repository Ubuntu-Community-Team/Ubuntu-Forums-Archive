---
title: "Any way to do a full OS re-install and wipe HD without disc?"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by Narcoleptic_Insomniac on 2009-06-23
So I've been having difficulties with the computer for a while now. I think I'm on Xubuntu 8.10, it should be the newer version Jaunty because I ran ```
sudo apt-get upgrade
``` not to long ago and when I restarted I didn't notice any difference. Anyway, it seems every time I want to install a program I run into a problem here, and then when I try to fix it I can't fix it because some other thing is broken and then I have to fix that, and run into the same thing as before. So I have concluded that my computer can't be saved and needs to be completely wiped clean of everything and totally re-installed. Is there any way to do this from terminal, I don't have access to any CDs to burn a new copy. If I can't, what is really the best thing I can do that doesn't involve spending money, and can be done immediately from this computer? Thank you in advance.

EDIT: The issue cannot be resolved, thanks for trying.

---

### Post by estyles on 2009-06-23
When you say you don't have a disk, does that mean you don't have a USB drive either?

Do you have an open partition on your hard-drive?  I've never tried, but I would think it might be possible to extract the image to another partition and install from that partition?

However, if you don't have a partition that isn't in use, I'm not sure you could even create one - you can't resize an active partition, which is why people generally suggest booting from a LiveCD if you need to resize the root partition...

---

### Post by Therion on 2009-06-23
Well before you do a full blown reformat and reinstall have you tried using the "Fix Broken Packages" option in Synaptic?

Beyond that, the command I think you're looking for is ```
apt-get -u dist-upgrade
```

---

### Post by JordyD on 2009-06-23
```
sudo apt-get uograde
```

does not upgrade to a newer version, it upgrades your packages, but only for your current version.

If you want to upgrade to Jaunty use
```
sudo update-manager -d &
```

The '&' is there so that you can close your terminal without killing the upgrade. It will open the update manager.

---

### Post by Narcoleptic_Insomniac on 2009-06-23
> **Therion said:**
> Well before you do a full blown reformat and reinstall have you tried using the "Fix Broken Packages" option in Synaptic?

Beyond that, the command I think you're looking for is ```
sudo apt-get dist-upgrade
```

I don't even have synaptic. I've lost the use of my left click, everything just disappeared from my desktop and I can't even delete programs with "sudo apt-get remove". There is no saving this computer lol. I have no access to any other computers, and I don't have USB drives. Yes, I am aware that I'm in a pickle. While I doubt it, it really seems like I have a virus, but how I could get a virus on Linux god only knows.

---

### Post by Narcoleptic_Insomniac on 2009-06-23
Ok well I'll have to end this thread here because a friend of mine whos rather computer savvy said he'd help me out tonight, hook me up with some new hardware, etc. I really appreciate your help.

---

### Post by JordyD on 2009-06-23
> **Narcoleptic_Insomniac said:**
> I don't even have synaptic. I've lost the use of my left click, everything just disappeared from my desktop and I can't even delete programs with "sudo apt-get remove". There is no saving this computer lol. I have no access to any other computers, and I don't have USB drives. Yes, I am aware that I'm in a pickle. While I doubt it, it really seems like I have a virus, but how I could get a virus on Linux god only knows.

Can't you just order a CD from Canonical? They're free of charge, plus no shipping costs.

---

### Post by Therion on 2009-06-23
Can you use Ctrl+Alt F2 to get to a TTY? 

From there you could try sudo apt-get -u dist-upgrade and hope for the best.  

I've never attempted this myself, mind you, but what the heck, right, you're dead in the water as it is...

---

### Post by irv on 2009-06-23
Do you know or have a friend or someone who has an Ubuntu CD that you could use to start from scratch? It could even be an older version. and then you could do an update and then a upgrade, until you get to the latest version (9.04).

---

### Post by wojox on 2009-06-23
Okay

type **sudo apt-get update**

then hit Enter

then type **sudo apt-get dist-upgrade**

This should solve your problem.

---

