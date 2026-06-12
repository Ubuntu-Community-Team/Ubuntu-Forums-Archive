---
title: "start x not working"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by adeelyas on 2010-06-11
how can i start ubuntu  in  graphical  mode when i type start x message appears start x is not installed what to do tell me plz

---

### Post by wilee-nilee on 2010-06-11
> **adeelyas said:**
> how can i start ubuntu  in  graphical  mode when i type start x message appears start x is not installed what to do tell me plz

Since we are addressing the command with no additional information ```
startx
``` is correct.

---

### Post by 3rdalbum on 2010-06-11
> **wilee-nilee said:**
> Since we are addressing the command with no additional information ```
startx
``` is correct.

Not really (startx needs to be run as root, and if you run it as root it will log you in as root too). The command should be:

```
sudo service gdm start
```

Ubuntu should automatically start in graphical mode anyway. Unless you're using Ubuntu Server, which doesn't have a GUI.

---

### Post by wilee-nilee on 2010-06-11
> **3rdalbum said:**
> Not really (startx needs to be run as root, and if you run it as root it will log you in as root too). The command should be:

```
sudo service gdm start
```

Ubuntu should automatically start in graphical mode anyway. Unless you're using Ubuntu Server, which doesn't have a GUI.

I didn't know that, thanks, I have only had to use it to startx from recovery once when I had to use the fix packages option.

---

### Post by warfacegod on 2010-06-11
> **3rdalbum said:**
> Not really (startx needs to be run as root, and if you run it as root it will log you in as root too).

I don't think I've ever had to run startx as root. I certainly didn't the last time I used it. That was right after 9.10 got the 2.6.31.21? kernel update and gdm refused to start. It did, of course, put me into the root user account.

---

### Post by wilee-nilee on 2010-06-11
> **warfacegod said:**
> I don't think I've ever had to run startx as root. I certainly didn't the last time I used it. That was right after 9.10 got the 2.6.31.21? kernel update and gdm refused to start. It did, of course, put me into the root user account.

I am a little confused about this, I just rebooted went to recovery used the dpkg fix then boot normally logged in and then startx and I am in the regular desktop.

Maybe I'm missing something here, besides a few synapses.

I originally suggested this with a preface that not having any more information the command itself was incorrect.

---

### Post by julio_cortez on 2010-06-11
> **3rdalbum said:**
> Not really (startx needs to be run as root, and if you run it as root it will log you in as root too).
I don't think it's necessary to have root privileges to run startx.
It happened to me a couple of times to login in failsafe mode with my account and then run startx without sudoing..

Am I missing something?

---

### Post by warfacegod on 2010-06-11
> **wilee-nilee said:**
> I am a little confused about this, I just rebooted went to recovery used the dpkg fix then boot normally logged in and then startx and I am in the regular desktop.

Maybe I'm missing something here, besides a few synapses.

I originally suggested this with a preface that not having any more information the command itself was incorrect.

Without all the login credentials, it will kick you into root. Go into Recovery and get yourself to a prompt and type startx.

---

### Post by oldos2er on 2010-06-11
I have a text login by default, and I never run startx as root.

---

### Post by wilee-nilee on 2010-06-11
> **warfacegod said:**
> Without all the login credentials, it will kick you into root. Go into Recovery and get yourself to a prompt and type startx.

Good to know, I rarely have to really mess with my computers they seem to just work so I didn't know this.

@oldos2er, that would be giant steps wouldn't it, like the signature.;)

---

### Post by emarkay on 2010-06-11
Thus please confirm:

I use Recovery mode, then "Continue Boot" and I get the CLI - Of course I then login with password and then just enter "startX" to run the GUI.

This is NOT running in root, correct?

---

### Post by oldos2er on 2010-06-11
Correct, except the command is ```
startx
```

---

### Post by afrodeity on 2010-06-13
Has startx been deprecated? I used to be able to startx with karmic in recovery mode, now I can't do this in lucid? Do we really have to run startx as root?

---

### Post by afrodeity on 2010-06-13
Frankly, if you own the machine, you own the hardware and if you switch hardware on you should have root access no matter what. I hope my password is the real deal to the realm, and not some bogus encrypted trojan clipper chip inspired stupidity.

Please, I would like to just have the same command from karmic and at verly least a polite message if you killing off sudo and the shebang.

---

