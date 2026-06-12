---
title: "Access to /home/username folder !!!"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by InfernalAngel on 2010-02-26
Uhm Hi there. I had an issue seem lame but I don't know how to solve it rite now.

I had a Toshiba laptop which installed the ubuntu 9.04. When upgrading to 9.10 the laptop crashed due to the over heat of the heatsink (yes thanks Toshiba for that function, I'm really thankful lol :P). 

The problem come to me that after the crash my system completely crash down and can't boot normal anymore seem it can't go the the GUI but it didn't show me the place for me to login in terminal either.

What i want to do here is to backup the /home/myuername folder. It's a matter of life and death to me becuz it full of porn (j/k), it has a lot of my past years project so I'll be in deep **** if I can't digging them out. 

I've tried out this solution: use another CD to boot but I can't access to /home/myusername because I've did changed to permission of them so It can only read by me (not even when you login as root). And since I've used the CD to boot so it counted as another system rite? and in this case my HD is like an external HD.

PLZ help me, I really want all my porns (I SAID IT'S A JOKE :) )back. Seriously that I really want to know there a way i can backup that folder.

Kind Regards

---

### Post by Peter09 on 2010-02-26
Have you tried holding the shift key down while the system is booting. You should then get a grub menue and from there be able to select recovery mode. If you can get there you can have the option to reconfigure your graphics drivers or get to a command shell. 
 
It would be unusual to lose Linux just because of a crash -- unless a disk has become significantly corrupt!

---

### Post by InfernalAngel on 2010-02-26
Uhm I'm not lose linux ... I'm getting more and more addicted to it. But here is my problem. It's crashed cuz it "on the way" upgrading from 9.04 to 9.10 ... I've just leave the computer thu the night and when morning come ... oops

If my laptop gona work to hard it'll raise a strike by shutdown (Toshiba common heatsink problem). So It'll eventually shutdown if I force to work hard. I wish I can use a whip ...

The only option now is bring the latop to the computer shop and ask them to fix the heatsink problem ... but it'll be after I can backup my folders first. So is there any solution to do that since I can take the HD out plug it in External HD box and use my Desky (also running Ubuntu) to backup the folder. The problem here is the permission restricted.

Kind regards

---

### Post by Peter09 on 2010-02-26
Are you saying that you laptop is broken - or did it just shutdown because it got hot. Normally a hot shutdown will resolve itself once it cools down. You should be able to boot into the laptop again.
 
If you are using another machine to look at the disk then using root should give you access to your files. Can you clarify your problem.

---

### Post by InfernalAngel on 2010-02-26
> **Peter09 said:**
> Are you saying that you laptop is broken - or did it just shutdown because it got hot. Normally a hot shutdown will resolve itself once it cools down. You should be able to boot into the laptop again.
 
If you are using another machine to look at the disk then using root should give you access to your files. Can you clarify your problem.

It shuttled down cuz it got hot, and if you're turning it on it'll run for a few minutes and shutdown again since it "think" it "so hot " again. Back in the past I needed another small fan and coolbase to keep it stable but ... the problem getting worse now. The shutting-down event do appear more frequently and repeated ... so It'll go to the shop soon when I got my hand on this month salary. So reboot the comp just give me a few minutes to work on the comp ... but I can't do any thing in a few minutes ...

I did not took the HD out and use it as a external HD on other machine yet but I did try to boot with the CD, it let me to access to the GUI since It created a virtual system by install CD and it can let me to access to my HD as external HD but I can't access to /home/mysuername since I remembered I've set some access permission restrict since the last time I've sent it to repair shop (it will come in with some .htaccess rite ? ) . So now I guess I can't access it anymore :( . Is it the same with on Window system with NTFS if you enable protection for Document folder then you can't access to it again even the HD was mounted from other window systems ???

Kind Regards
So sorry if I've troubled and confused u guys

---

### Post by Peter09 on 2010-02-26
Couple of thoughts-
 
With the machine turned off get the vacuum cleaner and try to suck any dust from the fan vents - that is most probably your problem. It many help enough to boot and transfer your stuff to a usb.
 
If you boot from a CD you may need to change the read/write access on your home folder.
 
the terminal command
 
```
sudo chmod 664 <path to your files> 
```
may give you read access to them.

---

### Post by InfernalAngel on 2010-02-26
> **Peter09 said:**
> Couple of thoughts-
 
With the machine turned off get the vacuum cleaner and try to suck any dust from the fan vents - that is most probably your problem. It many help enough to boot and transfer your stuff to a usb.
 
If you boot from a CD you may need to change the read/write access on your home folder.
 
the terminal command
 
```
sudo chmod 664 <path to your files> 
```may give you read access to them.
I know this is stupid but what happen if I had turned off the sudo for any other account except for the one which I supposed to login :D. So when the comp booting with the CD I can sudo and do the chmod for them ?

---

### Post by Peter09 on 2010-02-26
Booting from the CD gives you sudo rights for the system that you have booted. You should have rights over any local filesystem (disk) that you mount as well.
 
In short - you should be ok -

---

### Post by InfernalAngel on 2010-02-26
> **Peter09 said:**
> Booting from the CD gives you sudo rights for the system that you have booted. You should have rights over any local filesystem (disk) that you mount as well.
 
In short - you should be ok -
tks for great advices

---

### Post by Robster2 on 2010-02-26
Boot using a live CD or USB.

You should be able to access and mount your partition.

Back up your files then reinstall.

I bet you have a 64bit dual core Toshiba laptop.  The old ones got really hot.  The new ones are better.

---

### Post by A_M_S on 2010-02-26
> **Peter09 said:**
> Couple of thoughts-
 
With the machine turned off get the vacuum cleaner and try to suck any dust from the fan vents 


When using a vacuum cleaner, you can damage your hardware if the fan rotates. The fan acts as a power generator.

To remove dust from a fan, first remove it from the equipment and then proceed with the cleanning.

---

### Post by mikechant on 2010-02-26
> When using a vacuum cleaner, you can damage your hardware if the fan rotates. The fan acts as a power generator.

To remove dust from a fan, first remove it from the equipment and then proceed with the cleanning.

Given you're doing this with the power off, it might be a lot easier to carefully jam a small screwdriver in the fan blades while vacuuming it, to stop it rotating.

---

