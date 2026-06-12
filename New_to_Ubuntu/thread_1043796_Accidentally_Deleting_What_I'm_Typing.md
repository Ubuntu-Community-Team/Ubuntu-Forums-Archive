---
title: "Accidentally Deleting What I'm Typing"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by ziegegeist on 2009-01-18
I apologize if this has been answered elsewhere. I keep getting this thing pop up that asks me if I want to undo what I'm typing. There are other things like it, too. If I'm typing fast and don't catch it, it deletes everything I've typed. It's really frustrating. How can get this to stop? Thanks in advance! -Joel

---

### Post by mike2357 on 2009-01-18
Could you be a little more specific as to what's going on?  What application are you using?

---

### Post by ziegegeist on 2009-01-18
Sorry. It seems to happen anywhere I am entering text: in any of the Open Office applications, and in Mozilla. Undo, cut, copy, paste, select all, languages, check spelling, and so on. It could be something I'm accidentally doing with my hands.

---

### Post by Kellemora on 2009-01-18
HI Zieg

It SOUNDS LIKE, you are using a laptop with a touch pad and the cuff of your shirt or the heel of your palm is touching it.

If not that, check to see that you don't have the INSERT key Activated!

TTUL
Gary

---

### Post by handydan918 on 2009-01-18
> **ziegegeist said:**
> Sorry. It seems to happen anywhere I am entering text: in any of the Open Office applications, and in Mozilla. Undo, cut, copy, paste, select all, languages, check spelling, and so on. It could be something I'm accidentally doing with my hands.
Like hitting the DEL key?

---

### Post by ziegegeist on 2009-01-18
I must just be accidentally touching something, I guess. It is a laptop. It doesn't seem to happen with this computer when I switch to Vista. I'll see if I can tun the sensitivity down or something like that. Anyway, thanks again.

---

### Post by ziegegeist on 2009-01-18
Fortunately this keyboard has the delete key well out of my reach :)

I believe it must be the touch pad. I will see if I can figure out how to turn off that little menu except when I touch the right button.

---

### Post by stoogiebuncho on 2009-01-18
If you want to disable the "clicking" or "tapping" on your touchpad, simply do the following:

Open your xorg.conf file:
```
sudo gedit /etc/X11/xorg.conf
```

Find the section for your touchpad.

Add a line that says:

```
Option "TapButton1" "0"
```

Save.  You may have to restart for this to take effect, I can't remember.

---

### Post by ziegegeist on 2009-01-19
Worked like a charm! Many thanks!

---

### Post by theozzlives on 2009-01-19
I was going to say disable the click

---

