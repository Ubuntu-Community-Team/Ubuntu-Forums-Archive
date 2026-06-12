---
title: "will not boot - my own fault"
date: 2011-04-23
forum: New to Ubuntu
---

### Post by tongueman on 2011-04-23
Hi Folks,

Hope someone can help, my problem is of my own making and am feeling rather stupid but here goes...

I changed the permissions on my home folder to 'list files only' (dont ask why) but forget to change them back before rebooting. Now Ubuntu will not boot with a naulitlus error and another which I cannot remember at the present.

My question is; 

Since I can access root via recovery mode, is there something I can do there to reapply the correct permissions to the home folder?

Or if I get a live Ubuntu disk is there a a recovery option on the live disk whioch will reset this folder for me?

Many thanks in advance

T.

---

### Post by Hedgehog1 on 2011-04-23
From either recovery mode or booting off the LiveCD/LiveUSB, you will want to run the **chmod** command to set the flags back the way you want them.

For an overview:

[http://www.manpagez.com/man/1/chmod/]("http://www.manpagez.com/man/1/chmod/")

[http://en.wikipedia.org/wiki/Chmod]("http://en.wikipedia.org/wiki/Chmod")

In recovery mode:
```
cd /home
```
```
sudo chmod -R 666 *
```

Off the LiveCD/LiveUSB (change sda**5** to whatever partition you home directory is in):

```
sudo mount /dev/sda**5** /mnt
```
```
cd /mnt/home
```
```
sudo chmod -R 666 *
```



***The Hedge***

:KS

p.s. Please be care with this command - the value here is for documents and assumes no executables in the /home directory

---

### Post by coffeecat on 2011-04-23
> **Hedgehog1 said:**
> In recovery mode:```
cd /home
``````
sudo chmod -R 666 *
```

Two points. In recovery mode you get a root shell so you don't need the "sudo". Also, this will change the ~/.dmrc file to 666 which you don't want. It should be 644 or 600. Indeed, I wonder if the OP's problem is down to wrong permissions on the ~/.dmrc file in the first place. Also the /home/username folder itself needs to be 750 or 700 - anything else will cause problems. 

> **tongueman said:**
> I changed the permissions on my home folder to 'list files only' (dont ask why)

Do you mean you changed them to 400 or 444? Yes, that would cause a problem - see above.

> **tongueman said:**
> Now Ubuntu will not boot with a naulitlus error and another which I cannot remember at the present.

It would help if you post the exact error. In fact, always post the error message when you start a support thread. A hint as to what is wroing is usually in the error message. :wink: At the very least it gives the basis for a bit of creative forum searching and googling.

---

### Post by tongueman on 2011-04-23
Thanks for reading, sorry for being a bit vague, here are the exact errors I'm experiencing in the correct order;

1. Could not update ICEauthority file/home/col/.ICEauthority

2. There is a problem with the configuration server (/usr/libgconf2-4/gconf-sanity-check-2 exited with status 256)

3. Nautilus could not create the following required folders; /home/col/Desktop, /home/col.Nautilus.  Before running Nautilus, please create these folders or set permissions such that Nautilus can create them

I hope this makes this a little clearer and am extremely grateful for your help.

Col.

---

### Post by drs305 on 2011-04-23
I wrote a guide about /home permissions and .dmrc problems that may help you restore things:
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")

---

