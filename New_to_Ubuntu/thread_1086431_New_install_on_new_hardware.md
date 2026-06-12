---
title: "New install on new hardware"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by dimitriv on 2009-03-04
hi

I've just installed Intrepid on a brand new box which has an Asus M2N68-AM motherboard. The guy at the shop told me to download the latest drivers (&bios?) from Asus but I can't find anything for linux.

1. Do I need to upgrade any drivers/bios and if so how?

2. How do I increase the screen resolution from 800x600 (it only offers 800x600 or 640x480)?

3. Ubuntu says the machine has 2.8gb RAM. It actually has 2x2gb=4gb. Any comments?

Minor issues, it's all looking good...

Thanks

---

### Post by SunnyRabbiera on 2009-03-04
You should not need any drivers.
Your video issue is going to be a bit hard to fix but can you tell us your processor and what version of Ubuntu you installed.

---

### Post by dimitriv on 2009-03-04
Hi

It's a AMD Athlonx2 64bit dualcore 5000+ AM2 2.6GHz 1MB L2 Cache
Ubuntu 8.10

Thanks

---

### Post by Temposs on 2009-03-04
dimitriv,

Your RAM issue indicates that you did not install the 64-bit version of Ubuntu 8.10. If you want to utilize all your RAM, you'll need to reinstall with the 64-bit version.

For the video problem, we'll need to know the specific video card your box has, probably.

---

### Post by dimitriv on 2009-03-04
Thanks for your comments. The Asus M2N68-AM has onboard video (no external card).

---

### Post by Cresho on 2009-03-04
get an nvidia 8800gt to start.  it is way cheap.  onboard video, if it is nvidia, should be installed by

administration->hardware drivers-> choose nvidia.

that is if you have an onboard gpu.  also, dont use ati graphics since they are barely mature enough.  one last thing..install the 64bit os if you want 4gb ram support.

---

### Post by dimitriv on 2009-03-04
thanks. it has an Integrated Geforce®7 Series graphics. does that help at all?

---

### Post by dimitriv on 2009-03-04
[I]Re: onboard video, if it is nvidia, should be installed by

administration->hardware drivers-> choose nvidia.[/I]


If I go to administration->hardware drivers-> the next screen tells me No Proprietary Drivers are in use on this system and then gives me the option to activate 2 drivers
i. NVIDIA Accelerated Graphics Driver (version 173) and
ii. NVIDIA Accelerated Graphics Driver (version 177) Recommended

If I click Acitvate for either driver it asks for root password then appears to do nothing. Nothing changes. Presumably my Integrated Geforce®7 Series graphics is non NVIDIA???

Thanks

---

### Post by marco123 on 2009-03-04
If you have a slow internet connection, i.e. less than 5Mb/s it might sit there on 0% for a while, then it should install once it's downloaded.

Cheers, Marco

Edit: After they are installed you need to log out and back in again for them to be activated fully.

---

### Post by dimitriv on 2009-03-04
> **marco123 said:**
> If you have a slow internet connection, i.e. less than 5Mb/s it might sit there on 0% for a while, then it should install once it's downloaded.

Cheers, Marco

Edit: After they are installed you need to log out and back in again for them to be activated fully.

as an indication I downloaded the 64bit .iso and averaged around 100KB/sec up to 200KB/sec spikes
The downloading and installing driver screen pops up for a half a second showing 0% then dissapears. the download does not appear to run. thanks

---

