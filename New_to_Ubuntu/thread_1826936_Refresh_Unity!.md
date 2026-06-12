---
title: "Refresh Unity!"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by the-new-x on 2011-08-17
Hey guys, is there a way to restart unity, here is why:

[IMG]http://i1236.photobucket.com/albums/ff445/iareX/Screenshot-10.png[/IMG]

[IMG]http://i1236.photobucket.com/albums/ff445/iareX/Screenshot-9.png[/IMG]

So if anyone have a solution for this instead of restarting my laptop every time it happens, I would be grateful, thanks in advance!

---

### Post by Paqman on 2011-08-17
Hit Alt-F2 and type:
```
unity --reset
```

---

### Post by Frogs Hair on 2011-08-17
```
unity --reset
```
```
unity --reset-icons
```

---

### Post by the-new-x on 2011-08-17
but doesn't the command unity --reset also resets everything in unity, including the compiz settings and the pinned programs and all of the stuff!?

---

### Post by Frogs Hair on 2011-08-17
The command will reset all Unity settings to default . The icon command resets only the icons to default .

---

### Post by the-new-x on 2011-08-17
> **Frogs Hair said:**
> The command will reset all Unity settings to default . The icon command resets only the icons to default .
First of all, sorry it took me long to reply, having connection problems as usual, and is there something I can do to refresh and not to reset Unity, if so, please tell me!

---

### Post by Mjchopperboy on 2012-06-29
> **Paqman said:**
> Hit Alt-F2 and type:
```
unity --reset
```
Man, I spent hours customizing my Ubuntu. I wanted to refresh Ubuntu desktop so I put your command in Terminal. And I lost everything I'd ever done in Ubuntu. I'm really angry. Now, can anyone tell me how TO REFRESH UBUNTU. In windows, it's right click on desktop, and "refresh" button.

---

### Post by Grenage on 2012-06-29
> **Mjchopperboy said:**
> Man, I spent hours customizing my Ubuntu. I wanted to refresh Ubuntu desktop so I put your command in Terminal. And I lost everything I'd ever done in Ubuntu. I'm really angry. Now, can anyone tell me how TO REFRESH UBUNTU. In windows, it's right click on desktop, and "refresh" button.

Well as the following messages indicated, the reset command does.. reset unity.  What you're after is F5 (which also works in Windows), although seldom required.

---

### Post by poomerang on 2012-12-19
the answer is here: [http://askubuntu.com/questions/31849/how-do-i-restart-unity](http://askubuntu.com/questions/31849/how-do-i-restart-unity)

Press Alt + F2 and then run ```
unity
```. this will close and restart unity without affecting your settings - basically the same as logging out and in again.

it's probably too late now but at least the answer is public on this forum too :)

---

### Post by philinux on 2012-12-19
> **poomerang said:**
> the answer is here: [http://askubuntu.com/questions/31849/how-do-i-restart-unity](http://askubuntu.com/questions/31849/how-do-i-restart-unity)

Press Alt + F2 and then run ```
unity
```. this will close and restart unity without affecting your settings - basically the same as logging out and in again.

it's probably too late now but at least the answer is public on this forum too :)

Ubuntu 12.10
Alt F2 Unity crashed here. No launcher or top panel and windows top bar gone.

However after that I opened a terminal and used setsid unity. This restored the session mostly. It left xchat with no window controls. I had to quit it from the launcher and restart it. 

Second method from here [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

