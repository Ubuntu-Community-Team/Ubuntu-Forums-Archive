---
title: "Using Ubuntu Help Centre - Report a Problem"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Scunnered on 2009-04-30
I attempted to report a problem that I have been having but found that when I selected "**Report a Problem**" from the drop down menu that no form was made available to detail my experience.

I have attempted when using both the beta and final Jaunty to seek a resolution to my problem via the forum but so far no assistance is forthcoming.  

Basically what worked perfect in 8.10 does not work in 9.04 namely screen resolution. In 8.10 on a wide screen laptop all the screen is fully taken up with the basic desktop details yet when I downloaded the final 9.04 and did a clean install on a separate partition there is approx 1 inch of blank space to the left and right of the desktop details. It is like having a picture print in portrait when it should be landscape.

Please advise how this problem can be resolved as it is a pain in the nether region. I am not the only one who is having this problem. One responder to my post has reverted to 8.10 as he has given up on expecting a resolution to the problem.

How can I have what should be a simple matter rectified.

---

### Post by nandemonai on 2009-04-30
> **Scunnered said:**
> I attempted to report a problem that I have been having but found that when I selected "**Report a Problem**" from the drop down menu that no form was made available to detail my experience.

I have attempted when using both the beta and final Jaunty to seek a resolution to my problem via the forum but so far no assistance is forthcoming.  

Basically what worked perfect in 8.10 does not work in 9.04 namely screen resolution. In 8.10 on a wide screen laptop all the screen is fully taken up with the basic desktop details yet when I downloaded the final 9.04 and did a clean install on a separate partition there is approx 1 inch of blank space to the left and right of the desktop details. It is like having a picture print in portrait when it should be landscape.

Please advise how this problem can be resolved as it is a pain in the nether region. I am not the only one who is having this problem. One responder to my post has reverted to 8.10 as he has given up on expecting a resolution to the problem.

How can I have what should be a simple matter rectified.

I notice in your sig you're using Intel graphics, might want to scour the zillions on Intel threads as there are a heap of issues with Intel graphics this release.

---

### Post by Scunnered on 2009-04-30
**nandemonai**

Thanks for your prompt reply.  Your comment of "*might want to scour the zillions on Intel threads as there are a heap of issues with Intel graphics this release*." is really uninspiring.

My Ubuntu level experience would more than likely have me more confused than I am currently.  What ever happened to **KISS and if it ain't broke dont fix it** ?

I will patiently await a resolution to this problem as I am confident that I will not be the only one with Intel graphics.  I was under the impression that Intel had seen the light and were working with Linux.

Thanks again

---

### Post by nandemonai on 2009-04-30
> **Scunnered said:**
> **nandemonai**

Thanks for your prompt reply.  Your comment of "*might want to scour the zillions on Intel threads as there are a heap of issues with Intel graphics this release*." is really uninspiring.

My Ubuntu level experience would more than likely have me more confused than I am currently am.  What ever happened to **KISS and if it ain't broke dont fix it** ?

I will patiently await a resolution to this problem as I am confident that I will not be the only one with Intel graphics.  I was under the impression that Intel had seen the light and were working with Linux.

Thanks again

More of an observation than anything and I whole heartedly agree. I think the issue with the Intel drivers this release was major changes that didn't make it into the development freeze hence a bunch of cards  were blacklisted.

I do suggest checking out some of the Intel threads though as a bunch of people seem to have had success by reverting to the old drivers from what I've read.

Can't help with that myself though as I haven't been put in that situation luckily.

---

### Post by Scunnered on 2009-04-30
**nandemonai**

I had a look in the upgrading section and found so much information that as forecast I am even more confused than ever.  It looks that patience is the order of the day and that by 9.10 they will have resolved all the outstanding matters.

My observation of the Intel Graphics posts is that I will never again need to buy Epson Salts.

Fortunately I can attach my 19 Inch screen to the laptop and this strangely enough works OK. It will only be when I am on my travels that it will be a pain.

Once again thanks vm

---

### Post by gn2 on 2009-04-30
A simple fix could be to use the vesa driver instead of the Intel one?

---

### Post by Scunnered on 2009-04-30
**gn2**

I am still getting to grips with Ubuntu and don't want to add anything that I am unsure off. I had a look for the driver using hardware drivers but was only offered one for a wifi. 

If you can guide me to the driver I will give it a try always assuming that I can remove it if it does not do the trick.

I still have 8.10 loaded and find that with the exception of the wireless connection things are much better there.  I think that I will flit back and forth depending on what I am doing to get the best of both worlds.  I like using OOo3 and there are other odds and ends that dont depend on graphics so that might just do for now if all else fails.

Many thanks for your suggestion

---

### Post by gn2 on 2009-04-30
On the Grub screen's 9.04 entry press e to edit and add xforcevesa to the end of the instructions.

Another way to do it is to add xforcevesa to the end of the entry in your /boot/grub/menu.lst

To open it for editing, press Alt+F2 then type (or copy and paste): gksudo gedit /boot/grub/menu.lst

For example:
```
title Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.28-11-generic root=/dev/md0 ro quiet splash xforcevesa
initrd /boot/initrd.img-2.6.28-11-generic

```

Make a back-up copy of menu.lst before you edit it ;)

---

### Post by Scunnered on 2009-04-30
**gn2**

Thanks vm for your follow up.  I have been wrestling away with it without too much luck.

If I have followed you correctly I added the xforcevesa following ## End Default Options ## saving the change and rebooting.  There was no change in the display.

What I found did not exactly follow your example.  I found this 

"## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic

uuid		1a0ddd95-8bc2-483c-ab71-c62eeeca65fc

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1a0ddd95-8bc2-483c-ab71-c62eeeca65fc ro quiet splash **xforcevesa**
initrd		/boot/initrd.img-2.6.28-11-generic

quiet


title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)

uuid		1a0ddd95-8bc2-483c-ab71-c62eeeca65fc

kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=1a0ddd95-8bc2-483c-ab71-c62eeeca65fc ro  single

initrd		/boot/initrd.img-2.6.28-11-generic

I highlighted the insertion for ease.

If I got it right then it did not work.  If I got it wrong slap me about a bit and see if you can get it into my thick head.

Again my thanks for your kind assistance

---

### Post by gn2 on 2009-04-30
Looks like you got it right.
That should force use of the vesa driver.

Something else to try is to search Synaptic for "Intel" and mark the Intel graphics drivers for complete removal.

---

### Post by Scunnered on 2009-04-30
**gn2**

You now have me between the devil and the deep blue sea.  The only thing that I found that looked if it met your criteria was "xserver-xorg-video-intel.  I took this on blind faith and removed it and rebooted.

In the first instance an error message displayed advising that I was in low graphics and gave me a few options. Obviously I selected the wrong one initially and had to reboot a couple of times.  In the end I opted to accept the default graphics option and this worked.  All the desktop information fully populated the screen.

That was the good news.  The bad news was that when I attempted to link my 19 inch monitor to the laptop I was informed that there was no video input and to have that to work I had to reinstal the graphic driver.

As I said earlier I think that I will flit back and forth but at lease when I take the laptop away from home I will have it set properly.

My sincere thanks for all your kind assistance with this problem.

---

