---
title: "Internet slow &amp; a gripe"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by Struggling1 on 2010-06-01
I use Ubuntu Hardy Heron, and for some reason, my internet connection has slowed down to the point of madness.  I phoned my ISP, and there's nothing wrong from their side.  I find switching from tabs takes time, and every two minutes or so, the screen clouds over, and I have to wait between pages.
What's going on?
Please can someone help me!
Please do not use any fancy or complicated words in your reply because I will not understand what I have to do to solve the problem.  This brings me to another point.  Ubuntu reminds me of that Mother Goose rhyme "When she was good, she was very good, and when she was bad, she was bad."  I like using Ubuntu, so tears well in my eyes at the thought of having to go back to sucky old Windows; however, Ubuntu seems to be designed with computer geeks in mind, rather than for simple people whose specialities lie in other fields.  Imagine a car that only be driven by a mechanic, or a kitchen sink that can only be operated by a plumber?  Ubuntu feels like that sometimes.  It would be really great if some of you Ubuntu experts put together an "Ubuntu for Dummies" book or website so that there are easy instructions for us to follow when things go awry.

So, back to the question - I suppose I have to open that "terminal window" and type in a special command to make my internet work properly...?  What do I have to do?  I use Firefox by the way.  I am desperate.  Help! :(

---

### Post by HereInOz on 2010-06-01
First up, my 90 year old father-in-law uses Ubuntu without too many issues.  He is not a geek!!

Some questions:

Have you actually done a speed test on the connection? -
[http://www.pcpitstop.com/internet/bw.asp](http://www.pcpitstop.com/internet/bw.asp)

Have you tested your local area network speed between your Ubuntu machine and another on the network.  This could be a bit challenging, so ignore it if it is.

How do the other applications (Open Office, etc), behave?  Are they slow too or do they work as expected.

What sort of Internet Connection do you have?  Can you connect another computer to it and test its speed with that?

(Please note, I have not mentioned the terminal)

This sounds a little like a hardware issue rather than software or network, but I reserve the right to be horribly wrong :-)

---

### Post by t0p on 2010-06-01
> [SIZE=4][COLOR=#993300][B]There was a little girl
Who had a little curl
Right in the middle of her forehead. 
And when she was good
She was very, very good
But when she was bad
She was horrid! [/B][/COLOR][/SIZE][http://www.rhymes.org.uk/a116-there-was-a-little-girl.htm](http://www.rhymes.org.uk/a116-there-was-a-little-girl.htm)

The poem certainly *does* applicable to Ubuntu... but that's only because it's applicable to *all* software.  Personally, I've found Ubuntu easier to get my head round  than any other OS I've tried.

---

### Post by ShakeyJake on 2010-06-01
Actually there is an 'Ubuntu For Dummies' book. If the window greys out that sounds like it might be a disk i/o issue. There are a few guides arounf that instruct you on moving the FF cache to a ramdisk. This has the effect of cutting down the amount of time FF spends working with your HDD and speeds up the program. Might be worth trying as it's easy to do and a free fix.

---

### Post by abdusamed on 2010-06-01
YES.. FINALLY ... someone experiencing the same problem as he is... the browsing speed experience fluctuetes but most of the time it's dead... It's only while trying to browse the net. Doesn't matter which browser using, the browsing is incredibly bad. But downloads are fine, like after being pissed at the browsing, i decided to update ubuntu 10.04, updated and updated at full speed. After reboot... STILL BAD BROWSING. Not only that, but recently i've been noticing that the menu bar or the window bar of the opened doesn't seem to load. I have to kill Xorg and login again. 

Bascially, something bad is in ubuntu which doesn't let me browse, tried downloading a torrent via transmission, full speed and upload. But utorrent on wine doesn't seem to work. The funny thing is that it works sometimes. Actually most of the time but the browsing is REALLY BAD.. Monitoring my transfer rate using system monitor, it's like ubuntu doesn't care if i'm browsing or not. The rate usually stays around couple of bits.. then shoots up and stops again.

You might say it's my net.. but keeping the router on and rebooting the pc only to windows..surprisingly works FINE!! 9.10 worked well to but not in 10.04! WHAT'S UP WITH IT?

---

### Post by HereInOz on 2010-06-01
Ok, so from what you say it is not hardware, and it is not TCP/IP, for the torrents work ok and the file downloads are good.

So the next thing to suspect is DNS resolution.

the way to test this is to open a browser and type in:

[http://66.102.11.104/](http://66.102.11.104/)

This should result in the Google website coming up.  Then try:

[http://203.16.214.27](http://203.16.214.27)

This should give you the Internode website.

If it shows up without delay, but you normally experience delays when typing the URL, then there is a problem with your DNS resolution, and your DNS server is not getting the information to your browser for some reason.

Can you test it please?

---

### Post by Struggling1 on 2010-06-01
Thanks for the feedback. 
I live alone - I do not have another computer to test with.  My internet connection - Um, broadband...with a modem, not wireless.  It usually works very fast.
Anyway, I downloaded the file at pcpitstop, but it's an .exe file, and well,  I can't open it.  The little pop-up box says "choose application," but I don't know which one to use.
By the way, I also went to the Internode link suggested, and it came up immediately.  What now?
I haven't noticed any problems with Open Office - it's just the web browsing that has gone on strike.  
Am pleased that there is indeed an Ubuntu for Dummies book, no doubt a worthy investment for me.  FYI, I am not a he, but a she, though sadly this is one sister who is not doing it for herself just yet. :lolflag: One day I will reach the promised land of computer literacy; I will use words like router and synaptic in conversation and know what they mean.  Until then, more advice please!

---

### Post by Struggling1 on 2010-06-01
I don't know if this means anything, but it's just occurred to me that while web pages are going grey and slowing down, the internet radio (which launches in a little pop-up box entitled Webradio Mozilla Firefox) is playing without a problem.  No interruption, regardless of what's going on with the other pages...

---

### Post by abdusamed on 2010-06-01
i will report to u tom or the day after because right now I am connected to a WPA2 ad hoc network which UBUNTU does not connect and gave up trying. Although i was suprised i was able to create a network from ubuntu and share my net relativly easily but the network which I created was non secured because the secured network was givin me issues on the vista machine like the WPA2 security key wasn't vaild. It only worked on non secured. Because other uninvited guest could connect to the network, i perfered not to use it. But WPA2 network created by the Vista machine worked without a problem on windows 7 but in ubuntu machine, though it would detect the network but wouldn't connect to it.. i click on the network name in the network manager but it wouldn't do anything.. like simply ignore what i asked it to do. I pretty much gave up because I'm kinda tired of making threads on it.. I've experienced the bug since ubuntu 8.04 all the way up to 10.04! really sad if u ask me. There is some improvement in 10.04 and that is able to create a ad hoc and share net.. but not connect to ad hoc created by the other machine. 
Anyway... will report to u back as soon i get the wired net cuz i'm sharing the net right now.. it's wired to the vista machine and using windows 7 to connect to it

---

### Post by Struggling1 on 2010-06-01
> **HereInOz said:**
> First up, my 90 year old father-in-law uses Ubuntu without too many issues.  He is not a geek!!

Some questions:

Have you actually done a speed test on the connection? -
[http://www.pcpitstop.com/internet/bw.asp](http://www.pcpitstop.com/internet/bw.asp)

Have you tested your local area network speed between your Ubuntu machine and another on the network.  This could be a bit challenging, so ignore it if it is.

How do the other applications (Open Office, etc), behave?  Are they slow too or do they work as expected.

What sort of Internet Connection do you have?  Can you connect another computer to it and test its speed with that?

(Please note, I have not mentioned the terminal)

This sounds a little like a hardware issue rather than software or network, but I reserve the right to be horribly wrong :-)


I have since downloaded Google Chrome, and my connection is back to normal speed - fast, furious, fun.  Yippee!  I will always wonder why Firefox went bonkers, but at the end of the day, all i want to do is to do is use the internet, so if Google Crome is the way to kill this cat, so be it. :guitar:

---

### Post by HereInOz on 2010-06-01
It sounds a little like Firefox had got itself in a tangle in the area of DNS resolution.  If you were able to type in an IP address, and have the site come up immediately, then the problems were certainly DNS related.

If you want to use Firefox specifically, you could unintall it using the "Complete removal" option in Synaptic, then delete the .mozilla folder from your home folder (use CTRL H to show the hidden files).  This will allow Firefox to be re-installed as a completely fresh install.

If you like Chrome, then all is well.

---

