---
title: "how to remove xubuntu on ubuntu (dualboot)"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by cbbnewbie on 2010-05-07
hi to all i use ubuntu 10.04 and its not that fast on my laptop only 800mhz and 256mb memory 16mb videocard nvidia geforce2 go and 20 gig of hdd. I want to try xubuntu so what i did is to install it using the installation cd upon boot and when asked where to place it i checked install them side by side,, now im already enjoying ubuntu because on xubuntu i cant get my internet connection to work. What I want to do is to uninstall the xubuntu desktop, known linux for only a week so im a noob please help thanks..

---

### Post by narendraD on 2010-05-07
If you had Ubuntu and then installed Xubuntu along side, then it can be simple. Just go to System-->Admin --->Disk utility and format the Xubuntu partition. Then on a terminal run sudo update-grub to update presence of only one OS.

Offcourse backup any data on Xubuntu partition first.

---

### Post by ubunterooster on 2010-05-07
Edit:narendra beat me to say it

---

### Post by cbbnewbie on 2010-05-08
how do i know which one is xubuntu?

---

### Post by ubunterooster on 2010-05-08
go to places. Is there a dev/sda2?

A dev/sda(number) in "computer" will be the Xfce partition as it will show currently booted partition as  "filesystem"

---

### Post by cbbnewbie on 2010-05-09
done formating it and updating the grub, but during boot the grub menu still shows up, isn't it that if there is just one os that menu wont show up unless you press shift? how do i remove that??

---

### Post by ubunterooster on 2010-05-10
sudo update-grub

---

### Post by cbbnewbie on 2010-05-10
removed it thanks ubunturooster, learned a new thing thank you very much.

---

### Post by Sealbhach on 2010-05-10
Dude, 256MB RAM seems too little to run a full Ubuntu Desktop.

Why not try out LXDE as your desktop enviroment? You don't need to reinstall or anything.

Just do 

sudo apt-get install lxde

Then log out, select session LXDE and log in. To get back to Gnome, just log out and select session Gnome.

Give it a try, LXDE will probably me much faster for you.

.

---

### Post by ubunterooster on 2010-05-10
You are welcome, cbbnewbie. You could try getting lubuntu-desktop or lxde via synaptic if you want less RAM to be used

---

### Post by cbbnewbie on 2010-05-10
actually i removed ubuntu and installed xubuntu, i dont really know lxde but im in xubuntu now, the first is kubuntu then i tried ubuntu and now im in xubuntu its running qquite good now, is lxde lower? I'll research on it thanks eveyone,, I ove this forum!

---

### Post by ubunterooster on 2010-05-10
A regular lxde is lower but ... :( .... no menu on desktop right-click

I have 8 different desktop enviroments all on one partition.

---

### Post by narendraD on 2010-05-10
> **ubunterooster said:**
> A regular lxde is lower but ... :( .... no menu on desktop right-click

I have 8 different desktop enviroments all on one partition.


Wow, curious what they are. 

I had installed LXDE along with Gnome default and i liked it for the lower RAM needed.

---

### Post by ubunterooster on 2010-05-10
> **narendraD said:**
> Wow, curious what they are. 

I had installed LXDE along with Gnome default and i liked it for the lower RAM needed.
gnome [both the full and minimal], kde[and minimal], xfce[and minimal], lxde, openbox, blackbox, matchbox,

---

### Post by narendraD on 2010-05-10
What is the difference between full and minimal?

---

### Post by ubunterooster on 2010-05-10
Full has all features but minimal is lightweight and faster. Oh and gnome minimal has window buttons on the right by default, mostly little stuff that adds up.

---

