---
title: "Trapped in an endless chain of windows; no way out."
date: 2009-04-04
forum: New to Ubuntu
---

### Post by icyest on 2009-04-04
Okay, I finally managed to get a screenshot of this annoying pop-up I keep dealing with:
[http://img135.imageshack.us/img135/9703/screenshot4t.png](http://img135.imageshack.us/img135/9703/screenshot4t.png)
[[IMG]http://img135.imageshack.us/img135/9703/screenshot4t.th.png[/IMG]](http://img135.imageshack.us/my.php?image=screenshot4t.png)

I had to execute a delayed shot to even get this because this dialog box negates all of my commands and forces me to either enter text or click deny. This thereby locks my desktop. 

Huge problem: I can click 'deny,' but it will just pop up again immediately.
It just pops up every time I turn on my computer.

This is driving me INSANE! I hate these sort of linux problems! I've had it for weeks! I'm so sorry but I just can't fathom why they would invent something like this!

---

### Post by Didius Falco on 2009-04-05
> **icyest said:**
> Okay, I finally managed to get a screenshot of this annoying pop-up I keep dealing with.

Huge problem: I can click 'deny,' but it will just pop up again immediately. It just pops up every time I turn on my computer.

This may seem like a silly question, but have you tried typing in the password instead of clicking "deny"? Does it work?

If so, it sounds like what's bothering you is having to type it in every time you boot up.

Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1101618](http://ubuntuforums.org/showthread.php?t=1101618)


I've not run into this problem, so I can't vouch for the solution offered, but it seems to have others...

---

### Post by linuxuser21 on 2009-04-05
Did you get it after you installed something?  Btw, just press the Print Screen button on your keyboard for a screenshot.

---

### Post by -kg- on 2009-04-05
Have you tried entering your password and clicking, "OK"?

I think that network manager controls access to networks, which I believe would include access to your modem through ethernet or wireless.

---

### Post by pbpersson on 2009-04-05
> **linuxuser21 said:**
> Btw, just press the Print Screen button on your keyboard for a screenshot.

OK - that is a new one :o

---

### Post by linuxuser21 on 2009-04-05
> **pbpersson said:**
> OK - that is a new one :o

Yeah, but I just realized he can't do it if he has a password pop-up thing though.  lol.

---

### Post by icyest on 2009-04-06
> **Didius Falco said:**
> This may seem like a silly question, but have you tried typing in the password instead of clicking "deny"? Does it work?

If so, it sounds like what's bothering you is having to type it in every time you boot up.

Take a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1101618](http://ubuntuforums.org/showthread.php?t=1101618)


I've not run into this problem, so I can't vouch for the solution offered, but it seems to have others...

This will not work. Entering a password has the same effect as 'deny' it just pops up again, and again, and again.


Screenshot button is nullified.

---

### Post by Mark Phelps on 2009-04-06
This happened to me one day when I went to connect to a wireless network. 
 
Turns out that I had changed my password in Ubuntu since I had originally installed it.  The popup box wants the password you assigned when you ORIGINALLY installed Ubuntu, not the password you're using today.

Fortunately, I was able to remember my original password.

If you haven't changed from the original password, then this is not the same problem I experienced.

---

### Post by MockY on 2009-04-06
One of many reasons why I refuse to use NetworkManager.
Install Wicd and your problem disappears.

---

### Post by icyest on 2009-04-06
> **MockY said:**
> One of many reasons why I refuse to use NetworkManager.
Install Wicd and your problem disappears.

What's a network manager? I wasn't aware that you even need a software program to see your networks. All I know is that you plug your computer into an Ethernet jack or wireless, and it just works.

I don't know much about computer science by the way, so you're going to kind of have to slow down. I don't even know how to use a network manager; however, the interface of the previous Ubuntu 8.04 internet thingy was much simpler and easier to understand.

Also, I wasn't aware that you can even change your password. I've just been using the same one. How does a password error like this even occur Mark Phelps?

---

### Post by freak42 on 2009-04-06
ok you might want to delete the default keyring as shown here:
[http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/](http://ubuntu-tutorials.com/2007/07/06/clearing-or-resetting-the-gnome-keyring/)

however keep in mind that all passwords saved in there (wlan, nautilus network shares and others) might get lost.

if your x session is not usable because of the password window you can press ctrl-alt-f2 .. then login with your username and pw and then type:
```
rm ~/.gnome2/keyrings/default.keyring
```

or maybe the safer option which just moves/renames the file
```
mv ~/.gnome2/keyrings/default.keyring ~/.gnome2/keyrings/default.keyring.backup
```

then after you re-login your xsession nm-applet might ask you for your wlan password again.. you then can set an empty keyring password.. so you don't have to type it in everytime (this is of course somewhat insecure if others have access to your machine)

hth

---

