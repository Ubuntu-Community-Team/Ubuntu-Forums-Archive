---
title: "Ubuntu 10.04 Ethernet connection issue"
date: 2016-04-06
forum: Networking &amp; Wireless
---

### Post by walter20 on 2016-04-06
Good afternoon all, 
First let me start off by saying I am very new to Ubuntu and normally would not use it, however one of my projects has a requirement of Ubuntu 10.04. I understand that this is an old version, but it is the only version that supports LinuxCNC. That being said, I need to update some stuff on my computer and need the internet, and here is the problem. I have tried many different ways of connecting to the Ethernet, but all of them have failed. I have a DELL Optiplex 790 if that helps with anything. I recently read somewhere that it may be a driver missing for my NIC, but 1.) I have no idea how to acquire such drivers 2.) what my NIC is to see if it supported and lastly, if there is any other way of connecting to internet that might be supported like USB that would work. Thanks so much for any help! and I apologies if I sound ridiculous as it is my first experience with Ubuntu.

~Wally

---

### Post by Bucky Ball on 2016-04-06
Hi and welcome. You can install it on 12.04 LTS by [following the instructions here]("http://linuxcnc.org/docs/2.7/html/getting-started/getting-linuxcnc.html#_installing_on_ubuntu_precise"). 12.04 LTS is supported until 2017 which gives you a bit of time to work out an alternative.

10.04 LTS, as you mention. is no longer supported. Suggested you install a supported release. Your aim is to get online but getting online with an unsupported release is not a great idea. 10.04 LTS hasn't had security updates in quite some time.

---

### Post by walter20 on 2016-04-06
I would be more than willing to install an updated release, however LinuxCNC is only supported by 10.04 and nothing else unfortunately.

---

### Post by Bucky Ball on 2016-04-06
I provided a link for how to install it in 12.04 LTS in my last post. Click it.

---

### Post by light_yagami2 on 2016-04-06
> **walter20 said:**
> Good afternoon all, 
First let me start off by saying I am very new to Ubuntu and normally would not use it, however one of my projects has a requirement of Ubuntu 10.04. I understand that this is an old version, but it is the only version that supports LinuxCNC. That being said, I need to update some stuff on my computer and need the internet, and here is the problem. I have tried many different ways of connecting to the Ethernet, but all of them have failed. I have a DELL Optiplex 790 if that helps with anything. I recently read somewhere that it may be a driver missing for my NIC, but 1.) I have no idea how to acquire such drivers 2.) what my NIC is to see if it supported and lastly, if there is any other way of connecting to internet that might be supported like USB that would work. Thanks so much for any help! and I apologies if I sound ridiculous as it is my first experience with Ubuntu.

~Wally
  I know you don't want to upgrade because your program,  but you're allowing hackers to easily exploit your system because you're running a no longer updated version of Ubuntu.  as others have said,  you can upgrade Ubuntu 12.04 which should  be supported for another year.oor you can go to a different flavor of Ubuntu. also have you tried running that program in a newer version of Ubuntu?

---

### Post by Bucky Ball on 2016-04-06
> **light_yagami2 said:**
> ... have you tried running that program in a newer version of Ubuntu?

With some research you will find that the only option appears to be 12.04 and I have posted a link for that. ;)

---

### Post by QIII on 2016-04-06
Is this a personal project or one for your employer?  If for your employer, are they well aware of the danger?

If for you, is there an alternative CNC application that will work?  So many industrial CNC applications have been ported to embedded Linux devices that I would be surprised if there weren't something more current.

Must you use Ubuntu?  Is there something more modern for a different distribution?

---

### Post by Bucky Ball on 2016-04-06
> **QIII said:**
> Is this a personal project or one for your employer?  If for your employer, are they well aware of the danger?

If for you, is there an alternative CNC application that will work?  So many industrial CNC applications have been ported to embedded Linux devices that I would be surprised if there weren't something more current.

Must you use Ubuntu?  Is there something more modern for a different distribution?

+1. All good points to ponder.

---

