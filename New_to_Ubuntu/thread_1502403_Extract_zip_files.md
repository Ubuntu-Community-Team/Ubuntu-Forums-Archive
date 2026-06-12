---
title: "Extract zip files"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by windycitybro on 2010-06-05
On a partially related note, I have 9.10. When I DL .deb files, its ok, the system will install for me, but when I DL tar, .bz, etc. I don't know WHERE to extract them to i.e. which directory; etc, usr, and so on. 

So my Q is, where must the zip-type program files be extracted to? I dl a codec pack and tried to follow the command line tar -xvj all-20100303.tar.bz2, or something like that and it didnt work. I was able to mkdir, but not extract. 

Then I tried via GUI to extract and basically copy/paste...didnt work, then I tried to create another folder and paste inside of there...no dice. This was from GUI. 

I've seen some really good programs i wanna run, but their zips and I'd like to know where to put them an how to install once I extract them.

......yes I'm a newbie, but had been considering Linux for about a year. Finally after my last registry snafu due to some crazy unknown virus that may have tampered with reg. keys, I changed the value, then couldnt log back in. Luckily I was running 9.10 live and was able to get all the programs out, but at that point I decided that was my LAST microsoft virus burn and decided to make the full transition to Ubuntu, and WOW, ...all the time wasted with windows..........

Anyway....sorry....thanks

---

### Post by 29732 on 2010-06-05
Can't you install 7-zip if those don't work???

---

### Post by sgosnell on 2010-06-05
Extract to anywhere in your home folder.  You have full rights anywhere there.  You can make a folder manually, or have the archive manager recreate the folders.  I usually extract to home, and have it recreate the folders, so I can easily find the files.  You'll usually get a folder with the package name.  Just remember where you extracted the files so you can find them.  The best way to find them is to just have the archive manager open Nautilus in the folder you extracted to.

Most .zip files are Windows.  You won't be able to run Windows programs except under wine.  If you have wine installed, you can right-click on the .exe file and select Open with wine, and that should install it.

---

### Post by sanderd17 on 2010-06-05
normally, you should make your own post.

Firs question, why did you need extra codecs? aren't the ones in restriced extra's enough? [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

Second, if you use a tar.bz, you should unpack it and read the readme in it or follow instructions from the developers site. Every tar is different. For some you have to compile it, for others you don't.

---

### Post by Elfy on 2010-06-05
Please don't resurrect old threads that might appear to be the same issue - it's not always the case, posts moved to new thread

---

