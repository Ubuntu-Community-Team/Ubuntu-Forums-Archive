---
title: "alien wont convert my .rpm to .deb"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by aas452 on 2010-01-18
Hi 

I needed to convert a .rpm to .deb and I keep erroring out, I went ahead and attached the error code, has anyone ever ran into this error????

```


Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/awcommon
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: failure: couldn't find library libXm.so.2 needed by debian/awcommon/usr/aw/COM/bin/installKey (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
	find AWCommon-11.5 -type d -exec chmod 755 {} ;
find: AWCommon-11.5: No such file or directory
	rm -rf AWCommon-11.5


```

---

### Post by patchwork on 2010-01-18
First, I'm not an expert.  Someone else here may be able to add more than I can.  It appears to me that you are trying to install a 32 bit application onto 64 bit architecture.  This can be done, but you will need to download  libXm.so.2 manually and link to it.  I'm not exactly sure how to do this so that alien can find it, though it's probably done by setting the LD_LIBRARY_PATH in a configuration file somewhere.  I'm sure someone else here can set me straight or have more to offer, but that is where I would start.

---

### Post by Fire_Chief on 2010-01-18
Yes, patchwork is correct. Though it may be easier to get the 64-bit version of the rpm(if it exists) and then Alien will convert it straightaway.

Cheers!

---

### Post by aas452 on 2010-01-18
I don't see a 64-bit version out there, crap.

Wondering if some might be able to give me a hand through the process??

---

### Post by aas452 on 2010-01-18
So I after doing some research on the topic I downloaded libmotif from synaptic but I still get errors, is this the point where I have to link to the files?

```

Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
		xargs -0 -r -i cp -a {} debian/awcommon-server
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: debian/awcommon-server/usr/aw/COM/etc/lmflex shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/awcommon-server/usr/aw/COM/etc/lmgrd shouldn't be linked with libm.so.6 (it uses none of its symbols).
dpkg-shlibdeps: warning: debian/awcommon-server/usr/aw/COM/etc/sgiawd shouldn't be linked with libdl.so.2 (it uses none of its symbols).
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
	find AWCommon-server-11.5 -type d -exec chmod 755 {} ;
find: AWCommon-server-11.5: No such file or directory
	rm -rf AWCommon-server-11.5


```

---

### Post by Fire_Chief on 2010-01-18
Can I ask what RPM you are needing?

---

### Post by aas452 on 2010-01-18
Sure thing it is for Maya 2009 the AWCommon-server-11.5-19.i686.rpm & Maya2009_0_64-2009.0-452.x86_64.rpm

---

### Post by aas452 on 2010-01-18
sorry the correct .rpm are 

AWCommon-11.5-19.i686.rpm
AWCommon-server-11.5-19.i686.rpm

the other .rpm converted correctly (Maya2009_0_64-2009.0-452.x86_64.rpm)

---

### Post by Fire_Chief on 2010-01-18
You can install the rpms directly. I found this guide that may help you.
[http://combas3d.com/2009/05/setup-guide-maya-2009-sp1-linux-x64/]("http://combas3d.com/2009/05/setup-guide-maya-2009-sp1-linux-x64/")

Cheers!

---

### Post by patchwork on 2010-01-18
FROM:  [http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/](http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/)  " ...if you just convert the files given in the instructions, it is no need to separately make a AWCommon/Licensing .deb package, because when you run Maya the first time this will automagically pop up, asking for your license… Just be sure to make the temp directory as specified, this is where the license stuff goes… (AFIK)  Maya will try to write files to /usr/temp, so make sure to create the directory and give it write permissions: sudo mkdir /usr/tmp sudo chmod a+rwx /usr/tmp/"  There is a step-by-step tutorial here that seems to address what you are looking for.  In the comments area, another person had seemingly the same issues.  Maybe this will help?

---

### Post by aas452 on 2010-01-18
getting another error when I run the rpm

```
sudo rpm -ivh –nodeps AWCommon-server-11.5-19.i686.rpm
error: open of –nodeps failed: No such file or directory

```

---

### Post by Fire_Chief on 2010-01-18
Kind of hard to tell from the site post but the line```
sudo rpm -ivh –nodeps AWCommon-server-11.5-19.i686.rpm

```should look like this```
sudo rpm -ivh --nodeps AWCommon-server-11.5-19.i686.rpm

```
The nodeps option should have 2 dashes in front of it.

But overall I think the link that patchwork found is better for this process.

Cheers!

---

### Post by patchwork on 2010-01-18
The other common thing I'm seeing looking around for this is that maya may actually already be installed.  The awcommon stuff you are trying to install seems to be the licensing portion, which, by some accounts will run automatically when maya is launched.                                                                            [http://ubuntuforums.org/showthread.php?t=66859&highlight=maya+2009&page=36](http://ubuntuforums.org/showthread.php?t=66859&highlight=maya+2009&page=36)                                                                             It may be worth trying to launch maya from the terminal now.  As I said, I'm not an expert, but I don't think this will cause problems if it doesn't work.

---

