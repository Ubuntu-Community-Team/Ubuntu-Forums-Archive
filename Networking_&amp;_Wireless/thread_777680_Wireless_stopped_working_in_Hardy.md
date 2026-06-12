---
title: "Wireless stopped working in Hardy"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by MongooseCage on 2008-05-01
I used Ubuntu 7.10 with no trouble, I was amazed by how my wireless,video, and audio seemed to work seamless at boot on my Lenovo Thinkpad R60:). When Ubuntu 8.04 released I quickly got it burnt on to my CD(didnt work) and DVD(worked). 

But the wireless wasn't working, I supposed that there must be some sort of proprietary driver and stuff(modules,blah,blah). So I installed it.

Here is the problem,:confused:

Its not yet working! It doesnt recognize any wireless hardware whatsoever, I have sudo-ed everything possible and tried to find my wireless driver on the synaptic package manager as well. The driver is ipw3945, standard basic Intel driver. But it doesnt just work. It cant scan,WEP,WPA, nothing!I have downloaded Ubuntu 8.04 twice burnt 2 cds and 2 dvds but I havent got it to work! My Computer Science teacher who has Ubuntu said that his worked 'right out of the box' and I even checked on the list of supported Wireless Drivers and its there and known to work right out of the box for Hardy. I have also tried ndiswrapper, it doesnt work and I don't even think I need it. I am starting to think that there must be a very **stupid** reason behind it. My wireless works in Windows XP so its not a hardware fault.

So I am starting to think:
Its not **Hardware fault**
Its not **the image or a burning error**
Its no **Proprietary or Restricted Driver**
It must be **ME and MY NOOBNESS**
Please! I really need to get this to work! Because I have to get connected with the encrypted wireless connection in my school.

---

### Post by MongooseCage on 2008-05-01
bump,anyone?

---

### Post by MongooseCage on 2008-05-02
Should I install 7.10 and then upgrade to 8.04?

Anyone? Please???

---

### Post by Ayuthia on 2008-05-02
If you already have 8.04 installed, you should not need to install 7.10 and upgrade to 8.04.  The developers for this driver made an update and changed a few things.  You might try installing linux-backport-modules-hardy-generic.  That might help you out.

---

### Post by MongooseCage on 2008-05-02
I cant find it

i tried 
```

sudo apt-get install linux-backport-modules-hardy-generic

```

Somewhat, noobish. But I cant find it.

---

### Post by Ayuthia on 2008-05-02
Actually, it was my fault and not yours.  Try linux-backports-modules-hardy-generic.  I forgot the s in backports.  I should do more cutting and pasting...

---

### Post by MongooseCage on 2008-05-03
> **Ayuthia said:**
> Actually, it was my fault and not yours.  Try linux-backports-modules-hardy-generic.  I forgot the s in backports.  I should do more cutting and pasting...

Nope, no cigar, no chocolate, lol, my computer has already begun screaming wireless in all of its files

---

### Post by gabz8472 on 2008-05-19
Thanks Ayuthia! Both my wireless and audio were out of commission when i did a fresh install of Hardy on my Lenovo Y410. The wireless came right back with that solution. Of course, i also missed the "s" the first time around.

---

