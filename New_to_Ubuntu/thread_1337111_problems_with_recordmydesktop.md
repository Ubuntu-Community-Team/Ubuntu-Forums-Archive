---
title: "problems with recordmydesktop"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by YosefKaro on 2009-11-25
Hi to all,

I am trying to record my desktop using recordmydesktop to share it on Facebook but I am having troubles.

I was able to get it up and running and I was able to record my desktop and to stop the recording.  Following that, it would 'compile' or 'encode' the video just fine.  So everything runs smoothly up to this point.

The problem I ran into is how to save the video after it finishes compiling?  The main screen would pop back open as soon as the compiling would finish up and there is a save-as feature.  So I clicked the save-as, gave the file a name, indicated where to save it...etc, etc.  However, after doing this, I couldn't find the file anywhere.  What am I doing wrong?

-Yos

---

### Post by ukripper on 2009-11-25
What is the name of your file? you can put the first letter of your filename to search it via terminal:

as an example if your filename is myvideo. use below command
```
find $HOME -name 'my*'
```

just replace **my** with first two letters of your file you think you saved as.

---

### Post by YosefKaro on 2009-11-25
How interesting: that is what I named the file.  However, it is not to be found anywhere on my computer.  Maybe I'm supposed to do Save-as before I start the recording?

-Yos

---

### Post by ukripper on 2009-11-25
see this thread - [http://ubuntuforums.org/showthread.php?t=294605](http://ubuntuforums.org/showthread.php?t=294605)

---

### Post by YosefKaro on 2009-11-25
Ok, I read that post and I skimmed over many of the replies, however, it does not address my issue.  That thread covers installing and recording with recordmydesktop which as I wrote in my original post, I have no problems with.  My problem is with finding where the file goes...why when I think that I have saved it, it doesn't show up where I saved it to?

My question was and is, how do I save the file after making the recording?

-Yos

---

### Post by VertexPusher on 2009-11-25
> **YosefKaro said:**
> Maybe I'm supposed to do Save-as before I start the recording?
Yes. The button's name is misleading. It doesn't save a file but instead chooses a default saving location and name prefix. Any subsequent recording will go to that location. Existing recordings are not overwritten; instead, a number is appended to the file name.

You may still be able to find the previous recordings by searching for files named "out*" in your home directory. That's the default file name prefix, if I remember correctly.

---

### Post by YosefKaro on 2009-11-25
Now it's working; thank you all :D  I just have to play around with it now to figure out what resolution is best to use etc.

-Yos

---

