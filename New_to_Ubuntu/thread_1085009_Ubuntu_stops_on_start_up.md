---
title: "Ubuntu stops on start up"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by NikolaN on 2009-03-02
Hi everyone,

I've tried to install both Ubuntu (Twice) and Linux Mint on my laptop (Ubuntu is the one I want to get working), but I've come up against the same problem in both of them; When trying to boot from the live CD or install, the first loading screen with the status bar stops halfway and doesn't budge.

It doesn't even throw up any error code to give me an idea to search with, so as a last resort I'm looking for help here, and big apologies if this has been posted a million times before.

I'm guessing its something to do with my laptop and its components; its an Ei Systems 1201, the specs are as follows (I dont know whats applicable so I'm just putting it all in);

Intel Pentium Dual Core T2370 processor (1.73GHz),
Microsoft Windows Vista Home Premium installed,
The CPU has 1MB shared cache,
1 GB DDR2 RAM
120 GB hard drive (80 GB used)
Realtek sound

If theres anything I'm missing I'm sorry, I can try provide it. I know this is kind of a vauge problem but I'm really stumped at not even getting error messages. I've run the same CD in another computer with no problems, so I know its not the cd.

Thank you so much for any advice whatsoever.

---

### Post by 67GTA on 2009-03-02
Before you boot the CD, and at the CD menu, hit the F6 key to show the boot options. Then delete the "quiet splash" at the end. You will be able to see what is happening from the boot text. Also, have you tried booting in safe mode?

---

### Post by Crafty Kisses on 2009-03-02
You might want to check the md5sum on those disks. If they come back OK, then you might want to try doing a CLI install. If you still want to install Ubuntu you can check out the [Alternate CD]("https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD"). Read that then see if you can install it like that. Your specs are good enough to run Ubuntu though.

---

