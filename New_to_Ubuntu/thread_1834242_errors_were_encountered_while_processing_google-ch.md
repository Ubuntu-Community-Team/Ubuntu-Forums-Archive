---
title: "errors were encountered while processing: google-chrome-stable"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-08-27
What on earth does this error mean?
```
thomas@Thomas-Dell-DE051:~$ sudo dpkg -i ~/Downloads/google-chrome-stable_current_i386.deb
[sudo] password for thomas: 
(Reading database ... 154912 files and directories currently installed.)
Preparing to replace google-chrome-stable 13.0.782.215-r97094 (using .../google-chrome-stable_current_i386.deb) ...
Unpacking replacement google-chrome-stable ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libnspr4-0d (>= 4.7.3-0ubuntu1~); however:
  Package libnspr4-0d is not installed.
 google-chrome-stable depends on libxss1; however:
  Package libxss1 is not installed.
 google-chrome-stable depends on libcurl3; however:
  Package libcurl3 is not installed.
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Errors were encountered while processing:
 google-chrome-stable
thomas@Thomas-Dell-DE051:~$ 
```

---

### Post by saltmarshlamb on 2011-08-27
> What on earth does this error mean?That it didn't get installed as it needed some other packages that aren't installed. 

Try installing it with the software-centre or gdebi. 

Right click on the package and see what options you get. 

Personally I find gdebi quicker than the software-centre and installed it.

---

### Post by doppel.ganger on 2011-08-27
Got it. The computer had some updates that  needed to be installed.

---

### Post by sathishkumarkps on 2012-04-05
I overcome this error by installing the package libcurl3

apt-get install libcurl3

after that try to install google-chrome-stable_current_i386.deb

It ll work :)

---

### Post by G3nome on 2012-12-27
I had this issue as well. Was caused by missing dependancies and solved via
```
 
   sudo apt-get install -f

```

after that I just re-ran 
```

   dpkg -i google-chrome-stable_current_amd64.deb

```

Note: you can also use gdebi for the install if your not a fan of the CLI.

---

