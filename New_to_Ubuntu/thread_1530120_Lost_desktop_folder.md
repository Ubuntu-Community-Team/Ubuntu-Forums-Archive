---
title: "Lost desktop folder"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by fwin on 2010-07-13
Hi everyone,

I lost my desktop folder. I originally had 3 .txt files on my desktop then I decided to compress them to create a .zip file and everything worked well, I Left my .zip file on the Desktop. The next day when I tried to extract the files nothing happened, I could not extract the files  back to the desktop. I then tried to acces the Desktop via Places->Desktop and I got the following message:

Could not open location 'file:///home/r1/Desktop'
Error stating file '/home/r1/Desktop': No such file or directory

when I opened another folder that was in my desktop I noticed in the location bar that the path was:

/home/r1/kdenlive/Desktop/myfolder

So apparently my desktop folder moved to  the folder kdenlive while i was trying to extract the .txt files from the zip file. I tried to cut the desktop folder to put it back in:

/home/r1/

but the cut option is grayed out, so I had to copy it and now I have two desktops :

/home/r1/kdenlive/Desktop/

and

/home/r1/Desktop

How can i go back to NORMAL?, any help would be appreciated


By the way I use ubuntu 9.10

---

### Post by fwin on 2010-07-14
anyone?

---

### Post by samigina on 2010-07-14
After copy the Desktop folder back to /home/r1/ is everything working? If yes you should be able to delete the copy in /home/kdenlive. If you cant, try to do it like sudo user, you know, "sudo nautilus" in a terminal.

---

### Post by fwin on 2010-07-14
after copying it back to the /home/r1/ directory, it does not go back to normal because everytime i save something on my desktop it automatically saves it to the /home/kdenlive/Desktop folder. I have tried to use sudo to move it back to the /home/r1/ folder but it does not work, it only copies it.  

Thanks for the help samigina

---

