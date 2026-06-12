---
title: "No wifi after kernel update"
date: 2006-09-04
forum: Networking &amp; Wireless
---

### Post by djRobbieF on 2006-09-04
I updated my kernel to the optimized 686-smp kernel, and of course that resulted in my wifi card no longer being set up, as it is in the default 386 kernel for Ubuntu.

Can anyone please help me to install the wifi drivers into my kernel (I do not know what ones)?  I can obviously still boot into 386, so if there's a way in there to tell which drivers are being used, just let me know.

Essentially, wifi works perfectly in the default 386, but after updating my kernel, it no longer works.

Thanks in advance for your help!  I really want to get this to work (with the optimized kernel) as it will be a pretty large deciding factor (that and getting my nVidia card to work properly) in whether or not I switch to Ubuntu.

Cheers!

---

### Post by jISh on 2006-09-04
Are you using ndiswrapper? I haven't tested this out as I'm not going to bother till I update to stable Edgy, but I've heard the latest versions of ndiswrapper fix the kernel problems.

---

### Post by djRobbieF on 2006-09-04
I haven't installed *anything* into the new kernel, because I wasn't sure; but yeah I'd guess ndiswrapper would be a good starting point too.  I've never optimized my running kernel before, so although I've heard of ndiswrapper, I've never had need to install it (it comes with most major distros, I guess - cause my wireless always works).

I'll have to hard-wire an ethernet cable or something and try to apt-get it, because I suppose I'd have to do it within the 686 kernel, so it gets built properly.  Thanks for the tip - I'll try it in the morning (time for bed).

Cheers - and thanks!

---

### Post by djRobbieF on 2006-09-04
Will it be simply sudo apt-get install ndiswrapper and then that's it, my wireless should work?  Or is there more to it than that?

Thanks!!

---

### Post by cylon359 on 2006-09-05
You installed the new kernel, but if your wifi card driver is in the restricted modules package, it might not have gotten installed.  I think you can just "sudo apt-get install restricted-modules-686", but I'm not totally sure if that's what it's called.

---

### Post by djRobbieF on 2006-09-05
I get "linux-restricted-modules-686 is already the newest version".  Of course, this installed when I installed linux-686-smp...

Any other suggestions?

---

### Post by djRobbieF on 2006-09-05
sudo modprobe ndiswrapper   seems to have worked for me.  Thanks for your help!!

---

### Post by djRobbieF on 2006-09-05
CORRECTION - that did NOT fix the problem (my mistake; I forgot that I had connected Ethernet, and so was excited when after running the command I had Internet... just a dumb oversight)  :)

Please continue with the flood of advice  LOL

---

### Post by djRobbieF on 2006-09-05
My wirelss adapter is a TRENDnet TEW-423PI

---

### Post by djRobbieF on 2006-09-05
Another note:  I ran iwconfig from both the 386 (working wireless) and 686 (not-working) and the nickname on both is "acx v0.3.21" - so I am guessing I'm actually using the ACX driver?  But I really don't know where to go from here to get my wireless working.

Any help is appreciated!!

---

### Post by djRobbieF on 2006-09-05
Anyone?  PLEASE?  I'm just sitting here (the past few hours) hoping someone can help.  I've been googling and looking through the forums but still no luck.

---

### Post by djRobbieF on 2006-09-05
Well, I finally figured it out and wanted to post here, just in case anyone in the future has the same problem.

The issue is, the newer kernel defaults a newer firmware for ACX, which does not support my card.

Here's the fix:

Look at /lib/firmware/$(uname -r)/acx/readme.txt to see the available acx firmware versions.

Find the firmware that works for you by simply testing using the below method.  Start with the highest version and work your way down until you have a Wireless connection.

This is the one that worked:

```
sudo rmmod acx

cd /lib/firmware/$(uname -r)/acx/default

sudo cp ../1.7.0/* .

sudo modprobe acx
```

Note:  the 1.7.0 represents the VERSION of the firmware you want to use.  Replace the number each time with the next number from readme.txt - and once you've found one that gets you connected, just LEAVE IT, and you're fixed forever  ;)

Hope this helps someone.  I spent the past nearly 24 hours working this out... lame eh?  One day I'll be faster  LOL

---

