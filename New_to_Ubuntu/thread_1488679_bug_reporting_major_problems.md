---
title: "bug reporting major problems"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by pdlethbridge on 2010-05-20
I tried and failed to find anywhere to report a bug. I keep getting the info/tutorial pages. It would make more sense to make it easier to report a bug as most users are not that computer savvy. If I don't know the package, so what, if I explain it clearly and they have my email they can ask me a question. Please make bug reporting simpler, I've been able to do it before, but you are making it impossible.

---

### Post by philinux on 2010-05-20
Ok describe your bug see if we can get you sorted.

---

### Post by pdlethbridge on 2010-05-20
Okay. This morning after updating 10.04 and rebooting, I tried to install a CD from the Watchtower Society, and was told I couldn't. Wait a minute, I know a bad file from a good one and the system would not let me install the program.That wasn't the only executable program I couldn't install with wine, RTS10.exe from [http://www.atlasrr.com/righttrack.htm](http://www.atlasrr.com/righttrack.htm) was also denied. I've used these files since I was using 6.04. I have gone back to 9.04 for that and other reasons.
I consider this a bug, also I would like to report a bug in tvtime as I'm not able to get my TV capture card running.I tried this from one of the posts here and it worked in 9.04 but not 9.10 and 10.04. A suggestion to back date the kernel is beyond me. 
When I was in the Navy 40 years ago I visited england and traveled to see relatives in Lincoln.

sudo nano /etc/modprobe.d/saa7134        hit enter
next you will be asked for your password enter and press the enter key.

now in the nano editor, type the following lines pressing enter at the end of each one.

alias chr-major-81 videodev       enter
alias chr-major-81-0 saa7134      enter
options saa7134 card=42 tuner=43 oss=1       enter

now press the control key (ctrl) and the "x" key at the same time
you will be asked if you want to save file: saa7134 
say yes by pressing "y" key on the keyboard.

---

### Post by philinux on 2010-05-20
> **pdlethbridge said:**
> Okay. This morning after updating 10.04 and rebooting, I tried to install a CD from the Watchtower Society, and was told I couldn't. Wait a minute, I know a bad file from a good one and the system would not let me install the program.That wasn't the only executable program I couldn't install with **wine,** RTS10.exe from [http://www.atlasrr.com/righttrack.htm](http://www.atlasrr.com/righttrack.htm) was also denied. I've used these files since I was using 6.04. I have gone back to 9.04 for that and other reasons.
I consider this a bug, also I would like to report a bug in tvtime as I'm not able to get my **TV capture card** running.I tried this from one of the posts here and it worked in 9.04 but not 9.10 and 10.04. A suggestion to back date the kernel is beyond me. 
When I was in the Navy 40 years ago I visited england and traveled to see relatives in Lincoln.

sudo nano /etc/modprobe.d/saa7134        hit enter
next you will be asked for your password enter and press the enter key.

now in the nano editor, type the following lines pressing enter at the end of each one.

alias chr-major-81 videodev       enter
alias chr-major-81-0 saa7134      enter
options saa7134 card=42 tuner=43 oss=1       enter

now press the control key (ctrl) and the "x" key at the same time
you will be asked if you want to save file: saa7134 
say yes by pressing "y" key on the keyboard.


Ok.

1. Obviously a wine bug.

```
ubuntu-bug wine
```

2. Not sure but since it's a Tv capture card and the driver should be in the kernel I would do this.

```
ubuntu-bug linux
```

Let us know how you get on.

---

### Post by pdlethbridge on 2010-05-20
Well, the wine wasn't a problem, just the operator. I'll get back to you when I get the info you need on the tv card

---

### Post by pdlethbridge on 2010-05-20
I just submitted this:Bug #583550 about tvtime

---

