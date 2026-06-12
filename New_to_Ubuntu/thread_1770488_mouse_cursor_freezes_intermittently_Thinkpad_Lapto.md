---
title: "mouse cursor freezes intermittently Thinkpad Laptop"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by maciej234 on 2011-05-29
The mouse cursor freezes for a few seconds and it's a big problem.  I tried to change my grub to:  

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic nolapic"

but that did not solve.  By googling, theres all sorts of forums about Linux and mouse cursor freezing problems on Thinkpads.  I need this to go away ; can someone advise?

---

### Post by wildmanne39 on 2011-05-29
> **maciej234 said:**
> The mouse cursor freezes for a few seconds and it's a big problem.  I tried to change my grub to:  

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic nolapic"

but that did not solve.  By googling, theres all sorts of forums about Linux and mouse cursor freezing problems on Thinkpads.  I need this to go away ; can someone advise?
Hi, when does it do it?. What version of ubuntu are you using? what are your system spec?Laptop? how old is the system.Are you using the cube? or effects?

---

### Post by maciej234 on 2011-05-29
> **wildmanne39 said:**
> Hi, when does it do it?. What version of ubuntu are you using? what are your system spec?Laptop? how old is the system.Are you using the cube? or effects?



I'm using the newest version of Ubuntu, The system is brand new its a 2nd gen INTEL i5 2510.  It happens every 5 minutes, the cursor will be frozen and not respond for 2-3 seconds.

---

### Post by wildmanne39 on 2011-05-29
> **maciej234 said:**
> I'm using the newest version of Ubuntu, The system is brand new its a 2nd gen INTEL i5 2510.  It happens every 5 minutes, the cursor will be frozen and not respond for 2-3 seconds.Hi, do a search on the forums put in thinkpad cusor freezes and it will bring up your best answers.

---

### Post by corncob on 2011-05-29
I'm thinking hardware.  Are you using the touchpad or USB mouse?  If the latter, try another USB port or another mouse (or try the mouse in another computer).  Do you have another operating system on the computer?

---

### Post by maciej234 on 2011-05-31
it happens on live USB's for Linux mint and Fedora 15 too.  The mouse just times out for a few seconds and I cant move the cursor.  Happens on the Trackpoint and the touchpad

---

### Post by corncob on 2011-05-31
> **maciej234 said:**
> it happens on live USB's for Linux mint and Fedora 15 too.  The mouse just times out for a few seconds and I cant move the cursor.  Happens on the Trackpoint and the touchpad

Then it does sound like hardware.  I never had both a trackpoint and touchpad.  I wonder if they could be fighting each other.  Can you disable the one you use less?

---

### Post by maciej234 on 2011-06-16
> **corncob said:**
> Then it does sound like hardware.  I never had both a trackpoint and touchpad.  I wonder if they could be fighting each other.  Can you disable the one you use less?


ive tried disabling and using just the track pointer but the freezing still happens every few minutes

---

### Post by alexou2648 on 2011-06-23
Hi dude, I have exactly the same problem, the mouse cursor freezes, and i have to unplug the mouse and plug it to make the mouse work again. Btw, nothing appears in the logs about this mouse issue. 
So i opened a question in launchpad:
[https://answers.launchpad.net/ubuntu/+source/xorg/+question/162213](https://answers.launchpad.net/ubuntu/+source/xorg/+question/162213)

---

### Post by chw1984 on 2011-06-26
I am having the same problem using openSuse on a ThinkPad Edge 11. As far as I could see the problem might be related to the process 'kseriod' which seems to use a lot of cpu every time my mouse-pad freezes. Maybe this can help finding a solution to the problem...


I would highly appreciate any hints...



Thanks,

Chris

---

### Post by maciej234 on 2011-06-27
> **chw1984 said:**
> I am having the same problem using openSuse on a ThinkPad Edge 11. As far as I could see the problem might be related to the process 'kseriod' which seems to use a lot of cpu every time my mouse-pad freezes. Maybe this can help finding a solution to the problem...


I would highly appreciate any hints...



Thanks,

Chris


Ive tried opensuse and my mouse didn't 'stick/freeze' on there but I remember scanning a post that stated UBUNTU had code written that was responsible for the mouse freezing.  If anyone has a solution or a work around please post.

I am using Kubuntu now and have the same pattern occur.  Every few minutes the mouse will become stuck with now option but to wait until it unfreezes

---

### Post by chw1984 on 2011-06-28
> **maciej234 said:**
> Ive tried opensuse and my mouse didn't 'stick/freeze' on there but I remember scanning a post that stated UBUNTU had code written that was responsible for the mouse freezing.  If anyone has a solution or a work around please post.

I am using Kubuntu now and have the same pattern occur.  Every few minutes the mouse will become stuck with now option but to wait until it unfreezes


I should say that in my case it does not happen very frequently (~every 10 mins). I am also not sure if the problem has been there from the beginning... maybe it came with one of the patches I installed. I guess the best way to find out if we have the same problem is that you check with 'top' in the shell if the process 'kseriod' shows up when the mouse gets stuck.


Chris

---

### Post by chw1984 on 2011-09-03
This link should give some hints how to solve the problem. I haven't tried it yet but for others the described workarounds seem to have done the job.


[https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Touchpad_synchronization_issues](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Touchpad_synchronization_issues)



Cheers,
Chris

---

