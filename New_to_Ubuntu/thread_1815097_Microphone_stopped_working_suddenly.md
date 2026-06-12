---
title: "Microphone stopped working suddenly"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by rcktsingh on 2011-07-30
Hi All,

I am a very very disappointed Ubuntu "customer" here. About couple of weeks back, after extensive google search for about 3 hours, I fixed my microphone(which wasn't working at all). It worked perfectly fine when suddenly two days back, **_it stopped working again_**. I vaguely remember I had gone to some file and added a line to make the system recognize my Sony Vaio "something"( that's all I remember).

I had to switch back to Windows to attend an important skype meeting(kind of embarrassing in front of my colleagues that I had to take a 1 min timeout for that). 

All I need is a stable machine so I can work(which is why I like using a Linux machine) and have little bit of  fun at leisure time. Can't Ubuntu provide even that much to me? I am really disappointed at coming every other day with a "HEELLLPPP" message to fix every little problem. I don't have time to do all that every day. Hope Ubuntu/Canonical understands the value of its user's time. 

I use a Ubuntu 10.04, Sony Vaio system. Card: HDA Intel. Chip: Realtek ALC262. I have tried the several suggestions available, eg. playing with alsamixer/pavucontrol but nothing seems to be helping!

Any help is appreciated and please let me know if you need any additional information about my system. 

Thank you!

---

### Post by gordintoronto on 2011-07-30
Laptop sound has changed a lot since 10.04, almost all for the better. Would you consider trying a LiveCD of 11.04?

---

### Post by IWantFroyo on 2011-07-30
Natty and Maverick ship with newer kernels, and those are more likely to work.

Remember, the guys at your computer company need to spend a while making their computers work with Windows, and they're paid for it. People like me make Linux and Ubuntu as a hobby, and we need to consider drivers for computers a DOZEN companies are making.

We respect your opinion, but please try to resolve your problem before flaming, or at least testing the system OUTSIDE of a work environment before using it there.

EDIT: Interpreted your post wrong. Thought you were flaming. Sorry :)

---

### Post by Untold on 2011-07-31
I had the same problem while usin Mint 10.  After the Alsamixer and pulse audio did not fix it I ran:

"sudo apt-get upgrade"  after reading some forums and it worked.  I hope this helps.

---

