---
title: "is a home partition right for me?"
date: 2009-03-08
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-03-08
basically 8.10 is the first time i've used ubuntu.  i have done a lot of customizing and would hate to have to lose that when i upgrade to the newer version of ubuntu next month.  basically i can download the ubuntu installer on my campus network much faster than i can at home so it would be much faster for me to do a clean install then going through the software channel.  would a home partition keep all my settings intact?  i really want to get the new filesystem

---

### Post by Kareeser on 2009-03-08
Tentatively, yes. Most settings are stored in your home directory, so separating home onto a different partition would make things easier.

There may be more minute differences, but for the most part, yes.

I'll wait for someone else to chime in.

---

### Post by mamamia88 on 2009-03-08
is it possible to just do a copy paste of your home folder from old installation to new installation?

---

### Post by Skripka on 2009-03-08
> **mamamia88 said:**
> is it possible to just do a copy paste of your home folder from old installation to new installation?

On new install all you would do is tell the Ubuntu installer to use your old /home partition for /home, but maske sure NOT to check the box  to format.

Having a seperate /home partition is the smart thing to do.

---

### Post by mamamia88 on 2009-03-08
cool thanks

---

### Post by mkvnmtr on 2009-03-08
I thinknusing a home partition is the thing to do. But when I install on another computer I just use the hidden files for the things that are important to me like .mozilla and .mozilla-thunderbird. I will usually put them in the new home before I have opened the apps. If I wait until after I have used the app I have to put the current file in the trash first. It is much quicker than using the whole home folder.

---

### Post by crunchfighter on 2009-03-09
I just performed a fresh install of 8.10 when I upgraded my HD.  I did a drag and drop of the /home folder and it worked great for most things.

That said, I still had to update my repos, install my programs, and some things like my TomBoy notes are still MIA.  

For the most part though, copying /home worked very well.

---

### Post by talsemgeest on 2009-03-09
> **mamamia88 said:**
> basically 8.10 is the first time i've used ubuntu.  i have done a lot of customizing and would hate to have to lose that when i upgrade to the newer version of ubuntu next month.  basically i can download the ubuntu installer on my campus network much faster than i can at home so it would be much faster for me to do a clean install then going through the software channel.  would a home partition keep all my settings intact?  i really want to get the new filesystem
Basically, yes. The easiest way to keep your setting when reinstalling Ubuntu is to have a separate home partition. If you are going to keep your existing home files, make sure you copy the hidden files and folders as well.

---

