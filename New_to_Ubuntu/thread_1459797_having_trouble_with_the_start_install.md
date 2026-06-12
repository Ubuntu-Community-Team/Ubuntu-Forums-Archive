---
title: "having trouble with the start install :/"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by freddymunoz on 2010-04-21
Hi guys,

I am a total newbie on installing Ubuntu. just to get into details I run hp pavilion dv644us windows 7 Ultimate and I download Ubuntu 9.10 just recently. I saw some multiple tutorials on how to install Ubuntu and it seem quite simple but I got some problems. So I downloaded the iso and burn it to a disc and I run the disc and I wanted to install Ubuntu from windows. It will start to drop the files but as soon it gets into I think 3 seconds it will say "Permission Denied" so I went and try to install as an administrator by right clicking on the drive according to some forum I read but it was only for windows vista but apparently it did not have that option right click and run as an administrator. then I try to install from the DVD/DC, it boots up, the language options work chose english and then when I wanted to go to the install option after pressing enter it will freeze and then when I hit any key a loud sound will come up so I hard reset try again and I waited for a while nothing came up and still at the same screen and hit a key and the loud beep will start as well. so right now I am downloading Ubuntu 9.10 again and see if it was badly burned on the CD or something

---

### Post by undecim on 2010-04-21
From the CD menu, there is an option to check the cd. Run that and see what you get.

---

### Post by Zintha on 2010-04-21
> **undecim said:**
> From the CD menu, there is an option to check the cd. Run that and see what you get.
This is the only thing -I- can think of (which means there are 40 other easier options usually) but it would be a good start.

Check this first before downloading again, especially if you have a slow Internet connection like some.

---

### Post by |Mitch| on 2010-04-21
Burn it at a slow speed and see if that fixes the problem, you might have a bad burn. 

I always burn mine at 1X speed, not required but makes sure I get a good burn

---

### Post by freddymunoz on 2010-04-21
> **undecim said:**
> From the CD menu, there is an option to check the cd. Run that and see what you get.
how do you get to the menu?

---

### Post by |Mitch| on 2010-04-21
When you boot off the CD you get the option of running from the CD, Installing, Checking disk for errors etc...

---

### Post by freddymunoz on 2010-04-21
> **|Mitch| said:**
> When you boot off the CD you get the option of running from the CD, Installing, Checking disk for errors etc...
oh lol ok I will do that

---

### Post by freddymunoz on 2010-04-22
I just check for problems but no luck same symptoms with the beep

---

### Post by ddecator on 2010-04-22
> **freddymunoz said:**
> I just did that but no luck same symptoms

What did you try exactly? The check disk option when booting from the CD, or reburning the CD?

You should run an md5sum on the .iso to make sure that it downloaded properly. Sometimes even one file will be corrupt and can cause this to happen. 

You can get information on how to run an md5sum here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by freddymunoz on 2010-04-22
> **ddecator said:**
> What did you try exactly? The check disk option when booting from the CD, or reburning the CD?

You should run an md5sum on the .iso to make sure that it downloaded properly. Sometimes even one file will be corrupt and can cause this to happen. 

You can get information on how to run an md5sum here: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 sorry for that check disk option when booting the CD

---

### Post by freddymunoz on 2010-04-22
ok on the new download it gave me 100%. I am already burning the iso a CD at a slow speed hope this works

---

### Post by freddymunoz on 2010-04-22
re-burning it solved the problem and I am using the operating system right now thank you very much guys :) by the way it detected bad sectors on the disc what should I do

---

### Post by undecim on 2010-04-23
> **freddymunoz said:**
> re-burning it solved the problem and I am using the operating system right now thank you very much guys :) by the way it detected bad sectors on the disc what should I do

I would make sure to keep a backup of any data on it, because that means the drive isn't 100% reliable.

Other than that, Ubuntu shouldn't use the bad sectors, so that's just a little disk space you can't use.

---

