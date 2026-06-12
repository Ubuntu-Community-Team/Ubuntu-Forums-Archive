---
title: "Wireless and Dell Inspiron 1501"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by exsencon on 2008-02-01
I am checking out the live CD/DVD distributions of Ubuntu/Kubuntu on my Dell laptop Inspiron 1501.
My problem is that the wireless radar button on my laptop is off as soon as I put the CD/DVD in. For me the only way to get it working is to install the BCM43xx driver with fwcutter. After I do that I can turn the radar button on with fn-f2 and with some tinkering I get a 24Mb/s connection and I can remove my ethernet cable.

When I try to do the install with ndiswrapper this does not work. I can install my windows driver (bcmwl5) without any problem (sort of) but the radar button stays off and pushing fn-f2 has no effect. So no wireless. I did a quite extensive search but could find no answer. Is this a known problem and is there a solution or do I have to stick with the native bcm43xx driver (ndiswrapper giving a better connection 54Mb/s vs 24Mb/s)?

I tried Knoppix and Mandriva before with ndiswrapper without any problems.Before I install anything I would like to know what to expect.
Thanks

---

### Post by jan quark on 2008-02-02
this does not help you but I have the same laptop as you have 
and I have exactly the same problems as you

I am now online, using the fwcutter
ndiswrapper did not worked for me, no guide could help me...

it works now so fingers crossed, you are not alone

---

### Post by exsencon on 2008-02-03
> **jan quark said:**
> this does not help you but I have the same laptop as you have 
and I have exactly the same problems as you

I am now online, using the fwcutter
ndiswrapper did not worked for me, no guide could help me...

it works now so fingers crossed, you are not alone

Well I found a solution on the linux org forum and it WORKS! (for me)
Before doing anything you should put in the terminal:

sudo modprobe -r bcm43xx

After that you start the ndiswrapper with 

sudo ndiswrapper -i (path of the driver) and just continue

It worked for me, I could turn on my wireless card and got a connection (54Mb/s)
Here is where I found it:

[http://www.linuxquestions.org/questions/slackware-14/my-wireless-card-is-unrecognized-bcm4306-596743/](http://www.linuxquestions.org/questions/slackware-14/my-wireless-card-is-unrecognized-bcm4306-596743/)

(bottom half of the page)
Hope it helps, it did for me

---

