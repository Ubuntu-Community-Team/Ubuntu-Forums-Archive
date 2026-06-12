---
title: "rar files help required"
date: 2009-06-12
forum: New to Ubuntu
---

### Post by victorcrane on 2009-06-12
Howdy folks, I've recently installed unrar to make use of some music and movie files a friend sent me but when I extract the files it just leaves me with an empty folder. I can view the files in archive manger and even if I right click and select extract it shows the progress bar like it's extracting but then nothing happens. I've tried several folders and each time all I get is the folder itself with nothing in it. 

Am I being really dense? I've just come back to ubuntu after nine months with OpenSuse and that did all this business itself so I'm a bit lost. :)

---

### Post by Hospadar on 2009-06-12
Have you tried unrar-ing them by hand from the command line?

Maybe there's some error you aren't seeing that you'd be able to pick up on.

man unrar

at the command line for more info

You could also try the "free" (As in speech) version of unrar
either get unrar-free in synaptic and remove unrar, or simply ```
sudo apt-get remove unrar
sudo apt-get install unrar-free
```

---

