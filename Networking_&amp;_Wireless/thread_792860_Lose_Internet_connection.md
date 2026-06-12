---
title: "Lose Internet connection"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by gilloz on 2008-05-13
Recently I've notice that while either writing an email(Thunderbird) or on the Internet(Firefox), the screens dims down and loses the color and sits there for about 30 seconds and then switches back to my desktop and I lose my email, if writing something, or closes the webpage I was previously on.  I am still with Ubuntu 7.10.  A window then appears telling me that it is Not Responding.  Why is this happening now and what could be the causes of dropping the connection?  Anyone?

---

### Post by pytheas22 on 2008-05-13
Is your Internet connection really going down or is it just your email client and web browser that are crashing?  You could check by opening a terminal the next time the problem occurs and typing:

```
ping google.com
```

if you get a response, it means that the Internet is working.

I used to have a lot of issues with Firefox 2 crashing in the manner you describe.  I think it had to do with flash.  You could try installing Firefox 3 (it should be in the repositories even for 7.10) and see if it works better.  As for Thunderbird, I also had stability issues with it where the window would turn black and it would crash, but decided I liked Evolution better anyway.

Otherwise, there could be any number of reasons that these applications are crashing.  But if you're only getting this behavior with Firefox and Thunderbird, and everything else works fine, I would suspect that it has something to do with problems with Mozilla, and switching to Firefox 3 could help.  You could also try grabbing the Hardy build of Thunderbird to get a more recent version; if you don't know how to do that and can't figure it out by searching, ask.

---

### Post by gilloz on 2008-05-14
pytheas22, you are correct.  My DSL connection did not drop out, it's that my programs just terminated and took me back to my Desktop as if I just closed them.  I am using versions 2.0.0.14 for both Thunderbird and Firefox.  The Update Manager doesn't show a Firefox 3 as yet.  I also do not want to upgrade to 8.04 after reading all of the problems that everyone is experiencing as read on this forum.  It took me long enough to get my Ubuntu 7.10 to where I am at with it now.  I am happy with it with the exception of these few mishaps or problems.  I wish I could troubleshoot Ubuntu like I use to do in Windows when I had a Memory Dump or BSOD.  I would use programs like 
Windows Debugging Tool or HiJackThis and others to help me.  I have no clue what Ubuntu offers along those lines in troubleshooting problems.  I tried looking at all the logs and I can't find anything there related to this present problem, which BTW, doesn't happen always.  Sometimes I just wait long enough and the problem seems to disappear.  I don't know.  Thanks pytheas22 for your response though.

---

### Post by pytheas22 on 2008-05-14
There are extremely powerful tools that you can use to debug problems on Linux, like [gdb]("http://www.gnu.org/software/gdb/").  I don't know much about using them but if you have the time and this problem bother you enough, you could give give it a shot.  A simpler approach could also be just running firefox or thunderbird from the terminal; if you're lucky, they'll dump output relating to the crash.

Otherwise, a work-around would be using a different browser, like Konqueror, Opera (not free, sadly), Epiphany, et cetera, and a different mail client.

Also, you could burn an 8.04 live CD and run it to see how well your machine does with the newer version of Ubuntu.  I know a lot of people on these forums have had issues, but 8.04 for me, on two machines, was by far the easiest version of Linux that I've ever installed; I had to do virtually no configuration, which was an improvement over 7.10.

---

### Post by gilloz on 2008-05-14
Thanks.  You're one of few that have had a successful upgrade of 8.04.  You don't hear of them that much.  Today I received my CD from Ubuntu for 8.04 LTS.  I sent for it about 2 weeks ago.  I'm a little hesitant in installing it.  You see, I use an nVidia video card and there has been a lot of reporting of getting them to function with 8.04 also.  There just seems too much going against upgrading.  It is encouraging to hear your experience though.  Thanks for that.  I'll have to think about it a little.

---

### Post by pytheas22 on 2008-05-15
As far as nvidia goes: it will probably be hard to configure.  I don't know what the developers did, but they seem to have really messed up with the process to get the proprietary drivers installed.  I helped out at an installfest a couple weeks ago and I don't know of a single person for whom the restricted drivers manager worked the way it's supposed to for the nvidia driver.  It was embarrassing; we couldn't even really hack stuff by hand because the new xorg.conf is confusing.  We eventually ended up turning to [envy]("http://albertomilone.com/nvidia_scripts1.html"), which actually worked flawlessly in every case.  I am fortunate enough to have an Intel card (open-source drivers, cheap and good enough to run compiz well, if not games), so it wasn't a problem.

Anyway, I would still advise you to at least try 8.04.  If you use envy it shouldn't be that hard.

---

