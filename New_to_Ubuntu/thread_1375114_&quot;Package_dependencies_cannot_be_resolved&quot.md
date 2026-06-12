---
title: "&quot;Package dependencies cannot be resolved&quot;"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by juliarain on 2010-01-07
I'm trying to install Wine (Version 1.1.35-0ubuntu1) from the Ubuntu Software Center. I click "Install," and as soon as it starts loading, it gives me this error message: 
[INDENT]> Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.[/INDENT]How do I find out what software packages I am missing? 

I have Ubuntu 9.10 Karmic. 

Since I'm sure someone will berate me for wanting to run Windows applications in Linux, let me explain why I am doing this. I need Wine to install an "Internet Explorer for Linux" package I have downloaded. My employer's website doesn't work right with Firefox, especially in the scheduling / appointment manager part, and I would also like to use Internet Explorer for web-design purposes. 

Thanks for your help, 

- Julia

---

### Post by philinux on 2010-01-07
Just tried this and it installed fine on karmic. 

Try this from a terminal.

```
sudo apt-get install wine1.2
```

Post back any errors it spits out. By the way this is the beta version.

---

### Post by juliarain on 2010-01-07
It worked. You're awesome; thanks for your help! :D

---

### Post by juliarain on 2010-01-07
Just kidding... Wine installed fine, but when I tried to install the Internet Explorer package, it gave me this error, via pop-up: 
[INDENT]> The program rundll32.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience. 

This can be caused by a problem in the program or a deficiency in Wine. You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application. 

If this problem is not present under Windows and has not been reported yet, you can report it at [http://bugs.winehq.org](http://bugs.winehq.org). [/INDENT]After that, I tried to install an updated version of Wine (1.1.35), and the terminal told me I didn't have the right flex package: 
[INDENT]> checking for flex... no
configure: error: no suitable flex found. Please install the 'flex' package. [/INDENT]So I downloaded Flex, tried to install it, then got this error message after running "./configure": 
[INDENT]> configure: error: GNU M4 1.4 is required[/INDENT]So being myself, I went and tried to install that after downloading it from the internet. I got through the "make" command, and then got this after trying "make install": 
[INDENT]> (starting ... lines back)
/usr/bin/install: cannot create regular file '/usr/local/bin/m4': Permission denied
make[3]: *** [install-binPROGRAMS] Error 1
make[3]: Leaving directory '/home/julia/Downloads/m4-1.4.13/src'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory '/home/julia/Downloads/m4-1.4.13/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory '/home/julia/Downloads/m4-1.4.13'
make: *** [install] Error 2[/INDENT]?!?!?!?!?!?!?!?!?

---

### Post by SEECo on 2010-08-29
Hi, i can tell you how to resolve this problem because i also got the same problem in ubuntu  LTS Lucid Lynx. The thing you have to only do is download a run32.dll file extract it somewhere in your computer (i recommend desktop) the replace it in /wine/windows/system32. Then restart your computer and try installing it again.

---

### Post by SEECo on 2010-08-29
After doing that please reply to me that is this methed worked

---

### Post by QLee on 2010-08-29
> **SEECo said:**
> After doing that please reply to me that is this methed worked
SeeCo, please note that you replied to a post from Jan 7th, the OP might not be reading the forum these days so you might not get a reply.

---

### Post by SEECo on 2010-08-30
It's ok no problem. Beacause i am very new to this thing and very also  very new to ubuntu. So i joined ubuntu forums to learn something new. And by the way your are not that to whom i sent that reply

---

### Post by abusalem on 2010-08-31
I am encountering the same problem but with Gnome. What is the code for it ?

---

### Post by abusalem on 2010-08-31
I tried to install gnome using the terminal with the code sude apt-get install gnome and the following message came up :
some packages could not be installed 
broken packages 

what packages am I missing ? help please !

---

