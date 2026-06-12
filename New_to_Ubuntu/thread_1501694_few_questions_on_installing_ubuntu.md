---
title: "few questions on installing ubuntu"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Proto_Blaze on 2010-06-04
im installing ubuntu on my friends pc. but he has dial up... how would i configure the dial up connection? one the dial up is connected how do i update the drivers? third... i have the ubuntu installer on a flash drive.... am i able to have other folders on the flashdrive or does it have to be dedicated to ubuntu?

---

### Post by cariboo on 2010-06-04
> **Proto_Blaze said:**
> im installing ubuntu on my friends pc. but he has dial up... how would i configure the dial up connection?

Have a look at this [page]("http://https://help.ubuntu.com/community/DialupModemHowto/GeneralDiscussion")

>  one the dial up is connected how do i update the drivers?

To install any restricted drivers needed go to System->Administration->Hardware Drivers


>  third... i have the ubuntu installer on a flash drive.... am i able to have other folders on the flashdrive or does it have to be dedicated to ubuntu?

Have a look [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") for how to setup a persistent usb device.

---

### Post by Proto_Blaze on 2010-06-04
the dial up page you suggested wasnt working.... and i think i might have mistyped the flash thing.. just to make sure i just want to be able to install from the flash drive... not have an os thing.... but id like to have folders on it as well... here is what my drive currently looks like
[IMG]http://i49.tinypic.com/dpit1l.jpg[/IMG]
in the section you will see a folder called "My" this has nothing to do with the ubuntu installer. can i have this folder on my flash drive without it interfering with the installer? also i have a new question... can i use the installer on the flash drive more than once? i would like to put it on all my computers.

---

### Post by sandyd on 2010-06-04
> **cariboo907 said:**
> Have a look at this [[URL="https://help.ubuntu.com/community/DialupModemHowto/"]page]("https://help.ubuntu.com/community/DialupModemHowto/GeneralDiscussion")
[/URL] 


To install any restricted drivers needed go to System->Administration->Hardware Drivers




Have a look [here]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") for how to setup a persistent usb device.
fixed it for ya

---

### Post by sandyd on 2010-06-04
> **Proto_Blaze said:**
> the dial up page you suggested wasnt working.... and i think i might have mistyped the flash thing.. just to make sure i just want to be able to install from the flash drive... not have an os thing.... but id like to have folders on it as well... here is what my drive currently looks like
[IMG]http://i49.tinypic.com/dpit1l.jpg[/IMG]
in the section you will see a folder called "My" this has nothing to do with the ubuntu installer. can i have this folder on my flash drive without it interfering with the installer? also i have a new question... can i use the installer on the flash drive more than once? i would like to put it on all my computers.
a) its okay to have other folders on it.
b) you can install as many times as you want

---

### Post by sandyd on 2010-06-04
also, if your dial-up modem is supported (99.9% are) you should be able to simply right click on the network icon (in the tray [ top right corner of screen, on the panel ]) and setup the connection from there

---

### Post by shariqdon on 2010-06-04
HI I instal Ubuntu 10. every thing fine before First Question Answer, when I finish Question Answer Then Setup Is Stop Responced. And Still In This COndition , i am Wait 20min but NOt done What may i do....[IMG]http://sxbccg.bay.livefilestore.com/y1pgkKWpaHBlUgSQYdzfnXReE74lL2HyFBKmcltwBk_RwBEIxti3e6EtWWlNErzOoDaw9T6Az3HEbZMPVKUaPLqWz4a9LrJZJqu/1ubuntu.JPG[/IMG]

---

### Post by Proto_Blaze on 2010-06-04
you guys are great! thank you.... ive never been to a forum so helpful... it makes me realize how much windows forum people are jerks.... most of the time

---

### Post by sandyd on 2010-06-04
> **shariqdon said:**
> HI I instal Ubuntu 10. every thing fine before First Question Answer, when I finish Question Answer Then Setup Is Stop Responced. And Still In This COndition , i am Wait 20min but NOt done What may i do....[IMG]http://sxbccg.bay.livefilestore.com/y1pgkKWpaHBlUgSQYdzfnXReE74lL2HyFBKmcltwBk_RwBEIxti3e6EtWWlNErzOoDaw9T6Az3HEbZMPVKUaPLqWz4a9LrJZJqu/1ubuntu.JPG[/IMG]
its a problem in microsoft virtual pc, theirs currently a handful of users who are having problems.

if you want to try it out in a virtual machine, try virtualbox.org

---

### Post by Proto_Blaze on 2010-06-04
one last question.... what are beans and how does the bean system work on the forums?

---

### Post by shariqdon on 2010-06-04
> **carlee said:**
> its a problem in microsoft virtual pc, theirs currently a handful of users who are having problems.

if you want to try it out in a virtual machine, try virtualbox.org

I also Try to Dual OS mode Try with Bootable CD with Fresh Harddrive but not done and same condition...

---

### Post by sandyd on 2010-06-04
> **shariqdon said:**
> I also Try to Dual OS mode Try with Bootable CD with Fresh Harddrive but not done
what do you mean not done?

---

### Post by shariqdon on 2010-06-04
> **carlee said:**
> what do you mean not done?

Not Done mean Setup Process Hang, after First Question Answer.
Hang LIke My Picture... i already use 8 version , its Succesful instal and i use it


Ok I have another question , If I instal Older version ! can i Update it for 10ver ????

---

### Post by sandyd on 2010-06-05
> **shariqdon said:**
> Not Done mean Setup Process Hang, after First Question Answer.
Hang LIke My Picture... i already use 8 version , its Succesful instal and i use it


Ok I have another question , If I instal Older version ! can i Update it for 10ver ????

yeah, just run```
update-manager -d
```

---

