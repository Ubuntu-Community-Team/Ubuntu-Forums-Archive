---
title: "Totally new and having issues"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by nyghthawk on 2011-04-19
After having had enough of WinXP, I went ahead and did a switch to the current version of Ubuntu. Here's what I am trying to deal with and hopefully someone will be able to help me make sense of it. :P

First things first..I cannot get my cd drive to show up. If I go through the Places/Computer, it is there, but unless something is in the drive, it doesn't show up anywhere else. I don't *think* this is the way it is supposed to be. Feel free to correct me if I am wrong.

My other problem is a bit harder. I am running two hard drives. I screwed up and started to install Ubuntu on the wrong drive. For some reason, it glitched during install from CD and stalled. I restarted with my other drive, which was running WinXP. That was when I found out that I had gone over my pictures, videos, etc. It is not recognized by Ubuntu, except through System/Administration/Disk Utility. It won't let me mount it. What can I do to recover the files? I am not using the hard drive at this point and (for what it is worth) I do have access to an identical system that is running WinXP.

Thanks,
Mona

---

### Post by Paqman on 2011-04-19
> **nyghthawk said:**
> 
First things first..I cannot get my cd drive to show up. If I go through the Places/Computer, it is there, but unless something is in the drive, it doesn't show up anywhere else. I don't *think* this is the way it is supposed to be. Feel free to correct me if I am wrong.

Nope, that's how it's supposed to work.

> 
My other problem is a bit harder. I am running two hard drives. I screwed up and started to install Ubuntu on the wrong drive. For some reason, it glitched during install from CD and stalled. I restarted with my other drive, which was running WinXP. That was when I found out that I had gone over my pictures, videos, etc. It is not recognized by Ubuntu, except through System/Administration/Disk Utility. It won't let me mount it. What can I do to recover the files? I am not using the hard drive at this point and (for what it is worth) I do have access to an identical system that is running WinXP.


Yikes!

First of all: you're doing the right thing by not touching the drive.

You need to set up a location to recover your files to and then use [Photorec](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step) to recover your data. Photorec is a tool contained in the [testdisk](apt:testdisk) package.

---

### Post by nyghthawk on 2011-04-24
> **Paqman said:**
> Nope, that's how it's supposed to work.


You need to set up a location to recover your files to and then use [Photorec]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step") to recover your data. Photorec is a tool contained in the [testdisk]("apt:testdisk") package.

It worked!! \\:D/
Thank you! 

Now, I am trying to figure out how to open the disk image it created for all of the files it couldn't recover on their own. *chuckles* 

I have to admit, though..this has given me a good perspective on just how bloated Windows is. Over 70% of the files recovered are being deleted because they're nothing more than files needed to run Windows. 

Mona

---

### Post by candtalan on 2011-04-24
Welcome! And well done for your recovery actions. Take your adventures into Ubuntu (GNU/Linux) gently, and maybe also do the checking out thing a bit sooner than you might have previously expected, at least until you get the measure of stuff.

I have been using Ubuntu for over five years now, and I have never wanted to even take a glance back to using Windows again.

Enjoy

---

### Post by nyghthawk on 2011-04-24
I've been with it for a very short time, but I enjoy it. It runs better than Windows ever did for me and the best part is that it was able to find the dual processor that Windows couldn't. It's been interesting, learning how to get programs running and what to do when I have to use the Terminal. So far, I haven't messed anything up that I couldn't repair.

Other than accessing that disk image, I'm learning how to open ports so that hubby and I can use TCP/IP to play Diablo 2 together. That is proving more challenging. A lot to learn. Same with setting up the network so that his Windows comp can see mine. 

But I'm sure it will all come along at some point. :D

Mona

---

### Post by candtalan on 2011-04-24
Great. Now you have found these forums, you might find they can help with other questions, if your own approaches are problematic.

---

