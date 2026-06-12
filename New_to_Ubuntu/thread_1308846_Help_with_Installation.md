---
title: "Help with Installation"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Whitewind6177 on 2009-10-31
Hello, I'm an extreme noob to Ubuntu (I haven't even used it fully yet) and 'm going to install it on my PC tonight or tomorrow. I just wanted to make sure I was doing the installation right and that everything is going to do what I think it will do.

Firstly, what I want to have it do is Install Ubuntu as a partition, with Windows being the primary boot if possible, but that part's not that important. But if you can tell me how this might be possible, that would be great. I got to where I am here by clicking Manually partition. 

I already have 34 GB unallocated as a spot for ubuntu. What I want to know is, should the partition I install it to be Primary? I'm pretty sure it should be no matter what, but I'm just making sure. Also, is it alright to put the Ubuntu partition in the back? I want windows to run faster than Ubuntu, so I figured I'd put it in the back since the front partitions I've heard run faster, but It will still know I want to install it to that partition even though it's in the back right?

I'm also going to have a 1 GB swap file, and I'm pretty sure that should also be primary, right? I'm just confused on how it puts it on logical by default, but from what I've heard already, they should both be primary partitions. This should also be in the back, but when I create it second, it puts it ahead of the partiton I want to install ubuntu to. Is this fine?

Lastly, How do I know what partitions it's planning on installing to? I looked at the screen where it asks you to confirm everything, just to see what it would look like, and I can't seem to find where it tells you what partition it's installing ubuntu to, as I don't recall ever selecting any. This is what led me to believe it would just select the first partition, because maybe it figures you want ubuntu there...I don't really know. How does it choose where Ubuntu goes?

Well, that's all my questions for now. I'll post more questions if I find anything else confusing.

---

### Post by cariboo on 2009-11-01
> I already have 34 GB unallocated as a spot for ubuntu. What I want to know is, should the partition I install it to be Primary? I'm pretty sure it should be no matter what, but I'm just making sure. Also, is it alright to put the Ubuntu partition in the back? I want windows to run faster than Ubuntu, so I figured I'd put it in the back since the front partitions I've heard run faster, but It will still know I want to install it to that partition even though it's in the back right?

Linux doesn't care if it is on a primary or extended partition. Depending on your hardware and how new you Windows installation is Ubuntu will more than likely run faster than Window even if it is on an extended partition.

> I'm also going to have a 1 GB swap file, and I'm pretty sure that should also be primary, right? I'm just confused on how it puts it on logical by default, but from what I've heard already, they should both be primary partitions. This should also be in the back, but when I create it second, it puts it ahead of the partiton I want to install ubuntu to. Is this fine?

Again Linux doesn't care where tha swap partition is located.

The one thing to keep in mind is that a Linux distribution is totally different from Windows, most of what you know will not be much help running Ubuntu, be prepared to spend just as much time learning to use Ubuntu as you did learning everything you know about Windows.

> Lastly, How do I know what partitions it's planning on installing to? I looked at the screen where it asks you to confirm everything, just to see what it would look like, and I can't seem to find where it tells you what partition it's installing ubuntu to, as I don't recall ever selecting any. This is what led me to believe it would just select the first partition, because maybe it figures you want ubuntu there...I don't really know. How does it choose where Ubuntu goes?

I would suggest you use the manual partitioning option, that way you know what partition you are installing Ubuntu on.

Another thing to keep in mind is that Ubuntu doesn't use drive letters like Windows does, the partitions use device lables. In Windows the first partition of the first drive is called C: using Ubuntu the same partition would be called /dev/sda1. The way you described how you want to set up the partitions, if you put Ubuntu on a extended partition, would be installed on /dev/sda3 and swap would be on /dev/sda4.

If you have any more questions before doing the install, feel free to ask them here.

---

