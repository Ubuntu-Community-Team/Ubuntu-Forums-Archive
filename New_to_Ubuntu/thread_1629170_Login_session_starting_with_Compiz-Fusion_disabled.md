---
title: "Login session starting with Compiz-Fusion disabled (for no apparent reason)!"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by Forgotten Path on 2010-11-23
I've recently encountered a strange problem with my Lucid install.  Lately when logging in, Compiz-Fusion has been disabled.  It only happens when logging into my username, when anyone else logs in, Compiz is running with no problems.  Once I'm logged in, I can start Compiz from the terminal, or through the appearance settings by changing visual effects to custom, with no problem. And once running, Compiz behaves perfectly, no errors.
I have already tried reinstalling everything Compiz from Synaptic - it didn't help.  I feel like I'm missing something simple here, but I just can't figure out what's going on.

---

### Post by Forgotten Path on 2010-11-23
Adding "compiz &" to my startup applications had no effect...
:(

---

### Post by 00arthuryu on 2010-11-23
This a temporary / VERY BAD workaround, but you could make an sh script and put it in startup

save this as startupcompiz.sh through gedit
```
sleep 5
DISPLAY=:0 compiz --replace
```
open terminal and type:
```
chmod +x startupcompiz.sh
```
Add startupcompiz.sh into the system -> preferences -> startup applications

---

### Post by Forgotten Path on 2010-11-23
Didn't think about using a script at startup to call Compiz.  I've got Conky started from a script the same way.  Is the sleep command needed?  (I'm lazy and don't want to go back a change the sleep in my other startup scripts that require Compiz to be running)
Should I use
```
sleep 5
DISPLAY=:0 compiz --replace > /dev/null 2>&1
```

Any idea what could be going on?  Starting Compiz manually every login is VERY annoying.  And makes it impossible to show off my eye-candy to my Windows running friends (at least without looking like an idiot).

EDIT:  Okay, the script is working...  Login is a little slow, but not as bad as when Compiz was magically getting disabled...  Thanks for the work-around!

---

