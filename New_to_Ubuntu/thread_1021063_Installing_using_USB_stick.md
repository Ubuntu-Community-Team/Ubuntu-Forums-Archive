---
title: "Installing using USB stick"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by mercenary10 on 2008-12-24
I used this method: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) (the UNetBootin one).

I prepared the USB on my desktop, since I had ubuntu downloaded there, and tried to install it on my laptop, but it isn't going as planned. When it boots up, I get a menu with three options, Default, Help, and OEM. I click default, see the ubuntu loading screen, but then I get to this screen that shows "ubuntu@ubuntu $~". It just sits there, waiting for my input, but I have no idea what to do, lol. 

Any help is appreciated, thanks in advance.

---

### Post by sintacto on 2008-12-24
try
"startx"
let me know what hapens
is there a hard drive for swap space?
how much ram do you have?
"dmesg"will tell you some errors sometimes is handy.

---

### Post by mercenary10 on 2008-12-24
> **sintacto said:**
> try
"startx"
let me know what hapens
is there a hard drive for swap space?
how much ram do you have?
"dmesg"will tell you some errors sometimes is handy.

I tried it with a CD this time, got to the ubuntu menu, and it still took me to that silly command prompt with "ubuntu@ubuntu - whatever". No matter what I chose, try ubuntu without any change, or simply install ubuntu, it took me to the command prompt.

When I entered "startx", nothing happened. At the end of the wall of text, it gave me a "Fatal server error: no screens found". Also, I have 3GB of RAM.

---

### Post by TBomBM3879 on 2008-12-24
In that silly box with the [email]ubuntu@ubuntu...type[/email] startx and press enter and tell us what happens.

---

### Post by mercenary10 on 2008-12-24
> **TBomBM3879 said:**
> In that silly box with the [email]ubuntu@ubuntu...type[/email] startx and press enter and tell us what happens.

[QUOTE=mercenary10]When I entered "startx", nothing happened. At the end of the wall of text, it gave me a "Fatal server error: no screens found". Also, I have 3GB of RAM.[/QUOTE]

;)

---

### Post by TBomBM3879 on 2008-12-25
sorry didn't see that edit.

try

```
sudo dpkg-reconfigure xserver-xorg
```

if that doesn't work

```
sudo nano /etc/X11/xorg.conf
```

Tell us what the monitor and screen sections read

---

