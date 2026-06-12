---
title: "No Sound at all"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by dmaxel on 2010-08-18
Hi everyone,

I put the latest Kubuntu (10.04.1) on my USB drive so that I could test it out after being an avid Ubuntu user. Everything at least seems to be working fine, however there is no sound whatsoever! This is really strange as there are completely no problems in Ubuntu, but absolutely no sound in Kubuntu. I've been playing around with every single switch that Kmixer has to offer me (even what adding all possible channels, and changing the default channel), and alsamixer shows thumbs up too.

Could I get some help with this? Thanks :)

---

### Post by mastablasta on 2010-08-18
> **dmaxel said:**
> Hi everyone,
 
I put the latest Kubuntu (10.04.1) on my USB drive so that I could test it out after being an avid Ubuntu user. Everything at least seems to be working fine, however there is no sound whatsoever! This is really strange as there are completely no problems in Ubuntu, but absolutely no sound in Kubuntu. I've been playing around with every single switch that Kmixer has to offer me (even what adding all possible channels, and changing the default channel), and alsamixer shows thumbs up too.
 
Could I get some help with this? Thanks :)
 
 
what kind (type) of sound output is set in sound preferences?

---

### Post by dmaxel on 2010-08-18
Right now I have it set at "Master Front", although I've tried "Front" as well. Those are pretty much the only two possible true output channels.

If you mean something else, you'll have to show me where it is, as I'm not familiar with KDE (thus wanting to learn it :P)

EDIT: I went into System Settings --> Multimedia and chose an output device and clicked on Test. When I did that it played a sound, while the rest didn't (The sound cards seems to have an Analog and Digital output, only the Analog one works, which is fine). However, that "working" output cannot be "preferred" any farther up the list, so I'm stumped.

---

### Post by Ms_Angel_D on 2010-08-18
Not trying to be funny or anything but have you made sure you don't have headphones plugged in? I re-installed ubuntu twice one time trying to figure out what was wrong with my sound before I realized my kid had stuck my headphones in the jack and that's why I had no sound...lol.

---

### Post by Zeppelin! on 2010-08-18
I'm actually having the same problem with Ubuntu.

Basically:
9.10 - Could play laptop speakers, didn't test headphones
10.04 - No sound, headphones or laptop speakers.

Mind you, as I'm currently trying to get wireless working this issue is on my backburner.

---

### Post by dmaxel on 2010-08-18
> **Ms_Angel_D said:**
> Not trying to be funny or anything but have you made sure you don't have headphones plugged in? I re-installed ubuntu twice one time trying to figure out what was wrong with my sound before I realized my kid had stuck my headphones in the jack and that's why I had no sound...lol.
Hahaha well actually, my setup is like this right now: I have two boxes next to each other. Since I don't have any hardware to make the sound from two computers go through one speaker set, I have the speaker set plugged into one computer's output jack in the back and have my headphones plugged into the output jack in the back of the other computer. So yes, I have headphones plugged in, but intentionally (as replacement for speakers), and plugged into the back and not the front. I still don't get though that Ubuntu could be so easy as to just unmute and done while in Kubuntu it's a completely different story lol.

(Yes, I'm talking about desktops, sorry for not mentioning it earlier in case that helps.)

---

### Post by simosx on 2010-08-18
For your audio problems, the new way to collect information is described at 
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

In a nutshell, run

[FONT="Courier New"]ubuntu-bug audio[/FONT]

and follow the wizard.

Once you publish the report, write up here your launchpad.net bug URL.

---

### Post by dmaxel on 2010-08-18
> **simosx said:**
> For your audio problems, the new way to collect information is described at 
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

In a nutshell, run

[FONT="Courier New"]ubuntu-bug audio[/FONT]

and follow the wizard.

Once you publish the report, write up here your launchpad.net bug URL.Alright, I'll do that as soon as I feel good enough to go back upstairs (workouts are killers :P).

---

