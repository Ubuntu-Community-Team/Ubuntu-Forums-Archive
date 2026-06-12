---
title: "Facebook Crashes When Using Album Uploader"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-07-12
I'm trying to upload pictures on Facebook using the album uploader but when I do, I get a white box where the files should be listed. Firefox then freezes, preventing me from clicking on any links or tabs. I then have to force quit it. I install Java 1.6.10 using synaptic. I do remember when I first install Java and tested the album uploader it was working. But every time after that, Firefox crashes.

---

### Post by ChrisB111 on 2009-07-12
I don't have the same problems or the fix to yours but I use wine and ie6 to upload photos to facebook, to do this first install wine using synaptic then, install [ie4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") and I selected ie6, then just log on to facebook and upload photos. This isn't a fix just a workaround.

Chris

---

### Post by Sup3r3g0 on 2009-07-12
Thanks

---

### Post by ftabor on 2009-07-12
Let it finish loading.  Get up and go to the bathroom, get a cup of coffee, walk the dog, then come back, the Java AP should be finished loading by then and you can upload your pictures.

---

### Post by Sub101 on 2009-07-12
I find I must run Firefox as root to use the album uploader. Otherwise it says im not allowed.

---

### Post by Sup3r3g0 on 2009-07-30
Running firefox as root worked! I guess it's because my home folder is protected.

---

### Post by llamabr on 2009-07-30
Wine is very rarely the correct solution.

Make sure the pictures have the correct permissions, otherwise you won't be able to share them.

If they are large, let them upload for a while.  It sometimes takes a bit of time, and often images are larger than you think.

---

### Post by Sup3r3g0 on 2009-07-30
Thanks for the tip. 

My pictures are protected because it's in my home directory. That's why I have to use "gksudo firefox" for it to work.

---

### Post by Arup on 2009-07-30
Works fine here with FF or Opera, you need to remove existing Open JDK and use latest Sun Java 1.6.14 from the repos.

---

### Post by PCZahra on 2009-09-29
I get something like that. When the page finishes loading and the uploader applet is ready, the whole window goes grey and all of firefox freezes.
About 90% of the time this lasts for about 30 seconds, everything returns to normal and it works just fine.
However, if it goes over 30 seconds it can last for minutes and counting, because it's never returned from that state without being forced-quit. During this time, the dual-core processor is hanging at a constant 50% (i.e. I can only still use the computer because of the multi-processor).

On a possibly unrelated note, if I use the java uploader applet to upload files directly from my camera's memory card, find myself unable to eject the card because files are in use by an application, even after facebook has been left, the tab closed, the window closed, or firefox itself closed, and the only thing to have accessed the card (and then only read) was the uploader.

---

### Post by PCZahra on 2009-11-12
bump. I think the java folder tree is trying to load the entire directory structure of the computer before it does anything. if so, would this be facebook's problem, or sun's?

---

