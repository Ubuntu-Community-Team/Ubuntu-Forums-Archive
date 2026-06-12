---
title: "SSH to Ubuntu VM"
date: 2014-02-18
forum: Networking &amp; Wireless
---

### Post by cjnkns on 2014-02-18
Hi all:

I am having a bit of trouble figuring out why I am unable to SSH from my Windows host to my Ubuntu virtual machine. 
On the host I am able to successfully SSH into another server on the network. In my Ubuntu virtual machine I can access the web and ping google.com.
But, when I try to ssh form the Windows host to the VM I get "access denied". On the Ubuntu vm I can also SSH to localhost, but just not to the outside world.

I should also mention I am using a "bridged adapter" in the VM settings for Ubuntu. This seemed to be the easiest way to go as it gave out an ip address to the Ubuntu machine I could use to ssh.

Any help would be greatly appreciated.


edit:adding details
   Host: Windows 7
 Guest: Ubuntu 12.04

---

### Post by SeijiSensei on 2014-02-18
Can you ping the VM from outside?

Do you have any sort of firewalling rules on either the guest or the host?

---

### Post by cjnkns on 2014-02-18
Thank you for responding.

I am able to ping the vm using the ip address, but not the host name. Windows (host machine) firewall is turned off; the ufw status on Ubuntu (vm) is showing inactive.

---

### Post by cjnkns on 2014-02-18
Thank you for responding.

I am able to ping the vm using the ip address, but not the host name. Windows (host machine) firewall is turned off; the ufw status on Ubuntu (vm) is showing inactive.

---

### Post by SeijiSensei on 2014-02-18
So what happens if you use ssh with the IP address as the target?  Sounds like the problem is one of name resolution, not connectivity.

---

### Post by cjnkns on 2014-02-18
Well, I have to admit I completely dropped the ball on this one. I guess, when logging in via ssh it helps to use the correct user name.  ugh.
It was just user error. My user name for my work machine is one that I guess I was used to. So, when trying to ssh into Ubuntu I was using that instead of the one created by Ubuntu. 

Thanks for taking time to try and help though. I appreciate it.

---

