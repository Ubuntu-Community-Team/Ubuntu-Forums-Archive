---
title: "Performance tuning"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by cedar.bristol on 2009-06-06
I just recently installed, and I'm happy with the superior responsiveness and boot-up times vs. Windows, but I'm unable to play a DVD without it starting to hiccup a lot after about 20 minutes of watching.  Flash videos, even when I download them to the hard drive, are even worse.  I was unable to play DVD's at all until I downloaded vlc player.  Flash videos seem to do slightly better on some of the other players. My machine is no champion, it's 5 years old, but windows plays dvds and flash videos on this same machine without a problem.

Another issue is websites that are heavy on javascript, like facebook, really bog it down, much more than they ever did on Windows.

I'm still not going back to windows, I know that facebook, DVD playback and a few other things will work without any performance tuning if I reinstall windows, but I also know that the time boot-up, or to wake up from hibernation, will grow every day and withing a month boot-up will be taking over a minute and I will be able to count to 5 between the time I click on the start button and the the start menu actually appears.  I expect that if I learn to tune away these annoyances I find in linux, I'll be much happier in the long run.

So far, I've read [this article]("http://www.extremetech.com/article2/0,2845,2114123,00.asp") , on performance tuning, it was the highest rated on delicious.  I was hoping someone could recommend books, and/or other tutorials on the subject, particularly anything that can help with answering the following questions:

1. Does anyone know how to performance tune video players?  Do I set kernel settings to do this?  

2. Why does Ubuntu consume so much memory?  I just now typed free in a terminal and it shows 

             ```
total       used       free     shared    buffers     cached
Mem:        449520     443816       5704          0      23728     107128
-/+ buffers/cache:     312960     136560
Swap:      1317288      41564    1275724
```Does it really require a half a gig of memory just to run firefox with 3 tabs and one terminal window plus the GUI?  Do all linux distros gobble this much memory?  Or, does this indicate that there's a problem with the way my system is set up?

3.  I tried setting the max-threads value as per the article.  Raising it and lowering it both seemed to hurt video performance.  What are the tradeoffs involved in having a high or low value for this setting?

---

### Post by shifty_powers on 2009-06-06
dunno about the other two, but for number 2,

[http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm](http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm)

it's a fairly common question...

---

### Post by woedend on 2009-06-06
You aren't by chance running an intel video card are you?... as this behavior is typical for them in Jaunty by default, although it can be fixed.  Your problems seem to stem from graphics card driver issues, which will really bog down a system.  So, what do you have?

---

