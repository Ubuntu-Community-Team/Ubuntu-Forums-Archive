---
title: "Where are my old folders/files?"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by H4Marine on 2010-07-19
Installed Ubunto on two systems, should I be able to access data files (word, excel,pdf,jpeg etc) when running Ubunto that are already on the machine in My documents and sub folders? I can't find them anywhere, so next step I tried to load them into Ubunto (my docs) it said there was not enough room? the disc has plenty of space but ubunto seems to have only given the my documents folders a few Mb??? 

Otherwise I like it, and should I junk windows completely or is it worth keeping as an alternative?

Thanks

Neil

---

### Post by valbaca on 2010-07-19
I'm not sure if this is the same dual-bootin with Wubi, but everytime I've done a true dual-boot (windows first, ubuntu second **not **using Wubi) the Windows drive shows up just fine in the file browser. It's not mounted by default, but clicking on it asks for sudo password and you're able to browse the windows drive just like normal.

---

### Post by Paqman on 2010-07-19
> **H4Marine said:**
> I can't find them anywhere


Go to Places on your top panel, your Windows partition will be listed as XX MB Volume. Click to open it and you should be able to browse through the Windows file structure to your documents. If you installed with Wubi, you'll have to look in /host.

> ubunto seems to have only given the my documents folders a few Mb??? 

When you say your documents folder in Ubuntu, what do you mean? Is it your home folder (ie: go to Places and click on your username)

> 
Otherwise I like it, and should I junk windows completely or is it worth keeping as an alternative?


Depends if you have any Windows apps you still need to use. Also, if you don't have a disk to reinstall Windows in case you need it then it'd probably be best to keep it for now.

---

