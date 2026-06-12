---
title: "Images and watermarks"
date: 2009-12-06
forum: New to Ubuntu
---

### Post by 289531.EXE on 2009-12-06
I'm working on putting  my art work together  and was wondering, is there a way to put watermarks on an image? Does GIMP do that or would I need another program?

---

### Post by spcwingo on 2009-12-06
I'm not sure if GIMP does it, but phatch does.  Here's a link to their site:

[http://photobatch.stani.be/]("http://photobatch.stani.be/")

Here's their wiki page about watermarks:

[http://photobatch.wikidot.com/action-watermark]("http://photobatch.wikidot.com/action-watermark")

I hope this information helps.  :)

---

### Post by talsemgeest on 2009-12-06
> **289531.EXE said:**
> I'm working on putting  my art work together  and was wondering, is there a way to put watermarks on an image? Does GIMP do that or would I need another program?
Yes, simply add the watermark as a new layer onto the image, move it into place and adjust the transparency to make it semi-transparent.

---

### Post by 289531.EXE on 2009-12-06
Thanks for the info Phatch, I have no idea how to install it and the link said it couldn't find what i was looking for. As for gimp, how exactlycan i add a new layer? I would  like to add one picture on to the other and then make it transparent if that is possible-

Any simple step by step would be most useful, thank you.

---

### Post by spcwingo on 2009-12-06
Here's some direct links:

[download 1]("https://launchpad.net/%7Estani/+archive/+files/phatch_0.1.6-0ubuntu1~7.10~ppa1_all.deb")

[download 2]("https://launchpad.net/%7Estani/+archive/+files/phatch_0.1.6-0ubuntu1~7.04~ppa1_all.deb")

These are older versions, but they may just work.  To install just open with gdebi or from the terminal:

```
cd /path/to/deb && sudo dpkg -i ./name_of_package.deb
```

Let me know how it goes.

---

### Post by talsemgeest on 2009-12-06
> **289531.EXE said:**
> Thanks for the info Phatch, I have no idea how to install it and the link said it couldn't find what i was looking for. As for gimp, how exactlycan i add a new layer? I would  like to add one picture on to the other and then make it transparent if that is possible-

Any simple step by step would be most useful, thank you.
Heres a nice tutorial for you: [http://www.tankedup-imaging.com/gimp/layers.html](http://www.tankedup-imaging.com/gimp/layers.html)

---

### Post by 289531.EXE on 2009-12-07
Thanks!!!

---

### Post by stani on 2009-12-10
> **289531.EXE said:**
> Thanks for the info Phatch, I have no idea how to install it 

Phatch ships in the ubuntu repositories, so just do:
```
sudo apt-get install phatch
```

---

### Post by joes7 on 2009-12-10
Thanks, I was looking for this, too:)!

---

