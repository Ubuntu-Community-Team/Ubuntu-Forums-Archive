---
title: "Ubuntu 9.10 Live cd boot issue"
date: 2010-09-28
forum: New to Ubuntu
---

### Post by DSimm626 on 2010-09-28
I am trying to use a Ubuntu 9.10 Live cd and I can choose a language and then the next screen gives me all the options. I want to run off the Live cd. After 3 minutes I faintly hear the ubuntu sound but the screen remains black and eventually the system just stalls.

My specs:
ACER Aspire
Intel Pentium P6000 1.86 GHz
Intel HD Graphics
17.3 HD= LED LCD
3 GB Memory
250 GB SATA HD

I apologize if this is mentioned somewhere but I didn't find it in a search.

Thanks, David

---

### Post by lswartz on 2010-09-28
Fix a cup of coffee, it takes a while from the cd.

---

### Post by DSimm626 on 2010-09-28
Ok, I'll go eat dinner:)

---

### Post by DSimm626 on 2010-09-28
20 minutes and the laptop is just sitting there with a black screen. No HD or DVD-ROM movement(noise).

Any other ideas?

---

### Post by garvinrick4 on 2010-09-28
If you have a Cd download new iso file of Ubuntu and BURN it to a disk. Takes maybe 20 minutes. Burn at slowest speed possible.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by ankspo71 on 2010-09-28
Hi,
When you get to the boot options, press F6 and choose "acpi=off" or "noapic". You might need to hold down the right shift key as the ubuntu live cd boots in order to access these boot options first, or press the escape key like it says in the following link:
Here is more information on the boot menus for the live CD: 
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
Hope this helps.

---

### Post by DSimm626 on 2010-09-30
Nothing listed here is working. I tried just to install Ubuntu 9.10(instead of running off the Live cd) and the same thing happens. 

It lets me choose a language and the options screen comes up. So I click on install(or run off Live cd) and it runs for about 2 minutes with a black screen and then the HD and DVD-ROM drive stops spinning. Its been sitting for 10 minutes now.

I have Ubuntu 10.04 on Live cd so I will try it now and see what happens.

Any ideas? 
Maybe its just my new laptop Ubuntu doesn't like:(

---

### Post by ankspo71 on 2010-09-30
Hi,
It might be only an issue with running the live cd on that computer. Are you able to use the "Check this disc for defects" option when the live cd tries to boot? The downloads could have been good, but the burn could have ended up being bad. Here's a video that shows where to find that menu option in Ubuntu 10.04 [http://zootlinux.blogspot.com/2010/05/check-disc-for-defects-in-ubuntu-1004.html](http://zootlinux.blogspot.com/2010/05/check-disc-for-defects-in-ubuntu-1004.html) That page says you can use the space bar to get to that menu. I think the right shift key will work too.

Some computers don't like the graphical environment on the live cds, which is why Ubuntu makes an alternate cd too. Have you already tried installing from the alternate cds? The alternate cd doesn't have the graphical environment to install Ubuntu from though. It is a text based installer. Actually it doesn't have an option to run from a live environment either, so you aren't able to give Ubuntu a nice trial run first. 

Speaking of trial runs...
If you feel the need to do this, you can test another distribution's live cd to see if it will boot or not, and to check how well your hardware gets along with Linux... just for testing purposes before installing Ubuntu I mean. I find PClinuxOS to be good at automatically recognizing hardware (at least my hardware) and installing non-free drivers automatically during the live cd boot up process, which might be helpful in this situation.

---

### Post by DSimm626 on 2010-10-01
I brought my laptop to work today to let my Linux guru look at it. He can't figure it out. He did look through my BIOS and didn't see anything glaringly out of place.

He had a PClinuxOS live cd and that worked. Also tried his Ubuntu 9.04 and that worked. So I installed his Ubuntu 9.04 and it is working. I have a weak wireless signal here at work but got it to update once(47 files I think). 

So I tried to use my Ubuntu 9.10 live cd and the same thing happens, black screen. 

When I get home I will make a new live cd per garvinrick4's suggestion and try that.

---

### Post by DSimm626 on 2010-10-02
This problem is sorta resolved.

With the Ubuntu 9.04 loaded on my laptop, I just used the 'Update Manager' to install Ubuntu 9.10. It took a couple of hours to do but 9.10 is on my laptop!!! 

From here, I can update to Ubuntu 10.04.1 LTS if I so choose.

Although I still can not boot from a Live cd I did find a suitable work-around.

Thank you to everyone here for all their help. I'm sure I will be back soon with another problem as I continue to explore and learn Ubuntu and Linux itself.

David

---

### Post by lswartz on 2010-10-04
Nice job with lots of persistence & glad you got it working. I think ankspo71 was correct that you got a bad download or you computer didn't like a graphical install. I have 3 disks of 10.04 before I discovered that graphical issue on my own computer.

You might mark this thread as solved.

---

