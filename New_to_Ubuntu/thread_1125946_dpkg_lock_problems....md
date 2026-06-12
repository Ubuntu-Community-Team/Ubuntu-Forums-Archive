---
title: "dpkg lock problems..."
date: 2009-04-14
forum: New to Ubuntu
---

### Post by johonn on 2009-04-14
tried to install java, using xterm. got to a "license aggreement" screen, but unable to click "ok" because it's a terminal, and hitting Enter didn't work. So I ended up closing xterm and trying again in Terminal, hoping that it would work in there.
Now i get broken package errors in synaptic, and can't get locks i needed in command line. It has also told me to run dpkg --configure -a, which i did, but it didn't seem to have any effect. sometimes when running apt-get update I get a message saying 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY etc...
W: You may want to run apt-get update to correct these problems <-- note that i got this after running apt-get update, and subsequent runs would have the same effect. 
Other times, I just get the unable to lock the download directory, or the /var/lib/dpkg lock, or whatever. I really have no idea what is going on, except that I have broken packages and I don't know how to fix them.

---

### Post by Paqman on 2009-04-14
OK, you're kind of describing about four different things there.

Are you currently able to install anything? What exactly happens if you run:
```

sudo dpkg --configure -a

```

---

### Post by abn91c on 2009-04-14
when you get to the java license agreement in the terminal hit the** TAB** key to highlight the** OK** then press enter
you may need to do **sudo rm /var/lib/dpkg lock** to fix this

---

### Post by johonn on 2009-04-15
Paqman: I run that, but no output appears onscreen.
I can't install anything currently, because I evidently have packages that have unmet dependencies - I think this traces back to the uninstalled java package. I still can't get the download directory locked, and when I try to apt-get update, it tells me my key wasn't verified, and to run apt-get update. I am going to try and fix the java installation and get back here.
abn91c: thanks for the tip, I will try that.

---

### Post by johonn on 2009-04-15
Update: Am still not able to fix broken packages at this time, the "unable to lock download directory" error is still preventing my progress.

---

### Post by abn91c on 2009-04-15
> **johonn said:**
> Update: Am still not able to fix broken packages at this time, the "unable to lock download directory" error is still preventing my progress.
make sure synaptic is not open,or running then 
sudo apt-get clean
sudo apt-get check
sudo apt-get install -f

---

### Post by johonn on 2009-04-15
>apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Tried rm /var/lib/dpkg/lock and then tried above again, same result... This was after a logout/login to make sure nothing was running.

---

### Post by SuperSonic4 on 2009-04-15
Try ```
sudo rm /var/lib/dpkg.lock
``` or ```
sudo dpkg --configure -a
```

---

### Post by johonn on 2009-04-15
tried those already... see above posts

---

### Post by shaunehunter on 2009-04-30
give this a try bud:

sudo dpkg --configure -a

it will tell you the name of the package that screwed you up.

sudo dpkg -r "name of package that screwed you up"

that should fix things. did for me.

btw. when you install java and the EULA comes up. hit the right arrow button and the <ok> will highlight red, then press enter. 

hope this helps

---

