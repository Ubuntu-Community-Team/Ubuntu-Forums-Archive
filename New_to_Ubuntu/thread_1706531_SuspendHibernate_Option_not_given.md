---
title: "Suspend/Hibernate Option not given"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by kprice789 on 2011-03-14
So basically i can't get my laptop to suspend anymore. It used to about two days ago, have been doing a ton of Google searching with no luck. When i click my power button in the top right corner of my desktop i am given no option to Suspend or Hibernate, only shutdown or restart. In the power management options I can not change any of the options to suspend. When i push the suspend button on my laptop i get a error message...

Failed to suspend
Computer failed to suspend.
Failure was reported as: Cannot suspend

This is not much help. Please help Thanks :)

Ubuntu 10.10
HP-dv6-1355dx

---

### Post by vivek.pandey on 2011-03-14
hey
have you tried using terminal
atleast we would have a good error message to start with even if it fails
sudo /etc/acpi/sleep.sh force

---

### Post by vivek.pandey on 2011-03-14
sorry for double post

---

### Post by grahammechanical on 2011-03-14
Have you checked out the settings in the BIOS? The OS is responding to the suspend key press but it cannot do the suspend. What is preventing it? Is it the BIOS settings?

Regards.

---

### Post by kprice789 on 2011-03-14
Thanks for the help so far.

There is no error in terminal command, nothing happens.

Regards to the BIOS, i know its not that because in my Windows partition i can suspend and hibernate just fine.

---

### Post by techunit on 2011-03-14
you must have a swap partition to make it work.

---

### Post by kprice789 on 2011-03-14
There is also a swap partition.
Do you think it may not be working?

---

### Post by Quadunit404 on 2011-03-14
I had this same problem in the past and found a patched pm-utils that fixed this problem, but I have lost the link to the patched version. I wish I could help out, though.

I'll try looking through my threads later because I know I created a thread in Hardware and Laptops (I'm not necessarily a newbie to Linux, ya see :lol:) about a problem similar to this with my own laptop and the patched pm-utils was linked to there.

---

### Post by marl30 on 2011-03-14
This is one of the few issues that I have been waiting for months to see solved.

---

### Post by kprice789 on 2011-03-15
That would be great if you could find the link :)

Other..

Ubuntu is a great OS and Iv'ed used it for several years now since 8.04 :) Only reason i have windows is for school...

---

