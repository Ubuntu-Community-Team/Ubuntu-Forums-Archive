---
title: "Problems - Duel boot with Vista"
date: 2011-02-06
forum: New to Ubuntu
---

### Post by marnierobbins on 2011-02-06
Hi.

I am a complete newbie when it comes to Ubuntu but I've read good things about it online.  When it comes to computers well what can I say except that my computer illiterate family thinks I know everything about computers (and I'll just let them keep thinking that!) truth is that they just know very little . . . which makes me look good!  LOL.   I just have an average knowledge of computers - I'm an animal person, not a computer person!  

I am using a Toshiba Satilite X200 and running Vista Ultimate (which I hate!)  So I thought I would give Ubuntu 10.10 a try.   I installed it yesterday using the download that comes with the windows installer. I did an update and downloaded the software I wanted - open office & gimp. Then restarted. Now I get the following message while  Ubuntu is booting. 

"Modprobe: Fatal: Could not load/lib/Modules/2.6-35-25-generic modules.dep: No such file or dirrectory"

Didn`t really pay attention to the message because Ubuntu seemed to work fine once it was started.   So I turned the computer on this morning to do some work which was going fine until all of a sudden the screen seemed to do a quick jump and then all my fonts went blurry and incomplete.  So I rebooted, thinking it might help.  When Ubuntu restarted my toolbars were not there - nothing but wallpaper.  Without the toolbars I have no idea how to get to a menu or well . . . do anything at all.

So right now I am back to using Vista (sigh).  Can anyone tell me what I can do to get Ubuntu working?

---

### Post by Hedgehog1 on 2011-02-06
> **marnierobbins said:**
> Hi.

I am using a Toshiba Satilite X200 and running Vista Ultimate (which I hate!)  So I thought I would give Ubuntu 10.10 a try.   I installed it yesterday using the download that comes with the windows installer. I did an update and downloaded the software I wanted - open office & gimp. Then restarted. Now I get the following message while  Ubuntu is booting. 

"Modprobe: Fatal: Could not load/lib/Modules/2.6-35-25-generic modules.dep: No such file or dirrectory"

Didn`t really pay attention to the message because Ubuntu seemed to work fine once it was started.   So I turned the computer on this morning to do some work which was going fine until all of a sudden the screen seemed to do a quick jump and then all my fonts went blurry and incomplete.  So I rebooted, thinking it might help.  When Ubuntu restarted my toolbars were not there - nothing but wallpaper.  Without the toolbars I have no idea how to get to a menu or well . . . do anything at all.

So right now I am back to using Vista (sigh).  Can anyone tell me what I can do to get Ubuntu working?

Welcome to the forums, Marnie!

If you are still seeing just wallpaper, please try this:

Pres [Alt] + [F2].  With any luck, a 'run application' window will come up.

In the 'run application' window type the command:

```
gnome-terminal
```

If you do this, do you get a terminal at all?  if you can, then try this command in the terminal that just came up:

```
gnome-session
```

If you get the GUI - copy your documents to a USB stick or external hard drive quickly!

If you get errors, please tell us what they are.

Then we will look at why your laptop acted up...

OH - Please let us know if the laptop works for a while if it is allowed to cool down.


*p.s. I like your Freudian slip, calling it 'Duel' rather than 'Dual' boot.    I see the 2 OS's standing at 20 paces*...
:KS

---

### Post by marnierobbins on 2011-02-06
LOL@me and the DUEL thing.

just went and tried it . . . alt+f2 that is . . . nothing happens.

---

### Post by matt_symes on 2011-02-06
Hi

Try pressing CTRL ATL and t at the same time to get the terminal.

Kind regards

---

### Post by Hedgehog1 on 2011-02-06
Well Darn!  It was SUCH a good idea, too.

Try that [cntl]+[alt]+t first that matt_symes said (I am still learning, too!).

If you still cannot get the terminal, then:

To separate out some possibilities, would you reboot the Toshiba and bring up vista?

Then let us know if Vista comes up OK or not.

---

### Post by Hedgehog1 on 2011-02-06
I just noticed on your first post, you said you were back to running vista.

I guess this means that you are able to reboot into vista OK then.

Soooooo... Never mind that request.

Was this a Wubi install of Ubuntu (installed from inside vista)?

---

### Post by marnierobbins on 2011-02-08
Vista boots fine.

I reinstalled my Ubuntu which seems to have gotten rid of part of the problem.  I still am getting a fuzzy looking screen after a while.  I'm inserting a screen shot here.

hummm, well it looks ok in the thumbnail I just posted, but it doesn't look ok on screen!   The right side of my monitor is fine, everything else is degrated.

---

