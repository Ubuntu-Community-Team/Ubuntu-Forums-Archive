---
title: "Problem with detecting external harddrive"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Eruditio on 2009-06-02
I was experimenting with Ubuntu a few months ago and decided I didn't want to risk partitioning the harddrive I have Vista installed on, so attempted to install Ubuntu to an external USB harddrive. To cut a long story short, it failed. I wasn't able to boot Ubuntu from the harddrive or even Vista for that matter until I fixed GRUB. I fixed that but now whenever I plug my harddrive in, it's not detected by the computer (although the light on the harddrive lights up to indicate it's connected).

I'm running Ubuntu in a virtual machine atm and have Vista installed on my main harddrive. So if anybody knows how to fix this problem from either OS then please help! :)

---

### Post by utnubuuser on 2009-06-02
You're not giving much info.  Are you hitting F12 at boot to access the boot-options menu?
Is USB-boot enabled in your bios?

---

### Post by Eruditio on 2009-06-03
> **utnubuuser said:**
> You're not giving much info.  Are you hitting F12 at boot to access the boot-options menu?
Is USB-boot enabled in your bios?

I don't really understand why this applies. I don't want to boot from the external harddrive, I just want to fix it so that I can use it like normal again, before I tried (and failed) to install Ubuntu to it.

---

### Post by rob2uk on 2009-06-03
When you installed Ubuntu to the USB drive it will have been formatted as (most likely) ext3.

Vista can't read ext3 partitions, so that's why it doesn't show up in 'my computer'

You can follow [the instructions]("http://www.alohatechsupport.net/webdesignmaui/computer-tips-optimization/create_a_partition_with_window.html") to delete the ext3 partition and create a Windows readable one

---

### Post by Eruditio on 2009-08-14
Sorry - I realised I never replied! That worked perfectly, thank you so much for the help :)

---

