---
title: "Couple of New Install Questions"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by tcharmon on 2011-03-14
My system has a dual-boot setup with WinXP and UBUNTU 10.10...   I have a couple of questions that I really need some help with..

1.  Is there a way to turn off the password authentication window every time that I make some changes to my system?   It is getting quite annoying..   I am the only user to my system..

2.  I think there is a program call GRUB (not sure) that manages my dual-boot startup when I turn on my pc.  Is there a way that I can rearrange the order of systems/options in GRUB so my system will go automatically into winxp instead of Linux?   I would still like the option to go to Linux but not automatically..   I do a lot of on line gaming in WinXP..

Thanks in advance for your help..

---

### Post by dFlyer on 2011-03-14
The answer to both of your questions are yes. But I would like to know why you want to decrease your protection by doing away with passwords. By running as root/su your setting yourself up to get hacked. Remember linux is not windows. Linux has a lot of security unlike windows. By doing away with being a user and becoming root you have no more security than windows.

---

### Post by ~Plue on 2011-03-14
> **tcharmon said:**
> 
1.  Is there a way to turn off the password authentication window every time that I make some changes to my system?   It is getting quite annoying..   I am the only user to my system..
yes, you can read about it here >> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
what you're looking for is nearly at the bottom of that page, but it would be better to read the rest too so that you know what you are about to do

> **tcharmon said:**
> 
2.  I think there is a program call GRUB (not sure) that manages my dual-boot startup when I turn on my pc.  Is there a way that I can rearrange the order of systems/options in GRUB so my system will go automatically into winxp instead of Linux?   I would still like the option to go to Linux but not automatically..   I do a lot of on line gaming in WinXP..

manually:
run *gksu gedit /etc/default/grub *and change the value ***GRUB_DEFAULT=X ***to the the windows entry. after that, run *sudo update-grub*
(the first entry in the menu is number **0, **the second one as **1** and so on. i.e. if the windows entry is #3 it should be  GRUB_DEFAULT=**2**)

more on grub2
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)

edit/ using StartUp-Manager (easier):
install the package 'startupmanager' from the software center/synaptic/apt and use it to change the default OS selection
(it should be accessible through system > administration )

---

### Post by garvinrick4 on 2011-03-14
To see your menuentrys.
```
grep menuentry /boot/grub/grub.cfg
```

---

### Post by tcharmon on 2011-03-14
> **dFlyer said:**
> The answer to both of your questions are yes. But I would like to know why you want to decrease your protection by doing away with passwords. By running as root/su your setting yourself up to get hacked. Remember linux is not windows. Linux has a lot of security unlike windows. By doing away with being a user and becoming root you have no more security than windows.
 
Thanks for the reply..   Oh, I would like my Linux to be secure, it just seems sometimes that the number of times I have to enter my password is a little excessive..  Its like every 5-10 minutes..

---

### Post by Rubi1200 on 2011-03-15
> **tcharmon said:**
> Thanks for the reply..   Oh, I would like my Linux to be secure, it just seems sometimes that the number of times I have to enter my password is a little excessive..  Its like every 5-10 minutes..
What exactly are you doing that requires authentication "every 5-10 minutes"?

---

### Post by oldos2er on 2011-03-15
> **tcharmon said:**
> Thanks for the reply..   Oh, I would like my Linux to be secure, it just seems sometimes that the number of times I have to enter my password is a little excessive..  Its like every 5-10 minutes..

**sudo -i** will give you a root terminal for as long as you need it.

---

