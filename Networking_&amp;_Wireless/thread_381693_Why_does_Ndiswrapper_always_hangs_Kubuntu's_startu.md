---
title: "Why does Ndiswrapper always hangs Kubuntu's startup but not Ubuntu's?"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by Gustavo Narea on 2007-03-11
Hello, everybody.

I have installed several versions of Kubuntu and Ubuntu on a Dell Inspiron 6400 and a Dell Inspiron 1501, which require Ndiswrapper to use Wifi.

Ndiswrapper works like a charm on Ubuntu, but always hangs Kubuntu's startup at "Configuring Network Interfaces" for about 4 minutes.

What's wrong with Kubuntu? How can I work around this?

Cheers!

---

### Post by Condoulo on 2007-03-11
Well if you really are fond with the Kubuntu desktop and software, I suggest getting it to work in Ubuntu, and installing the Kbuntu Desktop Environment afterwards. But thats my opinion.

---

### Post by Gustavo Narea on 2007-04-11
I'm willing to spend time to solve this, but I just don't know how. Is there someone willing to help me spot the problem?

---

### Post by paullew on 2007-04-11
Have a look in /etc/network/interfaces in both of them. 

When booting up, the system tries to initialise all the specified interfaces in that file. That's where the long pause happens.

The ubuntu box probably has a clean interfaces file (because gnome network manager doesn't need it - it auto configures), and hence doesn't need to wait. 

I'm guessing that kubuntu doesn't have network auto detection (I've never used kubuntu), and still relies on the interfaces file entries - hence the bootup pause while it tries to initialise the interfaces. The more interfaces in the file, the longer the startup pause.

---

### Post by Gustavo Narea on 2007-04-12
> **paullew said:**
> Have a look in /etc/network/interfaces in both of them. 

When booting up, the system tries to initialise all the specified interfaces in that file. That's where the long pause happens.

The ubuntu box probably has a clean interfaces file (because gnome network manager doesn't need it - it auto configures), and hence doesn't need to wait. 

I'm guessing that kubuntu doesn't have network auto detection (I've never used kubuntu), and still relies on the interfaces file entries - hence the bootup pause while it tries to initialise the interfaces. The more interfaces in the file, the longer the startup pause.

Thanks for your answer, paullew!

I've confirmed that the problem occurs when running */etc/init.d/networking*, exactly when this script runs **ifup -a** (this is the command that hangs my computer!).

I haven't had luck looking for the *interfaces* file in Ubuntu, as it's not installed on my computer at this moment. I've also gotten in touch with several owners of the same model of my laptop, but their chipset is not Broadcom (they have a Intel ProWireless 3945ABG)... I'm still looking for other owners and if I don't find one, I'll install Ubuntu again.

Cheers!

---

