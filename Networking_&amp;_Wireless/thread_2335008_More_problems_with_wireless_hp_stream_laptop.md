---
title: "More problems with wireless hp stream laptop"
date: 2016-08-24
forum: Networking &amp; Wireless
---

### Post by pituga on 2016-08-24
Hi,

I have posted here before about problems with my hp stream.
I followed the instruction given on another post and opened the laptop, switched the antenas and it worked. A few weeks ago I lost signal again, i.e. cannot detect any wifi point.
I followed the recommendations of the post "ASUS laptop wireless" and generated the attached txt file. I can see the file just right in my laptop, but not on the computer I'm using now.
Can anyone check this report and guide me on how to solve my wireless problem?

---

### Post by chili555 on 2016-08-24
You posted the raw script. What we need is the data that's produced when you execute the script. [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by pituga on 2016-08-26
I'm really sorry, I must have selected the wrong one.
Will this help?

Thanks.

---

### Post by chili555 on 2016-08-26
We see that the driver module is not loaded. Does the wireless come to life if you load it?```
sudo modprobe rtl8723be
```Are there any clues in the log?```
dmesg | grep rtl
```> I have posted here before about problems with my hp stream.Where? I was unable to check your previous posts to try to see what went wrong.

---

### Post by pituga on 2016-08-26
Hi chili555,

When I try The first command, The output is: "Error: could not insert 'rtl8723be': requiered key not available".

As for The second command, nothing happens.

My last post was earlier this year, but i cant find it. I may have used an old user name.

I'm a really beginer with ubuntu. Can you guide me on what you are trying to do?

Thanks again.
P

---

### Post by chili555 on 2016-08-26
> Can you guide me on what you are trying to do?Sure; I'm happy to. I am trying to run a few terminal commands to see what could be going wrong and I think we've found it!>  "Error: could not insert 'rtl8723be': requiered key not available".Please see: [http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules](http://askubuntu.com/questions/762254/why-do-i-get-required-key-not-available-when-install-3rd-party-kernel-modules)

---

### Post by pituga on 2016-08-26
It worked chili555. I disabled The secure boot and when rebooted, I automatically got Internet connection. Thanks a lot for your help.

---

