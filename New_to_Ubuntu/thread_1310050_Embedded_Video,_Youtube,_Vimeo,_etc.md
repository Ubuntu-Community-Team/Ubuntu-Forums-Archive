---
title: "Embedded Video, Youtube, Vimeo, etc"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by eopi on 2009-11-01
I think I have Ubuntu 9.04, april 2009.  Sounds about right when I installed this. 

QUESTION:

I can't see video from any of the following: Embedded Video, Youtube, Vimeo, etc

I believe in the last release I found a thread that said do this to view all video.  So I went to Synaptic Package Manager and it worked.  

With this release I was prompted to download Adobe Flash player and I did it but now I can only see a Gigantic Arrow (play arrow).  And then nothing happens.  Sometimes I get sound from the video that skips like a broken record and an image from the video but it's not working.  

Any ideas. 

Thanks, 
Eopi

---

### Post by blazemore on 2009-11-01
Open a terminal
```
Applications -> Accessories -> Terminal
```

type in the following:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by fooman on 2009-11-01
go to synaptic (system > administration > synaptic package manager)....search for flash

scroll through the results and uninstall anything that says gnash or libswfdec in the title.

then install flashplugin-installer

when it completes,  close firefox if it is open,  then open it and try again.

hope that helps.

---

### Post by eopi on 2009-11-01
> **blazemore said:**
> type in the following:

```
sudo apt-get install flashplugin-nonfree
```

> **fooman said:**
> go to synaptic (system > administration > synaptic package manager)....search for flash

---SNIP---

hope that helps.
These post didn't go unnoticed.  Straight away I start to attempt fixes, and some stuff went through but I wasn't really able to test.  

Then I was prompted to upload Ubuntu 9.10 - the Karmic Koala.

So far I've updated to 9.10 and I'm able to view and hear (Sound) my Vimeo and Youtube clips.  I'm on to try embedded news clip, ,mpg and .wmv Web clips.

Thanks everyone. 

Appreciate it.

---

