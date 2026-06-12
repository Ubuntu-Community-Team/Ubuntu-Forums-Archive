---
title: "Clean install bug?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by rosswmcgee on 2009-10-30
Does the clean install of 9.10 have the same bug as the upgrade? 

Your system may become unstable

---

### Post by sdpiowa on 2009-10-30
I'm not sure.  However, I kept getting an error report that said something like that, and I did do a clean install.

---

### Post by connorh123 on 2009-10-30
Hi.
```
sudo apt-get clean
```

---

### Post by kansasnoob on 2009-10-30
> **connorh123 said:**
> Hi.
```
sudo apt-get clean
```

Would you care to quantify that with some reasoning?

Can all instability be fixed by running that command?

I know what it does but we shouldn't just randomly toss out commands with no explanation whatsoever.

What if the OP finds they've lost an app that they like? Would they know it's because a needed .deb was removed?

---

### Post by kansasnoob on 2009-10-30
> **rosswmcgee said:**
> Does the clean install of 9.10 have the same bug as the upgrade? 

Your system may become unstable

Need to be much more explicit.

Where do you see a "bug" that says "Your system may become unstable"?

---

### Post by connorh123 on 2009-10-30
Does it really need explanation?
I thought it was self-explanatory. Okay.
Pretty much what it does is it cleans out any worthless things that are on your computer. (ex:items in trash that take up way to much space)
Don't worry, nothing will happen to your files. I used this command earlier when I didn't have enough space for Karmic, none of my important files were gone.

---

### Post by rosswmcgee on 2009-10-30
Well I ran the sudo apt-get clean  

Then re booted no problem with bug so far. Then did a complete shut down, and re start again no more bug problem. If this continues then I have no more issuses
with the 9.10 upgrade. I did make a cd and can do a clean install if neccessary. 
So far and it has been close to an hour no more problems with 9.10.

I will wait several days before doing an upgrade on my wife's ubuntu 9.04 just in case. Please and thank you!

---

### Post by rosswmcgee on 2009-10-31
This morning after first boot bug returned, still that is the only upgrade issue I have left and I assume they will fix it, becuase I see a ton of people with the same problem when I report the error.

---

### Post by connorh123 on 2009-10-31
Did that command help you at all? If not, wait a couple of days, or in the mean time, file it as a bug [here.]("https://launchpad.net/ubuntu/+bugs")

---

### Post by ibuclaw on 2009-10-31
> **connorh123 said:**
> Does it really need explanation?
I thought it was self-explanatory. Okay.
Pretty much what it does is it cleans out any worthless things that are on your computer. (ex:items in trash that take up way to much space)
Don't worry, nothing will happen to your files. I used this command earlier when I didn't have enough space for Karmic, none of my important files were gone.

Wrong ....

[QUOTE=the manual][NOPARSE]        clean

            clean clears out the local repository of retrieved package files.
            It removes everything but the lock file from
            /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
            APT is used as a dselect(8) method, clean is run automatically.
            Those who do not use dselect will likely want to run apt-get clean
            from time to time to free up disk space.[/NOPARSE][/QUOTE]


Source of information: [http://manpages.ubuntu.com/manpages/karmic/en/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/karmic/en/man8/apt-get.8.html)


So FYI, running that won't really solve anything, albeit clear out maybe 50MB of debian packages cached locally.

But, then again, the OP hasn't really what the **bug** that they are getting, so it is hard to be certain whether or not this was a first time boot bug, or something that fixed itself in a recent package upgrade.

---

### Post by kansasnoob on 2009-10-31
> **rosswmcgee said:**
> This morning after first boot bug returned, still that is the only upgrade issue I have left and I assume they will fix it, becuase I see a ton of people with the same problem when I report the error.

It would be helpful if you posted the link to the bug report.

---

### Post by rosswmcgee on 2009-11-01
No one yet has answered my original ? 
So is the 9.10 problem 422536 confined to the upgrade and absent from the clean install?

422536 seems to be my only problem.

---

### Post by rosswmcgee on 2009-11-01
422536 seems to be my only problem, I read via google that it has been fixed, but I do not see it in my update manager.

---

### Post by rosswmcgee on 2009-11-02
Still no answer to the question will a clean install end the bug422536?

---

### Post by rosswmcgee on 2009-11-02
OK for me this thread is solved the answer I came up with is to bite the bullet, and 

do a clean install. The install went fine just like all my Ubuntu installs have, and the dreaded bug has fled, and all is well that ends well. Never say never but no windows for me.

---

### Post by arashiko28 on 2009-11-02
> **rosswmcgee said:**
> Well I ran the sudo apt-get clean  

Then re booted no problem with bug so far. Then did a complete shut down, and re start again no more bug problem. If this continues then I have no more issuses
with the 9.10 upgrade. I did make a cd and can do a clean install if neccessary. 
So far and it has been close to an hour no more problems with 9.10.

I will wait several days before doing an upgrade on my wife's ubuntu 9.04 just in case. Please and thank you!

Try to plug in an external drive or USB memory stick, it's when I get the crash notifier.

---

### Post by Ian Sinclair on 2009-11-03
Last time I looked, a clean install of 9.10 was available only to 32-bit machines. Despite an update todate today (containing a kerneloops package) the problems continue. I think a clean install of 9.04 in indicated.

---

### Post by rosswmcgee on 2009-11-04
Agreed! did it but when I installed the restricted drievers it gave me a blank screen

on bootup/ did another clean install all is well.

---

### Post by CaptainMark on 2009-11-04
you will still get this bug on a clean install, its related to ext4 ive read, should be fixed with a patch soon, dont worry.

---

### Post by philinux on 2009-11-04
> **Ian Sinclair said:**
> Last time I looked, a clean install of 9.10 was available only to 32-bit machines. Despite an update todate today (containing a kerneloops package) the problems continue. I think a clean install of 9.04 in indicated.


Ok some info needs clearing up.

1. 64 bit Karmic has been available since before alpha1. I should know I've been testing it for 6 months.


2. the bug [https://launchpad.net/bugs/422536](https://launchpad.net/bugs/422536) can be safely ignored if you read most of the informed posts.

---

