---
title: "Ubuntu not booting?"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by Jonypoo on 2010-08-27
Im kinda new to Ubuntu/Linux kinda thing so plz put like detailed instructions :) that would be very much appreciated.
I installed ubuntu yesterday and it works perfectly fine, it was freakin awesome actually :D
but i went to the hardware drivers button thing? n downloaded a driver for my ATi graphics card. I activated it and it said i needed a restart so i did. 
The same menu popped up, i clicked the first one then the purple screen with ubuntu with 5 circles came up n then black screen, and it just freezes there. any suggestions? i installed this using wubi so things might be different?
My com is 64-bit

---

### Post by Daniel0108 on 2010-08-27
Hi!
Try a Live CD or a Live USB Ubuntu...
Burn a Ubuntu Live CD on a DVD or a CD or a USB-device..
Thats the REAL Ubuntu :D
Wubi is just like a virtual os :)
Yours,
Daniel

---

### Post by WhatAreHackers on 2010-08-27
> **Jonypoo said:**
> Im kinda new to Ubuntu/Linux kinda thing so plz put like detailed instructions :) that would be very much appreciated.
I installed ubuntu yesterday and it works perfectly fine, it was freakin awesome actually :D
but i went to the hardware drivers button thing? n downloaded a driver for my ATi graphics card. I activated it and it said i needed a restart so i did. 
The same menu popped up, i clicked the first one then the purple screen with ubuntu with 5 circles came up n then black screen, and it just freezes there. any suggestions? i installed this using wubi so things might be different?
My com is 64-bit

 just a guess but you PROBABLY didn't install grub-pc after the installation??  i'm not sure if this will help Edit: lol... now that would be adding more detail... gratz lol...

---

### Post by bcbc on 2010-08-27
Your problem likely has everything to do with the graphics driver - and nothing to do with wubi (which incidentally isn't a virtual OS, but a real OS running off a virtual disk).

Also, installing grub-pc won't help - it's already there, and if you install the bootloader part, then nothing will boot (since wubi installs require the windows bootloader).

So what you need is someone to help you undo the driver install - I don't know how to do this. But I googled how to remove the ati driver - something to try... 

So when you boot, select the recovery option, and then select to drop to a root shell. Then run:
```
apt-get remove --purge xorg-driver-fglrx
```
After that, enter 'exit' to get back to the menu, or to restart:
```
shutdown -r now
```
Here;s a link for reference [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by QIII on 2010-08-27
When you say you "activated" it, did you go to the terminal immediately (before you shut down) and issue the command

```
sudo aticonfig --initial -f
```

?

---

### Post by Jonypoo on 2010-08-27
> **bcbc said:**
> Your problem likely has everything to do with the graphics driver - and nothing to do with wubi (which incidentally isn't a virtual OS, but a real OS running off a virtual disk).

Also, installing grub-pc won't help - it's already there, and if you install the bootloader part, then nothing will boot (since wubi installs require the windows bootloader).

So what you need is someone to help you undo the driver install - I don't know how to do this. But I googled how to remove the ati driver - something to try... 

So when you boot, select the recovery option, and then select to drop to a root shell. Then run:
```
apt-get remove --purge xorg-driver-fglrx
```
After that, enter 'exit' to get back to the menu, or to restart:
```
shutdown -r now
```
Here;s a link for reference [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

So when I clicked the Ubuntu, with Linux 2.6.32-24-generic (recovery mode) it just gives me a whole bunch of codes n then when it says done it tries to boot...
Am I supposed to press c to go into the command line or something?:o

---

### Post by bcbc on 2010-08-27
> **Jonypoo said:**
> So when I clicked the Ubuntu, with Linux 2.6.32-24-generic (recovery mode) it just gives me a whole bunch of codes n then when it says done it tries to boot...
Am I supposed to press c to go into the command line or something?:o

You should get a menu with a few options, one of them being a root shell. 

You know I've seen a few posts from people not being able to boot the latest -24 kernel. I'm wondering if this is the same problem. Try booting a -23 kernel instead - first normal, then if that fails, recovery.

---

### Post by WhatAreHackers on 2010-08-27
> **Jonypoo said:**
> Im kinda new to Ubuntu/Linux kinda thing so plz put like detailed instructions :) that would be very much appreciated.
I installed ubuntu yesterday and it works perfectly fine, it was freakin awesome actually :D
but i went to the hardware drivers button thing? n downloaded a driver for my ATi graphics card. I activated it and it said i needed a restart so i did. 
The same menu popped up, i clicked the first one then the purple screen with ubuntu with 5 circles came up n then black screen, and it just freezes there. any suggestions? i installed this using wubi so things might be different?
My com is 64-bit

 lol, i guess i should've read the terminal carefully, or somewhat at least, there goes 5 minutes of my life down the drain -.- , o well, live and learn

---

### Post by Jonypoo on 2010-08-27
> **bcbc said:**
> You should get a menu with a few options, one of them being a root shell. 

You know I've seen a few posts from people not being able to boot the latest -24 kernel. I'm wondering if this is the same problem. Try booting a -23 kernel instead - first normal, then if that fails, recovery.
I don't see anything with root shell....
I see ubuntu, ubuntu recovery mode, memory test, memory test serial console 115200, winodws 7 and vista. 
How do I change the kernel....?

---

### Post by Jonypoo on 2010-08-28
> **QIII said:**
> When you say you "activated" it, did you go to the terminal immediately (before you shut down) and issue the command

```
sudo aticonfig --initial -f
```

?

oh. did u have to haha. i thought it was activated by the menu alr haha. ah well. i'll do that when i get it to boot :)

---

### Post by bcbc on 2010-08-28
> **Jonypoo said:**
> I don't see anything with root shell....
I see ubuntu, ubuntu recovery mode, memory test, memory test serial console 115200, winodws 7 and vista. 
How do I change the kernel....?

I suppose if you installed ubuntu 10.04.1 you only have one kernel. So your only option is the recovery mode. If that's not working then I'm not sure what other choice you have.

If you installed yesterday, just reinstall. If you have data you need to recover, you need to do this before reinstalling or it'll be gone.

---

### Post by Jonypoo on 2010-08-28
> **bcbc said:**
> I suppose if you installed ubuntu 10.04.1 you only have one kernel. So your only option is the recovery mode. If that's not working then I'm not sure what other choice you have.

If you installed yesterday, just reinstall. If you have data you need to recover, you need to do this before reinstalling or it'll be gone.

Ah so is there a reinstall  option when i put it the cD? Or do i have  to uninstall (how?) Then install again?

---

### Post by Jonypoo on 2010-08-28
> **QIII said:**
> When you say you "activated" it, did you go to the terminal immediately (before you shut down) and issue the command

```
sudo aticonfig --initial -f
```

?

ok so i reinstalled it and typed in that code after i updated the driver in terminal, restarted n still didn't work :( pls help

---

### Post by WhatAreHackers on 2010-08-28
> **Jonypoo said:**
> ok so i reinstalled it and typed in that code after i updated the driver in terminal, restarted n still didn't work :( pls help

 Well, i'm not that knowledgable about Ubuntu 10.04, but... did you receieve any errors when you reinstalled?? for instance in the brackets, (The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again.) ?? if not, then i can't do much for you... i use 32bit, you use 64 bit, big difference =( but i also use ati also so yeah.....

---

### Post by bcbc on 2010-08-28
What type of ATI graphics card do you have?

---

### Post by WhatAreHackers on 2010-08-28
> **bcbc said:**
> What type of ATI graphics card do you have?

 who me or op? I don't want to be conceited and assume that it is me but, if it is me then... i have ati 4800 series video card

---

### Post by Jonypoo on 2010-08-29
> **bcbc said:**
> What type of ATI graphics card do you have?

ATi Mobility Radeon 5650

> **WhatAreHackers said:**
> Well, i'm not that knowledgable about  Ubuntu 10.04, but... did you receieve any errors when you reinstalled??  for instance in the brackets, (The installer encountered an  unrecoverable error. A desktop session will now be run so that you may  investigate the problem or try installing again.) ?? if not, then i  can't do much for you... i use 32bit, you use 64 bit, big difference =(  but i also use ati also so yeah.....

haha there was no error... it just asked me to restart my computer.

---

### Post by WhatAreHackers on 2010-08-29
> **Jonypoo said:**
> ATi Mobility Radeon 5650



haha there was no error... it just asked me to restart my computer.

 i mean during your reformating, were there any errors during set up?

---

### Post by bcbc on 2010-08-29
> **Jonypoo said:**
> ATi Mobility Radeon 5650



haha there was no error... it just asked me to restart my computer.

[http://ubuntuforums.org/showpost.php?p=9666366&postcount=30](http://ubuntuforums.org/showpost.php?p=9666366&postcount=30)
That post is for someone with the same issue who found a way to get it booting again. It appears the latest ati drivers don't work very well for this card. There is no solution (the thread is marked solved, but it's an old thread) - but a workaround to uninstall the driver is a start.

---

### Post by Jonypoo on 2010-08-30
> **WhatAreHackers said:**
> i mean during your reformating, were there any errors during set up?

nope none at all, haha ah well, i just wont install the drivers its fine :)

---

### Post by WhatAreHackers on 2010-08-30
> **Jonypoo said:**
> nope none at all, haha ah well, i just wont install the drivers its fine :)

k thats good

---

