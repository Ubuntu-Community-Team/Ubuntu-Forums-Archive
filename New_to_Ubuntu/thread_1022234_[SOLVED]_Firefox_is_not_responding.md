---
title: "[SOLVED] Firefox is not responding"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by greenleaves123 on 2008-12-26
OK, please forgive my ignorance, but I really don't know a thing about Ubuntu. I bought a Dell Inspiron Mini 9 and it came with Ubuntu. I only know how to use the graphical inferace.

I tried searching for this problem, but I can't find my exact problem.

OK, I don't know if this had anything to do with it, but my netbook overheated today. I had it on hiberation and closed the screen. I didn't know it was going to overheat so much. I took a bath, came back to find I could have burned the house down, it was so hot. 

Everything seemed to work fine after this overheating incident.

Then after a couple of hours, Firefox's scrolling became very slow. I couldn't click on the tabs or file or anything. When I minimize and maximize the browser, there is just an empty shell that comes up, just the outline of it. I can't close or exit Firefox either.

I've tried turning off the netbook, waiting a bit then turning it back on and the same thing happens. I did this a few times, the same thing happens.

The other stuff seems to work OK. I can use the other applications OK, it's just Firefox that is messed up.

Please help. I tried calling Dell technical support and they don't know anything about Ubuntu.

Please make your instructions easy enough for a child to understand. I am technologically challenged. LOL

---

### Post by moredhel on 2008-12-26
could you possibly run firefox through terminal and copy/paste what it says?

To open terminal:

Applications > Accessories > Terminal

then just type:

firefox

see if it says anything odd looking. Even if it doesn't, it till can't hurt to paste it!

---

### Post by greenleaves123 on 2008-12-26
OK, I opened up the terminal, I think.... Is it a big white screen that looks like a notepad??

It says: 

jenny@jenny:~$

I typed in firefox and hit enter, nothing happened.

---

### Post by kansasnoob on 2008-12-26
The first thing I would do is set up some sort of temp monitoring. I use computertemp. You can just go to Applications > Accessories > Terminal and:

```
sudo apt-get install computertemp
```

Then right click on whichever panel (top or bottom system tray) you'd like to add it to, click on Add to panel, and scroll to Computer Temperature Monitor, then select to install it. Once you see it in the panel right click the applet and select Preferences.

I set mine to read as so:

[ATTACH]97677[/ATTACH]

Then we'll see about Firefox! We don't want to fry the whole puter!

---

### Post by ercferret18 on 2008-12-26
if nothing works with firefox, you might want to try to reconfigure it. just type, "sudo dpkg-reconfigure firefox"

---

### Post by kansasnoob on 2008-12-26
I should have added that I have a secondary reason for trying to install computertemp. Quite simply to see if you still have internet connectivity!

---

### Post by ercferret18 on 2008-12-26
> **kansasnoob said:**
> I should have added that I have a secondary reason for trying to install computertemp. Quite simply to see if you still have internet connectivity!

hmm... well i guess that could be the problem too...

---

### Post by namdung on 2008-12-26
> **greenleaves123 said:**
> OK, I opened up the terminal, I think.... Is it a big white screen that looks like a notepad??

It says: 

jenny@jenny:~$

I typed in firefox and hit enter, nothing happened.

Your Firefox might have crashed. Try reinstalling.

Go to *System-->Admin-->Synaptic Package Manager*. You'll be asked to enter ur default password.

Search for *Firefox*. Look out for *firefox-3.0* or something similar. If it's checked, uninstall it by right click *Mark for complete removal*. This will remove all dependencies. Click *Apply* on the menu bar to complete the process.

Now repeat the same thing now but this select *Mark for installation*.

I hope I've made this simple for u to understand. Do write for further clarifications.

---

### Post by kansasnoob on 2008-12-26
> **ercferret18 said:**
> if nothing works with firefox, you might want to try to reconfigure it. just type, "sudo dpkg-reconfigure firefox"

I'm curious what:

```
gksudo firefox
```

Would do?

I think you have a good idea though! My next thought is that Flash may have caused the original overheating prob so I'd immediately install flashblock.

I've personally fallen in love with Ubuntuzilla!

[http://ubuntuzilla.wiki.sourceforge.net/?f=print](http://ubuntuzilla.wiki.sourceforge.net/?f=print)

---

### Post by greenleaves123 on 2008-12-26
OK, I put in the sudo command and got the temperature monitoring application, but I don't know where to right click to add it. Maybe my graphical inferace is different from yours. I have this little house icon at the very top lef and the Ubuntu icon right next to it. On the very top there is this bar that has my opened applications, kind of like what windows has at the bottom. Then in the top there is this bar with some icons, Entertainment, Games, Productivity, Learn and Web. There is a giant plus symbol at the right end of the bar.

I don't know how to open the temperature monitoring application.

---

### Post by ercferret18 on 2008-12-26
right click on either the top or bottom panel, they are those bars at the top and bottom that have menu, open windows, time etc... and click add to panel

---

### Post by kansasnoob on 2008-12-26
> **greenleaves123 said:**
> OK, I put in the sudo command and got the temperature monitoring application, but I don't know where to right click to add it. Maybe my graphical inferace is different from yours. I have this little house icon at the very top lef and the Ubuntu icon right next to it. On the very top there is this bar that has my opened applications, kind of like what windows has at the bottom. Then in the top there is this bar with some icons, Entertainment, Games, Productivity, Learn and Web. There is a giant plus symbol at the right end of the bar.

I don't know how to open the temperature monitoring application.

"Then in the top there is this bar with some icons, Entertainment, Games, Productivity, Learn and Web. There is a giant plus symbol at the right end of the bar."

Well try right clicking an open area of that bar or maybe the +. I'm not sure either with specialized desktops.

---

### Post by sayems on 2008-12-26
killall firefox

---

### Post by kansasnoob on 2008-12-26
> **namdung said:**
> Your Firefox might have crashed. Try reinstalling.

Go to *System-->Admin-->Synaptic Package Manager*. You'll be asked to enter ur default password.

Search for *Firefox*. Look out for *firefox-3.0* or something similar. If it's checked, uninstall it by right click *Mark for complete removal*. This will remove all dependencies. Click *Apply* on the menu bar to complete the process.

Now repeat the same thing now but this select *Mark for installation*.

I hope I've made this simple for u to understand. Do write for further clarifications.

We have not asked what version of Ubuntu this is. In 8.10 that would break a lot of stuff!

---

### Post by ercferret18 on 2008-12-26
i think you could also try (if you don't care about your bookmarks, history, passwords etc..) to start firefox with "firefox -ProfileManager" in a terminal, then delete the profile and create a new one. That might stop all the crashing.

---

### Post by greenleaves123 on 2008-12-26
OK, I did the uninstall, reinstall thing and also the gksudo thing.

The uninstall, reinstall made firefox work again! Except I lost all my bookmarks. Oh well, I didn't have too many. 

Thanks so much, now I hope everything is fixed. Let me try to figure out how to get the temp. monitor up and running...

---

### Post by ercferret18 on 2008-12-26
> **greenleaves123 said:**
> Let me try to figure out how to get the temp. monitor up and running...

yeah, that would be a good idea. good thing you got firefox to work.

---

### Post by greenleaves123 on 2008-12-26
OK, I figured out that I can switch to the classic Ubuntu mode. I did that and figured out how to add the temp. monitor. It says: TZ01: 44*C. Is that good or bad?

---

### Post by greenleaves123 on 2008-12-26
I just want to thank all of you, moredlhel, kansasnoob, ercferrect18, namdung, sayems.

Thanks for helping me out. Dell wasn't helpful at all. Thanks so much!

How if only I can figure out how to make this thread as solved?

---

### Post by ercferret18 on 2008-12-26
its at the top, under thread tools

---

### Post by kansasnoob on 2008-12-26
> **greenleaves123 said:**
> OK, I figured out that I can switch to the classic Ubuntu mode. I did that and figured out how to add the temp. monitor. It says: TZ01: 44*C. Is that good or bad?

Look back at my previous screenshot.

Since I'm used to Fahrenheit I use it! I also select text + graphic, just because I like it that way.

Basically anything more than 5 degrees above ambient temp makes me wonder what's running. The first thing I look at is System > Administration > System Monitor under the "Processes" tab.

Basically I've found Flash to be a killer so I always install "flashblock". Some prefer mozilla-noscript. Some like both, but either cuts down on cpu usage but should not interfere with what you want to use flash for!

---

### Post by sportscrazed2 on 2008-12-26
that sounds more like a hardware problem if it's overheating while in suspend.

---

