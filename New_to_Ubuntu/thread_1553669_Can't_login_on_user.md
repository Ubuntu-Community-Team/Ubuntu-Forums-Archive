---
title: "Can't login on user"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by elobee on 2010-08-15
Hello,
I installed ubuntu a couple of days ago after I had formated my computer and have messed around with it quite alot since then trying to learn it and it has gone pretty well without too many problems on the way. When I recently tried to start I got to the login screen but not further ahead. I rebooted a couple of times but it didn't go any better. What's happening is that when I press my user to login it starts loading, the screen gets black for a sec and then it returns to it's original state. If i click on my user again same thing happens again.
 
On one reboot I noticed a line before the Ubuntu loading screen appears that said something about something missing but I didn't see it long enough to memorize it and it havn't appeared after that one time.
 
So now I have to questions:
How do I access safe mode and most important; any idea's what's going on and how do I fix it?
 
I have ubuntu 10.04.
 
Thanks and btw, I gotta say I really like Ubuntu.

---

### Post by sandyd on 2010-08-15
> **elobee said:**
> Hello,
I installed ubuntu a couple of days ago after I had formated my computer and have messed around with it quite alot since then trying to learn it and it has gone pretty well without too many problems on the way. When I recently tried to start I got to the login screen but not further ahead. I rebooted a couple of times but it didn't go any better. What's happening is that when I press my user to login it starts loading, the screen gets black for a sec and then it returns to it's original state. If i click on my user again same thing happens again.
 
On one reboot I noticed a line before the Ubuntu loading screen appears that said something about something missing but I didn't see it long enough to memorize it and it havn't appeared after that one time.
 
So now I have to questions:
How do I access safe mode and most important; any idea's what's going on and how do I fix it?
 
I have ubuntu 10.04.
 
Thanks and btw, I gotta say I really like Ubuntu.
xorg problem.

when you get to the login screen, press alt-f1 and login.
post the output of ```

cat ~/.xsession-errors
```

---

### Post by elobee on 2010-08-15
alt f1 made nothing happen, but ctrl alt f1 worked, or have I done something wrong then?
 
anyway,
cat ~/.xsession-errors gives this:
 
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=sv_SE.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/etc/gdm/Xsession: Beginning session setup...
.: 34: Can't open /home/**user**/.profile
```

---

### Post by sandyd on 2010-08-15
try "touch ~/.profile"

---

### Post by elobee on 2010-08-17
Been away so havn't been able to investigaste this more until today

That command makes nothing happen

---

### Post by silverglade00 on 2010-08-17
That command creates a blank hidden file called .profile in your home directory. Carlee suggested it in order to help xorg find the file it is looking for here:

```
.: 34: Can't open /home/user/.profile
```

---

### Post by elobee on 2010-08-17
Still get *.: 34: Can't open /home/elobee/.profile* when running *cat ~/.xsession-errors*

---

### Post by elobee on 2010-08-17
After getting help from the #ubuntu-beginners channel (Thanks Phillinux and Hobgoblin) the problems seems to be that .profile is owned by 1000:1000 and not by me. Something called chroot was maybe needed.

So can anyone help me with solving this problem by chroot or maybe some other way?

Edit: apparantly it was owned by me when checking in the text mode.

Please, anyone know what to do?

Edit2: **What I can say is that the .profile actually exists and contains exactly the data it should contain, so what could be the problem?**

---

### Post by dagdeniz on 2010-08-17
I'm not an expert but what is owned by 1000:1000 should be owned by elobee, too; because 1000 should be your uid ("nano /etc/group" and you'll see the line "elobee: x :1000:"). I mean, I'm not sure you're going on the right direction by thinking about permissions. If you're right, setuid might solve the problem: 
```
sudo chmod +s /home/elobee/.profile
```I don't know, maybe worth trying? 
edit: ": x" without a space makes angry smiley ;)
edit2: ah, you can't login. with a live cd maybe?

---

### Post by elobee on 2010-08-17
I have logged in from the usb I installed ubuntu but the only thing I could acomplish from that was stating that the .profile actually is there and has the correct data in it.

And as stated above it turned out .profile in fact was owned by me.

I run that command u wrote from the CTRL ALT F1 terminal but it didn't change anything.

---

### Post by sandyd on 2010-08-17
hmm.. don't know what .profile is for.
I don't have one...

---

