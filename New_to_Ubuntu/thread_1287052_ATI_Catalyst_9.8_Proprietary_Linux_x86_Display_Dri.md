---
title: "ATI Catalyst 9.8 Proprietary Linux x86 Display Driver (ERROR ISSUE I need help)"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by TuLesto on 2009-10-09
Okay, I have Ubuntu Jaunty Jackalope... so I downloaded the ATI Catalyst 9.8 Proprietary Linux x86 Display Driver and uninstalled the ATI propriety driver with this line copied off of another thread: brian@brian:~$ sudo apt-get remove --purge xorg-driver-fglrx

I then restarted the computer and hoped for the best.

Once I was signed in I commenced with the installation of Catalyst 9.8 I was immediately thrown off by the system bar and its title as well as it's install options: "ATI Proprietary Linux Driver 8.65 Setup" and Install Driver 8.65 on X.Org 7.4 and later releases"... I have X.Org 7.4 but the Driver I downloaded was unmistakably the ATI Catalyst 9.8 Proprietary Linux x86 Display Driver. I even saved the installation instructions to harddrive and looked at the title. See here: [https://a248.e.akamai.net/f/674/9206...cat99-inst.pdf]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat99-inst.pdf")   and attatchment.

After a while of confusion I decided to install it anyway so I went on and did all the steps I was told to follow and restarted

What bothers me most is what happened after the restart... I was unable to start Catalyst Control Center. The error message has been attatched.

I've been digging through webpages and so far I've had no luck in finding an answer that will fix my issue. I will keep digging tomorrow but my hope is fading.


I'll keep you posted. Thanks.

---

### Post by halitech on 2009-10-09
what video card do you have and are you running 32bit or 64bit?

when the install finished, did you run
```
sudo aticonfig --initial
```

---

### Post by QIII on 2009-10-09
If you are at all interested ...

ATI has decided to get on the Linux highway and get their act together.

They skipped right over release 9.9 to fast track 9.10 for Karmic.  From all accounts, all of the bad ju ju from the past has been rectified.  Apparently ATI doesn't like looking at nVidia's backside any more at the back of the Linux dog team.

Neither of my test machines for Karmic has an ATI gpu, so I can't test it.  But I plan to use it for my 64 bit production machine when I install Karmic.

Just a tidbit ...

---

### Post by halitech on 2009-10-09
thanks for letting us know. Have you heard if it will support only the cards currently supported by the 9.8 driver or will it support the cards that are currently on the legacy list as well?

---

### Post by QIII on 2009-10-09
Unfortunately, I don't know if it will exhume anything from ATI's "legacy" grave.

---

### Post by halitech on 2009-10-09
in that case its not really much better then the current driver :(

---

### Post by TuLesto on 2009-10-09
> **halitech said:**
> what video card do you have and are you running 32bit or 64bit?

when the install finished, did you run
```
sudo aticonfig --initial
```

I am running a 32bit copy of ubuntu 9.04 with an ATI Radeon 3400

I ran this: sudo /usr/bin/aticonfig --initial

which if I'm not mistaken is basically the same thing but just now I copy pasted sudo aticonfig --initial from your reply. I am going to restart the computer in a moment just after I reply to the other users.

oh and this is a laptop the graphics card is integrated

---

### Post by TuLesto on 2009-10-09
> **QIII said:**
> If you are at all interested ...

ATI has decided to get on the Linux highway and get their act together.

They skipped right over release 9.9 to fast track 9.10 for Karmic.  From all accounts, all of the bad ju ju from the past has been rectified.  Apparently ATI doesn't like looking at nVidia's backside any more at the back of the Linux dog team.

Neither of my test machines for Karmic has an ATI gpu, so I can't test it.  But I plan to use it for my 64 bit production machine when I install Karmic.

Just a tidbit ...


COOL! thanks for that bit of information! very much appreciated since I am somewhat of a geek myself..

---

### Post by halitech on 2009-10-09
> **TuLesto said:**
> I am running a 32bit copy of ubuntu 9.04 with an ATI Radeon 3400

I ran this: sudo /usr/bin/aticonfig --initial

which if I'm not mistaken is basically the same thing but just now I copy pasted sudo aticonfig --initial from your reply. I am going to restart the computer in a moment just after I reply to the other users.

oh and this is a laptop the graphics card is integrated

should be the same but lets see what happens after a reboot

---

### Post by TuLesto on 2009-10-09
> **halitech said:**
> should be the same but lets see what happens after a reboot

ok rebooting now

---

### Post by TuLesto on 2009-10-09
> **halitech said:**
> should be the same but lets see what happens after a reboot


No, luck doesn't seem to be on my side

nothing happened


should I try reinstalling? I can back up my documents and all to my external hd... we can continue from there... or should we just push on?

---

### Post by TuLesto on 2009-10-09
> **TuLesto said:**
> No, luck doesn't seem to be on my side

nothing happened


should I try reinstalling? I can back up my documents and all to my external hd... we can continue from there... or should we just push on?

I still will want to install the latest driver from AMD/ATi

---

### Post by TuLesto on 2009-10-09
Halitech? Are you still with me?

---

### Post by TuLesto on 2009-10-09
Just a quick question... Is ubuntu 9.10 out yet?

---

### Post by TuLesto on 2009-10-09
> **TuLesto said:**
> Just a quick question... Is ubuntu 9.10 out yet?

Oh the beta is out... i can wait 20 days for the final.

---

### Post by TuLesto on 2009-10-09
oh come on I know I shouldn't be impatient and I'm usually not but I just drank 2 cups of coffee and well I feel supercharged now. 

could we continue with the thread please...

---

### Post by QIII on 2009-10-09
Wait for the final release.

There are still some issues being worked out...

(Don't try to install ATI's 9.10 driver.  It's for the 2.6.31.** kernel)

---

### Post by TuLesto on 2009-10-09
> **QIII said:**
> Wait for the final release.

There are still some issues being worked out...

(Don't try to install ATI's 9.10 driver.  It's for the 2.6.31.** kernel)

Wait, so is driver for ubuntu 9.10? -- OH! Ha ha! Right, no I understand... so you say they dont have a 9.9 driver. is 9.8 their latest release for Ubuntu 9.04?

---

### Post by sandyd on 2009-10-09
why don't you just do
jockey-gtk

it might not be the latest driver, but its tested a lot by ubuntu developers.

---

### Post by TuLesto on 2009-10-10
> **carlee said:**
> why don't you just do
jockey-gtk

it might not be the latest driver, but its tested a lot by ubuntu developers.

jockey-gtk? I'm guessing that it would be in the synaptic-package-manager.. i think it was actually Catalyst9-9 that i tried installing i have reinstalled my computer with the 64bit edition of ubuntu jaunty so it should be somewhat faster -- gaming might be smoother too... i hope since i'll be running wine

:) thanks a ton 
     P.S. Is jockey-gtk better than the default version they offer or is it the same? oh and also, i dont have an ati radeon hd3400 -- it's an ati radeon hd3200 and perhaps that is why i was having such difficulties. i will be doing more research for an ati driver and the hd3200 ...something like that. previously i had downloaded a driver from the imbedded driver section not for a notebook and i think thats where things went wrong

well i'll check back with you all in a few hours or so. ciao! and thanks for the emotional support.

---

### Post by TuLesto on 2009-10-10
> **TuLesto said:**
> jockey-gtk? I'm guessing that it would be in the synaptic-package-manager.. i think it was actually Catalyst9-9 that i tried installing i have reinstalled my computer with the 64bit edition of ubuntu jaunty so it should be somewhat faster -- gaming might be smoother too... i hope since i'll be running wine

:) thanks a ton 
     P.S. Is jockey-gtk better than the default version they offer or is it the same? oh and also, i dont have an ati radeon hd3400 -- it's an ati radeon hd3200 and perhaps that is why i was having such difficulties. i will be doing more research for an ati driver and the hd3200 ...something like that. previously i had downloaded a driver from the imbedded driver section not for a notebook and i think thats where things went wrong

well i'll check back with you all in a few hours or so. ciao! and thanks for the emotional support.

hm, seems like I'll be out for the rest of the day might get back later tonight. I'll get back to you all tomorrow. I'm just glad I was able to upgrade to a 64bit ubuntu 9.04  -- SCORE!

---

