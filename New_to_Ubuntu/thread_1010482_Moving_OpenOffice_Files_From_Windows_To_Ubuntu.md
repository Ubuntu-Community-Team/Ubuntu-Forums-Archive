---
title: "Moving OpenOffice Files From Windows To Ubuntu"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by mohab on 2008-12-13
Hi,

What is the easiest way to move my OpenOffice files from Windows Vista to Ubuntu? I have been trying Wubi and got so impressed I have decided to move over to Ubuntu within the next few days. 

As a test run, I emailed my open office files to my gmail account and tried to download the files in Ubuntu but got binfile and could not open it after many attempts. In Windows I opened to file from foxfire, but with Ubuntu I was only given the option of saving the files, and, again, could not get them to open in any of the programs I tried.       

My goal is to get out of Windows for many reasons,and I have discovered I can do all I need in Ubuntu. But, I have zero knowledge about working with Ubuntu and know nothing about commands or terminals, words I saw referenced in regard to bin files in other posts on this forum. 

Any suggestions would be appreciated.

---

### Post by Primefalcon on 2008-12-13
one way you could get a free file host and upload them to that and then download them again once your set up

for that try either

[http://www.badongo.com/](http://www.badongo.com/)

or 

[http://freespace.filefront.com](http://freespace.filefront.com)

---

### Post by linuxguymarshall on 2008-12-13
Here are some methods. Easiest ones first. Hardest ones last.


[LIST=1]
[*]Portable Media (Flash Drive, Portable hard drive, extra HDD, CD/DVD, etc.)
[*]Web Server (Read above)
[*]Transferring files in Ubuntu from windows (Need to install a NTFS reader, not hard but is harder than the other two)
[/LIST]

---

### Post by Epikuma24 on 2008-12-13
Burn them to a disk or put them on a flash drive
or duel boot them and click on places computer file system and look for where your files are ( recomended put in folder)

---

### Post by Primefalcon on 2008-12-13
well my first bet would of been a flash drive or such too but I figured since he was asking he doesn't have those options

---

### Post by gettinoriginal on 2008-12-13
Hi and welcome to Ubuntu !!  :p  Applications > Accesories > Terminal will bring up the terminal they are mentioning in posts and threads.  Most of the time, the command they give you can be copied from the thread and pasted into terminal to get the results.

I am not sure about the documents, but I will research it for you and get back to you on it.  :p

You also may want to bookmark this page, it is extremely helpful when changing from windows to ubuntu.

ttps://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/TransferringFilesAndSettings

---

### Post by richaoj on 2008-12-13
just copy them on to a thumdrive or burn them to cd (depending on how many there are -- i can't imagine you'd have so many to fill up a cd).  

You could also try an online backup service like dropbox . . . 

[www.getdropbox.com](www.getdropbox.com)

After you install, all you have to do is plug in the thumb drive, or put in the cd (or download and install dropbox).  and copy the files to your home folder.  

There is no difference in the filetypes between openoffice on windows and openoffice on linux.  There may be some formatting issues because of fonts, but you can easily fix that by installing the msft fonts later on.

---

### Post by Primefalcon on 2008-12-13
ahh yes I had forgotten about the fonts myself

go to your accessories panel and click on add/remove

in the search type "microsoft core"

you'll see the Microsoft core fonts come up just install that, and as said above the file types have no difference between them whatsoever. if tyou do have problems opening them it could be a permissions issue

hold alt and press F2 and in the pop up screen type the following

```
gksudo nautilus
```

use that to navigate to your files and then right click and select properties and then examine the permissions

note: This isn't the most efficient way but it is the most beginner friendly (aka graphical) method for overcoming what you asked

---

### Post by mohab on 2008-12-14
Thanks for all the helpful info. I can now figure this out with the great options you all have suggested.

---

