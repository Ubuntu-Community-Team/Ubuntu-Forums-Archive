---
title: "GLIBXX _3.4.11 Error message?"
date: 2010-05-23
forum: New to Ubuntu
---

### Post by Hygaphunkik on 2010-05-23
I have been interested in finding a good simple game developing package that children can use running on linux for a couple of years. I have made great use of Game Editor to develop small applications for linux with it. Unfortunately they needed to be made in windows at the moment. Apperently it will run on ubuntu but I allways get this error.

/usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by ./gameEditor)

Last time I tried to sort this out I completely trashed my computer, Is there anybody who can get [http://game-editor.com/Main_Page](http://game-editor.com/Main_Page) this package working on ubuntu. I tried recompiling it from the source code but I am not really on the ball with this and I have never successfully compiled anything more than a wordsearch creator.


Any help gratefully taken. Even a clue as to what this application is actually looking for.

Hygaphunkik.

---

### Post by Hygaphunkik on 2010-05-24
I know I only put this up yesterday but......

Well it has taken about 3 weeks numerous searches and one ruined ubuntu install but I have managed to get the released GE working on ubuntu 9.04


Basically I had to install three new debian files that updated the C++ compiler from what I can work out.

Those files are.
[http://packages.ubuntu.com/karmic/gcc-4.4-base](http://packages.ubuntu.com/karmic/gcc-4.4-base)

[http://packages.ubuntu.com/karmic/libstdc++6](http://packages.ubuntu.com/karmic/libstdc++6)

[http://packages.ubuntu.com/karmic/libgcc1](http://packages.ubuntu.com/karmic/libgcc1)

Many thanks to the people at GraphicAll.org and the blender thread for their help, even though they probably don't know they have helped here.

I am going to set up a laptop with 10.04 and will let everyone know how that works out.

---

### Post by Fedbh on 2010-11-18
Hi friend,

I am a new be

What shall I do with above files? to solve GLIBXX _3.4.11 problem

Thanks indeed

---

### Post by Hygaphunkik on 2010-11-18
Basically you need to follow the links in the second post and download the files that are there. 

Then you need to double click on them and a deb installation window will open. Just click on OK and the packages will be installed. HOWEVER......

If you are trying to run Game Editor it will run without any issues in ubuntu 10.04 (I have not tried 10.10 yet), if it is not a Game Editor issue I cannot vouch for this curing your problem. 

Oh yes you probably have to install those files in a particular order (it maybe the order that they are listed) but you can work it out because it will tell you that a dependency is not satisfied and give you a file name (which should be one of the ones you have downloaded).

Hope this fixes your problem whatever it maybe, perhaps you could give us all a few more details.

Hygaphunkik.

---

