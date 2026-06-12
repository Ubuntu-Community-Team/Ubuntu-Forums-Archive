---
title: "Installing Wireless Driver on Kubuntu"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by go7Ul1ai on 2008-07-08
Hello,

I love Ubuntu but I've just today received my Kubuntu Disk through the post (Thanks to Ship-It). I had to get help from a friend to install the right Wireless Driver on Ubuntu for my laptop, I understand that this will be different on KDE.

I am using an Fujitsu-Siemens Amilo Li1818 laptop and I'm planning on installing Kubuntu tomorrow (I haven't tried KDE much). Here are the steps to get wireless working on Ubuntu if this is any help for anybody in trying to get the wireless working on Kubuntu for me:
[http://thevistaforums.com/lofiversion/index.php/t30675.html](http://thevistaforums.com/lofiversion/index.php/t30675.html)

(scroll 1/4 down the page).

Edit: I copied and pasted from his post:
k so run these commands in a terminal window: (one after another)

CODE
sudo apt-get install ndiswrapper-utils-1.9 ndiswrapper-common


CODE
mkdir ~/.drivers


CODE
cd ~/.drivers


CODE
wget [http://c0lin.org/leeswireless.zip](http://c0lin.org/leeswireless.zip)


CODE
unzip -a leeswireless.zip


CODE
cd WLAN


CODE
sudo ndiswrapper -i sis163u.inf


CODE
sudo ndiswrapper -l


CODE
sudo ndiswrapper -m


CODE
sudo modprobe ndiswrapper


CODE
sudo reboot


CODE
sudo gedit /etc/modules


then add this to the bottom of the file after the last line:
CODE
ndiswrapper


Save the file.

CODE
sudo reboot

Thanks in advance,

Lee Jarratt

---

### Post by go7Ul1ai on 2008-07-08
Okay, I installed Kubuntu and did the commands from my original post, I'm now stuck on the sudo gedit /etc/modules bit. This is obviously a part of GNOME, what is the equivalent for KDE so I can continue with my Wireless Driver install?

Many thanks in advance,

Lee Jarratt

---

### Post by go7Ul1ai on 2008-07-09
And I thought Ubuntu Forums were famous for the great support. Never mind, I will go somewhere else for help. I'm going to see what Fedora is like :D

---

### Post by go7Ul1ai on 2008-08-04
Just came back to check if any one actually responded back, guess not -_-

---

### Post by nittybitty on 2008-08-05
I am having the same problems. In gnome you don't have to use the command line at all.  KDE is proud of itself but it falls short on installing missing hardware drivers from what I have experienced.

I am sure there is a solution. I have 87 windows open in firefox right now that are all search results for this same problem in KDE.

I am no Ubuntu expert, but I am determined to solve this very obvious and common problem and after I have perused all 87 windows, I shall return here with a solution.

---

### Post by Ayuthia on 2008-08-05
> **lee.jarratt said:**
> Okay, I installed Kubuntu and did the commands from my original post, I'm now stuck on the sudo gedit /etc/modules bit. This is obviously a part of GNOME, what is the equivalent for KDE so I can continue with my Wireless Driver install?

Many thanks in advance,

Lee Jarratt

You have two options.  The first is to use kate:
```
kdesu kate /etc/modules
```
The other option is to not edit the file but just add the word to the file:
```
echo ndiswrapper|sudo tee -a /etc/modules
```

kdesu is the equivalent of gksu and kate or kwrite are editors in KDE.

---

