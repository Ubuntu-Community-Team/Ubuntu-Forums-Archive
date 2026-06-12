---
title: "Toolbar display"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by Revjohn on 2010-10-19
Greetings. 

New to Kubuntu.  

Question I have... running Kubuntu on my desktop and my display is great.  Wonderful.  Everything looks right.

Installed Ubuntu 10.10 on my laptop (actually Kubuntu 10.4 then upgraded), and getting a weird display, or different display for some of my tool bar.  I have attached a screen shot.  

Dolphin has the display like I am used to, and then you will see in Firefox, how the tool bars are displaying... kind of in a 3D (GTK?) kind of display... just looks bad, and not uniform with other displays.  Most applications display like this... Open Office, etc. 

How do I go about changing this display?  I find it strange that some windows look one way, and other windows have a different look all together.

Thanks!

John

---

### Post by lovinglinux on 2010-10-19
That's because Firefox uses GTK instead of QT. You need to install [qtcurve](apt:qtcurve), then go to "System Settings >> Appearance >> GTK + Appearance" and select QtCurve and apply. Restart Firefox to see the changes.

---

### Post by Revjohn on 2010-10-19
Thanks.  Tried it but no luck.

Applied qtcurve, and no change.  

It is also not only in Firefox and Thunderbird.  

Some display this way and others don't.  

Synaptic Package Manager displays this way, but Dolphin doesn't.  Konqueror doesn't but OpenOffice does.  

Thanks for the suggestion.  

Any other ideas?

Thanks again!

John

---

### Post by lovinglinux on 2010-10-19
> **Revjohn said:**
> Thanks.  Tried it but no luck.

Applied qtcurve, and no change.  

It is also not only in Firefox and Thunderbird.  

Some display this way and others don't.  

Synaptic Package Manager displays this way, but Dolphin doesn't.  Konqueror doesn't but OpenOffice does.  

Thanks for the suggestion.  

Any other ideas?

Thanks again!

John

Dolphin, Konqueror  are KDE applications.  Synaptic doesn't show because is owned by root. To fix that, do this:

```

rm -f ~/.gtkrc-2.0
cp ~/.gtkrc-2.0-kde4 ~/.gtkrc-2.0
sudo cp ~/.gtkrc-2.0 /root/.gtkrc-2.0
```

---

### Post by Revjohn on 2010-10-19
says that it Can't find directory or file.  

Not sure what I am doing wrong, but acts like it doesn't exist.

Checked different places to start, etc... still no luck.

Thanks for your help and patience! 

John

---

### Post by lovinglinux on 2010-10-19
> **Revjohn said:**
> says that it Can't find directory or file.  

Not sure what I am doing wrong, but acts like it doesn't exist.

Checked different places to start, etc... still no luck.

Thanks for your help and patience! 

John

Apply the QtCurve settings again and post the output of these commands:

```
file ~/.gtkrc-2.0
```

```
file ~/.gtkrc-2.0-kde4
```

---

### Post by Revjohn on 2010-10-19
Well, I went back and installed packages that I thought had already been installed, and then did your steps outlines above...

And it works.  

Thanks for your help.  Amazing what stepping back and reworking the problem gets done!

So this leads to one more question... how does one mark this thread as SOLVED? :)

John

---

### Post by lovinglinux on 2010-10-19
> **Revjohn said:**
> Well, I went back and installed packages that I thought had already been installed, and then did your steps outlines above...

And it works.  

Thanks for your help.  Amazing what stepping back and reworking the problem gets done!

So this leads to one more question... how does one mark this thread as SOLVED? :)

John

You are welcome.

Click the "Thread Tools " menu on the top of the thread.

---

