---
title: "Flaky Intel 3945 ABG."
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by Chris Finney on 2008-05-16
I have an Intel 3945 ABG Wifi card that just will not perform. On first install of Ubuntu 8.04 (last night) it was fine. Reboot machine and it dies. There appears to be no guaranteed way to get it back into life, but changing the WAP password is most successful. Turning the Wifi off and on again will also kill it. I have checked many previous  postings with no luck. One seems to suggest this is a known problem. I guess what I would like to know is, is there any way to be notified of future fixes?

I'm a Linux novice so be warned.

---

### Post by chili555 on 2008-05-16
There is evidently a better iwl3945 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```Please let us know.

---

### Post by Chris Finney on 2008-05-16
On entering that code in "Terminal" I'm asked for my password, which it does not except (characters do not appear)! What have I done (or not done)?

---

### Post by chili555 on 2008-05-16
> **Chris Finney said:**
> On entering that code in "Terminal" I'm asked for my password, which it does not except (characters do not appear)! What have I done (or not done)?We're all about security. The characters are there, however, the terminal, for security reasons, will not show the characters, and by not even showing *****, will not even show its length. Put in that password and press enter. You will be off and running!

---

### Post by Czubek on 2008-05-16
> **chili555 said:**
> There is evidently a better iwl3945 in here:```
sudo apt-get install linux-backports-modules-hardy-generic
```Please let us know.

I installed this package and nothing happened :(
Shouldn't I do some more configuration?

---

### Post by chili555 on 2008-05-16
Has there been any change in your wireless performance? Can you get connected and stay connected?

---

### Post by Czubek on 2008-05-16
wifi led is on now but still can't connect.

---

### Post by chili555 on 2008-05-16
@Czubek-
Rather than highjack Chris's thread, let's continue over here: [http://ubuntuforums.org/showthread.php?t=796600](http://ubuntuforums.org/showthread.php?t=796600)

---

### Post by Chris Finney on 2008-05-16
Thanks for that about the password, just read the same thing on a help page and came back to try your script, slowly learning!
Tried your script but got this.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-hardy-generic

I'm not positive but I believe I installed "linux-backports-hardy-generic" last night using "Update Manager" having read another thread on the subject.

---

### Post by chili555 on 2008-05-16
You *are *connected to the internet, via ethernet cable, when you execute this command, right?

---

### Post by Chris Finney on 2008-05-18
Sorry, I'm missing the obvious! Did that update again but sadly no joy. The LED in the switch now works as it should, but I still lose connection if I deselect the wifi via the switch or reboot.
Some times it will lose the encription password but not normaly. Not found any gauranteed way of getting it going. Thanks againfor your help.

---

### Post by Chris Finney on 2008-05-19
I've been doing spread sheets today and noticed that if you leave the Wifi long enough, it will eventually connect. It may take up to 10 minutes, but it does get there in the end (I think)! When it does connect it has good signal strength, so maybe it's the WAP encryption slowing things down? Thanks again for your help.

One last question, or should this be another thread? I have started to try and learn about Linux, starting with the command line instructions. Do they work the same with all different distributions of Linux, as I did not seem to be able to make one instruction work.

---

### Post by XedGeneral on 2008-05-19
Same problem here... 

Have a 3945ABG card. Done almost everything. Doesn't work at all. I can find a lot of networks but I can't connect to them, not even one!

---

