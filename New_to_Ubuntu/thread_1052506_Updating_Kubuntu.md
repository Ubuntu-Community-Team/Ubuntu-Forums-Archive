---
title: "Updating Kubuntu"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by freeztar on 2009-01-27
I installed Kubuntu about a year ago and am just finally getting around to digging into it. I have the gibbon release and notice that there have been a few updates since then. I have read the free ubuntu pocket guide's suggestions for how to update via command line, but I'm not able to get online yet (it doesn't recognize my wireless card). From what I've read, version 8.10 has much better support for hardware and I'm hoping that updating will fix the wireless problem.

How do I do a manual update? Do I just burn a new disc and boot from it?

Also, several people have warned against using the default account while screwing around with things. How do I create a user account in Kubuntu?

Thanks in advance!

---

### Post by Svensk023 on 2009-01-27
The best way for a fresh and clean upgrade is to download the updated iso and burn it to a disc.

By default it should let you make a user account so you wont have the potential of damaging your system as easily when your signed in as root.

---

### Post by freeztar on 2009-01-27
Wow, that was quick, thanks!

I'll give it a try and report back if I have any problems.

---

### Post by Svensk023 on 2009-01-27
Please do tell me how it goes!

Good luck

---

### Post by freeztar on 2009-01-31
Well, I downloaded the 8.10 iso and used wubi to install it. After booting, it takes me to the login and after I hit enter all it shows is the desktop background and my arrow mouse cursor (which I can move around. No HD activity and it just sits there doing nothing (no further loading). Any ideas?

---

### Post by Svensk023 on 2009-01-31
I have only used wubi twice, and both times I have gotten a similar problem. So you can either check the wubi forums for further help, or take the plunge and partition your HDD.

-Good Luck

---

### Post by freeztar on 2009-02-01
> **Svensk023 said:**
> I have only used wubi twice, and both times I have gotten a similar problem. So you can either check the wubi forums for further help, or take the plunge and partition your HDD.

-Good Luck

Yeah, I think I'm just going to install it the old fashioned way. I already have made a partition of ext3 back when I installed Kubuntu 7.10. I actually tried installing Ubuntu 8.10 onto this partition as "\". It then said I needed a swap partition. This confused me a bit as I don't see an option in the Ubuntu installer to make a "\swap", just several other options like "\root". After doing some research, it appears that gparted can set up a swap partition so I'm going to try that and just install Kubuntu over the old installation. Wish me luck! :)

It's a shame wubi doesn't work as it would be a lot easier to convince win users to try ubuntu. :(

---

### Post by abn91c on 2009-02-01
> **freeztar said:**
> Well, I downloaded the 8.10 iso and used wubi to install it. After booting, it takes me to the login and after I hit enter all it shows is the desktop background and my arrow mouse cursor (which I can move around. No HD activity and it just sits there doing nothing (no further loading). Any ideas?
this is compiz related, usually removing it will get you to the desktop

---

### Post by freeztar on 2009-02-02
> **freeztar said:**
> it appears that gparted can set up a swap partition so I'm going to try that and just install Kubuntu over the old installation. Wish me luck! :)

No luck. :(
I currently have the following partitions: XP, Vista, Data, and kubuntu 7.10 on ext3. I was unable to make another partition for a swap. If I delete my current kubuntu partition, will I be able to create an extended partition that will hold both the root and the swap? Will this mess up grub?

---

### Post by freeztar on 2009-02-02
> **abn91c said:**
> this is compiz related, usually removing it will get you to the desktop

How do I do this? Recovery console?

---

### Post by abn91c on 2009-02-02
> **freeztar said:**
> How do I do this? Recovery console?
Yes do ```
sudo apt-get remove compiz
sudo apt-get remove compiz-core
sudo reboot
```

---

### Post by tarps87 on 2009-02-02
> **freeztar said:**
> Yeah, I think I'm just going to install it the old fashioned way. I already have made a partition of ext3 back when I installed Kubuntu 7.10. I actually tried installing Ubuntu 8.10 onto this partition as "\". It then said I needed a swap partition. This confused me a bit as I don't see an option in the Ubuntu installer to make a "\swap", just several other options like "\root". After doing some research, it appears that gparted can set up a swap partition so I'm going to try that and just install Kubuntu over the old installation. Wish me luck! :)

Before you do anything I think you need to understand what the swap partition is, it is not a way to transfer your data and should not be mounted as /swap. the swap partition is used for memory management, in particular paging. It should be formatted as the type swap (not ext3) and should not any mounted anywhere.
The recommended size for you swap partition is twice the size of your ram. This will allow for hibernating

More information on paging can be found here:
[http://en.wikipedia.org/wiki/Paging](http://en.wikipedia.org/wiki/Paging)

Hope this helps

---

### Post by freeztar on 2009-03-25
Thanks, that does help. I guess that's why my new install of Ubu will not hibernate properly. I set the swap as 2GB and I have 2GB of RAM...

---

