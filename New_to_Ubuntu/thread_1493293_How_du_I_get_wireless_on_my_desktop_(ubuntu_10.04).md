---
title: "How du I get wireless on my desktop (ubuntu 10.04)?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by geirknappen on 2010-05-25
I downloaded and installed Ubuntu 10.04 on my laptop a while ago, I noticed that no wireless driver was installed, so I connected my laptop to an Internet cable end clicked update, and that worked well. 

However... Now I am thinking about doing the same with my Desktop computer. When I installed Ubuntu 9.04, I did not have this problem with my desktop or my laptop, because the driver was already on the disk. So maybe I can insert the ubuntu 9.04 disk and use the same driver, or how do I do this? I think its a ralink 2500 wireless chipset.

---

### Post by SRST Technologies on 2010-05-25
You don't need the CD.  The driver for the Ralink 2500 is built into Ubuntu already.  Turn off the computer, plug in the ralink 2500, reboot, and it will work.  You may need to reboot one more time after you have installed the device and rebooted, but after the second reboot it will be fine.

One of my computers has a ralink 2500 in it and it's fairly ok, but it does not get great range so make sure the computer with the ralink 2500 is somewhat close to the router.

---

### Post by geirknappen on 2010-05-26
Well... The ralink was plugged in when i first installed.  When I right click the wireless symbol, it is possible to enable networking and notifications but it is not possible to enable wireless, it is just a gray area. What do I do to make it possible enable the wireless too?

---

### Post by SRST Technologies on 2010-05-26
Remove the device, reboot, plug in the device, reboot.  Should work right away.

---

### Post by izark47 on 2010-05-26
Ralink cards have a known issue with setting for wpk=spk. You need to set your router to use AES only, not tkip/AES.  once you have that done it should connect just fine.

---

### Post by geirknappen on 2010-06-22
"You need to set your router to use AES only, not tkip/AES."

I had no idea what to do, so I decided to use ubuntu 9.04 on my desktop computer. Like I said, I did not have this problem with ubuntu 9.04. I going to use ubuntu 10.04 for my laptop. Skype seems to work better on ubuntu 10.04.

---

### Post by geirknappen on 2010-09-12
I downloaded and installed the 10.04.01 point release, thinking maybe it will work now. It doesn't. I am not allowed to touch the router and can't set it to aes only. I can use 10.04.01 as long as i have a  very long lan cable plugged into the router and to my desktop. I really hope 10.10 will have wireless working.

---

### Post by migs73 on 2010-09-12
> **SRST Technologies said:**
> Remove the device, reboot, plug in the device, reboot.  Should work right away.
Did you try this?

---

### Post by geirknappen on 2010-09-18
> **migs73 said:**
> Did you try this?

Yes, I tried that many times. Nothing happened.

---

