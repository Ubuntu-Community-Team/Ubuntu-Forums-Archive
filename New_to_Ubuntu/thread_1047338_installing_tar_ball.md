---
title: "installing tar ball"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by DarinB on 2009-01-22
i have had a problem since 7.10 now i am using 8.10 
i must be doing something wrong
i download a tar ball ie gnormalize-0.63.tar.gz
i cd to Desktop
then: tar -xvzf gnormalize-0.63.tar.gz
no problem
then cd into gnormalize-0.63.
no problem
sudo ./configure
i get **file not found** **(((((this is where i am stuck this time)))))**
or when i get to 
**make** i get the same thing **file not found**
this has happened with many tar balls
i just gave up and only install deb or ubuntu packages.
i still do not know what is going on
i always cut and paste the commands an am careful to check 
the farthest i have gotten is install followed by the error 
file not found
i am curious why it is so difficult and how can i learn about what i am doing wrong if at all.

---

### Post by gjoellee on 2009-01-22
this is how to install gnormalize:
```

tar zxvf gnormalize-version.tar.gz
cd gnormalize-version/
./install
```

---

### Post by cmnorton on 2009-01-22
What about sudo -i, and then enter cd to the desired directory. Otherwise, you could submit a shell script to sudo, and let it do all that, but you would have to write the script.

---

### Post by avtolle on 2009-01-22
You should always check the extracted files for a "README" or "INSTALL" file before going further; usually, there will be instructions on what you need to do to install, as apparently there were for gnormalize.

---

### Post by cmnorton on 2009-01-22
> **avtolle said:**
> You should always check the extracted files for a "README" or "INSTALL" file before going further; usually, there will be instructions on what you need to do to install, as apparently there were for gnormalize.

Even better.

---

### Post by Nepherte on 2009-01-22
Apart from reading that readme file, never run configure and make with sudo privileges. It's not necessary. Only make install requires sudo privileges depending depending on what --prefix= you used in configure. So
```

./configure
make
sudo make install

```

---

### Post by DM was on fire! on 2009-01-22
> **avtolle said:**
> You should always check the extracted files for a "README" or "INSTALL" file before going further; usually, there will be instructions on what you need to do to install, as apparently there were for gnormalize.

Yep.

Or alternatively, right on the [Gnormalize](http://gnormalize.sourceforge.net/) page, under the install link, is the instructions. :P

(No worries though, I've done that sometimes. :D)

---

### Post by darksideforge on 2009-01-22
> **gjoellee said:**
> this is how to install gnormalize:
```

tar zxvf gnormalize-version.tar.gz
cd gnormalize-version/
./install
```

Are those three separate lines of code or just two? Also, will this procedure work for all tarballz or just for the gnormalize (i'm referring to the part after ~cd ((changing the directory)))?

In other words, if the name of the original tar was
"makemeajockey.tar.gz" then i would simply type

```
tar zxvf makemeajockey.tar.gz
cd makemeajockey/
./install/
```

???  Or are there other steps to it?

Also, under DarinB's orginal question, he lists using "-zxvf" (with a minus sign in front of the four letters) and that's where I've been getting an error with some of my stuff....what's up with that?

Sorry for being such a noob.

---

### Post by Gullstad on 2009-01-22
Usally it's a readme file with most tarballs :)

---

### Post by avtolle on 2009-01-22
> **darksideforge said:**
> Are those three separate lines of code or just two? Also, will this procedure work for all tarballz or just for the gnormalize (i'm referring to the part after ~cd ((changing the directory)))?

In other words, if the name of the original tar was
"makemeajockey.tar.gz" then i would simply type

```
tar zxvf makemeajockey.tar.gz
cd makemeajockey/
./install/
```???  Or are there other steps to it?

Also, under DarinB's orginal question, he lists using "-zxvf" (with a minus sign in front of the four letters) and that's where I've been getting an error with some of my stuff....what's up with that?

Sorry for being such a noob.

If the extracted directory is makemeajockey, then yes, that cd command you posted is correct. Once the tarball is extracted, there will be a directory created, with its name, and that is the name to use when executing the cd command. On the question you had about ./install, it depends on how the tarball was made, thus the need to read the README or INSTALL file, or the directions on the download site, to see what commands are needed. Sometimes, there will be an install script; sometimes, one must do make then sudo make install; it varies.

With reference to your question about the hyphen (or "minus sign"), I don't use it. Someone with a bit more knowledge might be able to clear this up for both of us.

---

### Post by darksideforge on 2009-01-22
Now I have a new issue.
a) I downloaded Flock 2.0.3 to my desktop.
b) I used Ark to extract the tar ball to my desktop.
c) I opened Applications>Accessories>Terminal
d) I attempted to change directories to get to my desktop by using the CD command. Here's what I'm getting:

```

name@name:~$ cd desktop
bash: cd: desktop: No such file or directory
name@name:~$ 
```


My plan was:

```
$: cd desktop
$: tar xvzf flock-2.0.3.en-US.linux-i686.tar.bz2
$: cd flock/
$: ./install/
```

However, I'm not sure if the third line will work (even though that's the name of the folder that was created on my desktop when I extracted to the desktop via GUI). But, that was my plan after hearing the advice above, BUT, now there's this problem where I can't cd to the desktop....what the heck am i doing wrong?

---

### Post by darksideforge on 2009-01-22
Using something from another thread, I thought maybe I was in the wrong directory, so I tried to cd into a /home directory and un-tar from there. Wrong.

After that, I moved the downloaded tar file TO the /home folder and THEN tried to un-tar. Here was the response:

```
name@name:/home$ tar xvzf flock-2.0.3.en-US.linux-i686.tar.bz2
tar: flock-2.0.3.en-US.linux-i686.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
name@name:/home$ cd darkside
name@name:~$ tar xvzf flock-2.0.3.en-US.linux-i686.tar.bz2

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
name@name:~$ 
```

I'm going to go out on a limb and assume, amongst other things, that ".bz2" files cannot be un-tarred and therefore cannot be installed in this fashion....?

Also, it should be remembered that I used the Ark to extract the downloaded tar to my desktop and when I did so, another folder (in addition to the tarball) was created and is simply called "Flock".

New suggestions anyone?

---

### Post by darksideforge on 2009-01-22
And one other issue, as far as someone talking about the ReadMe.txt files, the only one included is a short one-liner that gives a website for Flock's most-recent updates. There *is* no Install .txt file.

Can I safely assume that I shouldn't have unzipped the bzip2 file? Or at least, maybe I unzipped it in the wrong place?

How about this: has anyone successfully downloaded the .tar for FLOCK and installed it?

---

### Post by snova on 2009-01-22
> **darksideforge said:**
> ```

name@name:~$ cd desktop
bash: cd: desktop: No such file or directory
name@name:~$ 
```

Close. But Linux is case-sensitive, and Desktop is capitalized.

> **darksideforge said:**
> ```

name@name:~$ tar xvzf flock-2.0.3.en-US.linux-i686.tar.bz2

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
name@name:~$ 
```

I'm going to go out on a limb and assume, amongst other things, that ".bz2" files cannot be un-tarred and therefore cannot be installed in this fashion....?

It can. Bzip2 is just another way to compress files. It's a bit better than Gzip, but also slower (it's a tradeoff...).

In this case, it can be solved simply by replacing "xvzf" with "zv**j**f". The **j** refers to Bzip2.

> Also, it should be remembered that I used the Ark to extract the downloaded tar to my desktop and when I did so, another folder (in addition to the tarball) was created and is simply called "Flock".

Well, why didn't we just do that in the first place? :P

> **darksideforge said:**
> And one other issue, as far as someone talking about the ReadMe.txt files, the only one included is a short one-liner that gives a website for Flock's most-recent updates. There *is* no Install .txt file.

Hmm, that's unusually empty. Can you give me a listing of what that directory contains? I've a feeling you don't have to compile from source, it looks like a binary distribution.

---

### Post by darksideforge on 2009-01-23
Snova,
First and foremost: THANK YOU!!! Secondly, thanks again for taking the time to explain all this to a newbie. Third: you're telling me that **zvjf** is actually a way to un-tar the tar ball, is that correct? So...now that Flock has been extracted/unzipped/de-compiled and has its own folder on my **D**esktop ;) how will I install it from here? I can't find anything in a GUI format and nonetheless I'd like to learn how to do it via CLI, even though I realize that may be a little above my ability at this point. One last question for now and I'll leave you alone for a bit: in addition to the case-sensitivity, I've noticed (after viewing some other code on other threads) that sometimes --but only *some*times-- a "period" is placed in front of certain commands....any particular regimen to follow in terms of when to use one and when not to? (In other words, which type of commands use it and which ones don't?)?
Thanks Again!!

---

### Post by dmizer on 2009-01-23
Hello, and welcome to Ubuntu!

Please, whatever you do, try to avoid installing packages from source, it can cause problems and things often stop working after updates.

Always spend some time searching for a Debian package (or deb), or search google for something like:
package name ubuntu
or
package name site:ubuntuforums.org

I found this: [http://tnerd.com/2008/10/19/flock-20-how-to-install-flock-2-on-ubuntu-in-2-easy-steps/](http://tnerd.com/2008/10/19/flock-20-how-to-install-flock-2-on-ubuntu-in-2-easy-steps/)

1) download debian package
2) double click on Debian package and Ubuntu takes care of everything for you while you twiddle your thumbs.

---

### Post by 3rdalbum on 2009-01-23
Flock is distributed as a binary anyway, so once it's extracted you literally just double-click on the Flock icon.

I'm not sure why people are telling you how to extract tarballs from the command-line. File Roller (the archive manager that comes with Ubuntu) works well and you don't need to remember command-line switches or think about what type of archive you are extracting.

---

### Post by handydan918 on 2009-01-23
> **darksideforge said:**
> Third: you're telling me that **zvjf** is actually a way to un-tar the tar ball, is that correct? No! Some tarballs are gzipped and some are bzipped. It depends on which kind you have!  zvjf is correct for bzip; xzvf is correct for gzip.>  I've noticed (after viewing some other code on other threads) that sometimes --but only *some*times-- a "period" is placed in front of certain commands....any particular regimen to follow in terms of when to use one and when not to? (In other words, which type of commands use it and which ones don't?)?
Thanks Again!!
Generally, the only time you have to prepend a command with a ./ is when it is not a command that "lives" in your normal path. If you are trying to execute a file you have placed in /home, it will need the "./" to tell the shell to execute it.

---

### Post by oldos2er on 2009-01-23
To run Flock, run /somedirectory/flock/flock-browser

---

### Post by darksideforge on 2009-01-23
Just a quick note and then I'll respond to everyone who's been gracious enough to respond to me (and in the hopes of helping someone else down the line.

While going through and taking Screenshots to post on here so that you guys could *see* what I'm seeing via the GUI, I saw an icon in the Flock folder, VERY unassuming icon i might add, that said simply: flock-browser. I double-clicked on it and guess what? Yep....it started right up and took me to the flock homepage.

Can you guys believe that after all I've been through it was that simple?

Okay, last one to call me a moron gets NO coffee today!!!:popcorn:

---

### Post by darksideforge on 2009-01-23
> **oldos2er said:**
> To run Flock, run /somedirectory/flock/flock-browser

I knew there had to be a way to do this as "run" is a pretty common command, but I wasn't even sure I had the installation down to run anything. I might should've tried this first...THANKS!!!

---

### Post by darksideforge on 2009-01-23
> **snova said:**
> Close. But Linux is case-sensitive, and Desktop is capitalized.



It can. Bzip2 is just another way to compress files. It's a bit better than Gzip, but also slower (it's a tradeoff...).

In this case, it can be solved simply by replacing "xvzf" with "zv**j**f". The **j** refers to Bzip2.



Well, why didn't we just do that in the first place? :P



Hmm, that's unusually empty. Can you give me a listing of what that directory contains? I've a feeling you don't have to compile from source, it looks like a binary distribution.



Via the GUI, here's the message that comes up after double-clicking on the ReadMe.txt:
```

Information, including recently fixed bugs, and outstanding

issues, can be found online at

http://www.flock.com/products/flock/releases/latest/
```

---

### Post by darksideforge on 2009-01-23
> **dmizer said:**
> Hello, and welcome to Ubuntu!

Please, whatever you do, try to avoid installing packages from source, it can cause problems and things often stop working after updates.

Always spend some time searching for a Debian package (or deb), or search google for something like:
package name ubuntu
or
package name site:ubuntuforums.org

I found this: [http://tnerd.com/2008/10/19/flock-20-how-to-install-flock-2-on-ubuntu-in-2-easy-steps/](http://tnerd.com/2008/10/19/flock-20-how-to-install-flock-2-on-ubuntu-in-2-easy-steps/)

1) download debian package
2) double click on Debian package and Ubuntu takes care of everything for you while you twiddle your thumbs.

Where do you find this stuff and why couldn't you have told me about it 2 weeks ago? LoL!! Thank you!!:D:D:D

---

### Post by darksideforge on 2009-01-23
> **3rdalbum said:**
> Flock is distributed as a binary anyway, so once it's extracted you literally just double-click on the Flock icon.

I'm not sure why people are telling you how to extract tarballs from the command-line. File Roller (the archive manager that comes with Ubuntu) works well and you don't need to remember command-line switches or think about what type of archive you are extracting.

People are telling me how to extract tarballs because I didn't know how and I asked them...they interrupted the other poster in this thread (after solving his/her problem first) to explain the difference between gzips and bzip2's to me.  The problem was that there WAS no "Flock" icon...just an extraction folder on my desktop full of icons that didn't look in the least relevant or obvious...it was only by luck that I double clicked on a really ambiguous "flock-browser" icon and ended up with Install options.  Also, nobody that I asked originally had Flock, so nobody knew what kind of distro or program it was.

Thanks for the clarification though....I definitely appreciate you taking time to answer me...I'm still a total Newb so every little bit of advice, guidance, or direction I get is MOST appreciated!!

---

### Post by darksideforge on 2009-01-23
> **handydan918 said:**
> No! Some tarballs are gzipped and some are bzipped. It depends on which kind you have!  zvjf is correct for bzip; xzvf is correct for gzip.
Generally, the only time you have to prepend a command with a ./ is when it is not a command that "lives" in your normal path. If you are trying to execute a file you have placed in /home, it will need the "./" to tell the shell to execute it.

Thanks! I think I need to find a program that will compile all of these answers for me and put them into an encyclopedic journal!!   :p

---

### Post by snova on 2009-01-23
> **darksideforge said:**
> Snova,
First and foremost: THANK YOU!!!

:D

> Third: you're telling me that **zvjf** is actually a way to un-tar the tar ball, is that correct?

It all depends on the type of compression used. Each letter here does something different.

v = Verbose. It prints the name of each file it unpacks.
f = File. Basically, tar can operate on archives that aren't files... like tape drives, I think. I'm not really sure, but for the most part, this'll always be here.
z = Gzip compression (.gz files). This is both when you're creating or unpacking archives, or anything else really.
j = Bzip2 compression (.bz2 files). Same note.

The z and j here conflict, so I'm going to assume that one of them should be replaced with an x.

x = eXtract. It's the operation to perform on the archive. Other operations include Create, Update...

The trick to tar is to understand that it's **just** an archiver. It does no compression. Gzip and Bzip2, conversely, are only compressors. They do no archival, they take exactly one file as input and produce one file as output. tar merely makes the combination of these two tools easier to manage by doing the compression/decompression automatically.

---

### Post by darksideforge on 2009-01-23
WoW! Just killer information!!  Do you have a website you recommend for me to go and learn more of this type of thing?

I do have another question, but it's pretty specific so I'm going to start a new thread describing it and then I'll come back here and post a link to it.

Thanks again!

---

### Post by handydan918 on 2009-01-23
> **darksideforge said:**
> WoW! Just killer information!!  Do you have a website you recommend for me to go and learn more of this type of thing?

I do have another question, but it's pretty specific so I'm going to start a new thread describing it and then I'll come back here and post a link to it.

Thanks again!

Virtually every command in the inventory is documented in the man pages. for example, try ```
man tar
```

It will become evident that the man pages are not the friendliest way to figure things out "from zero", but they are useful, nonetheless.

---

### Post by darksideforge on 2009-01-23
Here is the link to the new thread I started specifically regarding the Flock Installation:

[http://ubuntuforums.org/showthread.php?p=6606072#post6606072]("http://ubuntuforums.org/showthread.php?p=6606072#post6606072")

---

### Post by darksideforge on 2009-01-23
> **dmizer said:**
> Hello, and welcome to Ubuntu!

I found this: [http://tnerd.com/2008/10/19/flock-20-how-to-install-flock-2-on-ubuntu-in-2-easy-steps/](http://tnerd.com/2008/10/19/flock-20-how-to-install-flock-2-on-ubuntu-in-2-easy-steps/)

1) download debian package
2) double click on Debian package and Ubuntu takes care of everything for you while you twiddle your thumbs.


Just a quick note to say thank you again; I used this link and it worked EXACTLY like the instructions said it would....Ha! Twiddling my thumbs for 45 seconds during the download/install was exactly right!!  :D

---

### Post by dmizer on 2009-01-23
> **darksideforge said:**
> Where do you find this stuff and why couldn't you have told me about it 2 weeks ago? LoL!! Thank you!!:D:D:D
Just like I said, I searched for: flock browser deb package: [http://www.google.com/search?hl=en&q=flock+browser+deb+package&btnG=Search](http://www.google.com/search?hl=en&q=flock+browser+deb+package&btnG=Search) the link I posted is the third search result. The first search result is a direct link to the flock deb package itself.

> **darksideforge said:**
> Just a quick note to say thank you again; I used this link and it worked EXACTLY like the instructions said it would....Ha! Twiddling my thumbs for 45 seconds during the download/install was exactly right!!  :D
Now THAT is how it's done in Linux :) I can't remember the last time I had to install something from source.

---

