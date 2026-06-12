---
title: "How to put in code"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by alpeezy on 2010-12-03
I am confused how do i put in:
sudo mkdir /etc/adobe 
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg

Terminal will not let me put all 3 in...

After the 1st line I get this output


perkins@perkins-desktop:~$ sudo mkdir /etc/adobe 
[sudo] password for perkins: 
mkdir: cannot create directory `/etc/adobe': File exists

Tried to put all 3 in no go what am I doing wrong thanks in advance!!!!

---

### Post by Foxheadz on 2010-12-04
just don't run the first one

---

### Post by alpeezy on 2010-12-04
Here is the output with the second one only..


root@perkins-desktop:/home/perkins# sudo su
root@perkins-desktop:/home/perkins#

---

### Post by Foxheadz on 2010-12-04
the second one just gives you root until you quit the terminal. 
Just type : sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg

---

### Post by alpeezy on 2010-12-04
Then here is the 3rd...


root@perkins-desktop:/home/perkins# root@perkins-desktop:/home/perkins# sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
bash: root@perkins-desktop:/home/perkins#: No such file or directory

Trying to do full screen on YouTube   

Thanks for your response by the way...

---

### Post by slooksterpsv on 2010-12-04
> **alpeezy said:**
> Then here is the 3rd...


root@perkins-desktop:/home/perkins# root@perkins-desktop:/home/perkins# sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
bash: root@perkins-desktop:/home/perkins#: No such file or directory

Trying to do full screen on YouTube   

Thanks for your response by the way...

Oops on that just type:
echo OverrideGPUValidation=1 >> /etc/adobe/mms.cfg

You don't need sudo or that if you already did sudo su, which is better to do for this instance.

---

### Post by alpeezy on 2010-12-04
All this does is take me back to root desktop as below:


root@perkins-desktop:/home/perkins# echo OverrideGPUValidation=1 >> /etc/adobe/mms.cfg
root@perkins-desktop:/home/perkins#

---

### Post by GrantStoner on 2010-12-04
It finishes silently. It has no output. You know it's done when it stops without an error.

---

### Post by GrantStoner on 2010-12-04
And the way I understand it, it looks like you tried to put them all in at the same time at first? If you're copying and pasting them from somewhere, just do them one at a time. It'll be easier to figure out where you made errors next time.

---

### Post by alpeezy on 2010-12-04
Thanks for your help...

---

### Post by asmoore82 on 2010-12-04
```
sudo su 
sudo echo \"OverrideGPUValidation = 1\" >> /etc/adobe/mms.cfg
```
^very, very bad habits:
`sudo su` is a big no-no without an extremely compelling reason.
`sudo -s` is a better alternative, but still unnecessary.
`sudo` has absolutely no effect on shell redirection operators(<, >, >>, etc.)

The most proper way to accomplish the same in ubuntu is simply this:
```
echo '"OverrideGPUValidation = 1"' | sudo tee -a /etc/adobe/mms.cfg
```
^I've also taken the liberty to clean up that `echo`, this just looks better to me :KS

---

