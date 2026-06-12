---
title: "ububtu 8.04 Network Interfaces Setup"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by Slider1611 on 2008-05-20
Hi all Iv`e been trying to set up my home server and i have tryed manny different version of UBUNTU... I am now on to UBUNTU 8.04 LTS SERVER EDITION, if any 1 can assist me in any way i would greatly appriciate it as i am now getting really **** off.
As for installing the progrom i have no problems it is when i come to trying to set up the server to host a web page i am stuck.
Now believe it or not i am not a beginner on computer i have been building and repairing for over 15years but as for a server this is anew addition to me and i am now really stuck, i have followed manny examples on the net IN DETAIL BUT every time i come to using the command "sudo /etc/init.d/networking restart" all i get is
 
 *reconfiguring network interfaces....
/etc/network/interfaces:10: unknown addres type
ifdown: couldn`t read interfaces file "/etc/network/interfaces"
/etc/network/interfaces:10: unknown address type
ifup: couldn`t read interfaces file "/etc/network/interfaces"
Saying FAIL IN BOLD RED LETTERS AT THE SIDE

If any one can help me i would greatly appriciate it as i am now getting rather mad plz 
Contact me at 
(MSN) [email]tweeksandperks@hotmail.co.uk[/email]
EMAIL [email]adam@tweaksandperks.com[/email]

Regards:
Adam

---

### Post by chili555 on 2008-05-20
If this is a server, may we assume it needs a static IP address? Please open a terminal and do:```
cat /etc/network/interfaces
```and let's see what is wrong on line 10.

---

