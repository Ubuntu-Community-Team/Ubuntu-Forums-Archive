---
title: "set timezone"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by pottzie on 2010-12-14
I'm using Ubuntu10.10, 64 bit. The time isn't correct, and I can't set it from System/Administration/Time and Date. I try, but the authorization keeps looping back. I tried "datemmddhhmmyyyy" in the terminal, but sudo didn't work (could have tried sudo su -- now that I think of it.)
 The Sys Admin won't let me set the timezone either. The "you have to unlock" icon set up loops the permisions, and seems to me like a seventeen step waltz to do what could be accomplished in two steps.
 I wanted to run the weather applet in the toolbar also, but there doesn't seem to be any way to tell it where I live so it can work. I have Fedora on another computer, and like the app that they have running in Gnome. It gets your location, and once that's done time and timezone are all included, so something that should be a no-brainer actually is. 
 Even a way to tell Ubuntu to get the time from the server would be great. Seems like that's the way Ubuntu worked until now.

---

### Post by seawolf167 on 2010-12-14
the current date & time:

```
date
```change the current date & time:

```
sudo date nnddhhmmyyy.ss
```nn=month (01-12)
dd=day (01-31)
hh=hour (00-23)
mm=minute (00-59)
yyyy=year
ss=second (00-59)


timezone:

```
tzconfig   --or--    tzselect
```

---

### Post by pottzie on 2010-12-14
Thanks
 Edit: I just went ot do it and realized "What the heck does 'nn' mean?"

 Shouldn't it be m(onth)m(onth)ddhhm(in)m(in)yyyy?=mmddhhmmyy.
 
 Edit again. It didn't work. I'm stuck having an operating system that works great, but it's stuck in a timezone from another dimension.

---

### Post by David D. on 2010-12-14
You may have the wrong time zone set for your location.  To change the time zone go to System>Administration>Time and Date.  Click on the padlock icon and enter your password to unlock, then choose a time zone that is correct for you.  For example, I live in the eastern USA, so my time zone is set to "America/New York".

The "Configuration" is where you can select a time server.

As for the weather applet, right click on the applet, select Preferences and choose a listed location near you on the location tab.

---

### Post by pottzie on 2010-12-14
Thanks. I'm at work now but will give it a try when I get home.

---

### Post by pottzie on 2010-12-15
The time info was good, looks like I'm in the right time zone now, thanks. The weather app is another story- just shows "default location," with no way to edit it or input my location.
 
 I think I've got the Bob Dylan weather app, 'cause I evidently really "Don't "need" a weatherman to know which way the wind blows!"

---

