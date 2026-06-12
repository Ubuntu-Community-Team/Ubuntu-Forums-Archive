---
title: "Not fully understanding the envelope in 10.04"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by listerdl on 2010-06-18
Hi, with the latest version of 10.04 I have a little envelope on the task bar, does anyone use it and does it work without issues?

Thanks!

---

### Post by warfacegod on 2010-06-18
That would be Evolution. It's sort of an all in one e-mail client, calendar, appointment scheduler, etc.

I can't speak to how well it works because I don't use it. In fact it's one of the things I remove when I do a fresh install.

---

### Post by Sharang.d on 2010-06-18
> **warfacegod said:**
> That would be Evolution. It's sort of an all in one e-mail client, calendar, appointment scheduler, etc.

I can't speak to how well it works because I don't use it. In fact it's one of the things I remove when I do a fresh install.

I want to keep the "Chat" option in the drop-down menu when clicked on it but remove the "Mail" , "Compose New Message" , "Contacts". Already uninstalled Evolution but the options are still there. How can i replace them with Thunderbird?

---

### Post by warfacegod on 2010-06-18
> **Sharang.d said:**
> I want to keep the "Chat" option in the drop-down menu when clicked on it but remove the "Mail" , "Compose New Message" , "Contacts". Already uninstalled Evolution but the options are still there. How can i replace them with Thunderbird?

Right click the Envelope and remove it.

You can drag n' drop the Thunderbird icon onto the panel. You can even drag it right from your menu if need be.

---

### Post by Sharang.d on 2010-06-18
You didn't read my post correctly. I said i want to KEEP the envelope on the panel and just Delete the "Mail" , "Compose New Message" and "Contacts" Menu items that come as a drop-down list when clicked on the envelope

---

### Post by warfacegod on 2010-06-18
Don't think that's possible not without modifying the source code anyway. You could try making your own panel launcher or menu and use the Envelope icon for it.

---

### Post by Paddy Landau on 2010-06-18
> **warfacegod said:**
> Right click the Envelope and remove it.
That removes the entire Indicator Applet, which also removes the sound icon. That means that I cannot adjust the sound any more.

---

### Post by warfacegod on 2010-06-18
> **Paddy Landau said:**
> That removes the entire Indicator Applet, which also removes the sound icon. That means that I cannot adjust the sound any more.

The sound should be on the Notification area not the Indicator Applet and removing the Envelope should remove neither.

---

### Post by Sef on 2010-06-18
> Quote:
Originally Posted by Paddy Landau  
That removes the entire Indicator Applet, which also removes the sound icon. That means that I cannot adjust the sound any more.
The sound should be on the Notification area not the Indicator Applet and removing the Envelope should remove neither.

It does remove the entire mail icon.

---

### Post by Sharang.d on 2010-06-18
So anyway, my problem still exists :(
Help someone?

---

### Post by empty_spaces on 2010-06-18
There is a way to connect the envelope icon to Thunderbird, so that it changes color whenever you receive an email in Thunderbird.
I'm at work so I can't go into too much detail, but I will recommend that you read the following thread entirely, understand all the options and then see which parts you want to follow.
[http://ubuntuforums.org/showthread.php?t=1465709](http://ubuntuforums.org/showthread.php?t=1465709)

---

### Post by Paddy Landau on 2010-06-18
> **warfacegod said:**
> The sound should be on the Notification area not the Indicator Applet and removing the Envelope should remove neither.
Unfortunately, they're both on the Indicator Applet.

If I right-click either the sound icon or the envelope icon and press "About", it shows "Indicator Applet 0.3.7". If I right-click the envelope and click Remove From Panel, it removes both, and I have to Add to Panel the Indicator Applet to get the sound icon (and the envelope) back.

It's not a problem, actually, it's just a tiny extra space on the task bar that probably I'll never use.

---

### Post by warfacegod on 2010-06-18
> **Paddy Landau said:**
> Unfortunately, they're both on the Indicator Applet.

If I right-click either the sound icon or the envelope icon and press "About", it shows "Indicator Applet 0.3.7". If I right-click the envelope and click Remove From Panel, it removes both, and I have to Add to Panel the Indicator Applet to get the sound icon (and the envelope) back.

It's not a problem, actually, it's just a tiny extra space on the task bar that probably I'll never use.

I just booted into a LiveUSB of 10.04 (feel like I need to wash my hands) and you're right. This is exactly the sort of idiocy I was referring to in that other thread. I'd guess the only way to get rid of the Envelope is to remove Evolution entirely.

---

### Post by Sharang.d on 2010-06-19
> **warfacegod said:**
> I just booted into a LiveUSB of 10.04 (feel like I need to wash my hands) and you're right. This is exactly the sort of idiocy I was referring to in that other thread. I'd guess the only way to get rid of the Envelope is to remove Evolution entirely.

i don't know if these two are related issues or not but i removed Evolution and all its libs. After rebooting the evolution sub-menu item was not there only the chat was there but my network manager icon also vanished :|
Which is why I'm accessing the net through XP as of now.
How do i get the Network Manager applet back? It's not there in the add panels dialog.

---

### Post by k3lt01 on 2010-06-19
The envelope will remain while you have applications that use it. Empathy, Evolution, and Pidgin can all use it so if you want to remove the email section from it you will need to remove Evolution from your system. The only thing that I have using mine is Pidgin, I removed Empathy and Evolution and installed Pidgin within minutes of installing 10.04.

---

### Post by Paddy Landau on 2010-06-19
> **Sharang.d said:**
> ... i removed Evolution and all its libs. After rebooting ... my network manager icon also vanished
For some strange reason, evolution-data-server-common is a dependency of gnome-applets, gnome-panel and various other bits.

Reinstall whichever of the following are missing: gnome-applets, gnome-panel, gnome-session, indicator-applet, indicator-applet-session, indicator-me, and ubuntu-desktop.

---

### Post by Soul-Sing on 2010-06-19
please do NOT remove [COLOR="Red"]all[/COLOR] evolution related pakages.

```
/usr/share/indicators/messages/applications
```
for removal default progs in the envelope

make thunderbird visible in the applet

```
sudo apt-get install libnotify-bin
```

```
sudo apt-get install bzr
```

```
bzr branch lp:libnotify-mozilla
```

```
cd libnotify-mozilla
```

```
./build.sh
```

in your home/yourname/mozilla map you got now; libnotify-mozilla.xpi

you can add this to your Thunderbird add-ons
restart Thunderbird: preferences: Libnotify Popups

[COLOR="Red"]additional step to make this perm. in the systray[/COLOR]

```
sudo apt-get install alltray
```

in the thunderbird starter: alltray thunderbird %u

---

### Post by Paddy Landau on 2010-06-19
> **k3lt01 said:**
> The envelope will remain while you have applications that use it.
I uninstalled Empathy, Evolution (except for evolution-data-server-common), and Pidgin. But I still have the envelope, with the only option "Broadcast". What else?

---

### Post by Elfy on 2010-06-19
> **Paddy Landau said:**
> I uninstalled Empathy, Evolution (except for evolution-data-server-common), and Pidgin. But I still have the envelope, with the only option "Broadcast". What else?

I believe removing the indicator-me package will do this - it did here anyway - possibly need a logout or panel restart afterwards.

---

### Post by k3lt01 on 2010-06-19
Beat me to it forestpiskie :lolflag:

Paddy that's what you do.

---

### Post by Elfy on 2010-06-19
> **k3lt01 said:**
> Beat me to it forestpiskie :lolflag:

I got all out of breath too :D

In fact there are a few of those indicator-thing packages which can add or take away function from the indicator applet - I suspect there will be more if notification area is really going.

---

### Post by Paddy Landau on 2010-06-19
> **forestpiskie said:**
> ... removing the indicator-me package...
I discovered that you also have to remove indicator-messages (and reboot).

Thank you.

---

