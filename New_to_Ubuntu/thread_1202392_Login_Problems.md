---
title: "Login Problems"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by tree56uk on 2009-07-02
[SIZE=2](I posted this elsewhere as well, Im desperate for help...)

Hey there. I downloaded the current 9.04 Wubi installer from the main site, it seemed to install well and I can boot up Ubuntu with no problems at all. However when I get to the screen where you put in your username and password, I put in my details and press enter, the screen goes blank for a few seconds except for the cursor, then the whole laptop reboots and takes me back to the OS selection screen. Another thing I noticed during the install was that it was downloading the Amd64 ISO, when im on Intel. I dont know if that matters. Any ideas? (Im also downloading the Wubi R134 to see if that will be any different) Thanks in advance.[/SIZE]

---

### Post by frunns on 2009-07-02
Don't worry about the Amd64, I'm not quite sure why it's called that, but it's usually just the naming of the 64-bit version... Can't give you much direction on your problem though.

---

### Post by tarps87 on 2009-07-02
If you computer has a 64bit processor then that image is fine, if not it should have died a log time ago :)

Have you made any changes to it since the install?

If you edit the boot line, highlight the boot entry and press 'e',
now edit the second line 'e' again (the line should start kernel).
Add this to the end of the line:
xforcevesa
now press enter and b to boot. This will start Ubuntu running using the vesa (failsafe) graphics driver

> **frunns said:**
> Don't worry about the Amd64, I'm not quite sure why it's called that, but it's usually just the naming of the 64-bit version... Can't give you much direction on your problem though.

It is called AMD64 for historic reasons, the 64bit processors were made by AMD, unfortunately it now causes confusion

---

### Post by tree56uk on 2009-07-02
> **tarps87 said:**
> If you computer has a 64bit processor then that image is fine, if not it should have died a log time ago :)

Have you made any changes to it since the install?

If you edit the boot line, highlight the boot entry and press 'e',
now edit the second line 'e' again (the line should start kernel).
Add this to the end of the line:
xforcevesa
now press enter and b to boot. This will start Ubuntu running using the vesa (failsafe) graphics driver



It is called AMD64 for historic reasons, the 64bit processors were made by AMD, unfortunately it now causes confusion

 I havent made any changes after the installation no. Thing is, my laptop is 32 Bit, so thats why I was thinking to myself during the install if it will work or not.   Im downloading another Wubi again to see if that works, if not, Ill try the the editing of the boot line like you say.

---

### Post by frunns on 2009-07-02
> **tarps87 said:**
> It is called AMD64 for historic reasons, the 64bit processors were made by AMD, unfortunately it now causes confusion

Yeah, I had **some** memory of something like that... 

Oh. You sure it's 32bit? As tarps is saying, it should've died some while ago if it is... Or I would think so at least. But if so, I'd say yeah, that's your problem.

---

### Post by tree56uk on 2009-07-02
Okay found out some possible useful info.  My Vista is 32 Bit and my computer itself is an ACPI x86-based PC.   I assume I am 32 bit. :/

---

### Post by tarps87 on 2009-07-02
Hmm, interesting, I would have assumed using a 64bit os on a 32bit processor would have thrown an exception as soon ans the kernel tried to boot. I have never tried it thought, I guess I'll have to :)
You can however successfully run a 32bit of on a 64bit processor. Could you let us know how it goes.

---

### Post by tree56uk on 2009-07-02
Okay, I think my Hardware is indeed actually 64Bit, so technically there should be no problems. Im still downloading Wubi again, and Ill try the bootline edits when I get to them. As a side note, a while back I used the Wubi installer for 8.04 Intrepid Ibex, that worked fine apart from the Atheros Wireless issues.

---

### Post by tarps87 on 2009-07-02
> **tree56uk said:**
> Okay found out some possible useful info.  My Vista is 32 Bit and my computer itself is an ACPI x86-based PC.   I assume I am 32 bit. :/

I believe that is a 64bit processor, if you boot into Ubuntu and press ctrl+alt+F1 you should be able to login without it rebooting.
Now type
```
sudo lshw ¦ grep cpu -A 10 ¦ grep width
```
or just 
```
sudo lshw ¦ grep cpu -A 10
```
This should show you the width of the cpu (32 or 64 bit)

However if the computer does reset it rules out a graphics problem

---

### Post by tree56uk on 2009-07-02
Okay, I did the Ctrl+Alt+F1, it caused my screen to go absolutly haywire. No idea what happened there.  I am going to try to force Vesa, but I have no idea where and when I edit the boot line entry :/

---

### Post by tarps87 on 2009-07-02
When you select which OS to boot you should be able to press e with Ubuntu highlighted. You many need to press escape before this, I am not using wubi so I can not say exactly how to do it.

When you say it when haywire did it reboot, I have a feeling this is not graphic related, it could just be a bad install. Have you tried installing the 32 bit or reinstalling the 64 bit version? If you have a spare cd it may be work burning a live cd and giving that a go, it may be a wubi issue. Unfortunately without a way to boot it we can't read any of the logs

---

### Post by tree56uk on 2009-07-02
> **tarps87 said:**
> When you select which OS to boot you should be able to press e with Ubuntu highlighted. You many need to press escape before this, I am not using wubi so I can not say exactly how to do it.

When you say it when haywire did it reboot, I have a feeling this is not graphic related, it could just be a bad install. Have you tried installing the 32 bit or reinstalling the 64 bit version? If you have a spare cd it may be work burning a live cd and giving that a go, it may be a wubi issue. Unfortunately without a way to boot it we can't read any of the logs

 When it went haywire about 95% of the screen flashed black and grey constanly, and about 5% of the screen at the top was flooded with code zooming at a rapid rate. I am downloading an ISO of a Live CD and ill try that. In the meantime, ill try the e thing now.

EDIT: the boot line edit didnt work, waiting for the live cd now.

---

### Post by tree56uk on 2009-07-03
Figured out the problem

My laptop is a Samsung R510, and there is a problem with the fact it has 4GB. So ive had to boot it with the - mem=3GB suffix to boot properly. That took some time to figure out! Using Jaunty now as I type this! Having a blast!

Thanks for the help guys!

---

### Post by frunns on 2009-07-03
Glad it worked out! :)

---

### Post by tarps87 on 2009-07-03
> **tree56uk said:**
> Figured out the problem

My laptop is a Samsung R510, and there is a problem with the fact it has 4GB. So ive had to boot it with the - mem=3GB suffix to boot properly. That took some time to figure out! Using Jaunty now as I type this! Having a blast!

Thanks for the help guys!

I've never heard of that, usually it just doesn't use all of the ram with the 32 bit version and it should work with the 64 bit. I guess this could be a wubi problem. Anyway I'm glad you managed to solve it (while I was busy sleeping :))

---

