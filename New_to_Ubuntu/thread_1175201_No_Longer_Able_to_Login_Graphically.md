---
title: "No Longer Able to Login Graphically"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by ToxicNostalgia on 2009-05-31
**[SOLVED]**

For some reason, I can no longer login graphically on my computer, but I can perform a console login without a problem. Everything works just fine until I get to the login screen which prompts me for my username and password. I enter my credentials, and the screen goes temporarily black for a second then it returns me to the login screen. I really don't understand why this is occuring. I don't have the appropriate knowledge to even know where to search for the problem, and that is why I am here, to ask for help not only to diagnose but to fix whatever is causing this issue. As you can tell, I am not very experienced with Linux. I am running Kubuntu 9.04, and I think, KDE 4.2.2. Any help would be greatly appreciated.

---

### Post by WinterMadness on 2009-05-31
go into the terminal and type dpkg-reconfigure xserver-xorg

that should do it if my experience serves me correctly

---

### Post by ToxicNostalgia on 2009-05-31
I went through the reconfiguration process, and it didn't solve my problem. Any other ideas?

---

### Post by SunnyRabbiera on 2009-05-31
It might be kdm, I would try sudo apt-get install GDM with your console login, it should ask you if you want to use either KDM or GDM.
GDM is an alternate login manager, it has a GUI and I find it more reliable then KDM.
KDM is what Kubuntu uses by default but the KDE4 version of KDM isnt that great.

---

### Post by ToxicNostalgia on 2009-05-31
I tried it, but I failed because I wasn't connected to the Internet. How do connect to the Internet via console? Or would another route be easier?

---

### Post by ToxicNostalgia on 2009-06-01
This really sucks. Not being able to really use my computer is killing me, I was watching The Office season 3, and now, I am bored out of my mind. I know it's sad, but I'm sick, and there isn't much else to do. Consider this a bump. More help would be greatly appreciated.

---

### Post by SunnyRabbiera on 2009-06-01
Sounds like Kubuntu's going into safe mode, during boot up try to press the escape button when GRUB is loading and see if you can use another kernel.
Did you get an update of some kind?
Perhaps you had a kernel update that failed to detect your graphics card, happens all the time.
If you can write down what comes up at the bootloader.

---

### Post by WinterMadness on 2009-06-01
Im interested to see what happens when you log in and type startx into the terminal

tell us what it says

---

### Post by ToxicNostalgia on 2009-06-01
> **WinterMadness said:**
> Im interested to see what happens when you log in and type startx into the terminal

tell us what it says

Wow, it just started up. There seems to be absolutely no problem with starting X from the terminal. Now, I'm logged in as normal. Of course, I don't want to have to start X via terminal every time I boot. So, my question is why is the login screen failing?

---

### Post by cariboo on 2009-06-01
It sounds like there is a problem with kdm, it may help to re-install it.

---

### Post by ToxicNostalgia on 2009-06-01
I purged kdm, and then re-installed it, and everything is back to normal. Thank you all. Marking this as resolved.

---

