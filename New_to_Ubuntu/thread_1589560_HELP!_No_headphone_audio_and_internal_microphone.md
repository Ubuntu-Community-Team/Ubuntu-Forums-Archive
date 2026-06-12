---
title: "HELP! No headphone audio and internal microphone"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by Saracho on 2010-10-06
Hello!!

I have a SONY VAIO VPCM121AX netbook  and it seems that when I installed ubuntu some drivers failed to install.

1. When I plug the headphones the speakers go blank as one would expect but the headphones don't work. No sound comes out.

2. The internal microphone doesn't work.

What can I do?:confused:

---

### Post by bprins on 2010-10-06
Which version of ubuntu are you running?

Not to push you into maverick, but with Ubuntu 10.10 (maverick) comes a great deal on sound improvements (alsa, pulse, driver support).

If your not running maverick already, you might want to give it a try.

---

### Post by Djalmahal on 2010-10-06
Open a terminal and type

alsamixer

It will come up with a windows where you can see and adjust master volume, headphone etc, maybe you can tweak it there.

Also under Preferences>Sound>Output you can manually switch between speakers and headphones, see if this can fix it even though it's no final solution

---

### Post by Saracho on 2010-10-06
> **bprins said:**
> Which version of ubuntu are you running?

Not to push you into maverick, but with Ubuntu 10.10 (maverick) comes a great deal on sound improvements (alsa, pulse, driver support).

If your not running maverick already, you might want to give it a try.

Well... i think this is ubuntu netbook remix? Ubuntu-Netbook 10.04 "Lucid Lynx" - Release i386

---

### Post by Saracho on 2010-10-06
> **Djalmahal said:**
> Open a terminal and type

alsamixer

It will come up with a windows where you can see and adjust master volume, headphone etc, maybe you can tweak it there.

i typed alsamixer and

the master has 93
speaker has 100-100
pcm-99-99
front mic boost 0-0
mic boost 0-0
beep 0-0

what does this mean and how do i tweak it?

---

### Post by Djalmahal on 2010-10-06
There should be also a headphone section, if it doesn't show up it probably means it's not recognized.

Go into the Sounds>Output section and see if it comes up there.

Tweaking means that in alsamixer you can change levels with the up down left right keys.

---

### Post by Saracho on 2010-10-06
> **Djalmahal said:**
> There should be also a headphone section, if it doesn't show up it probably means it's not recognized.

Go into the Sounds>Output section and see if it comes up there.

Tweaking means that in alsamixer you can change levels with the up down left right keys.

there isn't a headphone section and i tried tweaking the alsamixer and it didnt work

---

### Post by Djalmahal on 2010-10-06
That means Ubuntu doesn't detect your audio jack. Did you look around in the forums for similar problems with your type of netbook?

---

### Post by Saracho on 2010-10-07
> **Djalmahal said:**
> That means Ubuntu doesn't detect your audio jack. Did you look around in the forums for similar problems with your type of netbook?

Yeah, but i didn't see anything like it... how can i find out the hardware specs so i can look for the drivers?

---

### Post by Namara_the_Roatian on 2010-10-18
I've been having the same problems with my Asus Eee PC - running Ubuntu 10.04 Lucid Netbook edition. And also, like the OP, any sound settings don't even show the headphone jack or the microphone as an option to mess around with in the first place. Internal mic doesn't work and I have a joint headphone/microphone jack that isn't working, although the speakers do shut off when I plug in headphones - there just isn't any sound.

I've found several links illustrating how to fix the problem, but I'm too much of a newbie to try any of them. (i.e. Add *these* lines to *this* in *this thing*... what!?) I'm ignorant and need specific step-by-step instructions... 

I'm going to upgrade to Maverick and see if that helps...

In the meantime, here are the links I found if anyone can translate into "Baby Ubuntu User" terms so we can try them out:

This one is in Spanish, but a lot of people had luck with it --> [http://www.ubuntu-es.org/node/137762](http://www.ubuntu-es.org/node/137762)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/580183) (scroll through the comments, there are several solutions that people found [including my first link])

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/headphones-not-working-on-netbook-832425/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/headphones-not-working-on-netbook-832425/)

This seems to be a common problem - just run a search for it and you get a zillion hits. :-/


UPDATE: I upgraded to Maverick and my headphone jack now works. My internal microphone, however, still does not. Glad to at least have the headphones working, though. :-)

---

