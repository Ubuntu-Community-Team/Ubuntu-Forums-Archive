---
title: "Newbie....problems.....can't install build-essentials :-("
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by Newbie29 on 2007-02-22
Hi,
On my friend's encouragemant I installed Xubuntu on my Dad's old Laptop (a Hewlett Packard Omnibook XE2) about 3 days ago. Now, the problem is that I am trying to get mt Wireless network card (a D-Link DWL-g630 version E1) to work on it so as to connect to the internet from it. I've gone through enough sites and tutorials to realise that this is a well covered topic, however the problem is that when trying to install the ndiswrapper I have a problem, my Xubuntu doesn't recognize the "make" command and whenever I try it, this is what it shows:

bash: make: command not found

I have been trying to fix it or get around this problem, but I have not been able to get anything, and i don't want to give up hope because I've begun to like using linux more than windows......:lolflag: 

Anyways, today I came across the tutorial on this site ( [http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588) ), and over here it said that if you have a problem with the "make" command then to put in the cd and install the kernel headers and build-essentials. Well, I did that and I managed to install the headers, but when i try to install the build essentials using the package installer, across the top of the installer comes written (in red) :

Error: Dependency is not satisfiable: libc6-dev|libc-dev

Someone, please help me, but please bear in mind that I am still a noob to linux, and so if you coud please explain to me in layman's terms (i.e. in simple language),

Thx

---

### Post by renzokuken on 2007-02-22
you need to enable the universe and multiverse repos. see [http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://www.monkeyblog.org/ubuntu/installing/#enabling_extra_repositories) for a quick howto.

then from the command line run 

```
sudo apt-get update
sudo apt-get install build-essential
```

then try ndiswrapper again

---

### Post by mconway0003 on 2007-02-22
I'm not really familiar with the make command, but have you tried using 'man make' in the terminal or googleing the 'make' command?

---

### Post by chili555 on 2007-02-22
The error message just means you also need to install packages called libc6-dev and libc-dev. They may be on your CD, or you could go here: [http://packages.ubuntu.com/edgy/libdevel/libc6-dev](http://packages.ubuntu.com/edgy/libdevel/libc6-dev) and download the .deb file and install it with sudo dpkg -i lib6c-dev.xxxx.deb. I believe libc6-dev provides libc-dev.

I realize you are doing this to *get* internet capability, and you may have to get this on another computer and move it with a USB key.

Good luck and post back if we can help.

---

