---
title: "Cant install Ubuntu (look inside!)"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by serbforce on 2009-07-31
Hello everyone , i just recently switched from Windows (yuck) to Ubuntu and i love it , with a little help from this forum and all the aveilable online guides i managed to figure out everything i needed.
Thing is , i own 2 PC's and after i saw how great Ubuntu is i wanted to install it on my second machine also.
But thats when my first serious Ubuntu prolem came up: When i boot Ubuntu cd for the install it seems that it loads the settings and near the end it just goes black screen and stays like that forever (i cant even eject cd when that happans).
My configuration on the machine at question is :
-Pentium 4 3ghz
-Ati Radeon 2600 series HD (ive read that this might be the problem)
-512 ddr ram
-etc
I also recorded how the missfortunate event looks like with my cell phone but youtube wont let me upload it for some reason so i cant share it with you guys yet.

Any help/advice will be greatly appriciated.
Thanks in advance!
-Srdjan

---

### Post by llamabr on 2009-07-31
That sucks.  Where did you get this disk?  Is it the same one you installed from before?  Any scratches?  And does it work as a livecd?

---

### Post by slakkie on 2009-07-31
Which version are you trying to install?

---

### Post by serbforce on 2009-07-31
Its the same disk i used on first PC, i also burned 5 more copies from the ISO from the official site using both Ubuntu and Windows on 4x and 8x and always the same result.

> **slakkie said:**
> Which version are you trying to install?

9.0.4

> **llamabr said:**
>   And does it work as a livecd?

It does.

---

### Post by Humanum on 2009-07-31
Hi,

Can you try to download an iso file and make a new cd ?

Just in case the problem is related to the CD you have...

---

### Post by serbforce on 2009-07-31
> **Humanum said:**
> Hi,

Can you try to download an iso file and make a new cd ?

Just in case the problem is related to the CD you have...

I have ISO file on both machines i burned 6 different copies in total, even on different types of DVD's so the disk is 100% ok

---

### Post by aesis05401 on 2009-07-31
I should mention here that the cds ship with a utility to verify their integrity.  It should be on the menu where you choose to run livecd or install OS. 

You may require an 'alt' install cd because of the age of the hardware, but I know very little about that, so you will need to search a bit for more info.

---

### Post by serbforce on 2009-07-31
i used the utility and it checked out.
I dont what you mean by alt install CD?

---

### Post by wojox on 2009-07-31
Nine times out of ten if it freezes during install it's either RAM issues or a corrupted CD.

---

### Post by saidinesh5 on 2009-07-31
hey i do remember this problem.. my room mate had the same problem...
and ya. your CD ,probably,is perfectly fine...
i dont really know how he solved the problem , but these might help:

try a different version of ubuntu / a different distro ...
try getting into the console only mode(without starting X server) and install the approp. graphics drivers..

good luck :)

---

### Post by serbforce on 2009-07-31
> **wojox said:**
> Nine times out of ten if it freezes during install it's either RAM issues or a corrupted CD.

So you think it cant be the my Ati card?
And just to clear thing , it doesnt even start the installation, it freezes in that initial stage.

---

### Post by aesis05401 on 2009-07-31
Link:[http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate]("http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate")

I have never had to do this, as I only use Ubuntu on recent hardware.  Using this installation method will allow you to get Linux onto the machine.  After that, it usually takes some searching to find the right modifications to make that will allow you to install the full graphical environment. 

I have never done this personally, but a lot of people have.  Sorry I have no more good advice on this issue.

Best of luck.

Edit: There might be additional info on the requirements page for livecd: [https://help.ubuntu.com/community/Installation/SystemRequirements]("https://help.ubuntu.com/community/Installation/SystemRequirements")

---

### Post by serbforce on 2009-07-31
> **aesis05401 said:**
> Link:[http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate](http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate)

I have never had to do this, as I only use Ubuntu on recent hardware.  Using this installation method will allow you to get Linux onto the machine.  After that, it usually takes some searching to find the right modifications to make that will allow you to install the full graphical environment. 

I have never done this personally, but a lot of people have.  Sorry I have no more good advice on this issue.

Best of luck.

ok thank you very much , started the download :)

---

### Post by serbforce on 2009-07-31
OK i installed text ''alt'' mode Ubuntu, and it installs ok up untill the end, just before username screen, same bugged screen appears for a second and then switches to username screen, but i can not type anything there ....

---

### Post by jwleonard on 2009-07-31
I would recomend you backtrack a little and try reinstalling from the Live CD again.  I don't remember exactly where it is but somewhere on the initial screen where you choose to "try without installing" or "install to hard drive" (these aren't the exact wordings), you can choose to load the live CD in safe graphics mode.  I have to use this option on my Toshiba laptop with an ATI 200M chipset/onboard graphics.  It is in one of the options listed at the bottom (Either F4 or F6) then select safe graphics and boot the live CD.  If it boots you should be able to install to the hard drive from the booted live cd.  It should configure your video settings properly during the install.  I have attatched a picture of the screen I am talking about.[IMG]http://img21.imageshack.us/img21/2161/ubuntuinstall2.png[/IMG]

---

### Post by serbforce on 2009-08-01
> **jwleonard said:**
> I would recomend you backtrack a little and try reinstalling from the Live CD again. I don't remember exactly where it is but somewhere on the initial screen where you choose to "try without installing" or "install to hard drive" (these aren't the exact wordings), you can choose to load the live CD in safe graphics mode. I have to use this option on my Toshiba laptop with an ATI 200M chipset/onboard graphics. It is in one of the options listed at the bottom (Either F4 or F6) then select safe graphics and boot the live CD. If it boots you should be able to install to the hard drive from the booted live cd. It should configure your video settings properly during the install. 


Thank you so much, that was the right solution! i had some more trouble later installing drivers, but now everything is great.
Problem solved! :)

---

### Post by Geoff918 on 2009-08-01
Your problem is probably the x-server configuration. I had this problem with an old system, it would go to black screen, or sometimes I would get distorted lines for a moment or two and then black screen.

I wish I could remember how it was fixed, but if you look up the "delete x-server config" you should be able to find it on Google. I do remember I had to first boot into "Failsafe Recovery" first.

---

### Post by jwleonard on 2009-08-01
Glad to hear that worked for you!  I'm sure someone here can explain why it does that but I just know it normally works.

---

### Post by presence1960 on 2009-08-02
> **jwleonard said:**
> I would recomend you backtrack a little and try reinstalling from the Live CD again.  I don't remember exactly where it is but somewhere on the initial screen where you choose to "try without installing" or "install to hard drive" (these aren't the exact wordings), you can choose to load the live CD in safe graphics mode.  I have to use this option on my Toshiba laptop with an ATI 200M chipset/onboard graphics.  It is in one of the options listed at the bottom (Either F4 or F6) then select safe graphics and boot the live CD.  If it boots you should be able to install to the hard drive from the booted live cd.  It should configure your video settings properly during the install.  I have attatched a picture of the screen I am talking about.[IMG]http://img21.imageshack.us/img21/2161/ubuntuinstall2.png[/IMG]

nice! here is a link for future reference: [Boot options Live CD]("https://help.ubuntu.com/community/BootOptions")

---

