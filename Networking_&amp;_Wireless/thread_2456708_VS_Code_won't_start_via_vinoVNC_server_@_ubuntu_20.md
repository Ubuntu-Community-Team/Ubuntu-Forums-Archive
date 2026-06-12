---
title: "VS Code won't start via vinoVNC server @ ubuntu 20.04 server"
date: 2021-01-17
forum: Networking &amp; Wireless
---

### Post by vlnikolic on 2021-01-17
i am unable to start VS Code via VNC on UBUNTU 20.04 server.

here is the output of code --verbose

[https://textuploader.com/180mn](https://textuploader.com/180mn)

is there any known spell for this ?

thanks

---

### Post by #&amp;thj^% on 2021-01-17
How did you set this up?
Also include this please:
```
sudo systemctl status vncserver@1
```

---

### Post by vlnikolic on 2021-01-18
> **1fallen said:**
> How did you set this up?
Also include this please:
```
sudo systemctl status vncserver@1
```

thank you 1fallen,

here is the output:

$ sudo systemctl status vncserver@1

Unit [email]vncserver@1.servic[/email]e could not be found.

i am able to connect it without any problem, and i am unable to start vs code

---

### Post by #&amp;thj^% on 2021-01-18
> **vlnikolic said:**
> 
i am able to connect it without any problem, and **_i am unable to start vs code_**

Sometimes i get lost in translation, The problem is that VS Code uses Electron, which is the root cause of the bug. Bug was reported back in 2016 and is still not fixed.
Yours:
```
[main 2021-01-16T19:18:26.752Z] Error: EMFILE: too many open files, watch '/snap/code'
    at FSWatcher.start (internal/original-fs/watchers.js:165:26)
    at Object.watch (original-fs.js:1329:11)
    at new g (/snap/code/52**/usr/share/code/resources/app/out/vs/code/electron-main**/main.js:479:486)
    at u._createInstance (/snap/code/52/usr/share/code/resources/app/out/vs/code/electron-main/main.js:296:671)
    at u._createServiceInstance (/snap/code/52/usr/share/code/resources/app/out/vs/code/electron-main/main.js:298:814)
    at u._createServiceInstanceWithOwner (/snap/code/52/usr/share/code/resources/app/out/vs/code/electron-main/main.js:298:339)
    at u._createAndCacheServiceInstance (/snap/code/52/usr/share/code/resources/app/out/vs/code/electron-main/main.js:298:14)
    at u._getOrCreateServiceInstance (/snap/code/52/usr/share/code/resources/app/out/vs/code/electron-main/main.js:297:196)
```
There was a hack that was used then, but I'm unsure it will still work.
If you want to see if it will use:
**Imporant: # set the dynamic loader path to put your library first before executing VS Code.**
```
# make a copy of the relevant library
mkdir ~/lib
cp /usr/lib/x86_64-linux-gnu/libxcb.so.1 ~/lib
sed -i 's/BIG-REQUESTS/_IG-REQUESTS/' ~/lib/libxcb.so.1
# set the dynamic loader path to put your library first before executing VS Code
LD_LIBRARY_PATH=$HOME/lib code
```
Good Luck, and let us know if this still works.

---

### Post by vlnikolic on 2021-01-18
hello and thank you for your interest!

i've tried that surgery, but without any success.. code simply stand still, no any sign of starting application

: (

---

