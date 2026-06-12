---
title: "Remote server requires user input on start-up"
date: 2011-01-21
forum: New to Ubuntu
---

### Post by Ravagement on 2011-01-21
Hi There!

I've tried searching for the solution to my problem on this forum (and Google), but I have a feeling that I have failed simply because a lack of familiarity with the terminology involved.

I have a headless Ubuntu 10.04 (server edition) sitting in my cupboard at home. Unfortunately, the power grid in my area has repeatedly been messing up and as a result, we frequently lose power for a few minutes at a time - meaning the server loses power. Normally, this isn't a problem. The power switches back on and the server boots back up automatically and everything is fine. However, I frequently travel and take my portable hard drive with me (as a back-up just in case the house burns down or something), and when the power cuts out, the server doesn't properly load the OS.

The server gets to a point where it is mounting external drives, and gets to the backup drive and then requires some user input (either to plug in the hard-drive or to press 's' to skip mounting that drive). This is a problem as I am not there to give it user input! The OS has not booted enough to get the CLI or allow remote access.

Now, the obvious fix would be to buy a UPS, which I have already done. But sometimes the power cuts last longer than the battery backup can provide, so it doesn't properly solve my problem. The other solution would be to change my fstab to prevent auto-mounting, but then I'd lose the convenience of just plugging the usb hdd back into the server when I get home. I'd have to connect remotely and manually mount the external drive.

I rely on this server to handle various tasks for my business, such as web hosting and emails, so it can't just wait until I get back. Is there any way I could bypass the 'splash screen'/user interaction at boot while retaining the convenience of an auto-mount?

Thank you for your time,
Mark

---

### Post by cariboo on 2011-01-21
You could remove the external drive from auto mounting in /etc/fstab, and just mount it manually when needed.

---

