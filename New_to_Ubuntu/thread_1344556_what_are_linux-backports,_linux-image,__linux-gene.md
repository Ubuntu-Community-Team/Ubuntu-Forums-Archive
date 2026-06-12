---
title: "what are linux-backports, linux-image,  linux-generic-pae"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by roozbeh on 2009-12-03
Hi.

What are these?
I have a problem and i've seen some peaple get around that problem by updateing to latest kernel.

Which ones should i install if i want the latest?

---

### Post by roozbeh on 2009-12-03
for example i have linux-generic 2.6.31.15.28 installed
but linux, linux-image, linux-backports-modules-karmic, linux-backports-modules-2.6.31-15-generic(and pae), linux-386, linux-ec2 not installed.


can anybody give more information on what each of these are for?
and
which ones to go?

---

### Post by Cheezespread on 2009-12-03
> **roozbeh said:**
> for example i have linux-generic 2.6.31.15.28 installed
but linux, linux-image, linux-backports-modules-karmic, linux-backports-modules-2.6.31-15-generic(and pae), linux-386, linux-ec2 not installed.


can anybody give more information on what each of these are for?
and
which ones to go?

Roozbeh , 

PAE stands for Physical address extension - For me this translates to making your 32 bit Ubuntu installation being able to recognize the 4 GB RAM that you have or more . Since by default , 32bit OS's have a limit on the RAM being used( aroun 3.2Gb in Windows ).Depends on whether you motherboards supports PAE and all . Anyway, a PAE kernel needs to be installed rather than the default kernel which comes bundled.More on it [here ]("http://en.wikipedia.org/wiki/Physical_Address_Extension")

Backports are more of a software terminology referring to using an update which worked for a current version to be used to fix for an older version. Supposedly you have a software of version 1.5 and the new release 1.6 is released with a fix which 1.5 had . Some dev's port that fix to 1.5 without infact updating to 1.6 ( Thats what I believe it is ).
More on backports [here]("https://help.ubuntu.com/community/UbuntuBackports")

Linux-image files are the image files corresponding specifci to a kernel which your system might be having. Hope some one else clears this better , since I am not so sure how to .

On your question whether to update this , i would reccommend you to.

---

### Post by clhsharky on 2009-12-03
HI

What is your problem?

Good place to start about kernels.
[https://help.ubuntu.com/community/Kernel](https://help.ubuntu.com/community/Kernel)

---

### Post by roozbeh on 2009-12-03
well my problem is slow transfer rates with usb. i searched over internet and numerous peaple having this issue with numerous fixes. turning off sync option (with numerous ways) and....

but anyway as i came to this i am now also intrested to know the difference of these packages.

for example whats difference between 'linux', 'linux-386', 'linux-image'?
also as i get from Cheezespread, if i go with linuxs, i do not need backports, right?

---

