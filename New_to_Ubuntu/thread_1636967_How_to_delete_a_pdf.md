---
title: "How to delete a pdf"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by nu2this2 on 2010-12-03
Really new to 10.10. First time I ever attempted to create a pdf and think I fouled up.

I pasted an article to Open Office and saved the file. Since I was only testing the procedure I only pasted a small amount of the article, perhaps 1-2 pages. I clicked the pdf icon and it exported the file to the gallery. When I tried to open the file all I saw was symbols and lines and arrows etc. To make matters worse I saw in the lower left corner 1 of 1334 pages!!!

I can't seem to delete or remove this file. Is there anything I can do? Does Ubuntu 10.10 have a function similar to "restore your computer to an earlier time" as is found in Windows?

Any help would be greatly appreciated.

---

### Post by thomas144 on 2010-12-03
Hey there,
I think I can help.This probably isn't the normal way to do this, but it should work anyway. Go to Places > Home Folder on your top panel. Nautilus (AKA File Browser) should open up. When it does, hit Ctrl + H. This should reveal a whole lot of folders with names starting with dots. Go into .openoffice.org. What do you see in there?

P.S. Ubuntu doesn't have an option to restore your computer to an earlier time like Windows does.
Adding: I'm not sure what the gallery is in OpenOffice, but this should work.

---

### Post by libssd on 2010-12-03
> **nu2this2 said:**
> Really new to 10.10. First time I ever attempted to create a pdf and think I fouled up.

I pasted an article to Open Office and saved the file. Since I was only testing the procedure I only pasted a small amount of the article, perhaps 1-2 pages. I clicked the pdf icon and it exported the file to the gallery. When I tried to open the file all I saw was symbols and lines and arrows etc. To make matters worse I saw in the lower left corner 1 of 1334 pages!!!

I can't seem to delete or remove this file. Is there anything I can do? Does Ubuntu 10.10 have a function similar to "restore your computer to an earlier time" as is found in Windows?

Any help would be greatly appreciated.
I have never experienced anything like that with the Export as PDF function of OO3. 

I assume that somewhere you see a file icon. What happens when you right-click on it and choose Properties? What happens if you right-click, and choose Move to Trash?

If you truly can't delete the file using the graphical user interface, you could open a terminal window and try deleting the file using sudo (which gives you temporary superuser privileges, for which you must enter your password), but I suspect from your problem description that you might not be comfortable with that, but here's an example anyway. 

I have a file on my desktop called Zen.pdf that I'm going to delete at the command line.

Applications > Accessories > Terminal

```
libssd@libssd-10:~$ cd Desktop
libssd@libssd-10:~/Desktop$ ls -l Zen*
-rwxr-xr-x 1 libssd libssd 1449193 2010-08-15 21:20 Zen.pdf
libssd@libssd-10:~/Desktop$ sudo rm Zen.pdf
[sudo] password for libssd: 
```

The file is now gone:
```
libssd@libssd-10:~/Desktop$ ls -l Zen*
ls: cannot access Zen*: No such file or directory
```

Hope this helps; if not, we need more information from you.

---

