---
title: "Please Explain how to use WINE"
date: 2011-05-28
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-28
Hi folks, can you please explain to me how to use WINE in an easy way?  I have a windows 7 hard drive, and want to run word 2010 off of it for example, but other programs as well.

Pls help.  Maybe there is site that has pictorials, but have not found it yet.

---

### Post by Idaho Dan on 2011-05-28
Have you tried playonlinux?

---

### Post by TAspr on 2011-05-28
> **Idaho Dan said:**
> Have you tried playonlinux?

No, how does that make it easier to use WINE, just curious?

---

### Post by computerandu on 2011-05-28
> **TAspr said:**
> Hi folks, can you please explain to me how to use WINE in an easy way?  I have a windows 7 hard drive, and want to run word 2010 off of it for example, but other programs as well.

Pls help.  Maybe there is site that has pictorials, but have not found it yet.

You can always google for it...
any ways ,,,here is a link to my blog-post...it explains with pics about installing applications with wine..
[http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/](http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/)

---

### Post by Idaho Dan on 2011-05-28
Hey TAspr,
all I know is that it is already set up to run a lot of programs without having to mess with wine. 
I noticed it listed ms office as one it runs so I thought it might help.
Also, have you tried libre office? I really like it.

---

### Post by 3rdalbum on 2011-05-28
1. You have to install the program within Wine; you can't just run an already-installed program from the Windows side of your disk.

2. Only about 20% of programs run in Wine, many of those do not work very well, so you should stick with Linux programs wherever possible. I believe MS Office 2007 is supported with Wine, though, so you might have some luck.

3. To install MS Office in Wine, insert your CD and find the "setup.exe" program on it. Open up a terminal and type the word 'wine ' (without the quotes) and press the space bar to leave a space character at the end. Now drag the "setup.exe" program to the terminal. Click the terminal window again to bring it to the front, and then press Enter.

---

### Post by sandyd on 2011-05-28
> **TAspr said:**
> Hi folks, can you please explain to me how to use WINE in an easy way?  I have a windows 7 hard drive, and want to run word 2010 off of it for example, but other programs as well.

Pls help.  Maybe there is site that has pictorials, but have not found it yet.

don't bother. office 2010 is severly crippled in WINE. Even when running Svn.
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=17336](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17336)

Use office 2007 -> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4992) (read the HOWTO).

P.S. Good idea to install in seperate WINEPREFIX to avoid contamination.

---

### Post by TAspr on 2011-05-29
I as well, tried to use the "MOZBACKUP" utility that will backup bookmarks, etc. through windows.  Have anyone ever tried this utility?

---

### Post by TAspr on 2011-05-29
> **computerandu said:**
> You can always google for it...
any ways ,,,here is a link to my blog-post...it explains with pics about installing applications with wine..
[http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/](http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/)

Thanks Alot!

---

### Post by TAspr on 2011-05-29
> **Idaho Dan said:**
> Have you tried playonlinux?

Well, I tried playonlinux, and got this error message. (pic is attached)

---

### Post by Mark Phelps on 2011-05-31
First of all, if you want detailed Wine-oriented help, you would do better posting in the Wine subforum instead of here.

Second, my own experience with Wine has been abysmal -- seeing as how it took them 3 years to finally get SOME of Office 2007 working with wine.

Finally, Wine is always behind in MS Products because MS doesn't make any internal info available, so the developers have to reverse-engineer the products as best they can.  I wouldn't expect any Office 2010 products to work with Wine for at least another 18 months.

---

### Post by abre on 2011-06-01
> **computerandu said:**
> You can always google for it...
any ways ,,,here is a link to my blog-post...it explains with pics about installing applications with wine..
[http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/](http://computerandu.wordpress.com/2011/04/10/how-to-install-windows-application-exe-on-linux-ubuntu-with-wine/)

i try your suggestion, but if i open properties, i cant choose allow executing file as program

---

### Post by computerandu on 2011-06-01
> **abre said:**
> i try your suggestion, but if i open properties, i cant choose allow executing file as program

You cannot see the option of allow executing file as program or you cannot click it..??

Comment on the blog so that I'll be aware of your comments...

---

### Post by abre on 2011-06-01
> **computerandu said:**
> You cannot see the option of allow executing file as program or you cannot click it..??

Comment on the blog so that I'll be aware of your comments...
i cant click on it

---

### Post by TAspr on 2011-06-02
> **Idaho Dan said:**
> Hey TAspr,
all I know is that it is already set up to run a lot of programs without having to mess with wine. 
I noticed it listed ms office as one it runs so I thought it might help.
Also, have you tried libre office? I really like it.

Yes, I have tried Libre and I think it an very good program for standard word processing, etc., good enough for me.

What do you mean when you say all I know is that [SIZE=3][I]it is already set up to run a lot of programs without having to mess with wine.?
[SIZE=1]
[/SIZE][/I][SIZE=2]I am a little confused as to when to use it or not.[/SIZE][/SIZE]

---

