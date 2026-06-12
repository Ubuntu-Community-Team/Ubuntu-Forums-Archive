---
title: "Which browsers in Ubuntu Software store work best in Koala?"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-04-02
I've looked all over the forum and don't see my question addressed directly so I thought I'd try a new thread.

Have a dual boot with Ubuntu 9.10, Toshiba L350-S5933, ACPI x86 based PC, 32 bit OpSys, Intel Pentium Dual CPU T3400 @ 2.16GHz, 3.00MB Ram. Set up with WiFi, in home.

Tried the Firefox that came with the Ubuntu download and it works okay until you get to Pogo where it says that "The version you have is not acceptable" and won't work the games. Tried all of the update info I could find in Forums but nothing worked.

Installed Opera 10.10 Linux i686 2.6.31-20 Generic QT Library 3.3.8b (That's all offered for download to Linux/Ubuntu) Found that to be about as fast as dial-up in Win3/1/95 and it takes FOREVER open up the games. (Gave up after 5 minutes on Jigsaw Treasure at Pogo) Alson noted some video problems (blank screen) at other sites (like doing the question search right here while using Opera)

What I want to be able to do:
1. Put links it toolbar for things like getting my business website email, hotmail and Ubuntu forums.
2. Be able to go to sites like Pogo and not take all day to get into my "therapy" session.
3. Able to do chats with friends in places like Facebook.

I see a number of browsers listed in the Ubuntu Software Store under Internet but don't recognize any of the names. Can anybody bring me up to speed on the best choice in these or do I need to print out the list and spend a few days (trying) on the 'net researching. Have seen lots of referrals to Chrome and Chromium. What about those and installation?

Thanks for the patience to read all of this and any assists provided.](*,)

---

### Post by thenailedone on 2010-04-02
Hmmm... Well between Firefox and Opera you have mentioned two of the big ones out there (which is why you know them and why you tried them)... sounds to me the problem is not with the browser... maybe flash?  What have you gotten installed currently flash wise?

---

### Post by uRock on 2010-04-02
I have used Epiphany, it was pretty good. I now use chrome on my Karmic machine and Chromium on my Lucid. Chromium is in the repos for Lucid.

---

### Post by Linuxforall on 2010-04-02
Alongwith Opera, try Chrome, for Opera, try out latest beta 10.52 which is far more compatible than their earlier 10.10 and way faster, in fact fastest Linux browser out there. [http://my.opera.com/desktopteam/blog/2010/04/01/final-fixes-before-the-easter-holidays](http://my.opera.com/desktopteam/blog/2010/04/01/final-fixes-before-the-easter-holidays)

---

### Post by flyfishingphil on 2010-04-02
> **thenailedone said:**
> Hmmm... Well between Firefox and Opera you have mentioned two of the big ones out there (which is why you know them and why you tried them)... sounds to me the problem is not with the browser... maybe flash?  What have you gotten installed currently flash wise?
You noticed this was in Absolute Beginners, right?

How/where do I get the info on the flash and I'll post it.

Thanks

---

### Post by flyfishingphil on 2010-04-02
> **Linuxforall said:**
> Alongwith Opera, try Chrome, for Opera, try out latest beta 10.52 which is far more compatible than their earlier 10.10 and way faster, in fact fastest Linux browser out there. [http://my.opera.com/desktopteam/blog/2010/04/01/final-fixes-before-the-easter-holidays](http://my.opera.com/desktopteam/blog/2010/04/01/final-fixes-before-the-easter-holidays)
Thanks for the recommendation.

Is there a way, in Opera 10.10 to do the update to the 10.52, or do I have to do the full download, uninstall current, install new. If so, and here's where I've had the most problems, where might I find easy to read/use (for a Dummy) installation steps, or is it self extracting/installing?

BTW, in checking on updates in Opera it says 10.10 is the latest. In checking the site it refers to "stable version". Is the 10.52 stable? I spend a lot of time on the 'net with my business and need reliability.

---

### Post by thenailedone on 2010-04-02
> **flyfishingphil said:**
> You noticed this was in Absolute Beginners, right?

How/where do I get the info on the flash and I'll post it.

Thanks

Sorry... I also still see myself as an absolute begginer (but maybe I am not completely novice anymore)... 

Applications -> Ubuntu Software Center ... search for flash and see which of the results are ticked with a green tick to say it is installed...

(Sure there are better ways but this is one way)

---

### Post by flyfishingphil on 2010-04-02
> **thenailedone said:**
> Sorry... I also still see myself as an absolute begginer (but maybe I am not completely novice anymore)... 

Applications -> Ubuntu Software Center ... search for flash and see which of the results are ticked with a green tick to say it is installed...

(Sure there are better ways but this is one way)
It shows the "Ubuntu restricted extras" with all that includes and "Adobe Flash Plugin"

---

### Post by thenailedone on 2010-04-02
> **flyfishingphil said:**
> It shows the "Ubuntu restricted extras" with all that includes and "Adobe Flash Plugin"

Curious, running Firefox with the "Adobe Flash plugin" (Installer for the Adobe flash plugin for Mozilla) is making all sites work fine for me...

(let me try that pogo site...)

---

### Post by da burger on 2010-04-02
> **iRock said:**
> I have used Epiphany, it was pretty good. I now use chrome on my Karmic machine and Chromium on my Lucid. Chromium is in the repos for Lucid.

Slightly off topic but there is a PPA for chromium.

---

### Post by thenailedone on 2010-04-02
[www.pogo.com](www.pogo.com) working fine for me... Firefox 3.6.2 with the Adobe flash plugin...

---

### Post by flyfishingphil on 2010-04-02
Hokay Dokay! I went in and added the "Ubuntu Restricted Extras" for a second time, did the restart and checked it out. Working fine now. Glad to see that happen. Getting closer and closer to finding out how to save everything in Koala, save and recover all of my Windough$ files into Koala and do a total format and re-install so all that is there is Ubuntu. I'll play with for a while longer before I do that though.

Thanks for the assists. Guess this one is solved!

---

### Post by @rizz on 2010-04-02
hi,

   to install flash try this in terminal....

1. Step
```
$ sudo apt-get autoremove adobe-flashplugin
```

2. Step

```
sudo apt-get install adobe-flashplugin
```

3. Step

 Open firefox and Njoy!!!!

---

### Post by flyfishingphil on 2010-04-02
Got FF working fine but checked out Opera and it is till messed up. Want to "uninstall" it but can't find a way to do that. Tried both the Ubuntu Software center and Synaptic but neither one shows Opera 10.10. How do I get rid of it?

Got it removed. This is a DUH! I was using the Search and it didn't identify Opera. Entered it in Quick Search and there it was. Removed. All gone!

Mess with this long enough and I might just get the hang on Ubuntu!

---

