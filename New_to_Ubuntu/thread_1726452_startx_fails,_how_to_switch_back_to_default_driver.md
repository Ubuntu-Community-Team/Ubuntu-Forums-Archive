---
title: "startx fails, how to switch back to default driver"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by ubunovice on 2011-04-11
Hi
I installed 10.10 , and used it succesfully. After installing the NVIDIA-driver my  startx fails, I can only use runlevel 2 at this moment. Before solving the NVIDIA-problem I would like to switch back to the default video-driver in order to have a working desktop again.
Any help will be appreciated

---

### Post by mikewhatever on 2011-04-11
How did you install the driver, from the repositories or from nvidia.com?

---

### Post by ubunovice on 2011-04-11
I don't have a desktop at this moment to find that out , but I used the standard desktop/software_install environment; so it will be the repositories I think.

---

### Post by Hippytaff on 2011-04-11
you could try uninstalling the nvidia driver ```
 sudo apt-get --purge remove nvidia-*
``` and reboot. It will hopefully use the default low res efforts and then you can look into the Nvidia issue. Choose the recomended one from system -> administration -> additional drivers.

---

### Post by ubunovice on 2011-04-11
Hi Hippytaf

I just  did  sudo apt-get --purge remove nvidia-* and now I'm having a desktop running the lowres-driver again
I then went to system>administration>additionaldrivers and the system responded:
searching for additional drivers > no proprietary drivers are in use on this system 
Can you please be more specific about finding the proper nvidia driver, I have little or no experience
in this part of linux
Thanks

---

### Post by bab1 on 2011-04-11
> **ubunovice said:**
> Hi Hippytaf

I just  did  sudo apt-get --purge remove nvidia-* and now I'm having a desktop running the lowres-driver again
I then went to system>administration>additionaldrivers and the system responded:
searching for additional drivers > no proprietary drivers are in use on this system 
Can you please be more specific about finding the proper nvidia driver, I have little or no experience
in this part of linux
Thanks

The easiest way to install the latest nvidia drivers is to run the **sgfxi** script from [**_[COLOR="Blue"]here[/COLOR]_**]("http://smxi.org/site/install.htm#sgfxi").  I have used this on both real and virtual machines.  It works every time.  It is also reversible: meaning you can remove the proprietary drivers and revert back to the basic drivers if you wish.

---

### Post by Hippytaff on 2011-04-11
can you do```
sudo apt-get update
``` and then check to see if the drivers are offered to you in additional drivers?

---

### Post by ubunovice on 2011-04-12
hello Hippytaff

after  sudo apt-get update still no additional drivers available
thnx anyway

---

### Post by Hippytaff on 2011-04-12
Then [this]("http://www.psychocats.net/ubuntu/nvidia") might be worth a look

---

### Post by ubunovice on 2011-04-13
Hello Hippytaff and Bab1

I tried the sgfxi script but that ran into an error so stll no solution. After studying my Nvidia-installations I noticed that after installing Ubuntu 10.10 I had Nvidia level 173 ; short time ago ,during software-updates I had moved from 173 to 185 without noticing that on that moment. So I then reinstalled 173 and my Nvidia is working fine again. So my problem is solved (without really understanding it ). In the near future I am planning to study Nvidia-installations further but for the moment the problem is solved.
Thanks

---

### Post by Hippytaff on 2011-04-14
Your welcome. Glad you got it sorted.
 
Remember to mark the thread as solved in the thread tools at the top of the page.
 
:-D

---

### Post by halw on 2011-11-15
> **bab1 said:**
> The easiest way to install the latest nvidia drivers is to run the **sgfxi** script from [**_[COLOR="Blue"]here[/COLOR]_**]("http://smxi.org/site/install.htm#sgfxi").  I have used this on both real and virtual machines.  It works every time.  It is also reversible: meaning you can remove the proprietary drivers and revert back to the basic drivers if you wish.
How did you get it to run. When I tried in Kubuntu 11.10 I received a message that there was no such command. This is after I did Ctl+Alt+F1.

---

### Post by 3rdalbum on 2011-11-15
> **halw said:**
> How did you get it to run. When I tried in Kubuntu 11.10 I received a message that there was no such command. This is after I did Ctl+Alt+F1.

The script was in your home directory directly? If not, then move it or re-download it to there. Or navigate your terminal to the directory where it was downloaded.

Not sure you really need this script in Ubuntu these days, as Jockey does a good job. But knock yourself out if you like.

Also, just to note that the 'startx' command no longer exists on Ubuntu as far as I'm aware. Instead you use 'sudo service (display manager) start'. On Ubuntu 11.10 it's 'sudo service lightdm start'. On Kubuntu it's 'sudo service kdm start'. On earlier Ubuntus it's "sudo service gdm start".

---

### Post by halw on 2011-11-15
My issue is that after installing proprietary nvidia driver my screen was black after kde loaded.

FYI, this on a laptop with an nvidia geforce fx go5200 video card.

---

