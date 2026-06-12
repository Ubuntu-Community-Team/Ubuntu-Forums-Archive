---
title: "Acer Wireless"
date: 2007-11-07
forum: Networking &amp; Wireless
---

### Post by rcdeacon on 2007-11-07
I would like to install Gutsy on a Acer 5002 laptop that has a broadcom 4318 air force 1 wireless adapter. I have already tried once unsuccessfully. Is there anyone with a similar configuration that has got it to work and how did you do it. I am not new to linux but I am new to Gnome and Ubuntu so please be gentle.

---

### Post by jonathanmotes on 2007-11-07
Well, my laptop is an HP, but I have a similar wireless card. I used the instructions from here: [http://ubuntuforums.org/showthread.php?t=346083]("http://ubuntuforums.org/showthread.php?t=346083") to get mine to work. The only thing I did differently was to get my driver from HP rather than use the provided download. I don't know if Acer provides drivers, but if they do it would probably be a better option.

Also, make sure to use the version of ndiswrapper that is on sourceforge. I tried using the version in the repositories on my first try, but it didn't work. You will also have to change the version numbers from 1.37 to the current - 1.48 - I think. You could just hit tab to autocomplete after typing a few letters so that you won't have to make any changes, and I don't think that Gutsy includes the build-essential package and linux-headers listed, so install them using Synaptic.

Hope this helps!

---

### Post by rcdeacon on 2007-11-07
thank you for the help.

---

### Post by jonathanmotes on 2007-11-07
No problem. To follow up my last post, here's something that was confusing to me in the tutorial to me that you might already know about: the "linux-headers uname -r." Just typing this in Synaptic will not return you anything. 

I found out that "uname -r" returns your kernel version when you type it in terminal. So, to figure out which linux header package to install, just compare the terminal output with the "linux-headers" listed in Synaptic. 

In my case, I have the "2.6.22-14-generic" kernel, so I installed the "linux-headers-2.6.22-14-generic" package.

---

