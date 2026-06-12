---
title: "HELP!  Could not download all repository indexes"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by digitaladvertise.me on 2011-05-31
I am new to linux.  this is v9 and im trying to update it, maybe even to version 10.04.  I am getting this error.   

Any ideas????

-------------------------------------------------------

Could not download all repository indexes.    

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty/restricted/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-proposed/restricted/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-proposed/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-proposed/main/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-proposed/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-proposed/multiverse/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-proposed/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-proposed/universe/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-proposed/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-backports/restricted/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-backports/main/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-backports/main/binary-i386/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages)  404 Not Found
Failed to fetch [http://ftp.usf.edu/pub/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages](http://ftp.usf.edu/pub/ubuntu/dists/jaunty-backports/universe/binary-i386/Packages)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages)  404 Not Found [IP: 91.189.92.167 80]
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by LowSky on 2011-05-31
Version 9.10 support ended April 2011.
Which means you can't update from any repos.

The only way you will be able to upgrade is by LiveCD


Sorry. Normal releases are only supported 18 months. LTS releases like 10.04 have 3 years of support.

---

### Post by digitaladvertise.me on 2011-05-31
ahh, thanks.  thats a good piece of information to know.  again im new to linux. 

1) now, is there a way to "upgrade" easily?  i upgraded a fit-pc to 10.04 using a usb key, but this is a micro atx case machine and i cant seem to get it to boot from the USB key, and this machine (im using it now) doesnt have a cdrom. 

2) is there a gui interface to remotely manage linux, similar to logmein?  i saw they have some type of beta for linux, but says its command line, no gui interface.

thanks again!

william

---

### Post by rbowen1 on 2011-05-31
There is a current problem with the file repositories for updates right now.  Please see this thread:
[http://ubuntuforums.org/showthread.php?t=1772230](http://ubuntuforums.org/showthread.php?t=1772230)

Try again later this afternoon

---

### Post by Pand5461 on 2011-05-31
> **digitaladvertise.me said:**
> ahh, thanks.  thats a good piece of information to know.  again im new to linux. 

1) now, is there a way to "upgrade" easily?  i upgraded a fit-pc to 10.04 using a usb key, but this is a micro atx case machine and i cant seem to get it to boot from the USB key, and this machine (im using it now) doesnt have a cdrom. 

2) is there a gui interface to remotely manage linux, similar to logmein?  i saw they have some type of beta for linux, but says its command line, no gui interface.

thanks again!

william

1) I've seen an idea to make GRUB boot OS image from usb drive [here]("http://habrahabr.ru/blogs/linux/118472/") (first comment, in Russian). You must unpack the contents of iso image to usb drive first.

---

### Post by rbowen1 on 2011-06-01
The file repository for update manager appears to have been resolved.    I was just able to do my updates.    Try your updates now and they will probably work.

---

