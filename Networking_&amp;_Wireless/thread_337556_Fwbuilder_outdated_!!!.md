---
title: "Fwbuilder outdated !!!"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by BigBob on 2007-01-13
Hi all,

It look like Fwbuilder is severely outdated since months now ...

According to the Homepage of the project [http://www.fwbuilder.org](http://www.fwbuilder.org), the stable versions are 2.1.x

Also, actually, Ubuntu edgy only propose 2.0.x series and even in this series the latest proposed version is 2.0.9 (not the latest).

Anyone know if the 2.1.8 was released shortly or not ?

A++

---

### Post by chebe on 2007-02-14
I'm building mine ...
All you need is the [sources files]("http://sourceforge.net/project/showfiles.php?group_id=5314") 
Then you install what's required to build the packages :
```
sudo apt-get install build-essential fakeroot autoconf automake1.9 autotools-dev dbs debhelper libsnmp9-dev libssl-dev libtool libxml2-dev libxslt1-dev qt3-dev-tools zlib1g-dev
```

Now you're ready to build !
First we start with libfwbuilder
```
tar -xzvf libfwbuilder-2.1.9.tar.gz ; cd libfwbuilder-2.1.9
./configure --prefix=/usr
fakeroot checkinstall
sudo dpkg -i libfwbuilder_2.1.9-1_i386.deb
```
and then for fwbuilder
```
tar -xzvf fwbuilder-2.1.9.tar.gz ; cd fwbuilder-2.1.9
./configure --prefix=/usr
fakeroot checkinstall
sudo dpkg -i fwbuilder_2.1.9-1_i386.deb
```

For the menu entry:
First copy the icons:
```
sudo cp src/gui/icons/firewall_* /usr/share/pixmaps/
```
Then add the .desktop file:
```
sudo vi /usr/share/applications/fwbuilder.desktop
```
and paste the following:
```
[Desktop Entry]
Encoding=UTF-8
Name=Firewall Builder
Comment=Firewall Builder
Exec=fwbuilder
Icon=firewall_64.xpm
Terminal=false
Type=Application
Categories=Application;Network;
StartupNotify=true
```

And now you have it :)

---

### Post by halberom on 2007-02-19
The above install tip assumes you have the libqt3-headers package installed (probably part of KDE but is NOT part of gnome) - Something that threw me for a while.

---

### Post by yacko on 2007-05-16
I have tried this with version 2.1.11 and after running the ./configure and I try to run the fakeroot checkinstall I get the error "fakeroot: 152: checkinstall: not found"  What am I doing wrong here?

Thanks for any help anyone can give me.

---

### Post by gfowler on 2007-05-16
> **yacko said:**
> I have tried this with version 2.1.11 and after running the ./configure and I try to run the fakeroot checkinstall I get the error "fakeroot: 152: checkinstall: not found"  What am I doing wrong here?

Thanks for any help anyone can give me.

You need to install checkinstall i.e. sudo apt-get install checkinstall.

I had to run fakeroot as super user (sudo).
libfwbuilder installed fine but when installing fwbuilder I got:

dpkg: error processing fwbuilder_2.1.11-1_i386.deb (--install):
 trying to overwrite `/usr/lib/gcc/i486-linux-gnu/4.1.2/cc1plus', which is also in package g++-4.1

Which google gave me many hits on the problem but no solution, the most promising were in French, alas not my language.  So until some guru stumbles in here and straightens out the confusion I guess I'm stuck with the old version.

Jerry

---

