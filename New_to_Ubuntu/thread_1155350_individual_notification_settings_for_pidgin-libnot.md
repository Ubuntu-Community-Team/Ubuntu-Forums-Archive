---
title: "individual notification settings for pidgin-libnotify?"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by raccoonone on 2009-05-10
I just upgraded to Ubuntu 9.04, and I was using Guificiations for Pidgin, which has stopped working after upgrading. It seems to have been replaced by the pidgin-libnotify plugin, which looks nicer but I can't figure out how to customize it. With Guifications I could change the settings on a per user basis, so that I would only receive messages about buddies logging in and out for those that I want to receive notifications.
How can I customize this with the new version of Pidgin? I have a lot of buddies, but most of them I don't talk to very much, so I only want to receive notifications when certain buddies log on.

---

### Post by ashmew2 on 2009-05-12
Hi , 
_**Edit**_ : Why dont you install Guifications since you are comfortable with it ? 

```
sudo apt-get install pidgin-guifications
```_**Original Post**_ : 

If i understand you clearly , you should be able to get desired results by going into 
Tools > Buddy Pounces from Pidgin main Window.

Also , There are Tools > Plugins which have a comprehensive list of plugins you can use.

Also , ```
sudo apt-get install pidgin-plugin-pack
``` adds even more plugins to that list , so you might wanna check it out.

You must be wondering i gave you so many things you didnt need..but if i am not mistaken , the thing that you need was somewhere in there! ;)

---

### Post by raccoonone on 2009-05-14
Thanks, but the Buddy Pounce doesn't seem to use the notify-osd API, which is what I was trying to get. guifications is working for me now, I was just wondering if there was a way to use libnotify since it looks nicer.

---

### Post by FAJALOU on 2009-05-27
This is related.  Guifications was crashing my system so I am using the other notification, but what happens is that the notifications cover my gnome-panel. *Which I dislike with an avid passion because it covers the time etc.*  Is there a way to 'shift' the notifications down so they don't cover up the gnome-panel, or otherwise make the panel on top?  **Thanks a bunch!**


PS Please excuse my total lack of skills in GIMP.  I blotted everything out, but it still looks horrible, but it gets the point across!  :p

---

### Post by kpkeerthi on 2009-05-27
> **FAJALOU said:**
>  Is there a way to 'shift' the notifications down so they don't cover up the gnome-panel, or otherwise make the panel on top?

I would like to know how to fix this, as well. 

@FAJALOU
I was able change the position of the notification bubble by running **notification-properties**. I would like to keep it closer to system tray, but if I do, it covers the top panel. Anybody knows how to move the bubble down a bit so it doesn't cover the panel up?

---

### Post by FAJALOU on 2009-05-27
kpkeerthi,
     What is this about 'notification-properties'?  I tried running it but terminal says its not valid nor is it found with apt...?  Sounds like a good fix, but where to run it from, and how? thanks!

---

### Post by kpkeerthi on 2009-05-28
> **FAJALOU said:**
> kpkeerthi,
     What is this about 'notification-properties'?  I tried running it but terminal says its not valid nor is it found with apt...?  Sounds like a good fix, but where to run it from, and how? thanks!

OK. Here is what I did...
1. Uninstalled notify-osd
```
sudo apt-get purge notify-osd
```

2. Installed the standard notification system
```
sudo apt-get install notification-daemon
```

3. Reboot.

4. Ran notification-properties from terminal or ALT + F2. Here you can change the notification bubble orientation.

---

### Post by FAJALOU on 2009-05-31
Wish I had the same 'luck' that you had....

```
:~$ sudo apt-get install notify-osd
[sudo] password: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package notify-osd
:~$ sudo apt-get remove notify-osd

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package notify-osd
:~$ 
:~$ sudo apt-get install notification-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
notification-daemon is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
:~$ notification-properties
bash: notification-properties: command not found
:~$ 

```


Are you in Jaunty or Hardy?

---

### Post by Xodarap on 2010-05-04
I was frustrated by this too, so I wrote a little perl script to fix this. You can find it here: [pidgin libnotify for select users]("http://philosophyforprogrammers.blogspot.com/2010/05/pidgin-notifications-for-select-users.html").

---

### Post by reis on 2012-07-05
You can use the "Execute command" on the pounce configuration filling it with:

     notify-send "[person] is online"


And also check the Recurring option.

---

### Post by wildmanne39 on 2012-07-05
Old thread closed.

---

