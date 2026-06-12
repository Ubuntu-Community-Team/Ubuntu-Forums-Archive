---
title: "Is Software Center down today?"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by geoff_sct on 2011-06-01
I've tried several times to download WINE and a couple of other apps but nothing...... I also tried on another laptop with Ubuntu so I guess the site must be down. Any info?

---

### Post by Blasphemist on 2011-06-01
Seems to be working fine for me. If you have anything open that also uses your packages, that can stop you. Do you have synaptic or update manager running? If so, close them and the software center should go ahead and install whatever is queued.

---

### Post by seawolf167 on 2011-06-01
Does the command through the terminal work? 

```
sudo apt-get install wine
```

---

### Post by geoff_sct on 2011-06-01
This is what I get with Terminal


Reading package lists...Error!
E: Encountered  a section with no Package: header
E: Problem with Mergelist /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natt
y_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

I typed this all out. I must learn how to post screenshots for Terminal!

---

### Post by seawolf167 on 2011-06-01
You can select the text via your mouse, then middle click to paste.

As for the list problem, try clearing the list cache then reloading the lists


```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

then try installing wine again

```
sudo apt-get install wine
```

---

### Post by geoff_sct on 2011-06-01
Ok I'll try that. I  just opened the update manager and it said for me to report this bug. It's basically the same wording as the Terminal info.  I'll try clearing the cache.

---

### Post by geoff_sct on 2011-06-01
Ok I've got wine downloaded and installed (I guess) as per your Terminal instructions. A package configuration window is up with the User Agreement. It says <OK> at the bottom centre of the window. There is no way to click on it or anything and the return key doesn't do anything. Do I just close that window? Hope this gets easier with time and I'll eventually know how to do these codes. Thanks. I'll try Software Center after this for some other apps and see if it works now. But in the meantime--Do I just close that agreement window?

---

### Post by seawolf167 on 2011-06-01
Agree with the "ok" part - use the Space bar instead of the Enter key once you have it selected with the Tab key

---

### Post by Swagman on 2011-06-01
Indeed.. The TAB key scrolls (Moves between) the different options...Same as in Windows actually !!

---

### Post by geoff_sct on 2011-06-01
WINE seemed to install fine and I can now use the Software Center too . BUT my wife was doing all this along with me on her laptop. On hers she opened up WINE after installing and trying to open it a small screen opened that said "Updating" and then her screen went blank (black) and the computer is still on. Should she just force a shutdown and restart or is it actually doing something?

---

### Post by seawolf167 on 2011-06-01
> **geoff_sct said:**
> On hers she opened up WINE after installing and trying to open it a small screen opened that said "Updating" and then her screen went blank (black) and the computer is still on. Should she just force a shutdown and restart or is it actually doing something?

See if she can open a terminal using the keyboard shortcut, by default it is [CTRL][ALT][T], if not, she can switch to tty1 using [CTRL][ALT][F1].

Once a terminal is open, you can find the process for wine and kill it

```
ps -ef | grep wine
kill -i *pid*
```

where *pid* is the process id from the first command.

If she had to enter tty1 because a terminal wouldn't open, she can restart gdm with the following command

```
sudo service gdm restart
```

---

### Post by geoff_sct on 2011-06-01
OOPs she was just hibernating. All is well. Thanks again for your help. Hope the pocket guide gets us fluent with Terminal code.

---

### Post by seawolf167 on 2011-06-01
Hehe, that makes it even easier! Glad it's all working :)

Edit: see my link "linuxcommands" for some command how-to's

---

### Post by geoff_sct on 2011-06-01
Thank you very much seawolf! Your links are exactly what I need. I never really cared about this stuff but now I'm obsessed. ;)

---

### Post by seawolf167 on 2011-06-02
> **geoff_sct said:**
> Thank you very much seawolf! Your links are exactly what I need. I never really cared about this stuff but now I'm obsessed. ;)

Hehe, welcome to the club :P

---

