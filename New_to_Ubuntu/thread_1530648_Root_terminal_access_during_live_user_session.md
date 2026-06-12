---
title: "Root terminal access during live user session?"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by stevek123 on 2010-07-13
Can this be done? I messed up my vid drivers during 9.04 install. I cant even access a terminal now. I'd like to try and correct my oops from a live user session and re-install the xserver-xorg I've deleted. If I cant do this - I'd like to save some files I downloaded - but session says I cannot copy as I am not owner. F! (as in fail) How do I become owner so I can save the files. If I can do this I'll just re-install the whole mess.

---

### Post by snowpine on 2010-07-13
A very frequently asked question. :) There is no root account in Ubuntu; rather we use 'sudo', for example:

```
sudo apt-get install firefox
```

The closest Ubuntu has to a "root terminal" is the command:

```
sudo -i
```

More information here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by stevek123 on 2010-07-13
Yes I am familiar with sudo during normal login. ... but I dont understand your response. Does this mean that I cannot change the permissions of the locked files I want to save? (I cant figure out why they're locked in the first place). And does this mean that unless I know all the config and file locations I cannot update the vid drivers on the HD from CD session?
What will sudo -i do for me? (I tried your link but it just crashed my user session)

---

### Post by snowpine on 2010-07-13
Sorry, I misunderstood the question. :( I thought you were looking for instructions to enable a root terminal from the Live CD, never mind.

Maybe you are looking for something as simple as "Press Alt+F2, type 'gksu nautilus'"?

---

### Post by stevek123 on 2010-07-13
Thank you. I was able to easily transfer all the files to a usb. I couldnt get synaptic to alter the HD vid settings but at least I lose only time with a fresh re-install. Good practice I guess.

---

### Post by adamjkok on 2010-07-14
> **snowpine said:**
> A very frequently asked question. :) There is no root account in Ubuntu; rather we use 'sudo', for example:

```
sudo apt-get install firefox
```The closest Ubuntu has to a "root terminal" is the command:

```
sudo -i
```More information here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
More accurately, there *is* a root account in Ubuntu, it's just locked by default (the password is disabled). SUDO causes the current user to *impersonate* root.

---

