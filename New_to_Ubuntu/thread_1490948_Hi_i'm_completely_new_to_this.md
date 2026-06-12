---
title: "Hi i'm completely new to this"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by mrsleeps on 2010-05-23
so hey everyone my name is tyler and i'm using ubuntu for the very first time and really liking it even though i'm having a hell of a time but here is my quesiton. when i try to watch video's it is choppy and i can't get it fixed. also i know ubuntu says it loads fast and it does but when i open up the firefox it takes a little bit to get it to load. any and all help is appreciated because i want to use figure this out because i really like ubuntu dispite this. also i'm only running 1 and half gigs of ram. i'm just lost and kinda left in a daze of what i should do.

---

### Post by j7%&lt;RmUg on 2010-05-23
hey, glad to see your persevering through it. In answer to your problems, have you installed your graphics card drivers? if you have then try using something like VLC to play your videos, its available in software center.

Firefox can be a bit slow to start up on older machines (like mine) you can install a little program called preload to help alleviate some of the waiting, just go to software center and do a search for preload, or you can try a whole different browser if you like, i use a browser called chromium, which is also available in the software center.

Good Luck!

---

### Post by cotcot on 2010-05-23
The 1.5 Gigs ram is normally more than enough for the video playback. You can check how much ram you use with the system monitor. You can start this under --> System --> Administration --> System Monitor.
Some more info would be helpful. What kind of videos do want to play ? .avi , .mpg, dvd, 720x576, 1920x1080, What is the graphics chip or card in your computer ? What is you processor like ? Did you get normal playback on this computer before you had ubuntu on it? Which player are you using ? 
Concerning the browser : Opera is faster than Firefox.

---

### Post by DarkestRitual on 2010-05-23
Or you could use the official Google Chrome... I haven't checked into Chromium in a while though, so I may play around. I too am a n00b.

---

### Post by lovinglinux on 2010-05-23
> **DarkestRitual said:**
> Or you could use the official Google Chrome... I haven't checked into Chromium in a while though, so I may play around. I too am a n00b.

Also check [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). It has some tips on how to make it load fast.

Usually, what delays Firefox start is a database full of junk data and extensions. Extensions need to be loaded into ram when Firefox starts. If they are programmed to execute actions when Firefox loads, then Firefox won't be completely loaded until these extensions have completed their actions. If this actions involve database reading and writing, then the problem can be even worse.

---

### Post by amaroKer on 2010-05-23
You mean videos in websites such as YouTube eh?  I have the same problem, especially when I go fullscreen.  Flash 10.1 is hopefully going to fix performance on Linux, but like all proprietary software we're just gonna have to wait and see.

---

### Post by Kafubie on 2010-05-23
You can download Chromium web browser if you don't like Mozilla Firefox. (SUPERFAST)
Applications --> Ubuntu Software Center --> Search Chromium --> Install.

After installation, go to Applications --> Internet --> Chromium

---

### Post by mrsleeps on 2010-05-25
First off thanks for everyone trying to help out really appreciate it. if you can help me out but need more info just tell me what you it is you need and i'll be more then willing to tell you anything to help. i looked for chromium didn't find it gonna go through the thread and try all the idea's you guys gave me i'm hoping for the best. oh and plus i'm mainly talking about youtube video's and it only seems to have an issue when its someone video's of an actual real life event but when i watch video's like ubuntu how to video's seems to have little to no problem, i'm gonna try a whole new browser to see if firefox just doesn't like my computer. my video card is a geforce2, i'm currently trying to figure  out if i anything on the computer can tell me what my processor is if  not i'll just crack the case open but i'm trying to make myself search  and find things so i'll get use to it. and yes before i started using  ubuntu i was getting normal playback on youtube now nothing i have now  installed GNOMEDO and it helped with firefox with loading quicker. i do  know the processor is AMD just can't remember how big. once again Thanks  guys i appreciate the help.

---

### Post by stormchaser2063 on 2010-05-25
Who is your internet service provider? I had the same issue with you tube videos with my mac laptop and my 3.0 ghz compaq desktop running ubuntu 10.04 until i let the modem install the next updated version... course i am using cricket broadband usb modem for internet... works suprisingly well though. dont have a wired connection at home. firefox has its issues... i may look up chromium when i get home from starbucks tonight. on my mac laptop i use safari but i think that may be mac only. otherwise ubuntu is far better than windows and much easier to install than what my other option for my desktop was... i was going to make it a hackintosh and put snow leopard on it until my buddy suggested ubuntu.  the only real issue i have is the evolution mail and gmail but its not that big of a deal to check email by the usual way.
:) :)

---

### Post by jerenept on 2010-05-25
Chromium Bah. Epiphany. 'Official browser of GNOME' Really fast.
I am using the 10.4 version of adobe-flashplugin-nonfree, and the playback does not flicker, everything is pretty cool.

---

### Post by KdotJ on 2010-05-25
Welcome to Ubuntu :-)
Hope you enjoy your time here

---

### Post by stormchaser2063 on 2010-05-25
where would i find epiphany at? might want to check that out later when i get home if the heat doesnt kill me on the way home.

---

### Post by durand on 2010-05-25
> **stormchaser2063 said:**
> where would i find epiphany at? might want to check that out later when i get home if the heat doesnt kill me on the way home.

Ubuntu Software Center, search for epiphany. You could also try Midori. They're both based on the same core.

mrsleeps: It really looks like the problem is with your graphics driver. If you go to System > Administration > Hardware Drivers, there should be an option to install the nvidia driver. Try that. It should sort out the videos. Youtube/flash videos may still be buggy though because flash on linux is terrible at the moment.

---

