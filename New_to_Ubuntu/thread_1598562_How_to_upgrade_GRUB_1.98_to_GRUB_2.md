---
title: "How to upgrade GRUB 1.98 to GRUB 2"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by Jetso on 2010-10-16
I keep on seeing mentions of GRUB 2, but my version of GRUB is 1.98. How do I upgrade it, is there a command to run in terminal? Also, is there a way to change the names of the different OS's? And I saw where you could actually change the background color of GRUB, to a different color than black. How do you do *that*

---

### Post by Hippytaff on 2010-10-16
What version of ubuntu are you using...if you upgraded to 10.10 or are on 10.04 you've got grub2...don't know the answer to the rest of your questions though :-)

---

### Post by coffeecat on 2010-10-16
Grub 1.98 **is** grub 2. Grub 1 (legacy grub) never got beyond about 0.97.

Changing menu entries, pretty background pictures, all here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Hippytaff on 2010-10-16
> **coffeecat said:**
> Grub 1.98 **is** grub 2. Grub 1 (legacy grub) never got beyond about 0.97.

Changing menu entries, pretty background pictures, all here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Maybe I had too much wine toinght but I love you :-D

---

### Post by Jetso on 2010-10-16
OH! Haha, I thought it would say GRUB 2, not 1.98... Well thanks, haha.

---

### Post by MetroPietro on 2011-01-12
Hi, I am trying to upgrade from GRUB 0.97 to GRUB2. I have been using Ubu for 3 years, and at the upgrade to 9.10 I opted to keep GRUB because there was not much troubleshooting help on GRUB2 then. Now, lots of help and experience available online with GRUB2, and GRUB seems to be giving me trouble on Ubu 10.10.
When I Googled "Ubuntu 10.10 upgrade from GRUB 0.97 to GRUB2", this page came up first because of the keywords in it. However, it does not actually answer the question of how to upgrade from GRUB (0.97) to GRUB2 (1.98 and later). So I have come back to post this link to the Ubu page which gives instructions, caveats, and cautions about upgrading from GRUB to GRUB2.
It is [here]("https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202").

To check which version of GRUB you currently have installed, enter:
```
grub-install -v
```

---

### Post by drs305 on 2011-01-12
MetroPietro, I originally misunderstood the purpose of your post. Thanks for providing the link for others to reference. 

I've updated the community page to change "aptitude" to "apt-get" as the former is no longer installed by default.

---

