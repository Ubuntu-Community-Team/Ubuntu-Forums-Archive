---
title: "Mayday mayday!"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Kosimo on 2009-03-06
Hello guys, I need help!
I am installing ubuntu (intrepid) on my GF's laptop and everything went ok, but after installing it and make all the updates, now it reboots with a blank screen, (I can hear the ubuntu login, and if I type the username and password i can hear the login music)
I would like to install the restricted drivers thru the terminal>

So, anybody knows the package I need to install in order to do by terminal what I can do by hitting the "restricted drivers available"?

sudo apt-get install xxxxxx

ps> Using an ATI videocard

---

### Post by kanikilu on 2009-03-06
I'm pretty sure people will need to know what type of video adapter that laptop uses before they can suggest the proper package to install. ATI? Nvidia? Intel? ...

// Edit - Just noticed you modified your post. The last ATI card I used with linux was back with Red Hat 6 about 10 years ago, so I'll let someone a little more up-to-date field this one ;) You might have a look here, though: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by linuxisevolution on 2009-03-06
Kosimo, when the laptop turns on, *quickly* hit escape and select the third option down from the top. Your problem is that you've changed your kernel without changing the video drivers.

---

### Post by Kosimo on 2009-03-06
Thanks for the answer!
As I've said in the first post it is an ATI> Model HD2300 Mobile, 
which should be supported for the latest available drivers

---

### Post by Kosimo on 2009-03-06
> **linuxisevolution said:**
> Kosimo, when the laptop turns on, *quickly* hit escape and select the third option down from the top. Your problem is that you've changed your kernel without changing the video drivers.

Nope, I didn't install anything before the update. So was a really fresh installation! I've tried by booting using the "old" kernel, but it doesn't works, not even in recovery mode.

I am pretty sure that installing the latest restricted drivers will solve my problem

---

### Post by linuxisevolution on 2009-03-06
> **Kosimo said:**
> Nope, I didn't install anything before the update. So was a really fresh installation! I've tried by booting using the "old" kernel, but it doesn't works, not even in recovery mode.

I am pretty sure that installing the latest restricted drivers will solve my problem

Can you boot into "safe" mode to install the correct drivers? Start out by using sudo apt-get install fglrx . And see if that works..


EDIT: after the laptop boots to the nonexistant login screen, can you hit ctrl+alt+F1 and login? If so, after logging in, type startx and record the errors. hit ctrl+alt+backspace to end startx and see the errors.

---

### Post by bodhi.zazen on 2009-03-06
Not that your problem is funny, and I usually ask people to use descriptive titles such as "Help ATI" , your title made me LOL.

Install the ATI drivers or use the vesa driver ;)

---

### Post by Kosimo on 2009-03-06
> **bodhi.zazen said:**
> Not that your problem is funny, and I usually ask people to use descriptive titles such as "Help ATI" , your title made me LOL.

Install the ATI drivers or use the vesa driver ;)

I'll try to be more descriptive next time :P

So, I want to install a .deb with latest catalyst. Any idea about how to do that having only a working terminal?

---

### Post by Therion on 2009-03-06
This should do the trick:```
sudo apt-get install xserver-xorg-video-ati

```

Then maybe update with the Restricted Driver Manager, or install from source, or what have you, once you've got a GUI.

---

