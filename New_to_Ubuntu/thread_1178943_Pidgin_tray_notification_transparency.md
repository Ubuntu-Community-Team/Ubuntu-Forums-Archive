---
title: "Pidgin tray notification transparency?"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by illogic6 on 2009-06-05
I just started diving head first into linux a couple weeks ago and I have to say that I am absolutely in love with Ubuntu.

I tried out a minimal Ubuntu installation today and I've got just about everything I need working 100%.

The one thing that I don't quite know how to fix are the system tray notification bubbles that seem to just be there in a standard Ubuntu installation.

Pidgin used to alert me with a semitransparent,  growl-like bubble when I received an IM.  Now I'm getting these things:  [http://img195.imageshack.us/img195/6029/screenshotwbv.png](http://img195.imageshack.us/img195/6029/screenshotwbv.png)

Is there a certain package I have to install in order to get the cool looking notifications back?

Thanks!

---

### Post by Shadowking on 2009-06-05
> **illogic6 said:**
> I just started diving head first into linux a couple weeks ago and I have to say that I am absolutely in love with Ubuntu.

I tried out a minimal Ubuntu installation today and I've got just about everything I need working 100%.

The one thing that I don't quite know how to fix are the system tray notification bubbles that seem to just be there in a standard Ubuntu installation.

Pidgin used to alert me with a semitransparent,  growl-like bubble when I received an IM.  Now I'm getting these things:  [http://img195.imageshack.us/img195/6029/screenshotwbv.png](http://img195.imageshack.us/img195/6029/screenshotwbv.png)

Is there a certain package I have to install in order to get the cool looking notifications back?

Thanks!
Install "amsn" and ditch pidgin. Amsn has a better interface, plugins and all the usual IM features that pidgin (for some reason) does not have.

---

### Post by illogic6 on 2009-06-05
> **Shadowking said:**
> Install "amsn" and ditch pidgin. Amsn has a better interface, plugins and all the usual IM features that pidgin (for some reason) does not have.

I've tried aMSN and I know it has more features than Pidgin.  For whatever reason, I like Pidgin better.

Edit:  Regardless, other programs display notifications just like Pidgin.  Even if I switch IM clients, Transmission and every other program will still have ugly notifications.

---

### Post by Shadowking on 2009-06-05
> **illogic6 said:**
> I've tried aMSN and I know it has more features than Pidgin.  For whatever reason, I like Pidgin better.

Edit:  Regardless, other programs display notifications just like Pidgin.  Even if I switch IM clients, Transmission and every other program will still have ugly notifications.
ok...so choosing pidgin is a personal choice. That's fair.

You say that other programs give notifications as well. This means that it doesn't have anything to do with pidgin. Maybe some of the more experienced users can explain how to solve your problem. I'm still a fresh convert.

---

### Post by illogic6 on 2009-06-05
> **Shadowking said:**
> ok...so choosing pidgin is a personal choice. That's fair.

You say that other programs give notifications as well. This means that it doesn't have anything to do with pidgin. Maybe some of the more experienced users can explain how to solve your problem. I'm still a fresh convert.

Yeah...  I think it's some kind of OSD Daemon that displays those popup messages.  I don't know if I need to tweak some settings or install a completely different Daemon.

I'm starting to have trouble with Compiz as well.  Right about ready to just go back to a full install until I figure this all out.  :P

---

### Post by Kimm on 2009-06-05
Have you been playing with installing/removing packages?

The program that handles those semi-transparent bubbles is called "notify-osd", to install it again, do:

```
sudo apt-get install notify-osd
```

in a terminal. If it tells you that it is installed already, try this:

```
sudo apt-get --reinstall install notify-osd
```

to reinstall it.

What kind of problems are you having with Compiz?

---

### Post by illogic6 on 2009-06-05
> **Kimm said:**
> Have you been playing with installing/removing packages?

The program that handles those semi-transparent bubbles is called "notify-osd", to install it again, do:

```
sudo apt-get install notify-osd
```in a terminal. If it tells you that it is installed already, try this:

```
sudo apt-get --reinstall install notify-osd
```to reinstall it.

What kind of problems are you having with Compiz?

That is EXACTLY the information I needed.  It seems like it's working intermittently now though.

I've been trying to figure this out for hours now.  I'm afraid that something I did previously is causing a conflict.

Someone told me earlier that I needed to install pidgin-libnotify or something like that.  Should that be removed?

---

### Post by prvteprts on 2009-06-05
> **illogic6 said:**
> That is EXACTLY the information I needed.  It seems like it's working intermittently now though.

I've been trying to figure this out for hours now.  I'm afraid that something I did previously is causing a conflict.

Someone told me earlier that I needed to install pidgin-libnotify or something like that.  Should that be removed?

I would say don't remove that. I think that refers to the pidgin plugin (the envelope icon) that works with notify-osd to display the notifications. In Jaunty, the notifications were changed to have a more uniform appearance.

What do you mean intermittently? As I have observed, notifications have problems appearing after activating either fullscreen gaming or video.

---

### Post by illogic6 on 2009-06-05
I've been working with it a bunch.

I installed a fresh system.  I made sure I had libnotify1, pidgin-libnotify and notify-osd.

When a contact sends me their first message, my only notification is a changed system tray icon.

You can see what I'm talking about here:  [http://img411.imageshack.us/img411/8457/screenshot2odi.png](http://img411.imageshack.us/img411/8457/screenshot2odi.png)

Once a contact sends me a SECOND message, the notification appears just as I'd like them all to:  [http://img199.imageshack.us/img199/203/screenshot3i.png](http://img199.imageshack.us/img199/203/screenshot3i.png)

I'm unsure if this has anything to do with my problem, but this is the guide I followed to create this installation: [http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

The only packages I've installed in addition to those listed there are:  gimp, transmission, vlc, pidgin, konsole, inkscape, update manager, computer janitor, gtk-RecordMyDesktop, scheduled tasks, checkgmail.

If anyone has any insight at all, I'd appreciate it.  I've been pulling my hair out since this time yesterday, and I don't want to give up and go back to a standard install.  ;)

Thanks again!

---

### Post by illogic6 on 2009-06-05
Thank God I'm not the only person with this problem.

[https://bugs.launchpad.net/ubuntu/+source/pidgin-libnotify/+bug/363108](https://bugs.launchpad.net/ubuntu/+source/pidgin-libnotify/+bug/363108)

---

### Post by josephellengar on 2009-06-05
I'm having a problem as well with the old notifications appearing, rather than the new ones.

---

### Post by illogic6 on 2009-06-05
> **idigchess said:**
> I'm having a problem as well with the old notifications appearing, rather than the new ones.

I reinstalled Ubuntu and then got the package "notify-osd."

I haven't seen those old notifications since.

---

### Post by josephellengar on 2009-06-05
> **illogic6 said:**
> I reinstalled Ubuntu and then got the package "notify-osd."

I haven't seen those old notifications since.

Reinstalled the whole operating system?!  Not worth it.  I already have reinstalled notify-osd.

---

### Post by illogic6 on 2009-06-05
> **idigchess said:**
> Reinstalled the whole operating system?!  Not worth it.  I already have reinstalled notify-osd.

I still don't quite know what I'm doing and I may have installed some unnecessary packages trying to get these pop-ups back.  I reinstalled to make sure I didn't have any useless packages install because I'm uptight like that.  :P

Just relating my experiences...

---

### Post by Kimm on 2009-06-06
You could try

```

sudo apt-get install ubuntu-desktop

```

That should reinstall any packages that came with the system and might have been removed.

It sounds to me like notify-osd is crashing for some reason and then the standard notification-deamon takes over, could be because of a corrupt install disc, now if you have a decent internet connection and dont mind taking a slight risk, you could try this:

```

sudo apt-get remove libnotify*

```

to remove anything that has anything at all to do with libnotify (should be quite a lot, therefore it might be somewhat risky, I'm not on Ubuntu right now so i cant check what it would remove, perhaps you could type that command and tell us what it spits out?)

after that, do

```

sudo apt-get install ubuntu-desktop

```

to download new packages from the ubuntu servers and restore all the packages that where removed.

---

### Post by shae on 2009-06-06
You will also need to remove the package notification-daemon and reboot.

---

### Post by josephellengar on 2009-06-06
> **shae said:**
> You will also need to remove the package notification-daemon and reboot.

That's the step I missed, LOL.  The reboot.  :oops:

---

