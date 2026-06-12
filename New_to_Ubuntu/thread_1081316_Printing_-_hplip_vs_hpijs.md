---
title: "Printing - hplip vs hpijs"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2009-02-26
I already posted this in the hardware forum, but I haven't gotten any response yet, so I'm going to post it again here.  Hopefully that's not some sort of taboo.

My parents are running Ubuntu Hardy and have an HP Photosmart C4280 All-In-One that has been causing them some intermittent problems.  Some of the time it prints properly, sometimes it prints gibberish.

I looked around on the web a little bit, and found a page that said that I should be using the hplip driver:
[http://www.openprinting.org/show_printer.cgi?recnum=HP-Photosmart_C4280]("http://www.openprinting.org/show_printer.cgi?recnum=HP-Photosmart_C4280")

My parents are currently using the hpijs 2.8.2 driver.

Can anyone confirm that the hplip driver would actually be better for this printer?  I'm not familiar with the site I referenced, so I don't know how up to date it is.

And if the hplip driver is recommended, what's the best way to change the driver?  Do I just need to install hplip from Synaptic?

Thanks for your time.

---

### Post by wolfen69 on 2009-02-26
go [here]("http://hplipopensource.com/hplip-web/index.html") and download the hplip file to the home folder. then open a terminal and do: 
```
sh hplip-3.9.2.run
``` and follow the prompts. when given the choice, pick automatic install.

---

### Post by Irony on 2009-02-26
Yes the latest HPLIP driver works for your printer (which I also have) in Ubuntu and Mepis, I install it here;

[http://mepislovers.org/forums/showthread.php?t=19007](http://mepislovers.org/forums/showthread.php?t=19007)

However in Ubuntu and Mepis bordlerless printing on 6x4 doesn't work.

---

### Post by stoogiebuncho on 2009-02-28
> **wolfen69 said:**
> go [here]("http://hplipopensource.com/hplip-web/index.html") and download the hplip file to the home folder. then open a terminal and do: 
```
sh hplip-3.9.2.run
``` and follow the prompts. when given the choice, pick automatic install.

Thanks for the tip.  I followed the directions and so far it looks like everything is working.

---

