---
title: "Disc space problem"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by sho.hobbit on 2009-05-14
Hello,, I download ubuntu on my computer using WUBI and its working amazingly. I have it with windows vista., which i scarcely use nowadays, apart from one problem.
 
In ubuntu the program shows my disc space to be only 60 MB"s but in windows I have 16 Gb's. My hard disc is 500 GB's without any partition's, Maybe this is the problem.?
 
I have no clue as to what is the problem, I cant download anything on ubuntu since it shows lack of disc space, so I have to keep coming back to vista to download stuff and then go back to use it on ubuntu, completely messed up! It downloads perfectly well on vista, Yesterday I downloaded 4 movies so I guess there is no problem there.
 
Please help, I REALLY BLOODY HATE WINDOWS NOW!
 
P.S- Ubuntu ROCKS!!

---

### Post by bacardiandwatermelon on 2009-05-14
Is this what you are after?

[http://ubuntuforums.org/showthread.php?t=1149604&highlight=wubi+resize]("http://ubuntuforums.org/showthread.php?t=1149604&highlight=wubi+resize")

---

### Post by drs305 on 2009-05-14
When you install wubi you have to designate a *file* size. I emphasize that it is a *file size* because wubi is a file *inside* windows. Once wubi is installed, you can't really increase the size of wubi. So it is probably reporting the remaining space within the wubi install.

You can move some of the files *outside* of wubi or you can move your wubi installation into a real partition of its own using LVPM. 

LVPM:  [http://lubi.sourceforge.net/lvpm.html]("http://lubi.sourceforge.net/lvpm.html")

Here is a link to the wubi FAQ: 
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

### Post by Niniel on 2009-05-14
You mean in Windows you have 16 GB free, and in Ubuntu only 60 MB?
Since you claim not to have any partitions, I suspect you installed Ubuntu from within Windows with wubi. I don't know how to resize the wubi disk - you may want to check the [wubi documentation]("https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b") - but if you really like Ubuntu, maybe it's time for you do do a "proper" installation on its own partition. 
For that I recommend you delete as much as you can from your Windows installation - including things you've downloaded but don't really need anymore (and don't forget to empty the temp directories) - and then run the disk defragmenter a couple of times. Then use the Vista disk tool to shrink your Windows partition to free up at least 5 - 10 GB for Ubuntu. Unless you plan to install a lot of programs you don't really need more since you can download media files to your Windows partition. 
Then burn yourself an Ubuntu live CD and install from there into the freed-up space (make sure not to use the whole disk!).

Btw, why are you "hating" Windows now? There's not need for such declarations, we'll help you even if you prefer it to Linux.

---

### Post by mprince on 2009-05-14
> **sho.hobbit said:**
>  
Please help, I REALLY BLOODY HATE WINDOWS NOW!
 
P.S- Ubuntu ROCKS!!

Wubi is a great way to try ubuntu (it's how I got started) but maybe you should start thinking about a total ubuntu install and then say goodbye to windows.

---

### Post by sho.hobbit on 2009-05-14
> **Niniel said:**
> You mean in Windows you have 16 GB free, and in Ubuntu only 60 MB?
Since you claim not to have any partitions, I suspect you installed Ubuntu from within Windows with wubi. I don't know how to resize the wubi disk - you may want to check the [wubi documentation]("https://wiki.ubuntu.com/WubiGuide#head-fda2b476cbe51b911313b25d55e6bf70c6134b2b") - but if you really like Ubuntu, maybe it's time for you do do a "proper" installation on its own partition. 
For that I recommend you delete as much as you can from your Windows installation - including things you've downloaded but don't really need anymore (and don't forget to empty the temp directories) - and then run the disk defragmenter a couple of times. Then use the Vista disk tool to shrink your Windows partition to free up at least 5 - 10 GB for Ubuntu. Unless you plan to install a lot of programs you don't really need more since you can download media files to your Windows partition. 
Then burn yourself an Ubuntu live CD and install from there into the freed-up space (make sure not to use the whole disk!).
 
Btw, why are you "hating" Windows now? There's not need for such declarations, we'll help you even if you prefer it to Linux.
 
Bro, thanx a lot for your help, I think this is probably the best way to solve the problem. I will do this for sure.
But man, if you only knew what Ive been thru using windows, you probably would start hating it too. But i see your point and I will less provocative from now on.

---

