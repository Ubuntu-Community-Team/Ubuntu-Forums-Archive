---
title: "Help with using Jigdo..."
date: 2010-04-09
forum: New to Ubuntu
---

### Post by BugBuster on 2010-04-09
Hello,
Installed the Ubuntu 10.04 Beta2 today and so far everything seems great!!

Now since I will be updating my ubuntu installation when updates are available, by the time 10.04 final is released , I will be having all the packages that are supposed to be on the final.iso in my /var/cache/apt/archives.

So can I make jigdo use these packages in the local cache + the files on the beta iso that I have to build the latest iso.

Or will jigdo have to download all the needed packages from the ubuntu mirrors?

Note: Bandwidth is important for me as I am on a limited broadband connection

---

### Post by nixclusive on 2010-04-09
Just supply the path /var/cache/apt/archives to jigdo and it should not re-download unchanged files. :)

---

### Post by BugBuster on 2010-04-09
> **nixclusive said:**
> Just supply the path /var/cache/apt/archives to jigdo and it should not re-download unchanged files. :)

Thanks for replying. However jigdo prompts for path only once and there I have to give the path of the loop mounted previous iso file like "/media/cdrom". Where should I give the additional path /var/cache/apt/archives?

---

### Post by BugBuster on 2010-04-10
I think I found what I was looking for. Posting here as it may help someone.

[http://atterer.net/jigdo/debian-jigdo-mini-howto/x532.html#MORE-ABOUT-SCAN](http://atterer.net/jigdo/debian-jigdo-mini-howto/x532.html#MORE-ABOUT-SCAN)

I have not personally tried it as of now, but will report when I actually do so. Cheers!

---

