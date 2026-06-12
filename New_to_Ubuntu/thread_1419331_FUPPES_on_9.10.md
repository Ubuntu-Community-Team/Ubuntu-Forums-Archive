---
title: "FUPPES on 9.10"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by rkstanfi on 2010-03-01
I installed FUPPES and messed up the configuration as well as a few other things and now want to start over.  I am curious as to what the best way is to completely remove FUPPES.

Also, I am installing based on this guide: [http://server-servers.com/ubuntu-9-10-karmic-compile-fuppes-media-server-from-source/](http://server-servers.com/ubuntu-9-10-karmic-compile-fuppes-media-server-from-source/)

Is there a better guide out there?  I am curious because I can't find the package [FONT=Arial]t[/FONT][FONT=Arial]hreadlike-stubs0-dev and don't know if this is messing me up.[/FONT]  [FONT=Arial](After I installed FUPPES, I could see it listed as a media library but I could not see the files in the folder.)[/FONT]

Any help is greatly appreciated.

---

### Post by Shhnap on 2010-06-08
Um sorry for the late reply. The best uninstall method is to simply 'sudo make uninstall'. That should work.

As for the required packages, just look on the fuppes wiki: [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Dependencies#Using_Ubuntu_9.10_apt-get](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Dependencies#Using_Ubuntu_9.10_apt-get)

For more help use the fuppes sourceforge forums. :) I hope that points you in the right direction.

---

