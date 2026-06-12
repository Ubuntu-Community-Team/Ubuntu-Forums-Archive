---
title: "belkin wireless PCI Card problems"
date: 2005-09-23
forum: Networking &amp; Wireless
---

### Post by dreyvin on 2005-09-23
OK I found the driver .inf file and copied it to my Ubuntu OS. I installed the ndiswrapper utilities and I then used ndiswrapper as I have read but when I put in the command...
sudo ndiswrapper -i /home/randy/bcmwl5a.inf 
I get an error message stating invalid driver. Now what? I'm pretty new to this so all the help is greatley appreciated

---

### Post by davidknibb on 2005-09-24
You say that you found the driver .inf file.  The usual advice is NOT to use the one on the Driver on he Windows disk - but to find out exactly the one needed and then download it

Have you follwed the instructions exactly in


[Http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Install](Http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu#Install)

But before you start print out all of the instructions, and those in the included link referring to Install Windows Driver & Configure Inerface.

David

---

