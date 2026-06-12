---
title: "Firefox status:sleeping"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by OxTubu on 2010-07-14
When I try to start ff it's only visibly through the system monitor as "sleeping" and waiting channel "do_wait", nothing else. I've reinstalled and restarted multiple times without effect. 

What can I do, or what more clues might you need in order to be able to give me some advice?

---

### Post by emoguitarist06 on 2010-07-14
Open a terminal and type
> killall firefox
Then open firefox again

---

### Post by lovinglinux on 2010-07-14
> **emoguitarist06 said:**
> Open a terminal and type

Then open firefox again

If that doesn't work, see Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by OxTubu on 2010-07-15
> **lovinglinux said:**
> If that doesn't work, see Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

Step 4 (firefox -P) worked ONCE, then I was back to square one, with the process being hidden and "sleeping".

---

### Post by lovinglinux on 2010-07-15
> **OxTubu said:**
> Step 4 (firefox -P) worked ONCE, then I was back to square one, with the process being hidden and "sleeping".

So, you have created a new profile, started it and it worked. Then after closing you wasn't able to start it again, even starting the new profile?

Try this:

```
firefox -no-remote -P
```

This is not a fix, but just a hack to see if you can launch the profile even when another instance of Firefox is running.

---

### Post by OxTubu on 2010-07-15
> **lovinglinux said:**
> So, you have created a new profile, started it and it worked. Then after closing you wasn't able to start it again, even starting the new profile?

Correct

> **lovinglinux said:**
> 

Try this:

```
firefox -no-remote -P
```

This is not a fix, but just a hack to see if you can launch the profile even when another instance of Firefox is running.


Nothing happens:(

---

### Post by lovinglinux on 2010-07-15
> **OxTubu said:**
> Correct




Nothing happens:(

Did it output any errors in the terminal?

---

### Post by OxTubu on 2010-07-16
> **lovinglinux said:**
> Did it output any errors in the terminal?

No, that's the annoying part. The terminal is however "occupied" by some process, and warns about it whenever I close it. I have however run into an error-message when i close down the computer about some gnome-process that i have to kill. I will come back tomorrow when Ive had time at the computer (the right one).

---

### Post by lovinglinux on 2010-07-17
> **OxTubu said:**
> No, that's the annoying part. The terminal is however "occupied" by some process, and warns about it whenever I close it. I have however run into an error-message when i close down the computer about some gnome-process that i have to kill. I will come back tomorrow when Ive had time at the computer (the right one).

Try this:

```
killall firefox-bin
```

---

### Post by OxTubu on 2010-07-17
> **lovinglinux said:**
> Try this:

```
killall firefox-bin
```

You saw that coming?! When I shutdown after trying to start firefox i get the message that there is one application running and not responding, firefox bin. 

However, killall doesnt enable me to start firefox, it just removes the error message when I shut down.

---

### Post by lovinglinux on 2010-07-17
> **OxTubu said:**
> You saw that coming?! When I shutdown after trying to start firefox i get the message that there is one application running and not responding, firefox bin. 

However, killall doesnt enable me to start firefox, it just removes the error message when I shut down.

First use **killall firefox-bin** to kill all firefox processes. This will prevent Firefox from giving you a warning that it is already running. Then create a new profile by starting the profile manager with **firefox -P**. Creating a new profile will make sure you don't have a corrupted profile causing the problem.

---

### Post by OxTubu on 2010-07-19
> **lovinglinux said:**
> First use **killall firefox-bin** to kill all firefox processes. This will prevent Firefox from giving you a warning that it is already running. Then create a new profile by starting the profile manager with **firefox -P**. Creating a new profile will make sure you don't have a corrupted profile causing the problem.

So, each time I create a new profile I can start firefox ONCE. Then "killall firefox-bin" doesn't help, except when I create a new profile again. This way I at least can use firefox some (which is great) but the real problem is still there... :S

---

### Post by lovinglinux on 2010-07-19
> **OxTubu said:**
> So, each time I create a new profile I can start firefox ONCE. Then "killall firefox-bin" doesn't help, except when I create a new profile again. This way I at least can use firefox some (which is great) but the real problem is still there... :S

That's not a solution then. It should fix the problem and shouldn't be necessary to be executed twice.

Can you start it if you go to System Monitor and kill firefox-bin from there?

---

### Post by OxTubu on 2010-07-23
> **lovinglinux said:**
> That's not a solution then. It should fix the problem and shouldn't be necessary to be executed twice.

Can you start it if you go to System Monitor and kill firefox-bin from there?

Unfortunately no. When i try to start firefox the following processes is added to the system monitor (as far as i can notice)

*firefox
*firefox-bin
*run-mozilla.sh

Even if I kill all of those I still have to reboot or create a new profile.

---

### Post by lovinglinux on 2010-07-23
Check if you have libmoon package installed and remove it.

---

### Post by OxTubu on 2010-07-24
> **lovinglinux said:**
> Check if you have libmoon package installed and remove it.

I dont have it installed.

---

### Post by lovinglinux on 2010-07-24
What version of Firefox you are using?

---

### Post by OxTubu on 2010-07-24
> **lovinglinux said:**
> What version of Firefox you are using?

3.6.7+build2+nobinonly-0ubuntu0.10.04.1 (firefox)

according to software center

---

### Post by lovinglinux on 2010-07-24
> **OxTubu said:**
> 3.6.7+build2+nobinonly-0ubuntu0.10.04.1 (firefox)

according to software center

Looks like Mozilla dropped the ball with version 3.6.7 and released version 3.6.8 two days later (yesterday) to fix several issues with instability. If you want to try that version and you have a 32bit system, then you could install [Ubuntuzilla](http://ubuntuzilla.wiki.sourceforge.net/). Otherwise you could download it from Mozilla and install it manually or get if from the [ubuntu-mozilla-security](https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa) ppa. See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) tutorial.

---

### Post by rnbguitar on 2010-07-24
> **lovinglinux said:**
> If that doesn't work, see Firefox [[COLOR=Sienna]**General Troubleshooting Steps**[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html") tutorial.


Thank you for your advice. It works in me.:)

---

### Post by lovinglinux on 2010-07-24
> **rnbguitar said:**
> Thank you for your advice. It works in me.:)

You are welcome.

---

### Post by OxTubu on 2010-07-27
> **lovinglinux said:**
> Looks like Mozilla dropped the ball with version 3.6.7 and released version 3.6.8 two days later (yesterday) to fix several issues with instability. If you want to try that version and you have a 32bit system, then you could install [Ubuntuzilla](http://ubuntuzilla.wiki.sourceforge.net/). Otherwise you could download it from Mozilla and install it manually or get if from the [ubuntu-mozilla-security](https://edge.launchpad.net/~ubuntu-mozilla-security/+archive/ppa) ppa. See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) tutorial.

I now have ff 3.6.8. The upgrade was just"normal" update manager. Howver it doesn't solve my problem. :(

---

### Post by lovinglinux on 2010-07-27
> **OxTubu said:**
> I now have ff 3.6.8. The upgrade was just"normal" update manager. Howver it doesn't solve my problem. :(

If you start firefox from terminal, does it output any errors?

---

### Post by OxTubu on 2010-07-27
> **lovinglinux said:**
> If you start firefox from terminal, does it output any errors?

Nope. It only starts firefox-bin and a few other processes, but never actually displays firefox itself.

---

### Post by lovinglinux on 2010-07-27
> **OxTubu said:**
> Nope. It only starts firefox-bin and a few other processes, but never actually displays firefox itself.

Try to delete the file **secmod.db** from your profile and see if it works. Problems with that file started since Firefox 3.6.7 update. No solution yet that I'm aware.

---

### Post by OxTubu on 2010-08-31
> **lovinglinux said:**
> Try to delete the file **secmod.db** from your profile and see if it works. Problems with that file started since Firefox 3.6.7 update. No solution yet that I'm aware.

Sorry I've been inactive for so long, been very busy:(

Anyhow, is there any chance this problem will solve itself when the stable FF4 is out? 

I've simply decided to let it be as it is, and I create new profiles every time I have to use FF. 

Thank you for your help anyway!

---

### Post by lovinglinux on 2010-08-31
> **OxTubu said:**
> Sorry I've been inactive for so long, been very busy:(

Anyhow, is there any chance this problem will solve itself when the stable FF4 is out? 

I've simply decided to let it be as it is, and I create new profiles every time I have to use FF. 

Thank you for your help anyway!

Try this:

[https://addons.mozilla.org/en-US/firefox/addon/213326/](https://addons.mozilla.org/en-US/firefox/addon/213326/)

---

### Post by OxTubu on 2010-10-22
> **lovinglinux said:**
> Try this:

[https://addons.mozilla.org/en-US/firefox/addon/213326/](https://addons.mozilla.org/en-US/firefox/addon/213326/)

Unfortunately this only lead to firefox starting (as opposed to before) but freezing before I can access any functionality. 

Is this any lead? Or maybe I'll just have to wait until ff4, and hope that solves the problem.

---

### Post by lovinglinux on 2010-10-22
> **OxTubu said:**
> Unfortunately this only lead to firefox starting (as opposed to before) but freezing before I can access any functionality. 

Is this any lead? Or maybe I'll just have to wait until ff4, and hope that solves the problem.

I'm experiencing the same problem with FF 3.6.11, nevertheless, the ProfileCleaner extension solves the problem. I don't know what else could be causing this, but is definitely a file in your profile.

---

### Post by OxTubu on 2010-12-08
After installing Lubuntu (my machine is getting old/slow), the problem was still there!

I did however, finally, find the solution to my problem (on flashback.org). Turns out it was a program called Nexus personal, used for banking ID, that screwed things up. Running

sudo rm /usr/local/lib/personal/libP11.so && sudo apt-get install libp11-1

solved it. Thanks for the input! Now, how do I mark this as "solved"...?

---

