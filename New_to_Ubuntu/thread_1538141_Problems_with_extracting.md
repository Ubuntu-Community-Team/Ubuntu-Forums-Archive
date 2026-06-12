---
title: "Problems with extracting"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Truemedia on 2010-07-24
Hi, Iv'e just over the past few days converted over most of my computer needs from windows vista to the latest ubuntu using wubi for a dual boot.

Iv'e only had a few minor quickly solvable problems so far, and I'm more than impressed with how much ubuntu can do (my mouse thats only supposed to work on windows or mac even works).

As a web developer it was a priority for me to install a web server on ubuntu and even though I had problems with installing xampp on windows before I gave it another shot. Took a few times to get the commands right in terminal but I think everything is setup ok. Although I have a problem at the moment with getting files onto the server. 

I am trying to extract a couple of website based software distributions in zips and tar.bz2's (phpbb, joomla, moodle, wordpress, prestashop) but it says access denied when I try to use the archive manager. With terminal it keeps telling me that the file or directory doesn't exist with all the combinations of code i've tried.
**Example:**  ```
tar xvfz phpBB-3.0.3-PL1.tar.bz2 -C /opt/lampp/htdocs
```

I've even tried combinations of **cd** before hand and it's getting more confusing and frustrating. To make things simple I wanted to use the archive manager or terminal to extract directly from my downloads folder, but I just can't understand how to make this work from what I've already tried. Can someone please tell point me to a solution or correct me on the best way to do this thanks :).

---

### Post by lloyd_b on 2010-07-24
You have two problems that I see.

First off, when using the "f" option to specify the file, the file name *must* be the next thing immediately after the "f".  So in your example, it's trying to find a file named "z" (which doesn't exist).

Another problem you'd have encountered is that the "z" option invokes the "gzip" program to decompress the file, but "gzip" doesn't handle "bz2" archives (archives compressed with gzip typically end in "tar.gz" or "tgz").  For "bz2" files, you need to give it the "j" option instead.

Try this command line:```
tar jxvf phpBB-3.0.3-PL1.tar.bz2 -C /opt/lampp/htdocs
```
This assumes that the file "phpBB-3.0.3-PL1.tar.bz2" is in the current directory, and will be unpacked to the directory "/opt/lampp/htdocs". 

Lloyd B.

---

