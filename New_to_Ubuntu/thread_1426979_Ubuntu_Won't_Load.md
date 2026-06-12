---
title: "Ubuntu Won't Load"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by tdog10 on 2010-03-10
Hi!

I've been using Ubuntu since last summer.  I am using the current version of 9.1.  Last week, my Tomboy application stopped working.  When I click on it, the "loading Tomboy Notes" indicator pops up, then disappears, and Tomboy is not loaded.  I've tried removing and reinstalling.  Any suggestions?

Thanks!

---

### Post by Temposs on 2010-03-11
So, let's try a full uninstall like this:

```
sudo apt-get purge tomboy
```

Then open a file browser to your home folder and press Ctrl+H to show your hidden files. Change the name of your .tomboy folder to something else, like .tomboy-bak

Now, install tomboy notes again. See if it starts up now. Note that when it starts up this time, there will be no notes listed. But don't worry, all your notes are in the .tomboy-bak folder, so you can try copying your notes files back into the new .tomboy folder and see if tomboy still works after that.

---

### Post by tdog10 on 2010-03-11
Temposs,

I tried what you said and it didn't work.  I was also not able to see .tomboy when I showed hidden files in home.  What should I do next?  Thanks!

---

### Post by Temposs on 2010-03-11
I'm not sure what else to tell you, just that you have to try again and remember to press Ctrl-H in your home folder to see the hidden files.

---

### Post by sharm on 2010-03-17
What version of Tomboy is this?

Can you try starting it from a terminal with `tomboy --debug`, and then share the output you see?

---

