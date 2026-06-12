---
title: "Ubuntu 10.04 nothing but random crashes"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by deancasino on 2010-05-08
This is wearing me down. Mem test done for 24 hours, no problem. All drivers are up to date (I have an Nvidia card). Nothng is old about anything in or loaded into my computer. I need help.

Sadly, I can report I don't get system crashes in Windows 7....

---

### Post by jvc26 on 2010-05-08
Couple of ideas:

```
sudo apport-bug linux
```

To get a bug report sent off to launchpad - after all, if you don't report it, it can't get fixed.

And then on a different note, did you get these crashes in Karmic? Have you made any chances to hardware recently. What does the crash do, and does it crash out so you can't do anything, or is it still responsive to SysRq+REISUB.

J

---

### Post by cap10Ibraim on 2010-05-08
If you already have windows 7 why would you use Ubuntu ?! ):P

---

### Post by deancasino on 2010-05-08
> **jvc26 said:**
> Couple of ideas:

```
sudo apport-bug linux
```

To get a bug report sent off to launchpad - after all, if you don't report it, it can't get fixed.

And then on a different note, did you get these crashes in Karmic? Have you made any chances to hardware recently. What does the crash do, and does it crash out so you can't do anything, or is it still responsive to SysRq+REISUB.

J

I didn't get these lockups in Karmic. I've made no changes to hardware. The crash just freezes everything and it is unresponsive to SysRq+REISUB in this state.

Completely random too. Today once while editing in Gimp, yesterday while browsing (In Chrome) and a few days ago while simply playing music in Banshee.

Any help is appreciated.

---

### Post by sixthwheel on 2010-05-08
> **cap10Ibraim said:**
> If you already have windows 7 why would you use Ubuntu ?! ):P
Very helpful.:rolleyes:

---

### Post by deancasino on 2010-05-08
Bug reported here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577661](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577661) if anyone getting the same problem and wishes to add to the list.

---

### Post by deancasino on 2010-05-08
> **sixthwheel said:**
> Very helpful.:rolleyes:

Lol yeah, I just let the trolls, troll.

---

### Post by sixthwheel on 2010-05-08
> All drivers are up to date (I have an Nvidia card). 
Some people seems to be having those problems with the Nvidia cards.

Do a search on Nvidia/lucid.
You may have to go back to Karmic untill things get smoothed out.

---

### Post by deancasino on 2010-05-08
> **sixthwheel said:**
> Some people seems to be having those problems with the Nvidia cards.

Do a search on Nvidia/lucid.
You may have to go back to Karmic untill things get smoothed out.

Thanks for the advice, and yeah I think that may be the way to go.

---

### Post by sixthwheel on 2010-05-08
Another thing you can do, and this is what I'm doing, is dual booting Lucid and Karmic for now.

I'm having a few issues with Lucid, but I like it too much to let it go because of a few problems.

So for now I'm back to Karmic, but about once a day I go over to the Lucid side to get updates, and see how everything is progressing over there.

Sorry I couldn't be more help, but I'm a noob myself, and can only offer what I've learned in 3 months.

---

### Post by bomgd3 on 2010-06-09
removed

---

### Post by Keith Myers on 2010-06-09
This has been my experience also with Lucid.  Bug reports generated for random crashes.  Bug #'s 590325,590474,590477,591553.  I had about a day and a half where the system was stable and just after I posted that fact, the system crashed on me again.  Same experience of having ALT+SySRq R E I S U B do nothing also.  Always have to use the system reset button.  Haven't figured out just what upstream kernel I'm supposed to try as I am a complete noob.

Keith

---

### Post by Keith Myers on 2010-06-29
I installed the latest mainline kernel and I still have random, unrecoverable crashes.

Keith:confused:

---

### Post by CanBert on 2010-06-30
Same -- random crashes -- ran memtest -- all good --

This is on an older dell machine (2.4 ghz intel4)

I think it is graphics related.(using just the generic graphic drivers)

Screen will go blank then flash from black to white lines in monitor till I manually reboot machine.

---

### Post by sXeChris on 2010-06-30
> **cap10Ibraim said:**
> If you already have windows 7 why would you use Ubuntu ?! ):P
That's not a very intelligent thing to say.

---

### Post by holibut on 2010-08-25
Why that bug is marked as expired?
I just installed Ubuntu 10.04 on two machines. One is stable( I am using now), the other has the issue: random crash-lost video&key board responding.
The differences are:
on the crash one:
1. I add two partitions(mounted as /home, /opt) with partition tool of Ubuntu 7.10 
2. The graphic card is Nvidia LE 7300.

I mean the issue do exist, who can help or what can I help to resolve it?
Or some tunnel approach is appreciated if not too hard to follow.


Thanks a lot!

> **deancasino said:**
> Bug reported here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577661](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577661) if anyone getting the same problem and wishes to add to the list.

---

### Post by andymorton on 2010-08-25
> **cap10Ibraim said:**
> If you already have windows 7 why would you use Ubuntu ?! ):P

Because Ubuntu is superior to Windows 7 is just about every way

---

### Post by waggers on 2010-08-29
> **CanBert said:**
> Same -- random crashes -- ran memtest -- all good --

This is on an older dell machine (2.4 ghz intel4)

I think it is graphics related.(using just the generic graphic drivers)

Screen will go blank then flash from black to white lines in monitor till I manually reboot machine.
Exactly the same here. Older Dell machine (Intel celeron, so even older!) and crashes as described. Very frustrating!

---

### Post by Kellemora on 2010-08-29
After having horrendous luck with 10.04 I patiently waited for 10.04.1 to come out.  I see NO improvement in this OS.......

I have MOST of the problems already posted, including the black and white lines when it locks up, NOT Nvidia on that machine either, not ATI either.
In any case, 10.04.1 crashes on almost all of our computers DAILY.

8.04 STILL performs flawlessly!  Not a single complaint about 8.04 at all.

10.04 needs to be dumped in the circular file and they should build 8.04 up instead of abandon it as they plan.

We have 8 different computers here and 10.04.1 doesn't work on ANY of them!  Won't even load on most of them without doing it in some bizarre fashion that shouldn't even be necessary.

It's unfathomable to me that they call 10.04 an LTS release when it's not even CLOSE to being out of Pre-BETA testing yet.......
Oh, well, 3 years from now they might come out with a reasonable alternative, I'll wait for 12.04 to come out before messing with it anymore.  If they quit supporting 8.04 I have Debian already triple-booted so I have a RELIABLE OS to fall back on!

TTUL
Gary

---

### Post by cadogan281 on 2010-09-02
i have the same problem with random crashes,and the black and white stripes on the screen.my ram tested fine,so iam not sure what else it could be.i too am using an older 2.4ghz pc with intel 82845g graphics.is it logical to go back to 8.04 to stop the random crashing?thanks

---

### Post by waggers on 2010-09-02
This thread deals with the same subject and has some potential fixes, although I haven't found one that works for me yet:
[http://ubuntuforums.org/showthread.php?t=1558917](http://ubuntuforums.org/showthread.php?t=1558917)

---

