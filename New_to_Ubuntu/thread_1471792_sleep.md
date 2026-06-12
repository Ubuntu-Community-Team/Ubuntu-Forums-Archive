---
title: "sleep"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by MacKennedy on 2010-05-03
So 10.04 wont resume from sleep for me without a hard restart. 9.10 was similar, now it's just a blank screen instead of a blinking cursor. Is this still a common issue or is it something to do with my outdated hardware? I'm running an athlon 3200 with an msi motherboard with first gen sata. After 9.04 the installer does not see my hard drives so I'm guessing support for that board has ended. Any input is appreciated. 
Mike

---

### Post by nhasian on 2010-05-03
did you check to see if here is a newer bios for your motherboard?  that may help.

---

### Post by MacKennedy on 2010-05-03
You got me there, but I will do that. Thanks.

---

### Post by seenthelite on 2010-05-04
If you are getting a blank screen trying to resume from suspend, try waiting for about 1 minute and see if it then resumes. That is what is happening on on of my Laptops the first time I try to resume from suspend after rebooting. Then the next time I suspend it will resume normally, quickly, and I have to repeat this each time I reboot then it is okay until I reboot. I do not need to reboot often so it is not a big deal.

---

### Post by DrWig on 2010-05-04
I'm getting the same issue:

More info...
[http://ubuntuforums.org/showthread.php?t=1464559&highlight=drwig](http://ubuntuforums.org/showthread.php?t=1464559&highlight=drwig) 

cheers

DrWig

---

### Post by MacKennedy on 2010-05-04
updated bois but no luck. i guess its a holding pattern for now. i havent been at this long enough to start tinkering so ill just have to make due for now.

---

### Post by lavinog on 2010-05-04
What video drivers are you using?

---

### Post by techunit on 2010-05-04
If you have ATI graphics and installed restricted drivers for it then this will cause this problem...

---

### Post by cariboo on 2010-05-04
I'm not sure about the sleep problem, as I haven't had a problem with it since Dapper (6.06), but I now use MSI motherboards for almost everything. The problem with not seeing your SATA drive, is a problem with the Live installer, I have two system that exhibit the same behavior, the work around is to use the alternate installer iso. It is text based, but is fairly simple to use, instead of using a mouse you use the keyboard to navigate. It also comes with a couple of things you don't get with the Live CD, you can setup LVM (logical volume management) and full disk encryption.

---

### Post by MacKennedy on 2010-05-04
Thanks for the responses. ATI it is and restricted drivers they are. I will switch to the open source ones and see what happens. As for the installer not seeing my drives, I will download the alt .iso so at least I have it on hand in case I need it. Thanks again.

---

### Post by MacKennedy on 2010-05-05
ok, so switching back to the ubuntu video drivers did not work. it still wont resume from sleep.

---

### Post by ubunterooster on 2010-05-05
Is the screen even lit?

---

### Post by MacKennedy on 2010-05-05
depends, there are two settings in my bios for powermanagement. one causes the blinking cursor, the other blanks the screen but neither will resume. i have not tried hibernation and have reinstalled the ati drivers since i play games once in a while. i'll be building a new box later this year maybe, so hopefully that one will cooperate.

---

