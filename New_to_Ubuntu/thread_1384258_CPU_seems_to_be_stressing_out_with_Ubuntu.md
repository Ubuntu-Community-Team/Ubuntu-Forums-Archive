---
title: "CPU seems to be stressing out with Ubuntu"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by ThePinkWitch on 2010-01-18
I'm no expert but my CPU is constantly spiking to 100% and freezing my browser and windows. (I have a CPU monitor running) It seems to be under stress. When I open a program or Firefox especially. Firefox greys out for a few seconds. Emerald Theme manager greys out and locks up and stops responding. I don't seem to have the same problem when I run Windows. Any ideas what it could be? 

I have an old Acer SA80 with Intel 3.06 CPU, 2Gig RAM, Saphire X1650 Pro graphics if thats any help.

---

### Post by J V on 2010-01-18
linux gives apps more control over the CPU, if an app locks up it can freeze up the computer, which is why I have xkill on a keyboard shortcut...

flash is the main aggressor IME...

---

### Post by Kobalt on 2010-01-18
Hello,

Did you launch the System Monitor (Administration > System) to watch which particular program/process is eating up your CPU ?

---

### Post by Roger Allott on 2010-01-18
How many tabs do you have open on Firefox?

Firefox seems to be very resource hungry. You might like to consider Chrome or Chromium as an alternative.

---

### Post by ThePinkWitch on 2010-01-18
> **J V said:**
> linux gives apps more control over the CPU, if an app locks up it can freeze up the computer, which is why I have xkill on a keyboard shortcut...

flash is the main aggressor IME...

ok thanks. I'll look up xkill. :)

---

### Post by ThePinkWitch on 2010-01-18
> **Kobalt said:**
> Hello,

Did you launch the System Monitor (Administration > System) to watch which particular program/process is eating up your CPU ?

I have an info panel app which tells me what is using my CPU and all the stuff I have running in the background uses minimal but when I open something it sky rockets. Yes it is mainly Firefox, well I have just started using Swiftfox today. I have trouble with Emerald Theme manger greying out also. I usually only have one or two tabs open as well. Maybe my CPU is wearing out. It gets a bashing. Its on for at least 12hrs a day and I've had this machine for nearly 4 years :D

---

### Post by ThePinkWitch on 2010-01-18
> **Roger Allott said:**
> How many tabs do you have open on Firefox?

Firefox seems to be very resource hungry. You might like to consider Chrome or Chromium as an alternative.

I don't usually have a lot of tabs open, but I do have quite a few add ons. I'll check out Chrome. Thanks :)

---

### Post by eltama on 2010-01-18
As already suggested, flash is a resource hog, specially in linux. I use the addon flaskblock. It really improves the performance and memory consumption at the cost of just one more click when I really want to see a video. Addblock plus may also help.

Google's Chrome is also a good alternative. I find it very responsive, but it may use a bit more memory.

---

### Post by ThePinkWitch on 2010-01-18
I minimised Swiftfox and put System Monitor on and just watched it for about 10 mins. It constantly moves up and down. It moves between a low % and a mid number,  then spikes to 100% then goes down again. I can't see what app is causing it. Most stuff is sleeping except system monitor. The CPU seems to have ADHD :D (hyperactive)

---

### Post by Kobalt on 2010-01-18
OK.
Which Ubuntu version do you run, and what graphic card drivers do you use? You could also try disabling the Desktop effects to see if it has an impact.

---

### Post by J V on 2010-01-18
If you go to the proccesses tab and order by CPU descending you should see which proccess is using the CPU...

---

### Post by ThePinkWitch on 2010-01-18
> **Kobalt said:**
> OK.
Which Ubuntu version do you run, and what graphic card drivers do you use? You could also try disabling the Desktop effects to see if it has an impact.

I have Karmic 9.10 and the drivers were the ones provided by Ubuntu as when I go to the Hardware drivers page there are none installed. Another development this morning..when I logged on, the screen which gives you a choice of what OS to use I noticed there are 2 Ubuntu versions listed ( Linux2.6.31-17-generic and Linux2.6.31-14) and there is some sort of error message which flashes up but it's too fast to read. All I can catch is something is depreciated....yesterday I booted up and got an error message that some app had a problem and did I want to delete it which I did. All I could catch was this _TS client Applet and OAFIID:Gnome. I have ginen info on my computer in first post here. Thanks for your help :)

---

### Post by warfacegod on 2010-01-18
> **ThePinkWitch said:**
> I minimised Swiftfox and put System Monitor on and just watched it for about 10 mins. It constantly moves up and down. It moves between a low % and a mid number,  then spikes to 100% then goes down again. I can't see what app is causing it. Most stuff is sleeping except system monitor. The CPU seems to have ADHD :D (hyperactive)

Using System Monitor to watch our CPU consumption also uses a good amount of CPU. Instead type *top* into your Terminal and watch from there.

I had a similar issue a while ago with Firefox. Turned out to be an add-on called Ctrl-Fox. I removed it and no more CPU hijacking. You may also want to consider using Compiz or Metacity for a Theme Manager.

---

### Post by ThePinkWitch on 2010-01-18
> **J V said:**
> If you go to the proccesses tab and order by CPU descending you should see which proccess is using the CPU...

I went to Processes and there was one program which was constant obviously Sytem monitor and a couple that flashed on and off. It is xorg that flashes on and takes the CPU to 100%. Shouldn't the CPU run steady tho If programs are running and not go up and down. Whatever xorg is it comes on for a second and the CPU peaks to 100% and goes down again, but it's constantly going up and down even if I'm not doing anything. Is that normal?

---

### Post by warfacegod on 2010-01-18
> **ThePinkWitch said:**
> I went to Processes and there was one program which was constant obviously Sytem monitor and a couple that flashed on and off. It is xorg that flashes on and takes the CPU to 100%. Shouldn't the CPU run steady tho If programs are running and not go up and down. Whatever xorg is it comes on for a second and the CPU peaks to 100% and goes down again, but it's constantly going up and down even if I'm not doing anything. Is that normal?

You are describing almost exactly the same behavior I had. My best guess is that a Firefox add-on is the culprit here. To answer your question, no this not generally normal behavior. When you're idle your CPU should be about 5-10% roughly, with  the occasional little spike. I recommend you disable your FF add-ons one at a time to see if it's one of them stealling your CPU time.

---

### Post by ThePinkWitch on 2010-01-18
> **warfacegod said:**
> You are describing almost exactly the same behavior I had. My best guess is that a Firefox add-on is the culprit here. To answer your question, no this not generally normal behavior. When you're idle your CPU should be about 5-10% roughly, with  the occasional little spike. I recommend you disable your FF add-ons one at a time to see if it's one of them stealling your CPU time.

Ok thanks I'll try that. What is xorg? Any idea? oh and I'll try compiz. I'm using Emerald right now. :)

---

### Post by warfacegod on 2010-01-18
> **ThePinkWitch said:**
> Ok thanks I'll try that. What is xorg? Any idea? oh and I'll try compiz. I'm using Emerald right now. :)

Xorg is what runs your monitor, sort of. Compiz is fun.

---

### Post by ThePinkWitch on 2010-01-18
> **warfacegod said:**
> Xorg is what runs your monitor, sort of. Compiz is fun.

I have the cube and have got the skydome thing worked out and the top cap but can't work out how to get the bottom one with out turning on cube reflection and deformation. I like the rectangular cube not the spheric. It's pretty cool. So If I have compiz I shouldn't have Emerald as well? My machine is pretty messed up since I installed Ubuntu, I keep screwing things up :D I seem to have two versions of linux on here somehow. I get two to choose from when I boot up. Go figure. My monitor doesn't seem to be right either. I've had so many threads going everyone must scatter when they see my name :D Like... OMG NOT HER AGAIN!!

---

### Post by ThePinkWitch on 2010-01-18
"I recommend you disable your FF add-ons one at a time to see if it's one of them stealling your CPU time."

I disabled XMarks and its settled down heaps. It still spikes to 100% when I open anything up but it's just for a second. I'll see how it goes now. Thanks :)

---

### Post by audiomick on 2010-01-18
Hallo.
If you have time to read a bit
[http://en.wikipedia.org/wiki/Xorg](http://en.wikipedia.org/wiki/Xorg)

---

### Post by ThePinkWitch on 2010-01-18
> **audiomick said:**
> Hallo.
If you have time to read a bit
[http://en.wikipedia.org/wiki/Xorg](http://en.wikipedia.org/wiki/Xorg)

Hallo Michael :) I read that but it was just a bit like a jet taking off mate. Right over my head :D It was xorg tho that flashed on and made the CPU spike while I was watching, but I disabled an add on in Swiftfox and it does seem better.

---

### Post by audiomick on 2010-01-18
> **ThePinkWitch said:**
> Hallo Michael :) I read that but it was just a bit like a jet taking off mate. Right over my head :D 
No worries. Suffice to say that it is the bit between you and the nuts and bolts. It takes care of communicating your input (keybaord, mouse) to the computer and the output to you (monitor)

> It was xorg tho that flashed on and made the CPU spike while I was watching, but I disabled an add on in Swiftfox and it does seem better.
Who knows why...:) Anyway, fixed now. Glad to hear it:)

---

### Post by ThePinkWitch on 2010-01-18
> **audiomick said:**
> No worries. Suffice to say that it is the bit between you and the nuts and bolts. It takes care of communicating your input (keybaord, mouse) to the computer and the output to you (monitor)


Who knows why...:) Anyway, fixed now. Glad to hear it:)

Thankyou :)

---

### Post by warfacegod on 2010-01-18
> **ThePinkWitch said:**
> "I recommend you disable your FF add-ons one at a time to see if it's one of them stealling your CPU time."

I disabled XMarks and its settled down heaps. It still spikes to 100% when I open anything up but it's just for a second. I'll see how it goes now. Thanks :)

That is normal for opening apps. Don't sweat it. I must admit, I have seen your name rather frequently.

---

### Post by ThePinkWitch on 2010-01-19
" That is normal for opening apps. Don't sweat it. I must admit, I have seen your name rather frequently." 

I know, I keep screwing up :( 

I google a lot of stuff but sometimes I can't find the answer and sometimes the answer is too hard to understand for a Noob :D The scary thing is I have LOTS more questions :))))

---

### Post by warfacegod on 2010-01-19
> **ThePinkWitch said:**
> " That is normal for opening apps. Don't sweat it. I must admit, I have seen your name rather frequently." 

I know, I keep screwing up :( 

I google a lot of stuff but sometimes I can't find the answer and sometimes the answer is too hard to understand for a Noob :D The scary thing is I have LOTS more questions :))))

LOTS more questions is a good thing. It means you want to know and learn how to use your computer as opposed to it being a giant blinking beeping paper weight. Screwing up is fine. So that you know, I probably don't understand most of what you Google up either. Every person that ever has, is, or will use Linux is a noob to one degree or another.

Next time you want to get all :( about screwing up, just remember there are people here that are doing it on purpose:

[http://ubuntuforums.org/showthread.php?t=1379471]("http://ubuntuforums.org/showthread.php?t=1379471")

---

### Post by ThePinkWitch on 2010-01-19
> **warfacegod said:**
> LOTS more questions is a good thing. It means you want to know and learn how to use your computer as opposed to it being a giant blinking beeping paper weight. Screwing up is fine. So that you know, I probably don't understand most of what you Google up either. Every person that ever has, is, or will use Linux is a noob to one degree or another.

Next time you want to get all :( about screwing up, just remember there are people here that are doing it on purpose:

[http://ubuntuforums.org/showthread.php?t=1379471]("http://ubuntuforums.org/showthread.php?t=1379471")

LOL well that brightened up my boring evening :D I'll check back on that thread with a bourbon and popcorn :D I had to reinstall Ubuntu and windows three times in two weeks so I claim membership of the evil genius club heh.

---

### Post by PenguinInside on 2010-01-19
> **warfacegod said:**
> Using System Monitor to watch our CPU consumption also uses a good amount of CPU. Instead type *top* into your Terminal and watch from there.

I had a similar issue a while ago with Firefox. Turned out to be an add-on called Ctrl-Fox. I removed it and no more CPU hijacking. You may also want to consider using Compiz or Metacity for a Theme Manager.

Haha, I agree with that. GNOME System Monitor is often the highest CPU-consumer on my computer!

An alternative to top is htop. It's a lot more friendly, and you can simply change the sort criteria by clicking on the column headings. It runs in a terminal, though.

Click here from Firefox to install: [apt://htop]("apt://htop")

---

### Post by PenguinInside on 2010-01-19
> **ThePinkWitch said:**
> I went to Processes and there was one program which was constant obviously Sytem monitor and a couple that flashed on and off. It is xorg that flashes on and takes the CPU to 100%. Shouldn't the CPU run steady tho If programs are running and not go up and down. Whatever xorg is it comes on for a second and the CPU peaks to 100% and goes down again, but it's constantly going up and down even if I'm not doing anything. Is that normal?

The thing is, it's not really X that's the cause. The cause is Flash and Firefox. They, in turn, make X do the heavy lifting, which you see in System Monitor as X being a CPU hog.

Advice: Install Google Chrome. [http://www.google.com/chrome](http://www.google.com/chrome)
Also install [FlashBlock]("https://chrome.google.com/extensions/detail/gofhjkjmkpinhpoiabjplobcaignabnl"): 


Chrome's a lot faster than Firefox for some cases, and it handles JavaScript better, which is a majority of the web these days.

I have 13 Chrome windows open right now, with about 10 tabs in each. (For example, I opened about 10 or so threads from Ubuntu Forums from the Forum list.) Yet no Chrome process is taking more than 8% CPU. Many are taking 0%.

If you have a problem with CPU running chrome, just kill the Flash process. Do that either with the Chrome task manager. If you don't know how, just ask.

Once you kill Flash, CPU comes back to normal.

On Firefox, though, if I have just a single window open, things are OK. But if I have the amount open I normally have on Chrome or on Windows Firefox, CPU goes to 100%.

---

### Post by qyot27 on 2010-01-19
Since you're running 9.10, the notification panel applet can also cause excessive resource usage for some odd reason.  My Ubuntu install was nearly unusable for a couple-three weeks before I read that, took it off the panel, and voila, resource craziness solved (for the most part, anyway - Karmic is just a heftier beast in general; I miss the resource specs of Breezy, I really do).

---

### Post by ThePinkWitch on 2010-01-19
> **qyot27 said:**
> Since you're running 9.10, the notification panel applet can also cause excessive resource usage for some odd reason.  My Ubuntu install was nearly unusable for a couple-three weeks before I read that, took it off the panel, and voila, resource craziness solved (for the most part, anyway - Karmic is just a heftier beast in general; I miss the resource specs of Breezy, I really do).

Thanks for that :) I'll take it off. I'll try a smaller app for the CPU monitor. Its handy tho because I like to keep an eye on how much is being downloaded and uploaded from the internet. I really like Firefox but from what you guys are telling me I think I'll have to try a different browser. I'll miss my add ons tho.

---

### Post by ThePinkWitch on 2010-01-19
> **PenguinInside said:**
> The thing is, it's not really X that's the cause. The cause is Flash and Firefox. They, in turn, make X do the heavy lifting, which you see in System Monitor as X being a CPU hog.

Advice: Install Google Chrome. [http://www.google.com/chrome](http://www.google.com/chrome)
Also install [FlashBlock]("https://chrome.google.com/extensions/detail/gofhjkjmkpinhpoiabjplobcaignabnl"): 


Chrome's a lot faster than Firefox for some cases, and it handles JavaScript better, which is a majority of the web these days.

I have 13 Chrome windows open right now, with about 10 tabs in each. (For example, I opened about 10 or so threads from Ubuntu Forums from the Forum list.) Yet no Chrome process is taking more than 8% CPU. Many are taking 0%.


If you have a problem with CPU running chrome, just kill the Flash process. Do that either with the Chrome task manager. If you don't know how, just ask.

Once you kill Flash, CPU comes back to normal.

On Firefox, though, if I have just a single window open, things are OK. But if I have the amount open I normally have on Chrome or on Windows Firefox, CPU goes to 100%.


I'll try Flash block and see if that helps..If not I'll try Chrome. Thanks for your help :)

---

### Post by ThePinkWitch on 2010-01-19
> **PenguinInside said:**
> Haha, I agree with that. GNOME System Monitor is often the highest CPU-consumer on my computer!

An alternative to top is htop. It's a lot more friendly, and you can simply change the sort criteria by clicking on the column headings. It runs in a terminal, though.

Click here from Firefox to install: [apt://htop]("apt://htop")

I clicked on that link and it said it needed a program to open but I didn't know what to do with it.

---

### Post by audiomick on 2010-01-19
> **ThePinkWitch said:**
> I clicked on that link and it said it needed a program to open but I didn't know what to do with it.

You can just confirm that and let it do it's stuff. It stumped me that first time I saw it too. What it wants it "apturl", which I think should be there.

from man ```
apturl
```
```

       apturl - graphical apt-protocol interpreting package installer

SYNOPSIS
       apturl [options...] <URL>

DESCRIPTION
       apturl  is  a simple graphical application that takes an URL 
(following the apt-protocol) as a command line option, parses it and
carries  out the  operations that  the URL describes
(that is, it asks the user if he wants the indicated packages to be
installed and if the answer is positive does so).
```

i.e. a thing related to the package manager that uses a url to go off and get something.

---

### Post by warfacegod on 2010-01-19
> **ThePinkWitch said:**
> LOL well that brightened up my boring evening :D I'll check back on that thread with a bourbon and popcorn :D I had to reinstall Ubuntu and windows three times in two weeks so I claim membership of the evil genius club heh.

Sinister laughing and cackling are a requirement for enlisting.


Be aware that Firefox has better integration with Ubuntu than Chrome does. And that Google has never been too discriminatory about your privacy.

---

### Post by audiomick on 2010-01-19
This
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)
might help you get firefox to behave better.

---

### Post by warfacegod on 2010-01-19
Indeed, Pink Witch lady. audiomick has posted an excellent thread. I post it for people often. I am ashamed to admit that I did not think to post it here. (More really that audiomick beat me to it.)

---

### Post by qyot27 on 2010-01-19
> **ThePinkWitch said:**
> Thanks for that :) I'll take it off. I'll try a smaller app for the CPU monitor. Its handy tho because I like to keep an eye on how much is being downloaded and uploaded from the internet. I really like Firefox but from what you guys are telling me I think I'll have to try a different browser. I'll miss my add ons tho.
Not the same thing, actually.  That applet is one of the defaults - it appears as a mail envelope.

---

### Post by ThePinkWitch on 2010-01-19
"Sinister laughing and cackling are a requirement for enlisting."

I'm a witch, sinister and cackling is my job :D

---

### Post by ThePinkWitch on 2010-01-19
> **audiomick said:**
> This
[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)
might help you get firefox to behave better.

Thankyou once again Michael. You guys are awesome :)

---

### Post by ThePinkWitch on 2010-01-19
> **qyot27 said:**
> Not the same thing, actually.  That applet is one of the defaults - it appears as a mail envelope.

Oh ok.  TY :)

---

