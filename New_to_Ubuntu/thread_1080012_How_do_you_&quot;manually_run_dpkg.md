---
title: "How do you &quot;manually run dpkg?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by DonaldJ on 2009-02-25
I added a few new softwares.. the updater window locked-up.. I X'ed the window, rebooted, went into updater, and got a warning message after it built the list...   "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

I think it happened because updater on a new install got interrupted after the cable-modem failure, when the repair guys at the corner upgraded they system at the road side boxes, and I forgot to manually update this new install, and added on a few items...   It seems I "blocked the cards"..?


Pop up:  "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."


How do I manually "run 'dpkg --configure -a' to correct the problem"..?

---

### Post by iaculallad on 2009-02-25
Open your terminal (Application-Accessories-Terminal) and do what the error message say, only this time, include the sudo command:

```
sudo dpkg --configure -a
```

EDIT:

Issuing this command will prompt you for your password. Input the valid password and don't worry when characters don't echo on your screen. Just input your password and press Enter key when done.

---

### Post by DonaldJ on 2009-02-25
I did  "sudo dpkg --configure -a'...

Now I got  "You have three broken packages on your machine..  Run broken filter."

______________________


I just remembered there's something else I did...  Oyie!..  and maybe something else...  

I think it be best that I just reinstall Ubuntu...  I've really made a mess of this spare 36-gig hd...

Would the mods please delete this thread...  The OS is probably tooo messed up to fix...

---

### Post by konqueror7 on 2009-02-25
try doing a
```
sudo apt-get -f install
```

---

### Post by DonaldJ on 2009-02-25
I'll try that..."sudo apt-get -f install", and report...

_______________________________


OK.. it's doing a lot of installing, and some deleting...  I'll get back to this thread  after the reboot...

_______________________________

Oops! everything stops at the "sun java licence" window..  It can't click anything in that window...
Oh HeY!  the agree check box isn't there...  There's a big part of the problem.. or the beginning of it...

_______________________________



"Unable to unlock"  and "unable to get lock"..?

---

### Post by iaculallad on 2009-02-25
> **DonaldJ said:**
> Oops! everything stops at the "sun java licence" window..  It can't click anything in that window...

At the Java window, press the TAB key to highlight the OK "button" and press Enter key.

---

### Post by DonaldJ on 2009-02-25
I'm reinstalling right now...  Thanks for the advice, but this OS is seriously nuked...

---

### Post by Ripose on 2009-02-25
Reboot into "Safe Mode"

From the menu select "Fix Broken Packages"

Select "Resume Normal Boot"

Did it help?

---

### Post by stchman on 2009-02-25
I prefer to run gdebi over dpkg.

The difference is that gdebi installs dependencies.

---

### Post by DonaldJ on 2009-02-25
I have several PC's as backups.. so I reinstalled, and had it do the updates in the night...

Everything is running like it should, but when I rebooted after the updates, the personalized shut-down applet had a little problem, and asked to be deleted..?  I suspect it was a glitch from the damage in the previous install, still in the front end, which formatting with a W98CD, plus pull the battery, would have cleared...

I've made it a habit from running Windows virus OS, that whenever something evil gets into the OS, instead of fiddling with it, I format it...

---

### Post by oldos2er on 2009-02-25
Most problems in Linux can be resolved without reinstalling the entire OS. That said, when I first began using Ubuntu, I reinstalled it a few times after borking it, as a learning process.

---

### Post by DonaldJ on 2009-02-25
"Most"..  but I think I really messed this one up big-time...  It probably would have taken a lot longer to repair than it did to reinstall it...  
It took only about ten-minutes of my time to reinstall it...  

Since I had no treasures on the hd, I dropped in the DC, rebooted, and went onto the spare PC...  When I returned, it was ready to restart...  I got the updates working, and went to bed...  In the AM it was ready to to do the 250 add-on files, set prefs, done...

I think this mess was a combo: of the modem-crash, the loose cable connector, me tweaking and installing updates before the default updates, and a glitch with Java's install, and the fact "that it snowed all night"...

I thank you all for the keen info in trying to help me cure it...  I've been into Ubuntu for less than a month...  You guys seem like experts...  And the big of it is that when you teach others, you learn more about what you're teaching...  Everybody wins...  It's people like you who make everybody be winners... Thanks again...

---

