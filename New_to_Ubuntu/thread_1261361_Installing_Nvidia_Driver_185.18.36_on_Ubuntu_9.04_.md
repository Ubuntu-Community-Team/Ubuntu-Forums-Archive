---
title: "Installing Nvidia Driver 185.18.36 on Ubuntu 9.04 64bit"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by cookie9001 on 2009-09-08
Please Help, I am brand New to Ubuntu and Linux. I am trying to install the following driver 

nvidia-linux-x86_64-185.18.36-pkg2.run

I have read lots of threads and tried the following 

CTL-ALT F1

sudo bash
sudo /etc/init.d/gdm stop (everything works to this point)

This is where it goes wrong.
sudo chmod -x nvidia-linux-x86_64-185.18.36-pkg2.run

I have also tried sudo chmod -x /home/paul/desktop/nvidia-linux-x86_64-185.18.36-pkg2.run

I have also tried

sudo sh nvidia-linux-x86_64-185.18.36-pkg2.run

and sudo sh /home/paul/desktop/nvidia-linux-x86_64-185.18.36-pkg2.run

oh and also the above but without typing sudo

none of which seem to work. 

I have also tried the launchpad method which someone posted but did not work.

The problem is I really have no idea of what I am doing, can any one give me idiot proof step by step instructions? Please!!!!

---

### Post by LowSky on 2009-09-08
note you need to change directories for the installer
```

cd /path/to/installer
```
most likely
```

cd /home/*username*/Desktop
``` (capital D or it will screw you up)

then run the commands
```
sudo chmod +x NVIDIA*

sudo sh NVIDIA*
``` and follow the prompts

to restart gnome
```
sudo /etc/init.d/gdm start
```

I used these instructions
[https://help.ubuntu.com/community/NvidiaManual#Complete%20Manual%20Install](https://help.ubuntu.com/community/NvidiaManual#Complete%20Manual%20Install)

---

### Post by cookie9001 on 2009-09-09
Thank you for the advice, I will try this when I get home tonight. 
 
Regards
 
Paul.

---

### Post by cookie9001 on 2009-09-09
Brilliant, this worked a treat, thank you for your help:KS:guitar:

---

### Post by Perfect Storm on 2009-09-09
> **cookie9001 said:**
> Brilliant, this worked a treat, thank you for your help:KS:guitar:

Remember everytime the kernel gets patch/upgraded you need to install the driver again. That's the downside of installing the driver manually.

---

