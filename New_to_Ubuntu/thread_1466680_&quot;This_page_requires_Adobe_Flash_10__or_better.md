---
title: "&quot;This page requires Adobe Flash 10  or better&quot;"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Motorhead Kaze on 2010-04-30
This seems like such a noob issue, but damned if I can figure it out. I have had Adobe Flash running for a while, and been using Hardy for a long while too. But "South Park Studios" tells me "This page requires Adobe Flash 10  or better". 

Ok, so just in case I didn't really have it, I downloaded Adobe Flash 10 from source, rebooted, and still get the message. I don't have anything like nash or swf whatever the heck that thing is called. I can watch almost anything on the Net including News vids, YouTube, etc. just not THIS page for some reason.

I have followed instructions on several threads, but really cannot figure this out. Help?

Like I said, I am using Hardy.

---

### Post by Sealbhach on 2010-04-30
Your browser might not be picking up the flash plugin you installed.

In your browser, type

```
about:plugins

```in the address bar, and look in the section Shockwave Flash, you should see something like this:

**Shockwave Flash**

 File:  npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.0 r45

If it's not showing the lastest Flash, them download the .deb for 8.04 from here and install it:

[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29)

.

---

### Post by cuberts on 2010-04-30
> **Motorhead Kaze said:**
> This seems like such a noob issue, but damned if I can figure it out. I have had Adobe Flash running for a while, and been using Hardy for a long while too. But "South Park Studios" tells me "This page requires Adobe Flash 10  or better". 

Ok, so just in case I didn't really have it, I downloaded Adobe Flash 10 from source, rebooted, and still get the message. I don't have anything like nash or swf whatever the heck that thing is called. I can watch almost anything on the Net including News vids, YouTube, etc. just not THIS page for some reason.

I have followed instructions on several threads, but really cannot figure this out. Help?

Like I said, I am using Hardy.aha for your problem you just have to actually get Adobe flash 10, and you just have to install that plugin.

---

### Post by Motorhead Kaze on 2010-04-30
The read-out for "about:plugins" says I have hockwave Flash 9.0 r262 but I don't see it in Synaptic to remove that one and FF is not presenting the option.

Synaptic does say that I have adobe-flashplugin (version 10), and the flashplugin-nonfree version 10 too.

So I only have a plugin and need to get a program? Point me in the direction and I will grab it forthwith!

---

### Post by Sealbhach on 2010-04-30
> **Motorhead Kaze said:**
> Ok, so Synaptic says I have adobe-flashplugin (version 10), and the flashplugin-nonfree version 10 too.

So I only have a plugin and need to get a program? Point me in the direction and I will grab it forthwith!

What matters is the plugin your browser is using, please do the 
```
about:plugins
```thing. I've also given a link for the .deb file from the Flash site.

EDIT: OK I see your browser is using Flash 9.

Please try the link I provided from the Flash site.
.

---

### Post by Motorhead Kaze on 2010-04-30
I used the link you posted before typing my reply. This is actually the same page/link I used the other day, but my browsers are not recognizing the update. I follow the directions, get the plugin and go to install, and Ubuntu says I already have version 10 installed. Somehow, I need to get rid of version 9 and get 10 in here, but it is not happening automatically when install the plugin from that link.

---

### Post by Sealbhach on 2010-04-30
> **Motorhead Kaze said:**
> Yes, as I just wrote there I did about plugins, and was told that I have Shockwave Flash 9.0 r262 . I did use the link you posted, but that is the very same link I used the other day to get the plugin. I click the link and it says I already have version 10 installed. So somehow, I need to get rid of version 9 and get 10 in here, but it is not happening automatically when install the plugin from that link.

OK. Go into Synaptic and remove the flash plugin you have already installed.

Now, we need to remove the Flash 9 plugin as well. To do this, in a terminal run 

locate libflashplayer.so

and then delete that wherever you have it. The easiest way to do it 

sudo rm /path/to/libflashplayer.so

changing the path to whatever locations the "locate" commands give.

Then, reinstall from the Flash website from that link.

.

---

### Post by xumuk37 on 2010-04-30
Download this plugin from adobe web (libflashplayer.so) and just copy it to /usr/lib/mozilla/plugins/ ... this method always works! Good luck.

---

### Post by Motorhead Kaze on 2010-04-30
Sealbhach, that did it. Thanks big time!

Thanks to everybody else too!

---

### Post by Sealbhach on 2010-04-30
> **Motorhead Kaze said:**
> Sealbhach, that did it. Thanks big time!

Thanks to everybody else too!

Great! Well done.

.

---

### Post by Motorhead Kaze on 2010-11-22
Just popping back in to mark the title Solved. Thanks again.

---

