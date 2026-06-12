---
title: "DPKG Install Problem"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by ubergunner86 on 2009-11-30
I tried downloading a java update once (my Java works fine after I actually used the ones in Synaptic Package Manager) using dpkg.

I had to abort the download because it was not working for some reason or another.  

I receive the following error when downloading updates through update manager and installing through 'apt-get install.'

For example, this is the last error I got when downloading the update for 'tzdata' :


"
Preconfiguring packages...
(Reading database ... 303059 files and directories currently installed.)
Preparing to replace tzdata 2009r~repack-0ubuntu0.8.04 (using ... /tzdata_2009~repack-0ubuntu0.8.04_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2009s~repack-0ubuntu0.8.04) ...

Current default timezone: 'America/New York'
Local time is now:      Mon Nov 30 13:19:14 EST 2009
Universal Time is now:  Mon Nov 30 18:19:14 UTC 2009
Run 'dpkg-reconfigure tzdata' if you with to change it.


Setting up sun-java5-doc (1.5.0-20-0ubuntu0.8.04) ...
This package is an installer package, it does not actually contain the J2SDK documentation.  You will need to go download one of the archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and copied to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of J2SDK documentation
dpkg: error processing sun-java5-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were ecountered while processing:
 sun-java5-doc
E: sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java5-doc (1.5.0-20-0ubuntu0.8.04) ...
This package is an installer package, it does not actually contain the J2SDK documentation.  You will need to go download one of the archives:

    jdk-1_5_9-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of J2SDK documentation
dpkg: error processing sun-java5-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java5-doc
"



I actually had to type that, as, I could not actually copy and paste. 
The problem is that every time that I install/update I get this error and need to input 'no' twice.  It's not THAT big of an issue, just a pain in the you know what.  I'm assuming that there is some sort of 'dpkg' list file that stores updates that did not finish and other sorts of problems.  I just don't know where this file is and how to modify it correctly, if that is the case.  Thank you.

---

