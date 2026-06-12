---
title: "How do I remove FGLRX?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-05-03
I accidentally hit "activate" under hardware drivers. Ubuntu then installed the catalyst 9.3 drivers, which don't work under 9.04 and I guess Ubuntu isn't smart enough to know this.

I am at the shell. I have already done 
```
sudo apt-get remove xorg-driver-fglrx
```,
but i'm still getting a fragmented screen. 
How do i remove FGLRX?
what other commands do i need to issue?
is there a way to deactivate the driver from shell?

---

### Post by asuastrophysics on 2009-05-03
C'mon this is ridiculous I have no computer at all now. 
I've followed the ONLY necessary step that anyone seems to know about and it still fails. 
I can SEE FGLRX being loaded while running recovery console.

I need help. There has to be some other command that will prevent FGLRX from running at startup. What is it? 

Please i really need help. Even 6 months of using ubuntu isn't enough. I have no idea how this thing works.

---

### Post by clhsharky on 2009-05-03
What video chip do you have and did you restart your computer?

---

### Post by asuastrophysics on 2009-05-03
I have:
ATI Radeon HD 2400 PRO

Yeah, the computer was restarted, because after the scrambled desktop appears, not even CTRL ALT F1 works

How do I remove it?

---

### Post by clhsharky on 2009-05-04
with Synapic search ATI and check complete removal xorg-driver-fglrx, restart and try again.

---

### Post by Didius Falco on 2009-05-04
```
sudo apt-get purge xorg-driver-flgrx
```[FONT=monospace]

followed by 

[/FONT]```
sudo apt-get install xorg-video-radeon
```This will purge everything to do with the flgrx driver and install the xorg 2D driver.


then restart x by typing:

```
sudo /etc/init.d/gdm restart
```That *should* do it - I've never been in this position, so I have no personal experience with it...

I hope it helps...

On Edit: You may need to reinstall xserver-xorg-video-ati - try the steps above first, if they don't work, try them again with ```
sudo apt-get install xserver-xorg-video-ati
``` first....

Again, I'm going by what I could dig up searching, not by practical experience. It seems like the logical progression of steps to me, and it surely won't leave you any worse off....

---

### Post by asuastrophysics on 2009-05-04
> **clhsharky said:**
> with Synapic search ATI and check complete removal xorg-driver-fglrx, restart and try again.

I don't have X. X is gone, hosed by ATI.

I am left with a black screen, the shell. 
I know there's a way to start a version of synaptic from the shell, but I don't know what it is. 

I tried > sudo apt-get install xorg-video-radeon
and it tells me it can't find it. 

How do I launch the shell version of synaptic?

---

### Post by clhsharky on 2009-05-04
[sudo apt-get update
sudo apt-get upgrade]

than repeat as Didius Falco codes

---

### Post by Didius Falco on 2009-05-04
> **asuastrophysics said:**
> I don't have X. X is gone, hosed by ATI.

I am left with a black screen, the shell. 
I know there's a way to start a version of synaptic from the shell, but I don't know what it is. 

I tried 
and it tells me it can't find it. 

How do I launch the shell version of synaptic?

```
gksudo synaptic
```

---

### Post by ii Candor ii on 2009-05-04
I am also having the same issue. What is the shortcut key to launch the terminal? (Since I have no screen).

---

### Post by asuastrophysics on 2009-05-04
> **Didius Falco said:**
> ```
gksudo synaptic
```

i get WARNING ++: cannot open display:

doesn't launch. I KNOW there's a command for it. i've used it before in dire cases like this...

---

### Post by Didius Falco on 2009-05-04
> **ii Candor ii said:**
> I am also having the same issue. What is the shortcut key to launch the terminal? (Since I have no screen).

<Alt>F2

If you have a command line, you, in effect, already have a terminal running...

---

### Post by adult swim on 2009-05-04
have you already ran ```
sudo apt-get remove xorg-driver-fglrx

sudo apt-get install xserver-xorg-video-ati
```
as far as i know there is no program that looks like synaptic package manager in the terminal.  sudo apt-get install and sudo apt-get remove are the same thing as selecting a package to be installed or deleted in synaptic package manager

---

### Post by ii Candor ii on 2009-05-04
> **Didius Falco said:**
> <Alt>F2

If you have a command line, you, in effect, already have a terminal running...

Thanks for your help. Can you please describe the keystrokes after I have pressed <Alt>F2? If I remember right I need to type the command, press <tab> press <space> (to check the 'run in terminal' box), then do I just press <enter> or do I need to tab over once or twice before pressing <enter>? 

Thank you again for the help. I'm working blind here :(

---

### Post by asuastrophysics on 2009-05-04
> **ii Candor ii said:**
> I am also having the same issue. What is the shortcut key to launch the terminal? (Since I have no screen).

Candor, what you're seeing is terminal. That's all you get. 

It asks you to login with your username and password. 
Do it. 
Then you are in terminal. 

...This is all because Ubuntu doesn't have a SAFE mode...

(No, recovery mode doesn't count, because it doesn't launch X)

---

### Post by asuastrophysics on 2009-05-04
> **adult swim said:**
> have you already ran ```
sudo apt-get remove xorg-driver-fglrx

sudo apt-get install xserver-xorg-video-ati
```
as far as i know there is no program that looks like synaptic package manager in the terminal.  sudo apt-get install and sudo apt-get remove are the same thing as selecting a package to be installed or deleted in synaptic package manager

Yep, already tried that. FGLRX still loads.
But I managed to fix my problem. I ran the NEW 9.4 ATI installer.run file from shell and it works!!

But that doesn't address the problem at hand here. This is a serious bug. It bluntly ignores any removal attempts and continues to load on startup. BUG.

BTW, as soon as i find that synaptic manager for shell, i will post the command to launch it. I know i've used it before :)

---

### Post by ii Candor ii on 2009-05-04
> **asuastrophysics said:**
> Candor, what you're seeing is terminal. That's all you get. 

It asks you to login with your username and password. 
Do it. 
Then you are in terminal. 

...This is all because Ubuntu doesn't have a SAFE mode...

(No, recovery mode doesn't count, because it doesn't launch X)

Actually I am not seeing anything (except some garbled colors). Are you saying I need to hold <alt>F2 at bootup and it will boot into a screen I can see?

Sorry for the noob questions.

---

### Post by Didius Falco on 2009-05-04
> **asuastrophysics said:**
> Yep, already tried that. FGLRX still loads.
But I managed to fix my problem. I ran the NEW 9.4 ATI installer.run file from shell and it works!!

But that doesn't address the problem at hand here. This is a serious bug. It bluntly ignores any removal attempts and continues to load on startup. BUG.

BTW, as soon as i find that synaptic manager for shell, i will post the command to launch it. I know i've used it before :)

Did you try the purge option I listed? I also ran across a post that said they had to ```
sudo apt-get install xserver-xorg-video-ati
```

Before they could completely remove the proprietary driver. At any rate, I'm glad you got it fixed...

---

### Post by asuastrophysics on 2009-05-04
> **ii Candor ii said:**
> Actually I am not seeing anything (except some garbled colors). Are you saying I need to hold <alt>F2 at bootup and it will boot into a screen I can see?

Sorry for the noob questions.

Candor, if you see garbled colors, step back for just a sec.
 
ALT+F2 might not work, because your keyboard and mouse don't have any input.

So do this:

Step 1) Restart, and select "recovery mode"
Step 2) In "recovery mode" select "Shell with networking"
Step 3) It will ask you to log in. Do it. 
Step 4) Congratulations, you are in terminal!
Tell me when you get here ;)

---

### Post by Didius Falco on 2009-05-04
> **ii Candor ii said:**
> Actually I am not seeing anything (except some garbled colors). Are you saying I need to hold <alt>F2 at bootup and it will boot into a screen I can see?

Sorry for the noob questions.

You should just reboot into the Recovery mode and drop to a root shell with network support. That is the equivalent of a terminal and you can run commands from there.

BTW, in the future, you should start a new thread for your problem/question. It's considered rude to "hijack" a thread someone else started.

---

### Post by ii Candor ii on 2009-05-04
> **asuastrophysics said:**
> Yep, already tried that. FGLRX still loads.
But I managed to fix my problem. I ran the NEW 9.4 ATI installer.run file from shell and it works!!

But that doesn't address the problem at hand here. This is a serious bug. It bluntly ignores any removal attempts and continues to load on startup. BUG.

BTW, as soon as i find that synaptic manager for shell, i will post the command to launch it. I know i've used it before :)

Can you please post the commands you ran to fix this?

---

### Post by asuastrophysics on 2009-05-04
> **ii Candor ii said:**
> Can you please post the commands you ran to fix this?

Well, before i do that, i need to know what kind of video card you have. 
can you please post the output of 
```
lspci | grep VGA
```

**the | key is right above enter (took me a while to figure this out)
** VGA must be in all caps

otherwise, i might be giving you the wrong driver for your card.

---

### Post by ii Candor ii on 2009-05-04
> **asuastrophysics said:**
> Candor, if you see garbled colors, step back for just a sec.
 
ALT+F2 might not work, because your keyboard and mouse don't have any input.

So do this:

Step 1) Restart, and select "recovery mode"
Step 2) In "recovery mode" select "Shell with networking"
Step 3) It will ask you to log in. Do it. 
Step 4) Congratulations, you are in terminal!
Tell me when you get here ;)

Alright I made it into the terminal.

Tried the following and it was still garbled after restarting x

```
sudo apt-get install xserver-xorg-video-ati
sudo apt-get purge xorg-driver-flgrx
sudo apt-get install xorg-video-radeon
sudo /etc/init.d/gdm restart
```

Also Falco - I didn't realize I was hijacking a thread. I just thought since it was a similar situation it would fit there. Will try to learn better ubuntuforum etiquette.

---

### Post by ii Candor ii on 2009-05-04
> **asuastrophysics said:**
> Well, before i do that, i need to know what kind of video card you have. 
can you please post the output of 
```
lspci | grep VGA
```

**the | key is right above enter (took me a while to figure this out)
** VGA must be in all caps

otherwise, i might be giving you the wrong driver for your card.

Output of that command:
```

07:02.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
```

The machine I'm running is a Dell PowerEdge 1800 server.

Thanks so much for your help.

---

### Post by asuastrophysics on 2009-05-04
> **ii Candor ii said:**
> Alright I made it into the terminal.

Tried the following and it was still garbled after restarting x

```
sudo apt-get install xserver-xorg-video-ati
sudo apt-get purge xorg-driver-flgrx
sudo apt-get install xorg-video-radeon
sudo /etc/init.d/gdm restart
```

Also Falco - I didn't realize I was hijacking a thread. I just thought since it was a similar situation it would fit there. Will try to learn better ubuntuforum etiquette.

wait, why did you do this?
```
sudo apt-get install xserver-xorg-video-ati
sudo apt-get purge xorg-driver-flgrx
sudo apt-get install xorg-video-radeon
sudo /etc/init.d/gdm restart
```

forget that for now, i just need you to be in the shell. i don't even think the radeon driver works with 9.04 anyway

---

### Post by ii Candor ii on 2009-05-04
> **asuastrophysics said:**
> wait, why did you do this?
```
sudo apt-get install xserver-xorg-video-ati
sudo apt-get purge xorg-driver-flgrx
sudo apt-get install xorg-video-radeon
sudo /etc/init.d/gdm restart
```

forget that for now, i just need you to be in the shell. i don't even think the radeon driver works with 9.04 anyway

Tried it based on a couple of comments earlier in the thread.

I'm in the terminal... waiting patiently :)

---

### Post by asuastrophysics on 2009-05-04
ok, in that black shell boring terminal:
Step 1) Enter This:
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```
**If it asks you to install anything, press Y**
Step 2) Enter This: 
```
sudo nano /etc/modules
```
look for any lines with "fglrx" in them. Delete them. 
Now close the editor with CTRL + X. It will ask you to save. Just press ENTER.
Step 3) Enter This:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Step 4) Enter This:
```
sudo nano /etc/X11/xorg.conf
```
It should have a line somewhere like this:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
```
Step 5) Change it to look just like this:
```
Section "Device"
	Identifier	"Configured Video Device"
        Driver 		"ati"
EndSection
```
Step6) Hit CTRL + X and then hit ENTER. 

Now restart! Hope this helps :popcorn:

---

### Post by Didius Falco on 2009-05-04
> **ii Candor ii said:**
> Tried it based on a couple of comments earlier in the thread.

I'm in the terminal... waiting patiently :)

n/m

---

### Post by ii Candor ii on 2009-05-04
> **asuastrophysics said:**
> ok, in that black shell boring terminal:
Step 1) Enter This:
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```
**If it asks you to install anything, press Y**
Step 2) Enter This: 
```
sudo nano /etc/modules
```
look for any lines with "fglrx" in them. Delete them. 
Now close the editor with CTRL + X. It will ask you to save. Just press ENTER.
Step 3) Enter This:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Step 4) Enter This:
```
sudo nano /etc/X11/xorg.conf
```
It should have a line somewhere like this:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
```
Step 5) Change it to look just like this:
```
Section "Device"
	Identifier	"Configured Video Device"
        Driver 		"ati"
EndSection
```
Step6) Hit CTRL + X and then hit ENTER. 

Now restart! Hope this helps :popcorn:

Doh! Still garbled after running going through these steps and rebooting. Any other ideas?

---

### Post by asuastrophysics on 2009-05-04
sorry for the delay i'm studyin' for a really important exam ;)

> **ii Candor ii said:**
> Doh! Still garbled after running going through these steps and rebooting. Any other ideas?

yes, try just running 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then ```
sudo /etc/init.d/gdm restart
```

if that doesn't work, 
```
sudo nano /etc/X11/xorg.conf
```

and change ```
Section "Device"
	Identifier	"Configured Video Device"
        Driver 		"ati"
EndSection
```
to this:
```
Section "Device"
	Identifier	"Configured Video Device"
        Driver 		"vesa"
EndSection
```

this is the fail-safe video driver. 
but i think that you had the **exact same problem** i had:
FGLRX is *still, somehow* running when you turn on your computer. 

how did you get to this black screen anyway?
i assume you were installing a graphics driver?
BTW, your card is not supported by ATI in the newest driver release. This would explain why you have dropped to the shell

---

### Post by ii Candor ii on 2009-05-04
Will try when I get home from work today.

I was trying to get the additional effects working. I installed Compiz and was trying to install an ATI driver. The graphics make it so slow that I don't think I can use it without proprietary drivers. I'll probably end up buying a new graphics card because ATI does not support mine yet.

---

### Post by Didius Falco on 2009-05-04
> **ii Candor ii said:**
> Will try when I get home from work today.

I was trying to get the additional effects working. I installed Compiz and was trying to install an ATI driver. The graphics make it so slow that I don't think I can use it without proprietary drivers. I'll probably end up buying a new graphics card because ATI does not support mine yet.

Yeah, you are in a Catch-22 as far as the ATI drivers go. The 9.4 drivers from ATI don't support those older cards and the 9.3 drivers that do support them don't work in Ubuntu 9.04.

---

### Post by Elfy on 2009-05-04
> I know there's a way to start a version of synaptic from the shell, but I don't know what it is. 

were you meaning aptitude

```
sudo aptitiude
```

---

### Post by asuastrophysics on 2009-05-04
hahaha thank you :guitar:

i knew i had used it before. that's exactly what i was thinking of. it's a nice tool if you're stuck in shell and don't remember how you installed it. 

thanks man!

---

### Post by ii Candor ii on 2009-05-04
> **asuastrophysics said:**
> sorry for the delay i'm studyin' for a really important exam ;)



yes, try just running 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then ```
sudo /etc/init.d/gdm restart
```

if that doesn't work, 
```
sudo nano /etc/X11/xorg.conf
```

and change ```
Section "Device"
	Identifier	"Configured Video Device"
        Driver 		"ati"
EndSection
```
to this:
```
Section "Device"
	Identifier	"Configured Video Device"
        Driver 		"vesa"
EndSection
```

this is the fail-safe video driver. 
but i think that you had the **exact same problem** i had:
FGLRX is *still, somehow* running when you turn on your computer. 

how did you get to this black screen anyway?
i assume you were installing a graphics driver?
BTW, your card is not supported by ATI in the newest driver release. This would explain why you have dropped to the shell
Tried all of this. Still garbled. Looks like I might be screwed. Is there anything else I can try?

---

### Post by ii Candor ii on 2009-05-05
Bump.

---

### Post by asuastrophysics on 2009-05-07
candor, looks like you're suffering from the same problem i had.

FGLRX refuses to be removed. period. i'm gonna go file a bug report. something that you removed but still loads on boot is definitely a BUG

---

### Post by swinky on 2009-05-07
fglrx CAN be removed, I know because I have done it. Unfortunately, that was some weeks ago and due to finishing up my last semester of college, I have forgotten it in favor of final exams...

As I recall though, I am pretty sure I used the instructions that can be found [here]("https://wiki.edubuntu.org/X/Troubleshooting/FglrxInteferesWithRadeonDriver"). 

This problem happens because bits that *should* be removed when you remove fglrx don't get removed. Those little bits like to muck things up when you try to use the open source ati drivers.

---

### Post by Clancy_s on 2009-05-16
> **swinky said:**
> As I recall though, I am pretty sure I used the instructions that can be found [here]("https://wiki.edubuntu.org/X/Troubleshooting/FglrxInteferesWithRadeonDriver"). 

Thanks, that fixed it for me.

---

