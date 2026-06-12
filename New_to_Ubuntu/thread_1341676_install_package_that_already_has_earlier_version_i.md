---
title: "install package that already has earlier version installed"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by flylehe on 2009-11-30
Hi,

My Ubuntu 8.10 has its own ntfs-3g 1:1.2506-1ubuntu2 (intrepid). But there seems to be some problems of file operations not supported for mounted Windows ntfs drives, so I decided to build a newer version of nfts-3g "Stable Source Release 2009.11.14" from its source code on Ubuntu 8.10.

I used checkinstall to install the new version of ntfs-3g. Then Synaptic Package Manager said I had "nfts-3g" associated with the two installations and nfts-3g was upgradable, so I ungraded it and ended up having the old version again. What should I do correctly? 

Should I uninstall the old version? If yes, should I do it before install the new version or after?

Thanks and regards!

---

### Post by dcstar on 2009-11-30
> **flylehe said:**
> Hi,

My Ubuntu 8.10 has its own ntfs-3g 1:1.2506-1ubuntu2 (intrepid). But there seems to be some problems of file operations not supported for mounted Windows ntfs drives, so I decided to build a newer version of nfts-3g "Stable Source Release 2009.11.14" from its source code on Ubuntu 8.10.

I used checkinstall to install the new version of ntfs-3g. Then Synaptic Package Manager said I had "nfts-3g" associated with the two installations and nfts-3g was upgradable, so I ungraded it and ended up having the old version again. What should I do correctly? 

Should I uninstall the old version? If yes, should I do it before install the new version or after?

Thanks and regards!

If you want a later, stable version of a package then enable the Backports option in your software sources. Then all compatible versions of packages from the next Ubuntu release that have been backported to your version will be available.

---

### Post by Paqman on 2009-11-30
Uninstall the official one, then install the one you've got from source.

Are you sure there's no PPA that has the version you need?

dcstar: There's only 3 packages in [Karmic backports]("http://packages.ubuntu.com/karmic-backports/allpackages"), and none of them are ntfs-3g.

---

### Post by Locke_99GS on 2009-11-30
When you compile and install from source, the package manager doesn't know what you have installed, this is why installing from packages helps keep you sane. Get the source, debianize it, build it, then instead of installing it, package it into a deb file, and install it with dpkg or gdebi, or whatever. This way, your package manager will know what version it is, and can handle it accordingly.

---

### Post by dcstar on 2009-11-30
> **Paqman said:**
> Uninstall the official one, then install the one you've got from source.

Are you sure there's no PPA that has the version you need?

dcstar: There's only 3 packages in [Karmic backports]("http://packages.ubuntu.com/karmic-backports/allpackages"), and none of them are ntfs-3g.

The OP is running 8.10, so all the 9.04 backports for that release are available, but ntfs-3g is not one of them.

There are a **lot** of dependencies for the later versions of this package, I seriously doubt that the compiled software will function unless they are all met (and installing by bypassing the package manager will not tell you about this).

[http://packages.ubuntu.com/jaunty/ntfs-3g](http://packages.ubuntu.com/jaunty/ntfs-3g)

---

### Post by flylehe on 2009-11-30
@Locke_99GS:
What you said is what I did via checkinstall. My problem is Synaptic Package Manager detect the old and new installed versions associated with "ntfs-3g" but upgraded to the old version.


@Paqman:
I found one new version of ntfs-3g in PPA. But it is for Jaunty and mine is intrepid. Will it work?

---

### Post by flylehe on 2009-11-30
Actually when I installed the new version of ntfs-3g from its source code "Stable Source Release 2009.11.14". After "./configure", "make", I called "checkinstall -D make install". It is at this time I got errors:
 
> 
    Making install in libntfs-3g  
    make[1]: Entering directory `/home/ting/Desktop/ntfs-3g-2009.11.14/libntfs-3g'  
    make[2]: Entering directory `/home/ting/Desktop/ntfs-3g-2009.11.14/libntfs-3g'  
    test -z "/usr/local/lib" || /bin/mkdir -p "/usr/local/lib"  
     /bin/bash ../libtool   --mode=install /usr/bin/install -c  'libntfs-3g.la' '/usr/local/lib/libntfs-3g.la'  
    /usr/bin/install -c .libs/libntfs-3g.so.71.0.0 /usr/local/lib/libntfs-3g.so.71.0.0  
    (cd /usr/local/lib && { ln -s -f libntfs-3g.so.71.0.0 libntfs-3g.so.71 || { rm -f libntfs-3g.so.71 && ln -s libntfs-3g.so.71.0.0 libntfs-3g.so.71; }; })  
    (cd /usr/local/lib && { ln -s -f libntfs-3g.so.71.0.0 libntfs-3g.so || { rm -f libntfs-3g.so && ln -s libntfs-3g.so.71.0.0 libntfs-3g.so; }; })  
    /usr/bin/install -c .libs/libntfs-3g.lai /usr/local/lib/libntfs-3g.la  
    /usr/bin/install -c .libs/libntfs-3g.a /usr/local/lib/libntfs-3g.a  
    chmod 644 /usr/local/lib/libntfs-3g.a  
    chmod: changing permissions of `/usr/local/lib/libntfs-3g.a': No such file or directory  
    make[2]: *** [install-libLTLIBRARIES] Error 1  
    make[2]: Leaving directory `/home/ting/Desktop/ntfs-3g-2009.11.14/libntfs-3g'  
    make[1]: *** [install-am] Error 2  
    make[1]: Leaving directory `/home/ting/Desktop/ntfs-3g-2009.11.14/libntfs-3g'  
    make: *** [install-recursive] Error 1  

    
But running "make install" instead of "checkinstall -D make install" is successful. After running "make install", with its generated `/usr/local/lib/libntfs-3g.a', "checkinstall -D make install" is also successful. I just wonder why "checkinstall -D make install" itself does not work?

@dcstar:
How can I tell if the installed new version can work/function?

---

### Post by Paqman on 2009-11-30
> **flylehe said:**
> 
@Paqman:
I found one new version of ntfs-3g in PPA. But it is for Jaunty and mine is intrepid. Will it work?

Possibly not. A quick look at the versions available in the normal repos seems to indicate they have different dependencies:

[Intrepid = 1:1.2506-1ubuntu2]("http://packages.ubuntu.com/intrepid/ntfs-3g") 
[Jaunty = 1:2009.2.1-0ubuntu2]("http://packages.ubuntu.com/jaunty/ntfs-3g")

You're probably better off grabbing the .deb of the updated version from the Ubuntu repos than a PPA, btw. As long as you can sort out the dependency issues it's better to be using a proper Ubuntu package than it is to sign up to some random PPA or mess about compiling from source.

---

### Post by kevdog on 2009-11-30
#1 - Don't use checkinstall

#2 - Just do a sudo make install.  If you didn't screw around with ./configure path arguments, the program should be installed within the /usr/local tree whereas the default or older program is installed within /usr.  Usually by default your path statement is configured to look in /usr/local prior to /usr (like /usr/local/bin prior to /usr/bin).  If in doubt, do a 
which <executable_name>
and this will tell you where the source is located.

#3 Likely the Jaunty PPA will not work for Intrepid -- different dependencies -- however it is still possible to install yourself.  I've installed many programs within Intrepid that supposedly could not be installed, however I had to do dependency checking on my own (which can be a pain sometimes).  I guess it just depends however how bad you need the program installed.

---

### Post by flylehe on 2009-11-30
@kevdog:
Why not use checkinstall?

---

