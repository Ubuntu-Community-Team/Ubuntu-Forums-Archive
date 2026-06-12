---
title: "Incredibly slow updates"
date: 2007-03-11
forum: Networking &amp; Wireless
---

### Post by mrmonday on 2007-03-11
Hi everyone,

I recently decided to install beryl. For some reason it took a long time (much slower than dial-up) to download. After leaving my PC on overnight, Beryl had finally installed. Then the software updates program came up with 2 updates:
[LIST]
[*]linux-restricted-modules-2.6.17-10-generic
   Non-free Linux 2.6.17 modules on x86_64 generic
   From version 2.6.17.7-10.1 to 2.6.17.7-10.1-9746 (size: 8.0MB)


[*]linux-restricted-modules-2.6.17-11-generic
   Non-free Linux 2.6.17 modules on x86_64 generic
   From version 2.6.17.7-11.2 to 2.6.17.7-11.1-9746 (size: 8.0MB)
[/LIST]
Wouldn't the second be a downgrade? 

I clicked install update, and it started downloading... at speeds of about 1500 b/s. My connection normally downloads updates at up to 800kb/s. I cancelled the update, and would like to know why it is going so slow... and how to fix it. I can still access the internet at full speed, and download files at full speeds.

Thanks in advance for any help.

---

### Post by ciscosurfer on 2007-03-11
> **mrmonday said:**
> Hi everyone,

I recently decided to install beryl. For some reason it took a long time (much slower than dial-up) to download. After leaving my PC on overnight, Beryl had finally installed. Then the software updates program came up with 2 updates:[LIST]
[*]linux-restricted-modules-2.6.17-10-generic
   Non-free Linux 2.6.17 modules on x86_64 generic
   From version 2.6.17.7-10.1 to 2.6.17.7-10.1-9746 (size: 8.0MB)
[*]linux-restricted-modules-2.6.17-11-generic
   Non-free Linux 2.6.17 modules on x86_64 generic
   From version 2.6.17.7-11.2 to 2.6.17.7-11.1-9746 (size: 8.0MB)[/LIST]Wouldn't the second be a downgrade? 

I clicked install update, and it started downloading... at speeds of about 1500 b/s. My connection normally downloads updates at up to 800kb/s. I cancelled the update, and would like to know why it is going so slow... and how to fix it. I can still access the internet at full speed, and download files at full speeds.

Thanks in advance for any help.You should try again later in the day or even the next day.  Or, better yet, use a different download mirror.  What's happening is the repository location that you have listed in your /etc/apt/sources.list seems to be either down completely or running very, very slow (for any multitude of reasons).  Usually, in this scenario, I either wait it out and try again later, at which point in time your download speeds should go back up, or I comment out that line(s) in my sources.list and add a new mirror in its place.  You can find a list of mirrors here: [https://wiki.ubuntu.com/Mirrors?action=show&redirect=Archive](https://wiki.ubuntu.com/Mirrors?action=show&redirect=Archive)

As for your other question, I don't know much about how 64bit Ubuntu works, but it seems to me that either you have a module conflict, or that particular module requires the 1-9746 file instead.  Sorry I can't be of much help there.

---

### Post by mrmonday on 2007-03-11
Thanks, I will try again later. I am running 32bit ubuntu (I have no idea why... I have a 64 bit processor) How could I find out if there are any conflicts? I got a message a few minutes ago, about not being to authenticate the above files, saying it could be a hacker or something... is anyone else having/had this problem? Will the files be OK to download/install? 

Thanks.

---

