---
title: "BUG: soft lockup - CPU #0 stuck for 11s! [modprobe: 1742]"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by brucesmith on 2009-02-08
When I say I am an "absolute beginner," I mean, "don't start saying "command line" stuff because I won't understand!" It took me 10 minutes on this Forum page just to figure out how to open this posting!

I have an Acer Aspire X3200 with Windows Vista pre-installed. I bought a copy of The Official Ubuntu Book 3rd edition and used the 8.04 disk that came with the book to do a dual boot Ubuntu/Vista install. 

The install hung at the Install Ubuntu option before the install "Welcome" screen came up. I searched the web and found an advice telling me to use the alternate cd install, hit F6 at install menu and then, in the sentence at the bottom of the screen that ends in "splash--" it said to type in "pci=nomsi". I don't have any idea what that meant, but I did it and the install Welcome screen came up. The install went pretty normally (according to the book) after that although the step where I should have been able to import my saved Windows documents never happened.

I should add that this is my wife's computer. I have a Gateway dual booted with Ubuntu and Windows XP and have not had these problems.

Anyway, after the Acer install, I set up Evolution email so my wife could check her email and I restarted both Ubuntu and Vista several times with no problems so I shut down for the night.

This morning, when I turn on the power and get to the dual boot choice screen and just wait while Ubuntu decides to auto-load, I get the color screen with the Ubuntu logo and the little horizontal thermometer thingy. The orange rectangle starts across to the left and hangs up in the middle.

I had to shut off the power to get out. When I power on again, I now chose the second Ubuntu option on the dual boot choice screen...the one that says something about "recovery". When that one runs I get several black and white screens full of nonsense. Then is stops at a screen that says, 

BUG: soft lockup - cpu #0 stuck for 11s! [modprobe: 1742]

Pid: 1742, co mm: modprobe Tainted: G  D(26.24-23-generic #1 .......  

this runs off the right side of the screen so it may say more. There is a lot more stuff after this on the screen and if I watch, the screen flickers and changes some numbers on it, I suppose every 11 seconds.

I went onto Ubuntu site using my other computer and it looks like this is something that has been happening for years. The fixes shown are too complicated for me. 

What can I do? My wife was COMPLETELY frustrated by Vista and she was really happy with Ubuntu last night, so I'd like to get this working right.

This is a million times longer post than any other I see, so forgive me if I'm being somehow impolite or something. As I said, I'm the person in the world who really is an "Absolute Beginner"...I think I'm the one the Ubuntu people are trying to reach!!

---

### Post by houstonbofh on 2009-02-08
Some hardware just makes things difficult, and yours is that kind.  You might try looking to see if there is a local users group, or Ubuntu LoCo close.  Also, put your location in your profile.  This is just hardware that will take some experienced banging. :)  Worst case, there are several people (myself included) that can fix it for you mail order for a reasonable fee.

That, or dive into the rapids and learn to swim fast. :)  If you want to go that route, get the Intrepid Alt-Install.  There are MANY kernel fixes in it.

---

### Post by klange on 2009-02-08
Do you by any chance have an onboard Intel graphics card as well as a discrete nVidia card?

There's a bug with some Intel AGP drivers that can cause exactly what you described in such a situation.

---

### Post by brucesmith on 2009-02-08
To: Houstonbofh:
OK, I put Bloomington, Indiana in my profile. I don't know what "Ubuntu LoCo" or "Intrepid Alt-Insatll"  mean.

---

### Post by brucesmith on 2009-02-08
To: windowsucks:
I have no idea.

---

### Post by houstonbofh on 2009-02-09
> **brucesmith said:**
> To: Houstonbofh:
OK, I put Bloomington, Indiana in my profile. I don't know what "Ubuntu LoCo" or "Intrepid Alt-Insatll"  mean.
In spite of your first thought ;) LoCo stands for Local Community, and there is a big list here. [https://wiki.ubuntu.com/LoCoTeamList](https://wiki.ubuntu.com/LoCoTeamList)

But you want to talk to these guys. [https://wiki.ubuntu.com/IndianaTeam](https://wiki.ubuntu.com/IndianaTeam)  I am betting that one or more are very close, and could fix your problems for a burger and beer. :)

And the Alt-Install (when I spell it correctly) and a non-live cd installation method.  It is helpful for problem laptops.

---

