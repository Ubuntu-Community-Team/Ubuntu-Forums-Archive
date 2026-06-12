---
title: "Installed Ubuntu 10.04, boots and loads fine, but no keyboard function"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by t10opila on 2010-05-24
installed Ubuntu 10.04 this weekend, boots and loads fine, but no keyboard function. it worked on initial install, but now i have no function at all, mouse works and i can use on screen keyboard to log on, i have tried a number of different keyboard options (international with deadkeys and euro symbol on 5 key). anyone have this problem?

---

### Post by bodhi.zazen on 2010-05-24
Not sure if it helps, but what kind of a keyboard ?

Can you try an alternate keyboard or confirm that your keyboard still works (not something silly like a wireless keyboard out of batteries ... )

---

### Post by t10opila on 2010-05-24
its a laptop. do not have another keyboard to plug in, still functions properly in windows

---

### Post by Sealbhach on 2010-05-24
OK, one thing you could try. Reboot the computer, when it starts up, select recovery mode. Then choose drop to root shell prompt. Once there, run this command:

  ```
sudo dpkg-reconfigure -phigh xserver-xorg
```


then

```
reboot
```

See if it helps any. 

Also, in recovery mode you will be able to install updates and repair broken packages, though you will need to have your laptop connected to the internet with a wired connection.

.

---

### Post by simosx on 2010-05-24
> **t10opila said:**
> installed Ubuntu 10.04 this weekend, boots and loads fine, but no keyboard function. it worked on initial install, but now i have no function at all, mouse works and i can use on screen keyboard to log on, i have tried a number of different keyboard options (international with deadkeys and euro symbol on 5 key). anyone have this problem?

This might be a BIOS bug. Can you tell us what brand and model of computer/laptop you have? If you have laptop, do you try to run the laptop from battery instead of the mains?

---

### Post by t10opila on 2010-05-25
> **simosx said:**
> This might be a BIOS bug. Can you tell us what brand and model of computer/laptop you have? If you have laptop, do you try to run the laptop from battery instead of the mains?

bios were updated yesterday, no luck

---

### Post by t10opila on 2010-05-25
> **Sealbhach said:**
> OK, one thing you could try. Reboot the computer, when it starts up, select recovery mode. Then choose drop to root shell prompt. Once there, run this command:

  ```
sudo dpkg-reconfigure -phigh xserver-xorg
```


then

```
reboot
```

See if it helps any. 

Also, in recovery mode you will be able to install updates and repair broken packages, though you will need to have your laptop connected to the internet with a wired connection.

.

no keyboard function in recovery menu either

---

### Post by ashwinhgtx on 2010-05-25
Just curious, are you typing your posts with an on screen keyboard?

---

### Post by t10opila on 2010-05-25
> **ashwinhgtx said:**
> Just curious, are you typing your posts with an on screen keyboard?

im using windows. . . keyboard still works fine there

---

### Post by Elfy on 2010-05-25
It might help if you said what model laptop it is - a couple of people have asked.

---

### Post by t10opila on 2010-05-25
acer aspire 3000, bios updated yesterday, keyboard is international i suppose. . . has the euro symbol on the 5 key

---

### Post by QIII on 2010-05-25
Is this a stand-alone installation, or a Wubi installation?

---

### Post by t10opila on 2010-05-25
stand alone, a friend of mine has a boot disc. and everything seemed to work fine the day it was installed, starting the next day i had no keyboard. its a mess and a headache all rolled into one

---

### Post by QIII on 2010-05-25
> **t10opila said:**
> stand alone, a friend of mine has a boot disc. and everything seemed to work fine the day it was installed, starting the next day i had no keyboard. its a mess and a headache all rolled into one

I'll say!

I was on a coffee break and peeked in.  Don't really have time now to look, but if this isn't solved by the time I get the "energetic" young ones to bed tonight, I'll see what I can dig up.

Think positive.  There is a solution.

---

### Post by t10opila on 2010-05-25
> **QIII said:**
> I'll say!

I was on a coffee break and peeked in.  Don't really have time now to look, but if this isn't solved by the time I get the "energetic" young ones to bed tonight, I'll see what I can dig up.

Think positive.  There is a solution.

take your time, i still have windows up and running. im in no hurry

---

### Post by Cincinnatux on 2010-05-25
I'm having a similar problem.  I upgraded from Jaunty to Lucid and rebooting kept locking up at 'checking battery'.  When I tried to boot into safe mode it repeatedly restarted mythtv-backend even in CLI.  I removed mythtv then re-installed it and that allowed me then to boot as far as the login screen, at which point I discovered that neither keyboard nor mouse worked.  I swapped out keyboards and it made no difference; besides, the keyboard still worked at Grub, just not at the login screen.  Not sure what to do next.

---

