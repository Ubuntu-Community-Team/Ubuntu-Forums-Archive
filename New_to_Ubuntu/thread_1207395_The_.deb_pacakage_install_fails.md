---
title: "The .deb pacakage install fails"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by staar2 on 2009-07-08
When i am trying to install some .deb package ill get the error
```
staar2@star:/usr/local/opt/eclipse$ sudo dpkg --install /home/staar2/Desktop/scala_2.7.5.dfsg-1_all.deb
(Reading database ... 132653 files and directories currently installed.)                                                     
Preparing to replace scala 2.7.5.dfsg-1 (using .../scala_2.7.5.dfsg-1_all.deb) ...                                           
Unpacking replacement scala ...                                                                                              
[B]dpkg: dependency problems prevent configuration of <--- SOMETTHING WRONG HERE !scala:                                                                    
 scala depends on scala-library (= 2.7.5.dfsg-1); [/B]however:                                                                   
  Version of scala-library on system is 2.7.3-3.                                                                             
dpkg: error processing scala (--install):                                                                                    
 dependency problems - leaving unconfigured                                                                                  
Processing triggers for man-db ...                                                                                           
Errors were encountered while processing:                                                                                    
 scala                  
```

---

### Post by Paqman on 2009-07-08
Looks like you need to grab a .deb for the updated version of scala-library, too.

---

### Post by staar2 on 2009-07-08
Shouldnt it install the dependencies also or do i have to install separately ?

---

### Post by del_diablo on 2009-07-08
This is not Windows, erros actually mean something :P
It says the program needs "scala" of version X or higher, and it says that the version on your system is Y and its lower.

---

### Post by Zack McCool on 2009-07-08
> **staar2 said:**
> Shouldnt it install the dependencies also or do i have to install separately ?

It can't install dependencies on it's own unless they are available in one of your repositories.  If your system is fully updated, this is indicating that the version of scala in the repos for your release of Ubuntu is older than the require minimum.

First, start by making sure that you have the latest version installed from the repos: 
```

sudo apt-get update
sudo apt-get upgrade

```
Then, see what's there.  If it still is too old, seek out a newer version on the net.

---

### Post by Paqman on 2009-07-08
> **staar2 said:**
> Shouldnt it install the dependencies also or do i have to install separately ?

Your package manager can, but since you're install this manually you have to do some of the work.

---

### Post by staar2 on 2009-07-08
Yeah there were one library package missing so you can get here [http://packages.debian.org/sid/scala-library](http://packages.debian.org/sid/scala-library), but the problem is that the scala in the ubuntu repos list is version 2.7.3 but newest is 2.7.5.

One question more, how about installing the tar.gz version, to i need to know the paths were files will be located?

---

