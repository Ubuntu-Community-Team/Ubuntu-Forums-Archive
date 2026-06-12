---
title: "Swap files"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Dave W. on 2009-01-17
Hello folks,

I'm a Newbie with Xubuntu and all Linux.  I have an old system,  HP8755C,  800 MHz with 512MB of RAM, a GeForce graphics card FX 5500 128MB and a 40 GB HD.  Not a speed demon, but adequate for now.

Can I get this system to run better if I add a swap file?

I found this post [http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/](http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/)

If I open up the terminal and cut and paste those lines in,  will I be successful.  I'm alittle nervous about Gparted, unless I have some very specific instructions

I am new and a bit of a Hack so, please bear with me for now.  

Any other suggestions or ideas will be greatly appreciated. 
Thanks,
Dave

---

### Post by cariboo on 2009-01-17
I you used the automagic partitioning option when you installed, you already have a swap partition. Linux uses swap differently from Windows. Swap is only used when you run out of ram, so there is no benefit to creating a swap file.

Got to System-->Preferences-->Sessions and turn off any services you don't need, and the next time you restart they will not be started.

Jim

---

### Post by kestrel1 on 2009-01-17
If you just went for a standard install & let Xubuntu partition the drive you should already have a SWAP partition, so you shouldn't need to worry about it.

---

### Post by SanjoEel on 2009-01-17
Yes, a swap file will definitely help with your speed on that old box. It should be 1.5X your available RAM. There should be a resize option in gparted. If you use the empty space in your ext3 partition then you should not lose any data, since Linux does not fragment files like Windows does.
Still, make sure to back up your important files, just in case.

---

### Post by handydan918 on 2009-01-17
Before you run off half-cocked, just post the output of ```
sudo fdisk -l
```and we can see if you have a swap partition.

---

### Post by SanjoEel on 2009-01-17
Handy Dan that's a funny sig you got LOL

---

### Post by oldos2er on 2009-01-17
The Xubuntu installer should've created a swap partition for you. But if you're looking for speed, bump up your RAM to as much as your system can handle. Using swap slows everything down, since hard disk access is many many times slower than RAM access.

---

### Post by linux_tech on 2009-01-17
Also check in System>Admin>System monitor to see amt of swap in use.

Also ref :
[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

---

### Post by Dave W. on 2009-01-17
Thanks all for your quick replies, I let Xubuntu install completely on my drive.  Is there a way to see if there is a swap partition there? Or is this the answer?   The System Monitor shows Swap history of 4.5 MiB out of 1.4 GiB right now.  It that what I'm supposed to expect?  I really don't want to mess with it if I don't have to.  Since I'm new I'm not really sure what to do if I get conflicting replies.  I don't want to insult any of you kind people will to help me. I really appreciate your suggestions.

Thanks, 
Dave

---

### Post by Dave W. on 2009-01-17
I looked in the terminal, found out that I couldn't cut and paste, and it appears that I do have 3 partitions and one is labeled as swap.  

I think that I am good.  You folks are great.  Thank you for all your insights.  I guess that I have to accept the limitations of my system.  My RAM is at the max and I don't want to add money to this old box.  It is good for learning purposes.  

I've tried other distros and this variant seems to work the best. I have not froze up... yet.  I did disable the powernowd and it seems to work better.

Once again thanks,
Dave

---

### Post by oldos2er on 2009-01-17
"free -m" typed into a terminal will tell you if and how much swap is being used.

---

### Post by Dave W. on 2009-01-17
Thank you, I typed in free -m.  I'm not sure what it all means yet, but it looks like my system is max'd but holding fast.

Dave

---

### Post by albinootje on 2009-01-17
> **Dave W. said:**
> 
Can I get this system to run better if I add a swap file?


Glad to see that you've sorted it out now.

Your nice and old machine will be happy that swap is available in general, and you have enough swap already.
But swap, when used, is using the hard disk, and is much slower than RAM memory.
Just for your information.

---

### Post by Dave W. on 2009-01-17
Thanks albinootje,  I'm really learning so much today and you have all helped me so much!!

Dave

---

### Post by HyperHacker on 2010-01-18
I've noticed something similar; I have around 600MB of free RAM but it's still gradually using up swap space instead of that nice fast RAM. What's up with that? Swap is doubly slow for me since it has to pass through the disk encryption layer, so I'd rather not have it used unnecessarily.

---

### Post by oldos2er on 2010-01-18
You may need to tinker with vm.swappiness. See [https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

---

