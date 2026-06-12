---
title: "audio concern"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by zenCpel on 2010-06-16
**i am a new user of ubuntu, then i have a new sound card ****_CS4281 but then i dont  know how to configure or to setup it coz the driver for the said sound card is not executable due to it is on windows format,thats why icant hear any audio , is anyone who can help me or can walk me through my concern?? please..._**

---

### Post by yaaarrrgg on 2010-06-17
What's the brand and model of the sound card?

You won't use the Windows driver but a driver written for Linux.  Most drivers are included in with Linux, and work out of the box.

---

### Post by pete1983 on 2010-06-17
I would very strongly recommend upgrading to [COLOR="SeaGreen"]9.10[/COLOR] or [COLOR="YellowGreen"]10.04 LTS[/COLOR] in order to see if your card is supported under either of those versions. There are usually a good amount of hardware support additions with every new version. To be fair this is not always the case so you should try to run a live Cd or Usb f[COLOR="Red"]irst before install or upgrade[/COLOR] of each to see if the sound will work with another newer version of Ubuntu. 


Good luck zenCpel I hope this helps.

---

### Post by zenCpel on 2010-06-18
> **yaaarrrgg said:**
> What's the brand and model of the sound card?

You won't use the Windows driver but a driver written for Linux.  Most drivers are included in with Linux, and work out of the box.




re: my sound card is CS4281

---

### Post by Perfect Storm on 2010-06-18
> **zenCpel said:**
> re: my sound card is CS4281

There's a bug regarding your sound card driver in 8.04 so it's recommendable you'll upgrade your system. The newest version of Ubuntu is 10.04

Bug report: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/575538](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/575538)

---

### Post by zenCpel on 2010-06-18
> **yaaarrrgg said:**
> What's the brand and model of the sound card?

You won't use the Windows driver but a driver written for Linux.  Most drivers are included in with Linux, and work out of the box.


re: whre cn i find that driver on linux for my**_ CS4281_** sound card??

---

### Post by Perfect Storm on 2010-06-18
> **zenCpel said:**
> re: whre cn i find that driver on linux for my**_ CS4281_** sound card??

The driver comes with ubuntu, you don't need to install anything.
Read my comment regarding your version of Ubuntu and your audio card and its driver.

---

### Post by zenCpel on 2010-06-18
> **yaaarrrgg said:**
> What's the brand and model of the sound card?

You won't use the Windows driver but a driver written for Linux.  Most drivers are included in with Linux, and work out of the box.


re: i can hear a sound if im going to play a music video on youtube, but i cant hear any sound using rythmbox once im  goin to play the mp3 format song,,, hep me out please...

---

### Post by yaaarrrgg on 2010-06-20
Sounds like you need the mp3 codec as well.  After you've upgraded to 10.04, you can go to:

Applications -> Ubuntu Software Center 

(On older versions this is under Applications -> Add/Remove) 

And search for:

ubuntu-restricted-extras

Install that package.  It has the mp3 codec.  The codec is not included by default, because of licensing restrictions.

---

