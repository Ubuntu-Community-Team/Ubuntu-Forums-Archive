---
title: "Windows in Virtualbox"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-12-01
Can't get internet working. Wired and Wireless. Using a 1000he Asus EEE PC.

---

### Post by ukripper on 2009-12-01
Which version of ubuntu you are using?

---

### Post by LunaticHiatus on 2009-12-01
karmic

---

### Post by ukripper on 2009-12-01
well as you said you are using virtualbox it is not ubuntu's settings for networking you should be looking into, in otherwords problem is not ubuntu it is virtualbox. Shutdown your GUEST OS(ubuntu 9.10). Click into settings of your newly Ubuntu 9.10 Guest machine. make sure networking is enabled via NAT and PCnet-FAST III is selected.

---

### Post by LunaticHiatus on 2009-12-01
Indeed, the problem is not with Ubuntu. My wireless in ubuntu works fine and both of those are selected. I can pick up wireless on other operating systems using virtual box. This problem is unique to this version of xp. Could it be a driver issue? I'm not sure how virtualbox handles drivers.

---

### Post by eriktheblu on 2009-12-01
Are you using the open version of Virtualbox, or the full version?

Have you installed the guest additions?

---

### Post by ukripper on 2009-12-01
> **LunaticHiatus said:**
> Indeed, the problem is not with Ubuntu. My wireless in ubuntu works fine and both of those are selected. I can pick up wireless on other operating systems using virtual box. This problem is unique to this version of xp. Could it be a driver issue? I'm not sure how virtualbox handles drivers.
Internet is via NAT by default in virtualbox, so it doesn't matter if network drivers are detected in XP or not. Your host OS(ubuntu in this case) is providing NAT to your XP which shouldn't be a problem.

You have to make sure in settings on virtualbox you have selected PCnet-FAST III otherwise XP won't talk to your ethernet card properly.

---

### Post by underquark on 2009-12-01
Virtualbox isn't using a driver to access your wireless device.  You have a virtual machine networked to your real machine.  Shut down the virtual machine and go into the Settings menu in Virtualbox.  Click on "Network" and check the following:

"Enable Network Adapter" box is checked
Adapter Type set to PC-Net Fast III
Attached to NAT
"Cable Connected" is checked

---

### Post by LunaticHiatus on 2009-12-01
installed guest additions. My bad, works fine now.

---

### Post by baniasad on 2009-12-01
> **eriktheblu said:**
> Are you using the open version of Virtualbox, or the full version?

Have you installed the guest additions?

in my country i cant download these links(i don't know maybe filtered) 
[B]Forbidden 
Your client is not allowed to access the requested object.  [/B]
 
can anyone upload these links in  file hosting websites such as rapidshare.com etc.. 
[http://download.virtualbox.org/virtualbox/3.1.0/virtualbox-3.1_3.1.0-55467_Ubuntu_karmic_i386.deb](http://download.virtualbox.org/virtualbox/3.1.0/virtualbox-3.1_3.1.0-55467_Ubuntu_karmic_i386.deb) 
[http://download.virtualbox.org/virtualbox/3.1.0/VirtualBox-3.1.0-55467-Win.exe](http://download.virtualbox.org/virtualbox/3.1.0/VirtualBox-3.1.0-55467-Win.exe)
thanks

---

