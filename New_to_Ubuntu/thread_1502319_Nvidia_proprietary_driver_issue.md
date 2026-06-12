---
title: "Nvidia proprietary driver issue"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by mbzn on 2010-06-05
After installing 10.04 amd64 I downloaded the nvidia driver through hardware drivers, now on boot I get:

Ubuntu running in low graphics mode
failed to load kernal module
and something about no driver loaded

when i hit OK i get the options for:
Low graphics mode
Reconfigure x
Troubleshoot the problem
Exit to console login
restart x

Restarting X seems to give me a system where hardware drivers says the driver is in use but compiz doesn't work

the driver is: 
NVIDIA accelerated graphics driver (version current) [recommended]
I have a 9800gt card and running kernal 2.6.32-22
I've tried various things relating to other nvidia driver issues but none of it seems to do the trick.

Is there a solution to this?

Thanks in advance

---

### Post by ibe2fly4chu on 2010-06-05
I had this happen to me a few times on a fresh install of lucid. Here is what worked for me:
First i ran an update. To do this go to Terminal, type "Sudo apt-get update" without the quotes, it will then ask you for your password, enter it and watch the pretty writing on the screen :)

After all the updates are done, it will probobly ask you to restart, do so and then when you log back in, go back to hardware drivers, and select the recommended drivers. It should work shortly there after.

just to note: mines did crash one more time after all of that, however after i restarted x again and then went back to hardware drivers, it started working fine ever since.

---

### Post by mbzn on 2010-06-05
No luck for me, but thanks for the input

---

### Post by barney385 on 2010-06-05
sudo apt-get update

then:

sudo apt-get upgrade

Make sure you have the restricted extras repo enabled also.

I have an Nvidia card also, but I have an 8600GT. You might need to enable the Medibuntu repo also.

---

### Post by themusicalduck on 2010-06-05
Running sudo apt-get update won't do anything except refresh your software sources.

To upgrade software you need to run ```
sudo apt-get update
``` and then ```
sudo apt-get upgrade
``` afterwards.
Or you could just go to System > Administration > Update Manager and install them from there.

---

### Post by mbzn on 2010-06-05
Took a knock on my phone bill but that did the trick, Thanks alot!!!!

---

