---
title: "Just applied updates, I have NO SOUND after rebooting!"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by diablo75 on 2009-01-29
What can I say.  I just finished installing the latest updates. 

The sound card is a SB Audigy 2.  All the default Sound settings were set to auto detect originally.  I've since set them to Pulseaudio to see if it would make a difference and it hasn't.

EDIT:  Since posting this, I've discovered that the problem is related to a recent kernel update.  The latest kernel version that I have on my PC is 2.6.27-11.  Loading this up produces no sound.

But if I load up a previous kernel (version 2.6.27-9 in this case) I get sound!!!  So, short of manually selecting this kernel version I can't come up with any other solution... it's just a quick work around for now.

I hope there will be an update correcting this soon...

---

### Post by Crafty Kisses on 2009-01-29
I've seen a couple of threads stating the same issue my friend, so I don't think you're the only one.

---

### Post by diablo75 on 2009-01-29
I found a fix:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/310179](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/310179)

They SWAPED THE ANALOG/DIGITAL check box switch in the ALSA mixer.  I had to uncheck this.

I can understand why they did this... because when you look at that switch you think, "Ok... checking that probably enables digital."  But it didn't.  Now it does.  Which disables the analog outputs.

---

### Post by ged5 on 2009-02-02
Thanks. That has been my problem for the last 3 days. Fixed now.

---

