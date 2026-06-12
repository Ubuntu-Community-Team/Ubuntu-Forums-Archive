---
title: "trouble due to lack of experience with ndiswrapper, need help pretty badly"
date: 2008-02-24
forum: Networking &amp; Wireless
---

### Post by oh_hi95 on 2008-02-24
Alright, here's the deal; I'm trying to install a Netgear WG111v3 Wireless Internet Adapter (you get the picture) for use with my Dell Dimension 4400 that has Ubuntu 7.10 installed on it.  I perceived that something was wrong with ndiswrapper when it gave me the message "utilis not found" despite having specifically downloaded the "utilis" after encountering the issue.  so I decided to delete ndiswrapper from my system (in hindsight not a good idea, I don't need any chiding for this, trust me) so what I need is...

instructions on how to download ndiswrapper 
very detailed instructions on exactly where to put it
and instructions about how to verify that I've got all of the components

any help is very appreciated by this new user attempting to become linux savvy

---

### Post by kevdog on 2008-02-24
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by oh_hi95 on 2008-02-24
kevdog, 

your instructions are very useful, however, when I reach the point where the terminal line reads

me@me-desktop:~/driver$ sudo ndiswrapper -i WG111v3.inf

and press enter, the next lines say

installing setup ...
couldn't open setup.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.

does anyone have any advice for this situation?

any suggestions are very appreciated

---

### Post by oh_hi95 on 2008-02-24
okay, it turns out that I wasn't in the exact directory just a moment ago
so now the terminal line reads like this

till@till-desktop:~/driver$ sudo ndiswrapper -i setup.inf
installing setup ...
couldn't open setup.inf: No such file or directory at /usr/sbin/ndiswrapper line 217.
till@till-desktop:~/driver$ cd WG111
till@till-desktop:~/driver/WG111$ sudo ndiswrapper -i WG111v3.inf
driver wg111v3 is already installed
till@till-desktop:~/driver/WG111$ ndiswrapper -l
setup : invalid driver!
wg111v3 : invalid driver!
wgiiiv3 : invalid driver!

---

### Post by kevdog on 2008-02-24
Look at number #4 in the guide I wrote under the heading:

Common Tips Problems, Suggestions


I tried to make the guide as thorough as I could.

---

### Post by oh_hi95 on 2008-02-25
whoops, didn't see that there, I'm really awful at reading those types of things

I've got the steps down, all I need to do now is reboot, but I think it's going to work

thanks for all the help, your guide is really great

---

### Post by stooshbunutu on 2008-04-10
> **oh_hi95 said:**
> whoops, didn't see that there, I'm really awful at reading those types of things

I've got the steps down, all I need to do now is reboot, but I think it's going to work

thanks for all the help, your guide is really great

You can mark your thread as solved via the thread options menu at the top

---

