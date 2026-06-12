---
title: "Gksudo not working..."
date: 2009-07-28
forum: New to Ubuntu
---

### Post by Sardonism on 2009-07-28
The password prompt comes up just fine, and the authentication runs smoothly, but when it's time for the payload to pop up, nothing happens.  Since I'm setting up my system right now and I don't want to use sudo for graphical applications, this is a big problem for me.

I think that I started experiencing this issue right after I installed vmware player, though I can't be sure that this is the issue because I'm still fairly new to linux.

Help!

---

### Post by llamabr on 2009-07-29
does sudo work?  What errors do you see?

---

### Post by credobyte on 2009-07-29
> **Sardonism said:**
> The password prompt comes up just fine, and the authentication runs smoothly, but when it's time for the payload to pop up, nothing happens. 
 
What exactly you are trying to run ? What you mean by "payload" ?

---

### Post by vinutux on 2009-07-29
Do tou mean Alt+f2 gksu....?

---

### Post by QIII on 2009-07-29
The command is gksu, not Gksu.

gksu <> Gksu

But the OP wants to respect the sudoers, so should use gksudo, I believe.

---

### Post by llamabr on 2009-07-29
> **QIII said:**
> The command is gksu, I believe.  Not Gksu.

gksu <> Gksu

Those are different apps that do different things.  The OP seems to be absent, so I'm not sure which problem he/she's facing.

---

### Post by vinutux on 2009-07-29
> **QIII said:**
> The command is gksu, not Gksu.

gksu <> Gksu

But the OP wants to respect the sudoers, so should use gksudo, I believe.
[COLOR="Red"]
oh......sorry[/COLOR]

---

### Post by QIII on 2009-07-29
> **llamabr said:**
> Those are different apps that do different things.  The OP seems to be absent, so I'm not sure which problem he/she's facing.
 
Gksu does not work in the bash shell, as far as I know.  gksu does.  I could be wrong, of course.  After 50 years you start to get the idea that the more you learn the less you know.

Edit:  S'alright!  I made that edit after you posted.  Timing on forums is a bit of a problem...

---

### Post by Sardonism on 2009-07-29
Sorry guys, I was a little busy...

1.  Yes, sudo works.  When i try gksudo in a terminal, it behaves as normally up until after I supply the credentials.  I get no error messages and still no windows popping up.

2.  I made a typo on the capitalization.  I'm using the lower case gksudo, no typing errors there.  Sorry for the misinformation.

3.  When I say the payload, I mean a window of some kind popping up after the password prompt...  Like Nautilus or something.   Instead, nothing happens.

Also, with all of the said, synaptic will work, which confuses the hell out of me because I don't think it should if it requires gksu.  Any reason why this works but nothing else does?

---

### Post by QIII on 2009-07-29
Rats!

If it's not the capitalization, I'm as flummoxed as you are.

One of those situations where you want to use

```
gksudo DoWhatTheHeckITellYouYouStupidMindlessMachine
```

Won't do anything, but it sometimes feels good.

Hopefully someone will come along with some simple answer that will make fools of all of us...

---

### Post by Sardonism on 2009-07-29
Before I head off to bed I will try and explain in more detail my situation so we can narrow down the cause a bit more.

I reinstalled yesterday, switching from the 32 bit version of Jaunty to the 64 bit for various performance reasons.  When I was on my 32 box, I used an applet on my panel for quick and easy gksudo work , where I could just drag and drop what I needed root access for (I used gksudo “gnome-open %u” in the applet's command).  It worked well so I decided I wanted to use that again on my new 64 bit system.  And it worked great for a while, until I installed vmware player from a .bundle  (which I also used gksudo with because that's how I roll).  Although there were no noticable errors, following the installation my gksudo applet didn't work anymore.  So I tried gksudo nautilus in a terminal, failure.  I restarted the computer, failure.  I checked to see if gksu was present through synaptic and it was.  So I spent the next few hours googling it trying to find a fix.

I don't know what the problem is.  It's probably some kind of stupidity on my part, but in any case, tommorrow I will remove vmware player and see if anything chages and put up the results here.  Hopefully someone more knowledgeable can provide insight for me by that time.

---

### Post by Sardonism on 2009-07-29
Update: removing vmware doesn't solve the problem.  :/

---

### Post by Sardonism on 2009-07-29
It's been fixed.  I had to edit my hosts file and redo the loopback hostname for gksudo to work in the terminal again.

As for the panel applet, the qoutes in the command were all screwed up and they are fixed now.  Thanks guys.

---

### Post by Tux+ on 2009-09-20
> **Sardonism said:**
> It's been fixed.  I had to edit my hosts file and redo the loopback hostname for gksudo to work in the terminal again.

As for the panel applet, the qoutes in the command were all screwed up and they are fixed now.  Thanks guys.

Could you explain how you fixed it please? The above means nothing to me.

---

