---
title: "thinking of switching from Gnome to KDE"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-09-16
Hi Ya'll,
 Okay, so I loaded 10.04 Kubuntu a day or so ago. It has been a couple of years since I seriously looked at KDE. So far it is quite interesting. But very different in quite a number of things. Can anyone who might have done the same thing fill me on how to effectively make the switch? I have managed to get my Gmail in Kontact so far. It lloks like there are a few other interesting items. I am an end user, and in Gnome most items names sounded like what theey did, or at least using them for so long now, they do to me! HAHA! 
Do most of the applications work on KDE?
How do I switch my window buttons to the left?
Do I load Flash and all the extras the same way? Can i use Ubuntu-Tweak on it? DockbarX? I have not seemed to be able to get any  from KDE-Look to load, is there a loading difference between KDE 3 and 4? Does compiz work? How do I get a little bit of eye candy? How do I change my mouse settings? Does Wine work the same?

Everrything seems to be differnet. It is very cool looking, and I want to give an ernest shot at trying it. Anyone who has made the switch and liked it or even if you disliked it for a certain reason of it not doing something you were used to?

Thanks a lot,
AndyP79

---

### Post by snowpine on 2010-09-16
Here is the easiest guide I know of for switching from Gnome to KDE in Ubuntu:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by wilee-nilee on 2010-09-16
You can also add it as a desktop and choose between kde or whatever ones you want at login.

This does though add the desktop programs from each desktop to each other, which can be a advantage, but some from another desktop may not work on the native desktop running.

If you just want to load it while keeping Ubuntu run.
```
sudo apt-get install kde-desktop
```

I would do it this way personally I don't like kde in any shape or form so you might want to check it out first, and use the psychocats link when needed.

---

### Post by solar george on 2010-09-16
You can use gnome applications in KDE and vica versa but unless you particularly like a gnome application there's no reason not to use the KDE defaults. The only thing I always change is using Chromium or Firefox in place of konqueror for the web browser,

Take a look around KDE's system settings program if you want to customise something, window controls are under "Appearance">"Windows" in the system settings program.
KWin has built-in compositing features so you don't need compiz, you can configure that from the Desktop section of System Settings.

I'd suggest you install kubuntu-restricted-extras instead of ubuntu-restricted-extras to get flash and the like.

Wine will work the same in Kubuntu as in Ubuntu.

KDE SC 4.x is completely different from the 3.x series. The best way to install new themes and the like is to use the "Get new . .  ." button where it is available (e.g. "Get New Icon Themes" in the icons settings.)

---

### Post by McNils on 2010-09-16
> **AndyP79 said:**
> 
How do I switch my window buttons to the left?


I am on kde 4.5.1.
Just open systemsettings->workspace appearance->window decorations. Click on configure buttons. Drag the button in the way you want them.

There is a similar configuration in 4.4 if you find window-decorations.

---

### Post by Sylslay on 2010-09-16
No way!!! Gnome is more easy!!!
Used KDE for some time, but I like more Gnome.

---

### Post by beew on 2010-09-16
Wireless apparently is broken in KDE. Can never set it up, tried different machines with different cards, gnome nm always works but  never KDE. Other people I know also reported wireless problems in installing kubuntu.  I don't really like the kde desktop anyway, everything is hidden and it looks a lot like a cheap Windoze.

---

### Post by manny43 on 2010-09-16
If i were you i'd use LiveCD first and see if you get motivated to make the switch, personally i dont like KDE and i agree with Sylslay GNOME is easier
specially for Ubuntu beginners like me

---

### Post by Nythain on 2010-09-16
I'm not a fan of desktop environments in general, but I did recently run KDE 4.5.1 for a while, and I would have to say if I was gonna run a desktop environment it would most definitely be KDE 4.5.1...

in order to get KDE 4.5.1 in Ubuntu/Kubuntu, make sure you add the kubuntu-backports ppa. In a terminal simply type
```

sudo add-apt-repository ppa:kubuntu-ppa/backports

```
Then simply update your software manager and viola, packages for KDE 4.5.1 available :)

---

### Post by McNils on 2010-09-16
> **beew said:**
> Wireless apparently is broken in KDE. Can never set it up, tried different machines with different cards, gnome nm always works but  never KDE. Other people I know also reported wireless problems in installing kubuntu.  I don't really like the kde desktop anyway, everything is hidden and it looks a lot like a cheap Windoze.

I'm replying to your FUD over a wireless connection,  its not broken.

---

### Post by AndyP79 on 2010-09-16
Hey everyone, thanks for all the great replies. It is all something to take into account. I can definitly see what people mean about Gnome just being easier to use. That said, there is so much tweaking available in KDE. On the wireless issue, I have none. I set it up first thing after installing, though, it seems to be considerably slower for some reason. I am slowley getting used to a couple of items, as I am a little busy running around at the moment. 
For right now, I guess, if anyoone has any other tips or tricks that can lend a hand that would be great. Though, I feel this little twinge of conflict in me as I miss the simplicity of Gnome, but love the beauty of KDE. 
Thanks again everyone
AndyP79

---

### Post by david_ally on 2010-10-11
I think it is important that we just try and make things simpler. Let's leave what is simple and working alone while improving on features.

There is just no way to switch between gdm and kdm on 10.04, not even in the login screen under super user access.

Please can we get a fix for this?

Thank you

---

