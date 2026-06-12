---
title: "Can't connect to the internet."
date: 2011-06-21
forum: New to Ubuntu
---

### Post by fignig on 2011-06-21
old dell using a "Belkin wireless-g F5D7000" 

[IMG]http://i.imgur.com/1Umn5.png

halp.  Wat do?

:guitar:

---

### Post by westie457 on 2011-06-21
> **fignig said:**
> old dell using a "Belkin wireless-g F5D7000" 

[IMG]http://i.imgur.com/1Umn5.png

halp.  Wat do?

:guitar:

Hi Take a look at post #240 of this thread

[http://ubuntuforums.org/showthread.php?t=1604868&page=24]("http://ubuntuforums.org/showthread.php?t=1604868&page=24")

Follow it carefully one step at a time and you should have wifi working.

You will need an ethernet cable.

---

### Post by fignig on 2011-06-21
didn't seem to work

---

### Post by doctorbighands on 2011-06-23
According to your lspci, you have a Broadcom 4318 card. Assuming you're running Xubuntu 11.04, the following should get you up and running:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

After that's finished, head for System -> Administration -> Additional Drivers, activate the b43 driver, reboot, and you should be good.

---

### Post by mastermold on 2011-07-06
Op here.  Had a friend over and he was logged in when we were making the post.  the last command worked.  Thanks for all the help.

---

### Post by ClientAlive on 2011-07-06
> **doctorbighands said:**
> According to your lspci, you have a Broadcom 4318 card. Assuming you're running Xubuntu 11.04, the following should get you up and running:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

After that's finished, head for System -> Administration -> Additional Drivers, activate the b43 driver, reboot, and you should be good.


That is precisely the card I have. To-a-tee. I'm running Ubuntu 10.04 LTS now but I ran 11.04 for a while and had some serious trouble getting the wireless going. Not sure if it was something related to other hardware/ configuration issues specific to my machine - but ultimately the regular methods did not work for me. We ended up having to actually download the wireless driver and install them manually.

I wouldn't suggest one jump right to this if other, easier methods will work for them; but, if it comes down to it, here's the thread that details what we had to do.

[http://ubuntuforums.org/showthread.php?t=1731838&page=3](http://ubuntuforums.org/showthread.php?t=1731838&page=3)

Post #28

---

