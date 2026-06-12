---
title: "compiz and multiple desktops"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by hollowtd on 2009-02-09
I just put compiz on my computer on ubuntu 8.10. I can do the spinning cube and cylinder. How do I have multiple desktops open. For example, say I want to be chatting on here and then flip to another screen (ctrl+alt+ mouse hold down) and want to be playing black jack? And on another screen have skype uploaded and on another be working on a OpenOffice presentaion? Is this possible? I think it is. Thanks and totally new user so English is me mother tongue--as apposed to linux lingo yet. Cheers

---

### Post by unplugged23 on 2009-02-09
Yes!
In compiz under the general settings menu (or something similar) you can change the number of desktops you have open and working. Once you have your preferred amount open, you can open an application on one desktop and send it to another by right clicking on it and selecting the workspace you would like to send it to, or you could just open the program from the desktop you want it on.l

---

### Post by hollowtd on 2009-02-09
Thanks for that. Im under the general tab and see the button for show desktop under the "desktop size tab" It won't let me change it from one though? Is this it?

---

### Post by unplugged23 on 2009-02-09
If i remember correctly (am on slackware linux now so i cant double check) you should have to change tabs from the general menu at the top of the screen. then you should have 3 rows with a slider on them. one being horizontal desktop, another being vertical desktop, and another being number of desktops. I belive you just want to change the Horizontal desktop option to the number of desktops you would like and can leave everything else alone for now.

---

### Post by hollowtd on 2009-02-09
That worked great. Thanks for that. I'm not sure why the horizontal one works or what it does but that worked great. Gee, you guys are great help. 
Thanks again. Once I get good at this, I'll be able to help people out too. Cheers

---

### Post by unplugged23 on 2009-02-09
Great! Good Luck to you, and hopefully you will continue to have a great Ubuntu Experience!

---

### Post by hollowtd on 2009-02-09
Cheers and I absolutely love it so far. I love my mac too and have always hated MS. So this is great and thanks for the help again. Most appreciative.

---

### Post by cariboo on 2009-02-09
You can set the number of desktops at least two different ways. Right-click on the desktop switcher on the lower panel and select preferences, set the columns to the number you need. the second way is to open System-->Preferences-->CompizConfig Settings Manger, click the General Options button and select the Desktop Size tab, set the Horizontal Virtual Size to  the number of desktops you need.

Jim

---

### Post by hollowtd on 2009-02-09
Wow, that is great to know too. Thanks for that one too. Love the dog picture too. Thanks again.

---

### Post by unplugged23 on 2009-02-09
> **cariboo907 said:**
> You can set the number of desktops at least two different ways. Right-click on the desktop switcher on the lower panel and select preferences, set the columns to the number you need. the second way is to open System-->Preferences-->CompizConfig Settings Manger, click the General Options button and select the Desktop Size tab, set the Horizontal Virtual Size to  the number of desktops you need.

Jim

Yea, that is nice. I didn't know about that first way either. :)

---

### Post by Montblanc_Kupo on 2009-02-09
So here's something I've been wondering about... what does the "vertical virtual size" and "number of desktops" control? I can create vertical desktop rows... but I can't actually GO to any of them. How do you access these? I must be missing something simple...

---

### Post by unplugged23 on 2009-02-09
> **Montblanc_Kupo said:**
> So here's something I've been wondering about... what does the "vertical virtual size" and "number of desktops" control? I can create vertical desktop rows... but I can't actually GO to any of them. How do you access these? I must be missing something simple...

To go to the vertical desktops you can click on one of their icons in the bottom left. However, i've never been able to configure or figure out what the "number of desktops" does.

---

### Post by Montblanc_Kupo on 2009-02-24
> **unplugged23 said:**
> To go to the vertical desktops you can click on one of their icons in the bottom left. However, i've never been able to configure or figure out what the "number of desktops" does.

That won't work for Me... I can set the number of rows and collumns... but it will only allow Me to switch along the active row. I did find that by using the Expo feature... I could choose a new row.. but then I could only move along that row using the keyboard or click drag or switcher icons. *shrug* seems like either I'm missing something or it's missing some functionality.

---

### Post by yther on 2009-02-24
Along similar lines, I've been curious about something recently.  I can't actually *do it* because I had to disable compositing on my dual-head system for better video quality, but I'd still like to know.

On a two-monitor setup (dual outputs of same card, if it matters), is it possible to have multiple virtual desktops that operate *independently* on each monitor?  So, as opposed to running two different X sessions, I could mouse to the left one, flip desktops with "the cube" while the right screen stays put?

I realize I could simulate that by making everything on the right side "sticky" on all four desktops, but it wouldn't be the same.  :)  I don't even know if I'd find it particularly useful, but... sometimes you do things to see if you can!

So, anyone done that or know how I'd go about it?  If not, one of these days I'll experiment.

---

### Post by Montblanc_Kupo on 2009-02-24
Well... in the desktop cube settings there is a setting that asks how it should handle multiple screens... each on their own cube or on one big cube... I don't have multiple screens set up right now but that might be worth looking into.

---

### Post by yther on 2009-02-24
Awww, that sounds way too easy!  ;)

---

### Post by Bölvaður on 2009-02-24
> **yther said:**
> On a two-monitor setup (dual outputs of same card, if it matters), is it possible to have multiple virtual desktops that operate *independently* on each monitor?  So, as opposed to running two different X sessions, I could mouse to the left one, flip desktops with "the cube" while the right screen stays put?

umm... last time I checked it did not.

also:
development specially for multiple monitors in compiz has been dropped. so the only thing that will be stable is one big cube stretched over both monitors.

---

