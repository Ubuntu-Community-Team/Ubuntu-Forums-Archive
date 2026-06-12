---
title: "question"
date: 2010-06-10
forum: New to Ubuntu
---

### Post by 29732 on 2010-06-10
how do you install GIMPshop on linux? im running 10.04 and i've downloaded a source file for gimpshop and i'm still having problems

help

---

### Post by tom.swartz07 on 2010-06-10
Its not recommended that you install files from source.

Simply open the Software center from the Applications menu. Search for "Gimp" and click install.
Done! 

It should be located in Applications>Graphics

---

### Post by SlidingHorn on 2010-06-10
Could you change the title of the thread to something a little more detailed?  

What problems?  The more relevant details you provide, the easier it is to assist you. 

Also, development on gimpshop is on hold and, AFAIK, has been for a while - just something to chew on

---

### Post by pzkfw on 2010-06-10
If you do want to compile from source, you'll need the "make" package and gcc.  untar the package if it came in one.   Right click, Extract here.
cd to the folder.  Look for an "install" or "readme".  It "should" list the other things you need to run this.  Apt-get them.  Next read the instructions.  You will have to type make; make install;.  Or ./configure;  make; make install;

It may look like it's stuck in a loop but it's not.  Give it a few moments.

---

### Post by 3rdalbum on 2010-06-11
Just use Gimp from the Software Center. Gimpshop is just Gimp with rearranged menus, basically.

---

### Post by anewguy on 2010-06-11
+1 om using the one in the package manager.  While I know the intent of gimpshop was to make things appear a little more like another product, but you would be better off just using GIMP from the repos.

Dave ;)

---

### Post by 29732 on 2010-06-11
gimme a moment to get all the info..

---

### Post by 29732 on 2010-06-12
Ok, so many of you prefer GIMP better because it doesn't have more features than GIMPshop

And it seems sorta pointless?

---

### Post by tom.swartz07 on 2010-06-12
> **29732 said:**
> Ok, so many of you prefer GIMP better because it doesn't have more features than GIMPshop

And it seems sorta pointless?

Pretty much.
GIMPshop seems to be a messy version of regular GIMP. 

The dev releases of GIMP already have most of the features for GIMPshop, and you dont have to fight with installing it from source.

---

### Post by 29732 on 2010-06-12
ok, thanks

never knew that

---

