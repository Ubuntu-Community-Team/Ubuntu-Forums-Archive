---
title: "Firefox button in Ubuntu"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by Ctulhu on 2011-04-05
Something puzzles me about FF4 in Ubuntu (as opposed to Win7): In both OSs, I have the following settings: Show Navigation Bar, show StumbleUpon Bar, show Omnibar in URL, Tabs on Top. However, when I have only one tab open, then

- in Win7, the Firefox main button is visible in the top left next to that one tab, which is what I want;
- in Ubuntu, the Firefox main button is not visible. If I want to access its functions, I either have to open a new tab or have the Menu bar there permanently?

What am I doing wrong?

---

### Post by LowSky on 2011-04-05
Sorry i might be confused but

In Ubuntu Firefox

at the top go to View > Toolbars > Uncheck Menu Bar. and the new firefox will be in the corner

see image...

---

### Post by Ctulhu on 2011-04-05
Well, I tried

> at the top go to View > Toolbars > Uncheck Menu Bar.

and I tried right-clicking somewhere up there and unchecking the Menu Bar thing, but it doesn't happen; cf. attached <Screenshot1.png>. Only if I get at least one other tab does it show up; cf. attached <Screenshot1.png>.

---

### Post by beew on 2011-04-05
> **Ctulhu said:**
> Well, I tried

> at the top go to View > Toolbars > Uncheck Menu Bar.

and I tried right-clicking somewhere up there and unchecking the Menu  Bar thing, but it doesn't happen; cf. attached <Screenshot1.png>.  Only if I get at least one other tab does it show up; cf. attached  <Screenshot1.png>.

Well which Ubuntu are you running? Maybe you get the global menu (if you have upgraded to Ubuntu 11.04) which is on the top of the screen.

---

### Post by Ctulhu on 2011-04-05
Nope, it's 10.10.

---

### Post by beew on 2011-04-05
Are you going full screen?

---

### Post by Ctulhu on 2011-04-05
No, not full screen, but it happens regardless of whether the window is maximized or not.

---

### Post by beew on 2011-04-05
Try this do ALT+F2 and then in the box type ```
metacity --replace 
```

---

### Post by Ctulhu on 2011-04-05
Hm, will that interfere w/ compiz? Will try ...., thx.

---

### Post by Ctulhu on 2011-04-05
Nope, doesn't do it either :-|

---

### Post by beew on 2011-04-05
Then I am not sure what happens. I thought maybe the window decorator somehow was disabled so you lost the menu.

---

### Post by Ctulhu on 2011-04-05
Thx for trying. Any more ideas, anyone?

---

### Post by thouartsimple on 2011-04-05
I am using tabmix plus and I recreated this issue.  If you go to TabMix Plus options, display, then tabbar and have "hide the tab bar if you only have one tab open", then the Firefox button disappears.  Change it to NEVER hide the tab bar and you should be OK.

---

### Post by Ctulhu on 2011-04-05
Ah, that does it. Weird that that does it when I don't recall having changed stuff around. Still, nice, thanks!

---

### Post by thouartsimple on 2011-04-05
No problem, glad it worked! =D

---

### Post by Kixtosh on 2011-04-06
Glad you found a solution. Please mark thread as solved!

It's on the top right, above the first post, in the **[COLOR=DarkRed]Thread Tools[/COLOR]**.

---

