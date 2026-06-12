---
title: "Neither Chrome nor Chromium will launch after installing ubuntu 10.10"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by rstepesq on 2010-09-29
This past week I installed the ubuntu 10.10 beta.  Afterward, my favorite browsers, Chrome and Chromium, will not launch.  I have removed and reinstalled both but no luck.  Any ideas?  Thanks in advance.

---

### Post by andrewthomas on 2010-09-29
post the output of 

```
cat /etc/fstab
```If it contains a reference to **/dev/shm** get rid of it

---

### Post by cariboo on 2010-09-29
Have you got moonlight installed, if so remove it. Chrome/Chromium should start after it is removed.

---

### Post by andrewthomas on 2010-09-29
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/566788](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/566788)

---

### Post by jtarin on 2010-09-30
Try launching from the terminal and look for errors and post.

---

### Post by grendel38 on 2010-09-30
I'm having the same issue.  When I try to run chrome in a terminal I get:
> Attempting to load the system libmoon 
Segmentation fault (core dumped)


---

### Post by andrewthomas on 2010-09-30
> **grendel38 said:**
> I'm having the same issue.  When I try to run chrome in a terminal I get:
```
Attempting to load the system libmoon 
```


> **cariboo907 said:**
> Have you got moonlight installed, if so remove it. Chrome/Chromium should start after it is removed.

+1 you need to remove moonlight

---

### Post by grendel38 on 2010-09-30
wow thanks for the fast replies.  removing moonlight fixed things.

but I sort of need moonlight (at least if this is going to be a production machine) so long term, that's not the best solution.

on the other hand, I could just use firefox for everything - I never did get moonlight to work right on chrome anyway

---

### Post by andrewthomas on 2010-09-30
File a bug against moonlight.

---

### Post by TBABill on 2010-09-30
Mine did the exact same thing after I ran the upgrade. I have Sun Java installed so I had to remove the iced tea plugin via Synaptic because the upgrade reinstalled it. Works like a champ now.

---

### Post by rstepesq on 2010-09-30
> **TBABill said:**
> Mine did the exact same thing after I ran the upgrade. I have Sun Java installed so I had to remove the iced tea plugin via Synaptic because the upgrade reinstalled it. Works like a champ now.

Yes, that worked.  Removing the iced tea plugin allowed both Chrome and Chromium to work just as before.  Thanks for all the suggestions from everybody.

---

### Post by SedukiDude on 2010-10-10
This happened on my English laptop but not my Spanish laptop. When the message came up and asked if I wanted to delete my configurations on the English laptop, I did and got the bug report.

When asked to delete my old configuration on the Spanish laptop for some reason I decided to keep my old configuration and everything works great.

I am wondering if I can go to my backup and restore on the English laptop then upgrade to the Maverick and choose not to delete the old configuration? It should work for everyone.

---

### Post by wgarciamachmar on 2010-10-11
> **andrewthomas said:**
> +1 you need to remove moonlight

Thanks! I didn't even knew I had it.

---

