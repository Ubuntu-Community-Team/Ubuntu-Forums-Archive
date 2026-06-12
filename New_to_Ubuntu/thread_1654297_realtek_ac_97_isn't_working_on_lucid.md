---
title: "realtek ac 97 isn't working on lucid"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by Linyx on 2010-12-28
[SIZE=2]I had just replace my old PC to Athlon X2, and now when i check my pre-installed ubuntu on it, sound isn't working, 

I try to run from terminal "**alsamixer**", it couldn't found anything...when i type "sudo apt-get install alsamixer" > [B]E: Couldn't find package alsamixer.
[/B]
Moreover, i had also check from Live-CD, my sound isn't working....

when i open up my sound-preferences, hardware & input tab tab is empty, but in output, their is only one thing >** Dummy-output** strereo...

I have attached a **screen-shot** as well....
[/SIZE]

---

### Post by VonSpyder on 2010-12-28
is it disabled in bios?

---

### Post by Linyx on 2010-12-28
> **VonSpyder said:**
> is it disabled in bios?

[SIZE=2]well, i didn't check it in BIOS, but i problem is solved now, because their was a problem in Card..[/SIZE]

---

### Post by rmockler on 2010-12-28
Would you please tell us how you got the problem fixed in the card?
I believe I have a problem in my card also.

---

### Post by Linyx on 2010-12-28
> **rmockler said:**
> Would you please tell us how you got the problem fixed in the card?
I believe I have a problem in my card also.

[SIZE=2]i just bring a PC from one of my friend (x2) but sound didn't work in that, even i had try a live CD.....tabs are empty as i had posted in my 1st post....[/SIZE]I [SIZE=2]Didn't fixed it...thats why can't help you with that...but if you wish i will mark thread as unsolved thread,...may someone help..
[/SIZE]

---

### Post by VonSpyder on 2010-12-28
since i amfamiliar with this card and have had ubuntu versions 8.10, 9.04, 9.10, 10.04, and 10.10 work succesfully with it then I suggest to any who have this problem check the following:

Is the card enabled in bios?
are the speakers plugged into the correct 3.5mm jack?
is there another soundcard installed on top of it?
have you recently installed a sound application like jack, alsa or pulse audio?

---

### Post by rmockler on 2011-02-03
Wow, looking back this problem was in last year's calendar.  But I still have the problem, so here is my comment: I pass all the points in the post prior to this one, with one caveat.  If I plug in external speakers of any sort or headphones, including microphone, they all work great.  The failure is with the internal speakers - this is a laptop, I never carry external speakers with me in a work situation, but would still like to have audio through the internal speakers.  I have worked alsamixer to death in the last couple of months, and still no success.  I am open to any and all suggestions.

---

### Post by Linyx on 2011-02-04
> **rmockler said:**
> Wow, looking back this problem was in last year's calendar.  But I still have the problem, so here is my comment: I pass all the points in the post prior to this one, with one caveat.  If I plug in external speakers of any sort or headphones, including microphone, they all work great.  The failure is with the internal speakers - this is a laptop, I never carry external speakers with me in a work situation, but would still like to have audio through the internal speakers.  I have worked alsamixer to death in the last couple of months, and still no success.  I am open to any and all suggestions.

Can you post the screen-shoot of the tab in sound-preference, As i have in my 1st post.....

---

