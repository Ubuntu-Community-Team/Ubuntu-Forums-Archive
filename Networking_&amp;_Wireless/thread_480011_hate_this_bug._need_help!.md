---
title: "hate this bug. need help!"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by NfF on 2007-06-20
ok, ive posted  this problem quite a number of times, and still i don't get the answer.Question is:

How do i install WUSB54Gversion4, without an internet connection at all?
Do help me. Ive only got 29 more dayz before im converting back to Ubuntu

---

### Post by Ayuthia on 2007-06-21
I am thinking that this is not so much of a bug, but more of a lack of linux support in the hardware community.

From this thread ([http://ubuntuforums.org/showthread.php?t=477175](http://ubuntuforums.org/showthread.php?t=477175)), it looks like you have ndiswrapper installed.  Is that correct?  If so, what drivers do you have?  From the thread, it looks like you were able to see networks but was not able to connect.  If that is the case, can you go to the terminal and post the information that you get from ndiswrapper -l, ifconfig, and iwconfig?

The other thing that would be helpful is which version of Ubuntu are you running?  Is it 32-bit or 64-bit?  

Also, is your Windows computer close to your Ubuntu computer (are they the same)?  If so, it will help in getting some files downloaded and copied over to Ubuntu.  I saw that you were not able to install build-essential and linux-headers (kernel headers).  This is because not all the files were able to fit on the CD.  I think that they are on the DVD version though.  However, if you don't want to download 4 gigs of data, [http://packages.ubuntu.com/feisty/allpackages](http://packages.ubuntu.com/feisty/allpackages) would have the packages that you need.  Before we go into this step on how to get and install these files, I would like to verify that you have ndiswrapper installed.

Depending on when you respond, I might not be able to get back to you as quickly.  I am not going to be close to my laptop this weekend so if I don't see a response by tonight, I might not be able to get back to you until Monday.  Of course, someone else reading this might jump in and assist also.

---

