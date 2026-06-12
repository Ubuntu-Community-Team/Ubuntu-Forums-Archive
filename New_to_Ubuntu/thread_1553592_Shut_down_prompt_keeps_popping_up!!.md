---
title: "Shut down prompt keeps popping up!!"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by lordylordy on 2010-08-15
CAn Anyone help, it pops up every three secs or so & I'm unAble to do Anything - pleAse ignore cAp A's!!
 
Using 10.04, And complete newb

---

### Post by jmfal on 2010-08-15
welcome to ubuntu

need more info, is warning showing a message or error code?

are you on a laptop or a pc?

is your rig running hot?

did have problems installing ubuntu?

---

### Post by lordylordy on 2010-08-15
Hi

no there's no warning, the machine is working fine otherwise.  It's a PC, FujitsuSiemens, about 3 years old.  No probs installing.  I've been running 10.04 (clean install) for about a month i guess, no problems at all.  Went on hols for a week, started it this morning and it's been popping up the "Shut Down The Computer" window constantly.  Almost like there's a command going on in the background.  Infuriating.

Thanks in anticipation

---

### Post by jmfal on 2010-08-15
Sorry it took so long to reply, had to go to work.

tried to do some research didn`t find anything.

one did say power supply finally went out.

could be a major problem some where, or , I don`t know!

anyway try=system>administration>system monitor>proccesses
and see if an app is running that you know you shut-down

I`m on the net and the only thing that is running is gnone-system-monitor, should be the same for you. If that doesn`t find any thing try in a terminal

        ```
 top
```

this command will show all proccesses that are running, maybe there will be a message or error code if something is going wrong.

post it so somebody can help you!

you can try and run a memtest=restart>boot menu>memtest
to see if your memory is good, should run it at least 2-3hrs, 6-8 is better

or, open up the case and check for loose connections (power down first) make sure memory is seated securly, make sure cpu fan spins freely

just giving some options

F.Y.I. Give as much info as you can as many pass over your thread when they have to try and read your mind, don`t be scared to ask a stupid question, as the only stupid question is one that isn`t asked..

good luck, I`m going to bed

---

### Post by lordylordy on 2010-08-20
thanks to those that replied.  I have now discovered that it isn't just my install that does it.  Live CDs do it too - but get this...

All gnome distros that I have tried on live cds have done exactly the same thing!!

a kde distro (OpenSUSE) didn't!!

I'm d/ling PcLinuxOs KDE to see if it is better.

I've reset my CMOS, that doesn't help.

Weird.

---

### Post by jonnywombat on 2010-08-20
what happens if you log into failsafe gnome session?

---

### Post by lordylordy on 2010-08-20
how do i do that?

---

### Post by jonnywombat on 2010-08-20
Assuming you have set things up so you have to enter your password to log in...

Boot the machine upto the log in screen.

At the bottom of the screen in the right hand corner (i think) you will see a box marked session, which will have the word Gnome in it.

Click on that box and select Failsafe Gnome

Log in as normal.

---

### Post by lordylordy on 2010-08-20
figured out the failsafe and yes, it does it then too!

---

### Post by kroq-gar78 on 2010-08-20
just saying but probably not, but can it be a virus?

---

### Post by lordylordy on 2010-08-21
Don't think it can be viral on a fresh install or live CD

---

### Post by lisati on 2010-08-21
> **lordylordy said:**
> Don't think it can be viral on a fresh install or live CD

I agree that it's unlikely to be [malware]("http://en.wikipedia.org/wiki/Malware"). 

On my machines, the "shutdown" dialog pops up if I tap the power key. I'm wondering if something is intermittently mimicking this action, even unintentionally.

---

### Post by lordylordy on 2010-08-21
Well, I've tried lots of Gnome kernel live CDs and they all do it.  I've just run PCLOS KDE and all was fine, am d/l Kubuntu and will try that but it certainly seems that my PC has developed a dislike of Gnome kernel distros.  Presumably it's something in my BIOS but I've flashed etc and still no joy. 

Just plain weird :-k     ](*,)

---

### Post by kroq-gar78 on 2010-08-21
oh didn't read that part sorry

---

