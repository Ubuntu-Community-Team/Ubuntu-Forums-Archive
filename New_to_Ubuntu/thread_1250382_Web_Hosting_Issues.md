---
title: "Web Hosting Issues"
date: 2009-08-26
forum: New to Ubuntu
---

### Post by fiveironfrnzy08 on 2009-08-26
Hey,
I'm kinda just starting out with servers and that fun stuff. I've got Ubuntu 9.04 Desktop, Apache, Bind, and a few other things installed and I've been messing around a bit with those. I've got a site up that I'm trying to configure a little bit. I can view from the computer with Ubuntu on it by putting in [www.giuseppesnewbrighton.com](www.giuseppesnewbrighton.com), but can only it from another computer if I put in my external IP address (174.*.*.*). Do I need to do further configuration with Bind9 or Apache to resolve that to [www.giuseppesnewbrighton.com?](www.giuseppesnewbrighton.com?) I just don't really know where to go from here, kinda stuck.

By the way, I'm trying to do all this without using any hosting services online or anything like that. So I want to do it all completely organically, so to speak. I also chose not to get a static external IP address from qwest in order to save money/challenge myself. For now I'd like to just make the appropriate alterations whenever qwest changes my external IP. 

Thanks in advance

---

### Post by wizard10000 on 2009-08-26
The reason the other machines require an IP address is that they're most likely not using your DNS server but one provided by their ISP.

---

### Post by oldsoundguy on 2009-08-26
An FYI and an important one:

MOST (if not all) internet service providers do NOT allow running of an on line server on a residential feed or node.
They will not only shut you down, but they will deny you service in the future. 
Severs require much more bandwidth than the normal user because of the UPLOADING.
That is why they charge EXTRA or commercial rates.
CHECK your EULA with your carrier!

---

### Post by expatCM on 2009-08-27
when you get round to thinking about a fixed IP, do remember the free service from dyndns

[http://www.dyndns.com/](http://www.dyndns.com/)

There are other people doing this as well but I am not sure who ...

---

