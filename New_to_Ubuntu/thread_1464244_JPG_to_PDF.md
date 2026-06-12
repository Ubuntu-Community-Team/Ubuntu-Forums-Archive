---
title: "JPG to PDF?"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by slughappy1 on 2010-04-28
I need to convert a whole bunch of jpg files to pdf. I keep reading that imagemagik should be able to do it. I get an error every time though.
```
jason@Barnaby:~/Documents/Stuff$ convert *.jpg foo.pdf
Segmentation fault
jason@Barnaby:~/Documents/Stuff$ 
```

---

### Post by kaibob on 2010-04-28
That is is an ongoing problem that's been around for some time. The simplest solution is to install graphicsmagick by way of synaptic. The command is then:

```
gm convert *.jpg foo.pdf
```

For additional information on graphicsmagick go to:

[http://www.graphicsmagick.org/](http://www.graphicsmagick.org/)

---

### Post by slughappy1 on 2010-04-28
Thank you. I didn't even see one reference to graphicsmagik when looking.

---

### Post by kaibob on 2010-04-28
I upgraded to lucid a few days ago and decided to see if the included version of imagemagick might be better. As a test, I converted 10 JPEG's that were each about 3 MB each to a PDF without any issue. So, if you are going to upgrade to lucid, you might want to give imagemagick another try.

---

### Post by slughappy1 on 2010-04-28
I do plan on it, thanks.

---

### Post by kwanylongy on 2012-07-17
Thank you for creating this thread! 

I have this problem of converting jpg to pdf and your thread introduced 'convert' this great command to me! Saved me hours! :D

---

### Post by sujitrjadhav on 2012-07-17
Thanks vm for this thread. I learned a very useful new command. I am using ubuntu 12.04 ( Actually Pinguy OS based on Ubuntu 12.04) and the command worked very fine on my laptop.

---

### Post by nothingspecial on 2012-07-17
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

