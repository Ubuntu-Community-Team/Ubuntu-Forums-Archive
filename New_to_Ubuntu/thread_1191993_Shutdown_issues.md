---
title: "Shutdown issues"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by C. M .Hughes on 2009-06-19
Hi all,
I am having intermittent shut down warning messages on my Ubuntu 9.04 installation. It happens about 1 in every 3 shutdowns/reboots; it is not a big deal to me, but I do wonder if I should try and fix it. 

I have tried to locate the shut down log in 

/var/log/messages
/var/log/syslog.0

but the warning messages that flash up (very quickly) before the Ubuntu splash screen do not appear to be there. Does anyone have any ideas?

Many thanks

---

### Post by porchrat on 2009-06-19
We kind of need to see the messages in order ot help you.

Although there is a generic error message that appears at shutdown on most machines running Ubuntu (in my experience anyway) that contains some red in the title and it mentions HAL among other things. From what I recall about that message a certain daemon required to send messages from one element to another has shutdown before the elements that need to utilise it to receive messages. It is more of a warning than an error as it doesn't (or at least has never for me) cause any problems.

Although this is all speculation until you get us a picture of that error message (try using a camera, that is what a lot of people having these sorts of issues do).

---

### Post by C. M .Hughes on 2009-06-20
Many thanks for your response. 

I've done lots of restarting/shutting down since last night, but haven't managed to produce the same warning message- d'oh! I'll repost when I have a picture. Thanks again.

---

### Post by shankhs on 2009-06-20
It rains when you dont have an umbrella!

---

### Post by raymondh on 2009-06-20
Does the shutdown message involve "compositing"?

---

### Post by LewRockwell on 2009-06-20
> **shankhs said:**
> It rains when you dont have an umbrella!

the probability of a flat tire increases proportionately relative to the inverse square of the kilometer distance to the nearest source of compressed air

---

### Post by C. M .Hughes on 2009-06-20
Hi all,
Attached is a picture of the warning message- I hope it's viewable (my screen looks horrible in this pic). 

Here is a bit of background info:
1. I installed 8.10 on my Dell laptop a month or so ago
2. I followed [this guide]("http://ubuntuforums.org/showthread.php?t=760568") to get my wireless card working.
3. I then used the update manager to upgrade to 9.04

I'm wondering if I have to re-enter this code:

echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist b43legacy | sudo tee -a /etc/modprobe.d/blacklist

Many thanks

---

### Post by Ayuthia on 2009-06-20
> **C. M .Hughes said:**
> Hi all,
Attached is a picture of the warning message- I hope it's viewable (my screen looks horrible in this pic). 

Here is a bit of background info:
1. I installed 8.10 on my Dell laptop a month or so ago
2. I followed [this guide]("http://ubuntuforums.org/showthread.php?t=760568") to get my wireless card working.
3. I then used the update manager to upgrade to 9.04

I'm wondering if I have to re-enter this code:

echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist b43legacy | sudo tee -a /etc/modprobe.d/blacklist

Many thanks

The screen is saying that you are missing the blacklist in front of the words b43 and b43legacy.  You will need to go into the file and add the word blacklist in front of it.  You can edit the file by doing this in the Terminal:
```
gksu gedit /etc/modprobe.d/blacklist.conf
```

---

### Post by C. M .Hughes on 2009-06-20
Thanks Ayuthia! 

I went into /etc/modprobe.d/blacklist.conf

and sure enough (at the end of the file), I had

b43
b43legacy
blacklist b43
blacklist b43legacy

So I now have

# b43
# b43legacy
blacklist b43
blacklist b43legacy

I'll repost if I have any more errors.

---

### Post by C. M .Hughes on 2009-06-21
Hi again everyone,
My sincere thanks for helping me through my last shutdown problem. 

I now have another screen that flashes up on shut down, but not every time. It seems to happen only after having the computer on for more than about 15 minutes. I don't fancy my chances of getting a picture of this one, it flashes up way too quickly. 

I suppose I go back to my original question: is there a shutdown log that has all messages that are outputted on shutdown?

Many thanks.

---

