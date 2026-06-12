---
title: "Copy Large File to IPOD"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by perito on 2010-08-19
Ok so I want to copy a 6GB files from my hard disk to the Ipod
The ipod has a lot of free memory as in the picture attached.
On ubuntu, the file transfer starts normally but only copies 4.0 GB then shows the error message.
On Win7, the transfer doesnt start at all and a similar message is shown.

My question is, why is this error message appearing? I have alot of free memory and the file can fit normally.
Also is there any software or way to force copying the movie to the ipod?

Thanks

---

### Post by sydbat on 2010-08-19
> **perito said:**
> Ok so I want to copy a 6GB files from my hard disk to the Ipod
The ipod has a lot of free memory as in the picture attached.
On ubuntu, the file transfer starts normally but only copies 4.0 GB then shows the error message.
On Win7, the transfer doesnt start at all and a similar message is shown.

My question is, why is this error message appearing? I have alot of free memory and the file can fit normally.
Also is there any software or way to force copying the movie to the ipod?

ThanksAccording to the first picture, the iPod is using msdos as its file system. There are major limitations as to the size of files it can handle...obviously less than 4GB.

Perhaps try to make smaller files, or break apart the big ones.

---

### Post by halitech on 2010-08-19
the third image says it all, the file is simply too large for the file system of the ipod. It is (supposedly) formatted in msdos which has a 4gig limit on file sizes. 

see here: [http://en.wikipedia.org/wiki/File_Allocation_Table](http://en.wikipedia.org/wiki/File_Allocation_Table)

---

### Post by perito on 2010-08-19
hmm so the only solution is to break up the file into smaller files.
Keeping in mind its a movie, how can I do this?

How can I break up the movie into smaller peaces?

---

### Post by halitech on 2010-08-19
you don't need to break it up into smaller parts, you can use something like Handbrake to re-encode it into a smaller size. Handbrake can actually encode for ipods with a preset designed for ipods.

---

### Post by rtlustyo on 2010-08-19
Yea if you just want to watch the movie on your ipod then re-encode it. If you want to transfer it to another computer or play it on a tv, then I would keep the original format and just split the file in half.

---

