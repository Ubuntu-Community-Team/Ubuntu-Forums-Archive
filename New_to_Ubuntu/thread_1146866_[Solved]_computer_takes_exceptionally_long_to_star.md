---
title: "[Solved] computer takes exceptionally long to start..."
date: 2009-05-03
forum: New to Ubuntu
---

### Post by jimmybarcelona on 2009-05-03
Just today my computer starts getting hung up on start up. It boots to the point of displaying the ubuntu orange and black display bar, then freezes about 1/8 of the way there. It happens consistently wheneve I boot up the machine. So I hit ctrl+alt+F2 to switch over to the non GUI. The following message comes up:

[99.808.8500] Buffer I/O error on device sr0, logical block 1102838.

Then the message repeats itself with different numbers at the front in brackets and different numbers at the end. the numbers at the end included logical block 1102832, 1102859, 1102800, 1102814, 1102815. The numbers to the left changed to fast for me to write them all down. After almost 5 minutes of this the computer eventually switched over to the GUI and logged me in normally. What does is a buffer I/O error on a logical block?

I'm running ubuntu intrepid on a dell vostro 1500, if that helps.

---

### Post by Didius Falco on 2009-05-03
> **jimmybarcelona said:**
>  The following message comes up:

[99.808.8500] Buffer I/O error on device sr0, logical block 1102838.

What is a buffer I/O error on a logical block?

I'm running ubuntu intrepid on a dell vostro 1500, if that helps.

Note: I do **not** have any expertise in this area at all.  

After doing some Googling, I was able to determine that device sr0 is a mass storage device - CD or DVD drive.

Is there a CD or DVD in your Drive? Have you recently installed a new one, or had problems with your current one?

My best guess from the error is that the kernel thinks that it is a writeable device, and keeps trying to write to it, until it finally gives up and lets you in.

Where to go from here? I don't know for sure, try to play a CD or DVD in Ubuntu and see if you get errors. 

I know I haven't given you much of an answer, but I hope I've at least given you some avenues to explore...

Good luck

---

### Post by jimmybarcelona on 2009-05-03
Thanks for the post, it pointed me to exactly where the problem was. There was a cd in my cd drive that forgot was in there. The Cd was unreadable to my drive, I don't know what it was formatted as. Anyways, you were right. My computer was trying to write to the cd upon start up and it wasn't working. Thanks for the help!

---

### Post by Didius Falco on 2009-05-03
My pleasure - I learned something doing the search. Now, if I ever get that error, I'll know where to start looking. :P

Please mark this thread as solved - just edit your first post, hot the **Go Advanced** button and type "solved" at the end of the thread title. You could also change the thread title to something like "Buffer I/O error on device sr0 - Solved", so that others with the same problem have a better chance of finding it during a search.

Regards,

Didius

---

