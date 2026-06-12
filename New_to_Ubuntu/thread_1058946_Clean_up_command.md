---
title: "Clean up command"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by burnetbj on 2009-02-03
Hello People

Several months ago someone had posted a command to clean up files that were unused for someone in another thread. I went along with it and it seemed to work great as after wards I only had one kernel showing in boot menu and what not. 

I since have lost the command somewhere, can anyone tell me what that command was.

Seems like it was something like one of the following but cant remember and they dont seem to work 

sudo apt-get auto upgrade 
sudo apt-get auto update
sudo apt-get auto purge 

Thanks

---

### Post by taurus on 2009-02-03
You mean something like

```
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by burnetbj on 2009-02-03
Thanks for the response

I did try the two commands suggested and I still have 3 kernel versions showing during boot...

Altho those seem very close to the command I am searching for, didnt seem to resolve the issue

Thanks tho

---

### Post by taurus on 2009-02-03
If you want to remove an old kernel, go into synaptic and **Search** for linux-image.  Then, remove the oldest one from there.

---

### Post by leonardo_neo on 2009-02-03
These are the commands commonly used to clean up.

> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

If you want to get rid of old kernels, then use the following tutorial...

> [http://www.youtube.com/watch?v=i7G91hIFyQI&eurl=http://video.google.com/videosearch?q=how%20to%20remove%20old%20kernel&oe=utf-8&rls=com.ubuntu:en-US:u](http://www.youtube.com/watch?v=i7G91hIFyQI&eurl=http://video.google.com/videosearch?q=how%20to%20remove%20old%20kernel&oe=utf-8&rls=com.ubuntu:en-US:u)

Beware for not to delete something essential. Also it is a good idea for not to delete the kernel which is last to the recent one.

Best of luck :)

---

### Post by burnetbj on 2009-02-03
Thank you kindly 

I appreciate all the help 

How could I ever leave this place :)

---

