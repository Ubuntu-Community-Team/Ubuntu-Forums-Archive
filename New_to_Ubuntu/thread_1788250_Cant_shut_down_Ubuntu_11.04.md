---
title: "Cant shut down Ubuntu 11.04"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by reelo2228 on 2011-06-22
I installed Ubuntu on this old PC, but got it up and running, then this problem came that i cant switch off the PC using ubuntu. It first logs off quite instantly, then the screen switched off, but the PC just kept running non-stop, i had to hold the power button to turn it off :/ i read from another forum that it has something to do with acpi controller or something, how do i fix this??

---

### Post by ewgchard on 2011-06-22
Try typing halt from the terminal shell 

Chard

---

### Post by reelo2228 on 2011-06-22
The Pc is at another place, coz i installed it for some another guy, will try that. But wht does it do? will it solve the problem, or do i have to type that everytime i shutdown??

---

### Post by dcsoldschool53 on 2011-06-22
In a terminal, type```
sudo shutdown -h now
``` to shutdown the computer now, and```
sudo reboot
```to reboot your system. For each one you will have to type in your password. This will not solve the problem, but you will be able to shut down and reboot the computer with no problems.

---

### Post by dcsoldschool53 on 2011-06-22
This can also help, with the two commands, make a launcher so that you can have to buttons to click. You are in natty, and I don't have that. Some one else with have to help you start the launcher, but this is what you will need to have for the entries.```
Name: Shutdown
``````
Command: sudo shutdown -h now
``````
Comment: Shuts down the computer system complete.
``````
 Icon: use whatever icon you want to use
```And you can do the same for the reboot command too.

---

### Post by reelo2228 on 2011-06-23
Sory for late reply, i tried the shutdown command and made it to a shortcut, but it still wont switch off the PC, worst of it, immediately after log off, the screen turned to a jitter of colours, as if it freaked off that i'm going to kill its power xD

---

### Post by nik1979 on 2011-08-30
there are a series of threads regarding 11.04's problem shutting down/reseting.

In my Laptop Lenovo Y430, the problem manifests when I press reset or shutdown nothing happens. 

I noticed I can shutdown when freshly booted, but as soon as I had programs running, even if I turned them off, I cannot shut down anymore. 

My solution was to Switch From User (third option in the power down menu), then shut down from there. 

Hope this gets resolved eventually. Awesome boot loading time, but  going to switch from user to shut down is a bit of a hassle.

---

