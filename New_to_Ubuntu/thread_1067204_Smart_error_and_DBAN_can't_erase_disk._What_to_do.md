---
title: "Smart error and DBAN can't erase disk. What to do?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by kramer65 on 2009-02-11
Hello,


I have been getting SMART errors for my hard disk for a while now. I finally got my hands on a new hard disk and wanted to send my old one back to samsung for the warranty.

Since I have quite some sensitive work related information on it I wanted to destroy all data on it. This brought me to Darik's Boot And Nuke, which I burned on cd and tried to run. 

When trying to nuke the disk however, I get this error:

```
DBAN finished with non-fatal errors.
This is usually caused by disks with bad sectors. 

Send the log file with all support requests.

Hardware clock operation... blabla
```

I know that there is something wrong with the disk since that is why I started all this. But I don't know what bad sectors are and the most important question is now:

How can I sucessfully nuke the disk so I can send it to the guarantee service?

---

### Post by NewJack on 2009-02-15
I just learned that the "Secure Erase" method is the best.  Check out this article: [http://blogs.zdnet.com/storage/?p=129](http://blogs.zdnet.com/storage/?p=129)

I haven't tried it personally, but recently found out about this from some security expert friends of mine.  They say it is better than DBan's because it writes at a lower level (more thorough).

Good Luck!

UPDATE: Actually, you can go direct to CMRR to grab the utility and also get the documentation.  [http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

---

### Post by kramer65 on 2009-02-15
Thanks for that tip. I downloaded the file, burned the iso to a disk, and booted it. It then gives some options to boot with or without EMM68 (or something). I tried all methods and it constantly says that it couldn't boot the autoexec, or I get a clean dos promtp: 
```
A:\>
```

Do you have any other ideas?

---

