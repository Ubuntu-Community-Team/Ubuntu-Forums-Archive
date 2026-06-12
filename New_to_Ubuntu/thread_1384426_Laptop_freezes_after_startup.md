---
title: "Laptop freezes after startup"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by halo45121 on 2010-01-18
My Inspiron 1420 freezes maybe... 30 seconds or so after getting to the desktop. The screen freezes up, still showing whatever was on the screen, and I cant use my mouse/keyboard/anything. I'm testing the memory right now, and then I'll try (much to my disdain) to reformat the hard drive and reinstall Ubuntu 9.04.

If anyones got any suggestions as to what the problem is, or any input that could be helpful, please post.
Thanks!

-Matt


ETA: And, if I boot from any bootable CD, it's fine. Which makes me think it's the hard drive, but I don't really know.

---

### Post by MarkC502 on 2010-01-18
Doubt its the hard drive, but to check you can load from a live disk then see if you can mount your disk and open files etc. If yes and you see no problems then you could have some sort of software glitch. I have a few questions though that would help me help you.

1. Does this PC have 9.04 currently, If so did this start after an update ?

2. Did you in 9.04 select distribution upgrade and let it try to go to 9.10?

3. When it is frozen do any keys combos work Ctrl+Alt+Backspace etc ?

4. Does it always freeze after the exact same interval or does it sometimes do it in 15 sec and sometimes in a minute ?

5. can you open any programs before it freezes?

Let me know

---

### Post by halo45121 on 2010-01-18
1) I had just updated to 9.10. It worked for a while, but then the problem started.
2) See #1
3) Nope. I can't do anything, it completely locks up.
4) Uh, I just got a stopwatch and tested it, it varied from about forty seconds to a minute and ten seconds.
5) Yep, but you can't use them after the freeze.

---

### Post by MarkC502 on 2010-01-18
Man I hate the advice I am about to give but it is what I have done recently.

I have had problems with 9.10 on several laptops etc and after fiddling to fix this and that I decided for several machines to just use 9.04 and wait for the next release comming up. I personally have had nothing but bad experiences when I have used the UPGRADE function. I have since stopped using it and instead I do clean installs if I want to upgrade distributions as I find it less problem prone and if there is a post install problem I know I started with fresh install and so it makes it easier for me to rule out "what ifs" in my head.

If you have allot of stuff on your Ubuntu partition then this might be a problem for you to avoid losing valuable data. Hopefully you have a seperate data partition that you keep your stuff on. If not you could use live disk to mount and then transfer data to a USB storage device.

I don't doubt that your situation might be able to be fixed another way but I am not sure of any easy ones. Basically you would have to boot to a command line only and you could try "sudo dpkg --configure -a" & "sudo apt-get check" to try and fix broken dependencies or installation errors from a bad update etc.

EDIT : you could try pressing Ctrl+Alt+F1 as soon as it boots to go to an alternate commandline only login, then login using your username and pass. The command below will turn off the gnome desktop which is still running ( if not fromzen yet ) on your system in the other windows you left by pressing ctrl+alt+f1.

Command to try

sudo service gdm stop

that would turn off gnome desktop and maybe if you could do that fast enough it might avoid the freeze. That is assuming that one of the graphical components of ubuntu is freezing etc thus allowing you to run those commands I mentioned. Worth a try.

Sorry that is all the help I can be. I would vote for fresh 9.04 then never pick Upgrade to 9.10 ( you can turn off it even suggesting it in the update settings - I do this always )

---

### Post by halo45121 on 2010-01-18
Good advice. I had several problems with 9.10 too. I'm just gonna reinstall 9.04 and stick with it, provided that it works correctly. And I don't keep any important software on that computer, I mostly just use it for web browsing.

ETA: Reinstalled 9.04, working fine. Gonna wait for whatevers next to upgrade to.

---

