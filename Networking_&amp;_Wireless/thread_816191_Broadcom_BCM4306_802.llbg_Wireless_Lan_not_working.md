---
title: "Broadcom BCM4306 802.llb/g Wireless Lan not working.  Somebody HELLLLPPPPPP!!!!"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by arachal on 2008-06-02
Anyone out there to help me get my wireless to work?:mad:

---

### Post by untermensch on 2008-06-02
I have a bcm4318 wireless chip. I would recommend a.)getting rid of it. b.) installing new fwcutter. c.)updating your ndiswrapper. or d.) getting rid of it. 
I would try b, then c, then d. =p
[http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133](http://ubuntuforums.org/attachment.php?attachmentid=30328&d=1177147133) <-- is the link for the native bcm drivers. I found it to be no problem.

---

### Post by chrisby on 2008-06-02
open the terminal from applications-> accessories menu then

sudo apt-get install b43-fwcutter. 

follow prompts

---

### Post by arachal on 2008-06-02
I tried that.  Message says cannot find package b43-fwcutter.

---

### Post by untermensch on 2008-06-02
also: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)
or: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)

---

### Post by chrisby on 2008-06-02
b43-fwcutter should be straight out of the repositories.  Do you have all of the software repositories enabled?

System-> admin-> software sources

I have everything checked on ubuntu software page, and hardy partner/ partner source code checked on the second page.


You may also want to reload the software list from the repositories.

---

### Post by arachal on 2008-06-02
Thanks.  I will have to try this when I get home tonight.:KS

---

