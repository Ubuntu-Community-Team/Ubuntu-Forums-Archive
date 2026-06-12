---
title: "An enquiry to solve a common problem? (novice user)"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by kalebka55 on 2010-08-01
to whom it may concern

I have been a frustrated microsoft user for a while. now I am a happier (questionable) ubuntu 10.04 user and am thoroughly happier with my conversion.

The reason for being questionably happier is of course the few bugs/problems that have come with linux/ubuntu 10.04.  The common problem that I have observed is with Skype and webcams that I have read many users have a problems with.  I too have that problem and have tried all suggestions with no success (with a sprinkle of frustration).  {HP dv2000 built-in webcam}

My suggestion for this problem (I should actually try it for myself but would rather ask for detailed knowledge whether it is theoretically possible) is whether to install skype via a virtual OS, Microsoft XP for example, and then following the regular procedure and trying to use skype normally.  Is it possible to work? if not, why?  I will be trying this suggestion of mine soon (but have a feeling it wont work....it just seems too easy!!) 

I look forward to any responses and any theory will be appreciated.

Regards

---

### Post by jerenept on 2010-08-01
I think that would work, but the OSE version of Virtualbox from the Repositories does not support USB. 
You will need to use the one here: [http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

But i think this will work out.

---

### Post by Paqman on 2010-08-01
> **kalebka55 said:**
> The common problem that I have observed is with Skype and webcams that I have read many users have a problems with.  I too have that problem and have tried all suggestions with no success (with a sprinkle of frustration).  {HP dv2000 built-in webcam}


What is the actual problem you're having with your webcam? Is it just Skype, or is it also broken if you install Cheese?

---

### Post by kalebka55 on 2010-08-02
> **Paqman said:**
> What is the actual problem you're having with your webcam? Is it just Skype, or is it also broken if you install Cheese?
Webcam works just fine for everything else... it just doesn't send my picture through and the 'test' option also shows a blank window (in skype).

---

### Post by Paqman on 2010-08-02
So the problem is just Skype? Have you tried the Skype support site?

[https://support.skype.com/](https://support.skype.com/)

---

### Post by 0004tom on 2010-08-02
[http://ubuntuforums.org/showthread.php?t=1443838](http://ubuntuforums.org/showthread.php?t=1443838)

Have a look at this, it seems to solve my issue which was like yours.

---

### Post by kalebka55 on 2010-08-06
> **0004tom said:**
> [http://ubuntuforums.org/showthread.php?t=1443838](http://ubuntuforums.org/showthread.php?t=1443838)

Have a look at this, it seems to solve my issue which was like yours.
ooo4tom...  Thanks for the suggestion! but unfortunately i got this message: 'chmod: changing permissions of `/usr/bin/skype': Operation not permitted'-  am completely wasted from trying to fix this problem.  am just going to have to go video-less.  My laptop was configured for WinXP and I deleted it from pure frustration.  Seems webcam is just not compatible for skype via linux.
Cheers and thanks again-always worth a try. :)

---

### Post by jerenept on 2010-08-06
you should use "sudo" if you are 'chmod' ing something.

for example:```
sudo chmod -a -w -x ~/foo
```

then enter your password.

---

### Post by kalebka55 on 2010-08-26
> **jerenept said:**
> you should use "sudo" if you are 'chmod' ing something.

for example:```
sudo chmod -a -w -x ~/foo
```then enter your password.


No such success im afraid.  ive posted thread as solved.  video is just a luxury on skype anyways.  I appreciate your time though!  Many thanks!

---

