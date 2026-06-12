---
title: "Problem when changing home folder locations"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by AlNaimi on 2010-03-15
Hi every one....
Every time i tried to change home folder locations by editing:
gedit ~/.config/user-dirs.dirs
And save it...
I works fine for few time, But after some rebooting, it go back again as original...
What should i do to prevent that?

Thanks

---

### Post by Steven_S on 2010-03-15
As a newbie, I was just reading this topic: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Did you check there?

---

### Post by chaanakya_chiraag on 2010-03-15
That's more for changing the partition on which your home directory is located.  From what I understand of the question, AlNaimi wants to change the *folder* which is used as the home folder.  Is that right AlNaimi?

---

### Post by AlNaimi on 2010-03-15
Yes, chaanakya_chiraag....
Not the whole Home folders, just...
Documets, download,...etc...
Is it a bug with ubuntu?
Thanks

---

### Post by oldfred on 2010-03-15
Have you tried linking them?

Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of blog
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

mount data and link folders into home
ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents
   ln -s /usr/local/fred/data/Pictures
etc for every folder

---

### Post by chaanakya_chiraag on 2010-03-15
I wonder if you could use the ```
usermod
``` command to change the home folder for a user...  I'll look into it when I get home.

---

### Post by AlNaimi on 2010-03-15
Thanks oldfred & you too chaanakya_chiraag
> Have you tried linking them?
yes, I have... 
It work, but it is workaround solution...Thanks

maybe usermod code will do something...
Thanks to you guys

---

### Post by chaanakya_chiraag on 2010-03-15
What you want is ```
usermod --home --move-home /home/WHATEVER
``` where WHATEVER is the name of the desired home directory.

---

