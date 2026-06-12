---
title: "Ubuntu 9.10 64-bit fresh install. mega noob. how to allow permission to install stuff"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by Hypnotic Smith on 2010-04-22
I have just installed Ubuntu 9.1 on my computer and I am having some complications. Been reading many forums on how to get things running from a fresh install of Ubuntu but nothing seems to work for me. I've tried running terminal and copy and pasting updates and other lingo stuff.

When I go into Ubuntu Software Center under applications, I can't install anything (install button doesn't even come up with any of the programs). It's like I need a permission or I need to unlock some architecture setting that allows me to download wtf I want to. I'm not sure what to do. I'm a noob^4 but if someone can help me I would be so grateful.

I need to download codecs and a bunch of other things. Eventually I will be playing World of Warcraft (WoW) in no time. I can't listen to music, watch movies, or go on youtube to watch videos. I'm basically working from a fresh install of Ubuntu 9.1 64 bit.

[COLOR=DarkRed]Please help me. Call me (Warren) @ 801 889 0425 (Utah Cell) if you feel you can help me. My email is [EMAIL="coloredfingers@live.com"]coloredfingers@live.com[/EMAIL][/COLOR]

---

### Post by empty_spaces on 2010-04-22
What is the error when you try to install a program?
For example, let's say you want to install VLC media player.

To do that, copy-paste the following in the terminal
**sudo apt-get install vlc**

It should ask for your user password, type that in (you won't see any characters) and hit enter.

Copy-paste any errors in this thread.

---

### Post by QIII on 2010-04-22
Might I make a suggestion?

Although _spaces has given you a perfectly valid command line instruction that should work, I am concerned that you are having problems with the normal package management systems.  You should be able to use those.  (Do try the command.  It would be diagnostic.  If you can't run the command with elevated sudo privileges, something deeper may be wrong.)

Unfortunately, I don't know what you may have "cut and pasted" that my have otherwise caused issues.


PS:  Generally, those of us who help here don't like to make direct contact off-line or through private messages in helping with an issue.  It's not that we are an unfriendly lot.  What we would like to see is problems resolved here on the forums so that others can benefit from the solutions found.

PPS:  On thinking about this for a moment, do you remember ever getting a message something to the effect that you should run "sudo dpkg --configure -a"?[FONT=monospace][/FONT]

---

### Post by maxrpowell on 2010-04-22
Heres what to do. I think this will fix your problem.

you can do it through the terminal with this code:
'sudo apt-get update'

or you can do it through the package manager this way

1 Go to System -> Administration -> Synaptic Package Manager
2 Enter your password if it prompts for it
3 Hit the 'RELOAD' button in the top left hand corner of the package manager

Hope it works! Tell me if it does.

---

