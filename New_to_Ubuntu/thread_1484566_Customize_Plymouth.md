---
title: "Customize Plymouth"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by k33bz on 2010-05-15
Ok, I know there are a few choices I have when it comes to customize the plymouth boot screen. But are there other themes available then besides the few that are available in the synaptic manager?

Also is there a way I can make my own plymouth boot loader theme?

---

### Post by warfacegod on 2010-05-15
Lots of them here: [http://gnome-look.org/]("http://gnome-look.org/")

This may be highly useful as well: [http://ubuntuforums.org/showthread.php?t=1358026]("http://ubuntuforums.org/showthread.php?t=1358026")

---

### Post by k33bz on 2010-05-17
OK, maybe I am misunderstanding what plymouth is. I thought plymouth was the program that booted up before anything else and provided with the boot screen. You know the screen that shows the loading bar right before the login screen. By default it shows that gawd awful purple screen with a light orange loading bar and saying Ubuntu above it. I have found a few other choices in the synaptic manager to change this to a few different ones. However I wanted to find more or better yet create one.

PS running 10.04

---

### Post by warfacegod on 2010-05-17
Okay, I give up. I just installed 10.04 into my experiment drive. Again.

I hated the Beta release. I hated the UNE release. And I hate this one.

I can't get that gdm2 package to work properly for it. It will change the theme, icons, and even disable the user list but it won't recognize the any images. Change the wall paper, change the whole ...ugliness.

I installed it in 9.10 because I disliked that splash (hate this one too) and it worked perfectly.

If I were you, I'd go back to 9.04 because it has the best balance of customizability and stability. Customizing went way down hill in 9.10 and now, with 10.04, its just awful. Try messing with the panel in UNE and you'll see what I mean. Actually, you probably already get it with this splash thing.

---

### Post by k33bz on 2010-05-18
> **warfacegod said:**
> Okay, I give up. I just installed 10.04 into my experiment drive. Again.

I hated the Beta release. I hated the UNE release. And I hate this one.

I can't get that gdm2 package to work properly for it. It will change the theme, icons, and even disable the user list but it won't recognize the any images. Change the wall paper, change the whole ...ugliness.

I installed it in 9.10 because I disliked that splash (hate this one too) and it worked perfectly.

If I were you, I'd go back to 9.04 because it has the best balance of customizability and stability. Customizing went way down hill in 9.10 and now, with 10.04, its just awful. Try messing with the panel in UNE and you'll see what I mean. Actually, you probably already get it with this splash thing.

as far as the gdm2 I use ubuntu tweak to customize it, the bg image needs to be put in the right directory for it to be loaded. Im on my wifes computer right now, so I cant tell you which folder that is. But it can not be in a /home/usr folder.  As far as the boot splash, there are other ones available, check synaptic manager under plymouth.

All I want is a tutorial on fully customizing the boot screen.


I wont go back to 9.04, 10.04 is so much better, just losing alot of the customizable options which is what I hate. My next step would to lose Ubuntu all together and go straight to Debian.

---

### Post by warfacegod on 2010-05-18
> **k33bz said:**
> as far as the gdm2 I use ubuntu tweak to customize it, the bg image needs to be put in the right directory for it to be loaded. Im on my wifes computer right now, so I cant tell you which folder that is. But it can not be in a /home/usr folder.  As far as the boot splash, there are other ones available, check synaptic manager under plymouth.

All I want is a tutorial on fully customizing the boot screen.


I wont go back to 9.04, 10.04 is so much better, just losing alot of the customizable options which is what I hate. My next step would to lose Ubuntu all together and go straight to Debian.

I use Ubuntu Tweak myself. Its an excellent tool. Didn't occur to me suggest it because I can't get it working in 10.04.

I tried to install Debian a few weeks ago. It absolutely refused to install properly.

---

### Post by k33bz on 2010-05-19
Google Ubuntu Tweek for 10.04. Its a different software source then what is available by default. Works [perfectly. But as said before, if you dont have the picture in the right file, which is /usr/share/backgrounds, then it wont load up when you boot your computer.

---

### Post by warfacegod on 2010-05-19
From what I understand Ubuntu Tweak is available in 10.04's Synaptic as ubuntu-tweak. At some point today, I'm going to reboot into my 10.04 in my experiment partition and verify this.

---

### Post by Excedio on 2010-05-19
> **warfacegod said:**
> From what I understand Ubuntu Tweak is available in 10.04's Synaptic as ubuntu-tweak. At some point today, I'm going to reboot into my 10.04 in my experiment partition and verify this.
 
As the OP stated, there is one available by default. I take that to assume that it is in Synaptic already. But it's not working correctly.
 
k33bz also suggested doing a google search to find the compatible version. Without installing it myself ans testing, I would recommend following what is stated here: [http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html](http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html)
 
Written May 7th.

---

### Post by k33bz on 2010-05-19
> **Excedio said:**
> .
 
k33bz also suggested doing a google search to find the compatible version. Without installing it myself ans testing, I would recommend following what is stated here: [http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html](http://www.ubuntugeek.com/how-to-install-ubuntu-tweak-in-ubuntu-10-04lucid-lynx.html)
 
Written May 7th.
 Thats the tutorial I used to install Ubuntu-Tweak, it it works perfectly fine.


I am going to take it as no one knows how to customize or find other boot loaders splash screens with 10.04? (other than the few that are available in the synaptic manager of course).

---

### Post by warfacegod on 2010-05-19
[http://ubuntuforums.org/showthread.php?t=1445724]("http://ubuntuforums.org/showthread.php?t=1445724")

This guy is considering putting together a guide for 10.04. Perhaps, if more users request it, he'll do it.

---

### Post by k33bz on 2010-05-19
Thanks for the link, I posted a msg on his thread, hopefully we can get a tutorial on customizing the boot screen :)

---

### Post by warfacegod on 2010-05-19
If it gets done, I *may* consider switching to 10.04. In spite of all the bugs it is still more stable than 9.10.

---

### Post by Dkkline on 2010-05-19
Am I right assuming you want to change the "splash screen" / "login background"

if so, you might want to try this:

Open a Terminal and run this command:

Code:
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
Then logout, and you'll see an Appearance window pop up. Change it to how you prefer it, then close it and login as usual.

When you have logged in after finishing the customizing, run this command to prevent the Appearance window from opening at the GDM screen every time.


Code:
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop



or 

gksu -u gdm dbus-launch gnome-appearance-properties

and then CTRL + F2 type: gnome-keyboard-properties and go under the tab "accessibility" and uncheck "Accessibility features can be toggled with keyboard shortcuts , then log out and log in, and TADA!

hope this might help

p.s., if you look for more backgrounds, or other artwork for gnome, try CODE: sudo apt-get install gnome-art

---

### Post by k33bz on 2010-05-19
Thank you, but no its not the background or anything that has to do with the GDM login screen.

The boot loader screen is what I want to customize :)

EDITED:

This is what I used to change my plymouth boot screen, however I have only seen this tutorial, and havnt seen anywhere else I can get a different boot screen that is "not available" in the synaptic manager [http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13]("http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13") Down at the bottom


And so there is no more confusion on what I want to change here is the default:
[IMG]http://lh6.ggpht.com/_1QSDkzYY2vc/S47Fu4uYWsI/AAAAAAAAAcY/9KExu6KAKpc/s400/boot.png[/IMG]

---

### Post by warfacegod on 2010-05-19
I used gdm2setup to change the wallpaper in 9.10 login screen. It applied the wallpaper also as the background for that leaving only the logo and progress bar. This with the white 9.10 logo is rather elegant, I think.

---

### Post by warfacegod on 2010-05-20
Okay so I booted into my 10.04 (retch!) and (a day late, sue me) no ubuntu-tweak in Synaptic.

---

### Post by k33bz on 2010-05-22
They posted a link in this thread on the first page, you need to add that repo to your sources.

---

### Post by warfacegod on 2010-05-22
That's what I figured. I downloaded it directly from the site as I usually do.

---

### Post by HeadHunter00 on 2010-08-29
> **warfacegod said:**
> Okay, I give up. I just installed 10.04 into my experiment drive. Again.

I hated the Beta release. I hated the UNE release. And I hate this one.

I can't get that gdm2 package to work properly for it. It will change the theme, icons, and even disable the user list but it won't recognize the any images. Change the wall paper, change the whole ...ugliness.

I installed it in 9.10 because I disliked that splash (hate this one too) and it worked perfectly.

If I were you, I'd go back to 9.04 because it has the best balance of customizability and stability. Customizing went way down hill in 9.10 and now, with 10.04, its just awful. Try messing with the panel in UNE and you'll see what I mean. Actually, you probably already get it with this splash thing.
Yah, the meaning of linux is becoming more and more distorted, well at least the meaning of gnome. I mean customizability is what linux is all about.

---

### Post by HeadHunter00 on 2010-08-29
> **warfacegod said:**
> Okay so I booted into my 10.04 (retch!) and (a day late, sue me) no ubuntu-tweak in Synaptic.
Add the getdeb repository from getdeb.net
I know that they have ubuntu-tweak.

---

