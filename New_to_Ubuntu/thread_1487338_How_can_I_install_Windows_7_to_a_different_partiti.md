---
title: "How can I install Windows 7 to a different partition?"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by thejakeman on 2010-05-18
The only OS on my computer right now is Ubuntu 10.04. I just switched over from Windows 7 a little less than a month ago but I'm already feeling the gaming withdrawal symptoms. I want to install 7 in a new partition so that when I boot up the computer I get to choose which one to load. What's the easiest way to do this?

---

### Post by -humanaut- on 2010-05-18
If you have Ubuntu installed across your entire drive you'll have to shrink the assuming Ext4 partition and create a Primary NTFS partition to put Windows 7 on the problem is this will wipe out your Grub boot loader so you'll need your Ubuntu LiveCD handy to repair grub and reinstall the bootloader.

---

### Post by thejakeman on 2010-05-18
And how does one "repair grub and reinstall the bootloader"?

---

### Post by Werner7 on 2010-05-18
Sorry this is not about your problem you have. Just like -humanaut- said is the way you do it. But Steam is coming out for linux in a few months! Not saying you have to wait for steam to come to linux before gaming, just support gaming on linux when steam launches their linux version!

---

### Post by pizza-is-good on 2010-05-18
EDIT: I was beat to it(and they have clarified the doubts I had), you can probably disregard my post...

The way how I know how to do it would be to wipe your ubuntu, boot from the Win7 CD, and go through the process of installing windows.

I know that there is a way to do it without loosing ubuntu, but I don't know how.

I think that if you install Win after Ubuntu, windows can't deal well with the partitions, and the windows boot manager won't let you choose ubuntu, so you need to re-install grub.

Sorry for the lack of knowledge there. If anything I bumped the thread....

As a side note, you could consider installing 7 in ubuntu using virtual box, and play your games there.
I can help you with that process if you'd like to do that, as I have done it several times.

Send me a PM to get me back to the thread if you want to do that, and I'll write up the instructions for how to do it.

On the bright side, Steam is making a linux-native version of their software, so gaming in linux is going to improve quickly.

---

### Post by thejakeman on 2010-05-18
Yeah I've tried the VirtualBox thing, but I need more RAM. I've known how to install Ubuntu after Windows without a hitch but not vice versa. I'm backing stuff up now, I'm planning on wiping it, installing windough$ and then installing Ubuntu. Thanks for the help guys

---

### Post by -humanaut- on 2010-05-18
> **pizza-is-good said:**
> EDIT: I was beat to it(and they have clarified the doubts I had), you can probably disregard my post...

The way how I know how to do it would be to wipe your ubuntu, boot from the Win7 CD, and go through the process of installing windows.

I know that there is a way to do it without loosing ubuntu, but I don't know how.

I think that if you install Win after Ubuntu, windows can't deal well with the partitions, and the windows boot manager won't let you choose ubuntu, so you need to re-install grub.

Sorry for the lack of knowledge there. If anything I bumped the thread....

As a side note, you could consider installing 7 in ubuntu using virtual box, and play your games there.
I can help you with that process if you'd like to do that, as I have done it several times.

Send me a PM to get me back to the thread if you want to do that, and I'll write up the instructions for how to do it.

On the bright side, Steam is making a linux-native version of their software, so gaming in linux is going to improve quickly.

You don't have to delete the Ubuntu partition, though it is far easier if you install Windows first so you don't have to reinstall and correct Grub. I'd agree with your method if you have little or no experience in system recovery or rescue.

---

### Post by thejakeman on 2010-05-18
I'm too lazy to find my Ubuntu disc, so I'm doing it the hard way... Jeez I'm such a stereotypical American 15 year old...

---

