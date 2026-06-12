---
title: "upgradin to 9.04, partition question"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by unitedwefall on 2009-04-23
Hi

I've been using ubuntu desktop for a few months and i love it (although i'm still dual booting with vista, and want to stay that way). Now 9.04 is out i want to get rid of 8.10 and use that instead. I just want to format my 8.10 partition and start again but im not really sure how, on the partioioner i guess you choose the custom bit but im really crap and i have no idea how to do it.

Thanks

x

---

### Post by Law506 on 2009-04-23
Scratch what I wrote, didn't think that all the way through.

---

### Post by ubername on 2009-04-23
> **unitedwefall said:**
> Hi

I've been using ubuntu desktop for a few months and i love it (although i'm still dual booting with vista, and want to stay that way). Now 9.04 is out i want to get rid of 8.10 and use that instead. I just want to format my 8.10 partition and start again but im not really sure how, on the partioioner i guess you choose the custom bit but im really crap and i have no idea how to do it.

Thanks

x

You should be able to upgrade from your upgrade manager (system>administration>update manager). If you do not get a message at the top of the screen saying 9.04 is available, you may need to click the settings button and make sure that 'Release Upgrade' has 'normal releases selected.

---

### Post by unitedwefall on 2009-04-23
Well the "guided setup entire disk" option is trying to get me to format my whole hard disk, including vista so i recon that isn't right, thanks though!

I dont want to just upgrade though, i want to format that partition and just basically "start again" surely you can do that through the partition manager on the live cd?

---

### Post by Law506 on 2009-04-23
> **unitedwefall said:**
> Well the "guided setup entire disk" option is trying to get me to format my whole hard disk, including vista so i recon that isn't right, thanks though!

Yea, that is why I retracted my previous statement, was thinking of something totally different. My bad on that one.

---

### Post by unitedwefall on 2009-04-23
> **Law506 said:**
> Yea, that is why I retracted my previous statement, was thinking of something totally different. My bad on that one.

haha thats ok, thanks anyway!

Anyone else got any ideas? i know this is probably really easy but i'm crap. Also sorry for the spelling mistake in the title of this thread.

---

### Post by michy99 on 2009-04-23
I don't have the disk, as I am not upgrading at this time, but I believe there is an option to partition manually. You just need to choose the partition that your current Ubuntu is on and leave the rest alone.

It's a good idea to backup all your data first.

---

### Post by SuperSonic4 on 2009-04-23
You can pick to partition the disk manually. From there you should be able to identify your ubuntu installation and select to install / there. You can also use the manual to have partitions for /home and anything else you like

---

### Post by unitedwefall on 2009-04-23
cool, what filesystem type should i use?

---

### Post by Paqman on 2009-04-23
> **unitedwefall said:**
> cool, what filesystem type should i use?

The default is ext3. You've also got the option of using the newer version ext4, which should help you boot faster.

---

