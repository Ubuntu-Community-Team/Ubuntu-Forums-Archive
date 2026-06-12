---
title: "Need help please installing Brother MFC-290C"
date: 2010-11-15
forum: New to Ubuntu
---

### Post by bgil66 on 2010-11-15
Hi- I am having difficulty getting my printer to work. Am completely new to linux ubuntu here is what I tried and doing something wrong. the cups wrapper and lpr I have put on my desktop if that helps, thanks for your help:

jacob@jacob-Compaq-Presario-CQ60-Notebook-PC:~$ sudomkdir/var/spool/lpd
bash: sudomkdir/var/spool/lpd: No such file or directory
jacob@jacob-Compaq-Presario-CQ60-Notebook-PC:~$ sudo mkdir /var/spool/lpd
mkdir: cannot create directory `/var/spool/lpd': File exists
jacob@jacob-Compaq-Presario-CQ60-Notebook-PC:~$ sudo dpkg -i --force-all mfc290clpr-1.1.2-2.i386.rpm
dpkg: error processing mfc290clpr-1.1.2-2.i386.rpm (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc290clpr-1.1.2-2.i386.rpm
jacob@jacob-Compaq-Presario-CQ60-Notebook-PC:~$ sudo mkdir /var/spool/lpd
mkdir: cannot create directory `/var/spool/lpd': File exists
jacob@jacob-Compaq-Presario-CQ60-Notebook-PC:~$ sudo dpkg i --force-all mfc290clpr
dpkg: need an action option
 Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
 Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
jacob@jacob-Compaq-Presario-CQ60-Notebook-PC:~$ sudo dpkg -i --force-all mfc290clpr#
dpkg: error processing mfc290clpr# (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc290clpr#
jacob@jacob-Compaq-Presario-CQ60-Notebook-PC:~$ sudo dpkg -i --force-all mfc290clpr-1.1.2-2.i386.rpm
dpkg: error processing mfc290clpr-1.1.2-2.i386.rpm (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc290clpr-1.1.2-2.i386.rpm
jacob@jacob-Compaq-Presario-CQ60-Notebook-PC:~$ sudo dpkg -i --force-all mfc290clpr-1.1.2-2.i386.rpm
dpkg-deb: `mfc290clpr-1.1.2-2.i386.rpm' is not a debian format archive
dpkg: error processing mfc290clpr-1.1.2-2.i386.rpm (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 mfc290clpr-1.1.2-2.i386.rpm
jacob@jacob-Compaq-Presario-CQ60-Notebook-PC:~$

---

### Post by cariboo on 2010-11-15
You can get .debs for your printer [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-290C"). Once downloaded, just double click the package and depending on you Ubuntu version, let gdebi or the Software Center install them.

BTW if you try to install from .rpm, you need to convert them to .deb first using alien, which is in the repositories.

---

### Post by bgil66 on 2010-11-15
Thanks I am using 10.10. How do I let the software center install them? thanks so much

---

### Post by bgil66 on 2010-11-15
ok I downloaded both printer drivers double clicked and the software center installed them-very cool. But after installing them and trying to print a test page its just hanging in "processing" state?? do I need to also install the scanner/pc fax drivers too to make it work?

---

### Post by migs73 on 2010-11-16
Welcome to the forums!

Try this tutorial; [http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)

It is a bit old but still works (did for me and others recently).

Best of luck.

Mike

---

### Post by bgil66 on 2010-11-16
thanks all got it going!

---

