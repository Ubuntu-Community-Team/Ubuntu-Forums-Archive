---
title: "Installing Xautoclick??"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by khfrekek on 2009-06-04
okay im a total Ubuntu NOOB, and i have no idea how to install this package i downloaded, i know you have to do something in terminal.. im not sure though.  so the package that i downloaded is: xautoclick-0.20-src.tar.gz, in the directory: /home/zack/Firefox Downloads. any help would be greatly appreciated! thanks!

---

### Post by keplerspeed on 2009-06-04
Of firstly open a terminal, from applications>accessories>terminal. Then enter this code to get into the right directory:
```

cd /home/zack/Firefox\ Downloads/

```
Next we need to unpack the archive:
```

tar -xzf xautoclick-0.20-src.tar.gz

```
While in the terminal (and after it has finished unpacking) enter this to move into the new folder:
```

cd xautoclick-0.20-src

```
To see whats in the new directory:
```

ls

```
Hopefully there will be a README or INSTALL file in there somewhere. If there is, do this to see it:
```

gedit filename

```
This should tell you how to install it. If you cant follow it, post the README file instructions here.

---

### Post by SunnyRabbiera on 2009-06-04
Well if you like you can reduce the need to double click like in windows by simply opening up your home folder, go to edit then to preferences, and in the "behavior" tab you can set single or double click.

---

### Post by keplerspeed on 2009-06-04
Thats probably easier yes. Is that what your trying to do khfrekek??

---

### Post by khfrekek on 2009-06-04
oh oaky all of that worked!! thanks! okay then it said:

$Id: INSTALL 62 2008-10-17 11:34:25Z ivovp $

Be sure you have the proper development packages for your distribution
installed (i.e. something like xserver-xorg-dev, gtk2-dev, et cetera).

After that, run:

./configure
make
sudo make install

and when i type ./configure, terminal says: no such directory

how do i tell it what directory to configure?

---

### Post by khfrekek on 2009-06-04
oh no im now trying to just do double click, to do a LOT of clicks, while im doin other stuff :)

---

