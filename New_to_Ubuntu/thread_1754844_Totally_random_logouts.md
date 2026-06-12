---
title: "Totally random logouts"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by llmunro on 2011-05-10
Hi all,

I upgraded from Maverick to Natty through the update manager.  All is great (and I'm even liking Unity), but I swear that Natty has a mind of its own, as it will quite suddenly and unexpectedly just log out at completely random times.  I thought for a while that maybe I was accidentally hitting a sneaky log out shortcut, but this will happen even when I am only touching the trackpad and no where near any option to log out.  This is intensely annoying, as you might imagine.

Any thoughts?  Should I try a clean install?

Best,
Lisa

---

### Post by parthgadhia on 2011-05-10
> **llmunro said:**
> Hi all,

I upgraded from Maverick to Natty through the update manager.  All is great (and I'm even liking Unity), but I swear that Natty has a mind of its own, as it will quite suddenly and unexpectedly just log out at completely random times.  I thought for a while that maybe I was accidentally hitting a sneaky log out shortcut, but this will happen even when I am only touching the trackpad and no where near any option to log out.  This is intensely annoying, as you might imagine.

Any thoughts?  Should I try a clean install?

Best,
Lisa

It happened to me as well this evening. Rhythmbox stopped, screen flickered, and I was at the login page. :confused:

---

### Post by HDave on 2011-05-10
I would try a clean install as a last resort.  Did you run with compiz on in the past?  My first thought would be a graphics driver problem.  I'd toggle hardware drivers for your video adapter from proprietary/open-source and see what happens.

Also try logging in with "ubuntu classic (no effect)" and see what happens after a while.  This disables compiz altogether.

---

### Post by tkelito on 2011-05-10
Ran into this issue previously with a box running 10.04.  It was the result of the KVM switch being flakey.  Not sure why it interpreted as the logout command but it seemed to always happen at the most in opportune times.

---

### Post by llmunro on 2011-05-10
Hey tkelito,

What's a flaky KVM switch?  I tend to think that the random logouts are a Natty problem, as I never had this problem with 10.10.

I'm trying Ubuntu Classic and will report if this issue continues.

Best to all,
Lisa

---

### Post by wildmanne39 on 2011-05-11
> **llmunro said:**
> Hey tkelito,

What's a flaky KVM switch?  I tend to think that the random logouts are a Natty problem, as I never had this problem with 10.10.

I'm trying Ubuntu Classic and will report if this issue continues.

Best to all,
Lisa

I had that happening to me, also my screen was going white it was because I am running a nvidia graphics card and the proprietary driver was the most current and it is not compatible at this time with natty, I had to install the 173 nvidia driver, dont know if this applies to you, I hope it helps.

---

### Post by TheNessus on 2011-05-11
I've had the same. Only with 11.04, never with previous versions. Only on Unity, not with other DEs. Intel HD graphics card, latest out of the box driver.

---

### Post by llmunro on 2011-05-11
I was hoping that switching to Ubuntu Classic would fix the problem, but it persists.  I may go back to Maverick, as it really is annoying.

Is this a bug?

Best,
Lisa

---

### Post by porfiry on 2011-05-11
Also experiencing random logouts after doing a fresh natty install. Graphics chip is also intel; mine is a Mobile GM965/GL960.

---

### Post by wildmanne39 on 2011-05-11
> **llmunro said:**
> I was hoping that switching to Ubuntu Classic would fix the problem, but it persists.  I may go back to Maverick, as it really is annoying.

Is this a bug?

Best,
Lisa

Hi, this is a bug for people with the nvidia card and is listed as one, with the fix using the 173 driver but not sure with other cards.

---

### Post by tkelito on 2011-05-16
> **llmunro said:**
> Hey tkelito,

What's a flaky KVM switch?  I tend to think that the random logouts are a Natty problem, as I never had this problem with 10.10.


Sorry for the delayed response, a KVM switch is a Keyboard-Video-Mouse connector that allows you to hook multiple desktops (or laptops) up to 1 Keyboard, 1 Monitor and 1 Mouse.  For example my server room at the office has tons of machines but when I am working I can control all of them by toggling through a KVM that lets me switch from one machine to the other with the flick of a button.

And I think I meant flakey, not flaky.  My KVM at the time was failing, it had a bad input as a result was giving one of my boxes weird inputs and it kept on logging out at the most in opportune time.

---

### Post by ZaHACKieL on 2011-05-16
> **wildmanne39 said:**
> Hi, this is a bug for people with the nvidia card and is listed as one, with the fix using the 173 driver but not sure with other cards.

What is 173 driver? It's happening to me too with Natty. I'm on a Dell XPS17 with Nvidia GeForce 555M.

When I installed Natty, the advanced effects and Unity worked but it also happened to me that when I installed the restricted Nvidia drivers, the advanced effects and Unity stopped working =/

---

### Post by 5149.5 on 2011-05-16
I have the problem as well. I have had it happen with only firefox running. My video adapter is intel.

---

### Post by ZaHACKieL on 2011-05-16
> **5149.5 said:**
> I have the problem as well. I have had it happen with only firefox running. My video adapter is intel.

I had that happen three times. The first one was after installing Nvidia restricted drivers. They downloaded/installed correctly and before I could restart to complete the installation it just spontaneously logged out and I think that messed up the installation because my graphic acceleration stopped working after restarting.

I don't remember what was I on the second time it happened but the third one followed this chain of events...

Login
Open emesene
Open Chrome
Close emesene
Open Thunderbird
Random logout

---

### Post by ZaHACKieL on 2011-05-17
One more thing I noticed is that I'm almost sure that once in happens it never happens again in the same session. Anyone?

---

### Post by mlupton on 2011-05-19
True, it seems that every time this happens it only happens once a session. Earlier when I was using Ubuntu Classic [No Effects] I didn't have any issues, I guess it's because there was no need for Compiz to even be functioning. Everything works in Unity and it was a clean install, but it really frustrates me when I am trying to finish working on something.

---

### Post by ZaHACKieL on 2011-05-19
Well since the last updates (I think I updated my system 2 nights ago) I haven't had random logouts but I've experienced system hangs twice, which is even more frustrating. I´ ll report if I have news =D

---

### Post by E. Volh Tiw on 2011-05-20
This happened to me too.

What I did was to logout as soon after I boot up, then login again. Ever since I started doing that, I had no random logouts.

---

### Post by dFlyer on 2011-05-20
This has also happen twice to me. Each time I had Firefox 4 running with about 5 or 6 sites opened.

---

### Post by beew on 2011-05-20
> **wildmanne39 said:**
> Hi, this is a bug for people with the nvidia card and is listed as one, with the fix using the 173 driver but not sure with other cards.

Actually that happens to me on a machine with an ATI card.  It is a clean install oo so it is not just people who suffer from a bad upgrade. With Nvidia there is another problem of freezing (with the nouveau driver)

---

### Post by beew on 2011-05-20
> **dFlyer said:**
> This has also happen twice to me. Each time I had Firefox 4 running with about 5 or 6 sites opened.

Yup Firefox when I try to open new window or Smplayer when I try to open a file.

---

### Post by E. Volh Tiw on 2011-05-20
I don't think it's a particular program causing it. I've had this happen with Firefox, as well as without Firefox.

From what I've read in launchpad, it could be caused by X. Someone said they think it's unstable during the first run, and it somehow loads correctly after logging back in. (Which is why I logout and login after I boot, and it seems to work.)

---

### Post by duke.tim on 2011-05-20
This is a bug, you could help by going to lanuchpad and reporting that this bug affects you! They also might want additional information :)

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/778490](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/778490)

General info on bug reporting

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by mlupton on 2011-05-23
Does anybody else find it a little strange how things worked better with the beta version of NVIDIA's proprietary driver, but when NVIDIA finally felt good enough to release an "official" version of their Linux driver, everything went weird? I hope NVIDIA responds to these bug fixes and makes the next driver release a little nicer.

---

### Post by 5149.5 on 2011-05-24
This problem has nothing to do with a specific graphics adapter or the OS level. A search on these boards shows that this has been going on since 9.04. It happens on ATI, Nvidia, and Intel vga adapters. The reason it is still happening can be seen by looking at the bug that is listed above. Status is confirmed, importance is undecided, and no one is assigned. With all of the complaints you would think that more than 29 people are effected but that is the current count. This would never work in a business environment.

---

### Post by ZaHACKieL on 2011-05-27
> **E. Volh Tiw said:**
> I don't think it's a particular program causing it. I've had this happen with Firefox, as well as without Firefox.

From what I've read in launchpad, it could be caused by X. Someone said they think it's unstable during the first run, and it somehow loads correctly after logging back in. (Which is why I logout and login after I boot, and it seems to work.)

I did the same thing about logout-login but the problem is that when I do that, I don't know why, my CPU's temperature raise like 20 degrees and stays like that. It's usually around 45 (both) and with this 2nd login it gets to ~65. When I check the system monitor during the second login I see that gnome-panel is consuming 100% of CPU while during the first login it says 0%.

Anybody noticed the same thing?

BTW I don't get only random logouts but also random freezes.

---

### Post by E. Volh Tiw on 2011-05-27
I started getting random freezes after my "login-logout" solution, too. After some more searching, I encountered yet another "solution", that seems to work, so far...

Disable compiz effects:
- Enhanced Zoom Desktop
- Animations
- Grid
- Snapping Windows

Source: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/780358/comments/5](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/780358/comments/5)

---

### Post by ZaHACKieL on 2011-05-27
I'll try that mate thanx! What about the increase in CPU temperature? You get that too? It seems that during the second login, gnome-panel is consuming 100% of CPU

---

### Post by E. Volh Tiw on 2011-05-27
I had a sudden X freeze today.

The mouse pointer can move around the screen, but clicking doesn't work.

The keyboard also doesn't respond, except for the Fn key and the combinations to adjust screen brightness. I cannot open a Terminal to issue any commands.

However, I had stopped doing the login-logout thing because things seemed going back to normal. I'll go back to that workaround tomorrow, and see if it makes any difference.

As for temperature, I think Natty is hotter than Maverick. I'll see if I notice it upon the second login, tomorrow.

---

### Post by ZaHACKieL on 2011-05-29
I disabled the effects you said (except for animations) and I haven't had logouts/freezes until now but some days ago I experienced the same thing you said, i.e. mouse can move but click doesn't work. Keyboard didn't work either but I believe the Caps Lock LED still worked (it doesn't when Ubuntu totally freezes).

So let me know if you notice the temperature change and I'll tell you if I have those issues again. Cheers! XD

---

### Post by ZaHACKieL on 2011-05-29
I disabled the effects you said (except for animations) and I haven't had logouts/freezes until now but some days ago I experienced the same thing you said, i.e. mouse can move but click doesn't work. Keyboard didn't work either but I believe the Caps Lock LED still worked (it doesn't when Ubuntu totally freezes).

So let me know if you notice the temperature change and I'll tell you if I have those issues again. Cheers! XD

---

### Post by bomgd3 on 2011-06-04
Yup.  Same problem for me.  Totally random.  I was typing earlier and suddenly, bam, back to login screen.

---

### Post by E. Volh Tiw on 2011-06-04
I enabled the updates channel in Sources, and upgraded xorg, the kernel, and other things.

So far, I have not had any other freezes. But, if I re-enable the effects that cause the logouts, I still get kicked out of my session. So, the issue is not solved in any recent update.

---

### Post by tjeremiah on 2011-06-05
this issue is very annoying ](*,) One minute I am typing and then BAM, im greeted with the login screen again. This usually happens when I use firefox.

---

### Post by 501st_alpha1 on 2011-06-07
I have the same problem. Ubuntu 11.04, fresh install, GNOME environment (no Unity), Intel HD integrated graphics. I don't think this ever happened to me in 10.

---

### Post by benjamin.s.vaccaro on 2011-06-07
Hello, I've read through the posts and I hate to continue the impressive broken record complaints. 

I have also experienced identical issues with Chrome 11.0.696.71 on Ubuntu 10.10 with my laptop. Then I tried upgrading to 11.04 to be greeted by a the infamous video card/OS disconnect. Alas, I am back on 10.10 and the issue persists.

A few specs:
Computer: Dell Inspiron E1505
Ubuntu Version: 10.10 x86_64
Processor: Intell Centrino Duo 1.83 GHz
Nvidea: "NVIDIA accelerated graphics driver (version current) [Recommended] - It doesn't want to give me the specific number, 173 etc, but if it is recommended then it should be sought and thus the problem is not in selecting the correct/wrong driver but rather the interaction between programs
Compiz: Isn't that 95% of why we use ubuntu? >.>


Perhaps something of valuable note: When I originally installed Ubuntu 10.10 the issue was not prevalent - and it did not become an issue until post launch for 11.04. I'd also like to note that there are a few ways of logging out of Chrome which may help alleviate the issue as a temporary fix.
Methods of logging out:
1. Click on the "X" at the top left or right corner of the window
2. Click on the "x" on the tab (only closes out of chrome if there is one tab open)
3. Right click and choose "close" on the bottom panel
4. File(wrench) -> exit
5. System Monitor
6. Ctrl + Q
7. Alt + F4

I personally find option 3 to work best at closing chrome without logging out, but this isn't always the case. 

Sorry I couldn't help solve the issue, but hopefully this information will help our heroes who are able to debug it.

---

### Post by ZaHACKieL on 2011-06-08
As for now, to summarize, there are three (random?) things that happen and are probably related: logouts, freezes and unresponsive X (read post #29). 

At least we know that when a random logout happens it seems that it usually doesn't happen again during that new session.

For the freezes we can't do anything I guess.

For the unresponsive X what I do is go to tty1 and reboot from there.

Also, it seems that disabling some effects can help a bit (read post #27).

I also noticed that when you login then manually logout and login again, my CPU temperature raises a lot (read post #26 and #28) and gnome-panel consumes 100% of CPU.

More ideas, suggestion, comments?

:D

---

### Post by wolfen69 on 2011-06-09
I was getting random log outs, and other weird things, but found out my memory was not compatible with an AMD cpu. I switched the memory out and all was well. Sometimes you need to take a look at hardware issues also.

Doing full hardware diagnostics can reveal a lot. Don't always assume that it's the fault of software.

---

### Post by ZaHACKieL on 2011-06-09
> **wolfen69 said:**
> I was getting random log outs, and other weird things, but found out my memory was not compatible with an AMD cpu. I switched the memory out and all was well. Sometimes you need to take a look at hardware issues also.

Doing full hardware diagnostics can reveal a lot. Don't always assume that it's the fault of software.

That could be true but I think it would be a coincidence that all of us with different machines are having the same issue. I have the same problem with two new laptops (a Dell XPS 17 and a Toshiba NB505 netbook). I don't have the problem in my netbook anymore because I'm using the classic-no-effects desktop but it happens if I move to the classic desktop (with effects). So I don't think two different vendors will use incompatible hardware in their system.

So, it can happen that just by chance you are experiencing the same issue due to a hardware problem but I firmly believe this is not the case ;)

Thanx for your comment anyway. I'm sure it will be useful to remember your issue and solution.

---

