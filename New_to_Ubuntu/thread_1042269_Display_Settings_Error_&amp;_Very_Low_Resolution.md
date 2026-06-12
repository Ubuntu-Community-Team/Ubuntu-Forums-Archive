---
title: "Display Settings Error &amp; Very Low Resolution"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by the*hero on 2009-01-17
I am spankin new to Ubuntu and I am really looking forward to all that I can do with it. However I am still getting used to it. I need a few bits of help.

I have a 17 in monitor which normally has a resolution of above 1200. I can't get it to go higher than 800X600. Really difficult to see even now. I played round in the terminal trying to edit stuff but couldn't get anywhere. So I thought I had an nvidia driver so I installed some nvidia settings and after I completed that now I get a n error saying that Ubuntu is booting into low graphics mode and when I view the error log it says:
///////////////////////////////////////////////////////////
5394 5139
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Sat Jan 17 10:04:16 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
5394 5139
cp: cannot stat `/etc/X11/xorg_conf': No such file or directory
/////////////////////////////////////////////////////////////////////

I'm not sure what I'm missing. How do I check what my driver I do have or what kind I need. Basically, I just need to get the screen resolution fixed so I can see anything to start really using Ubuntu.

---

### Post by jimmy the saint on 2009-01-17
What video card do you have in the computer?  It looks like the xorg.conf file has been fragged.  You should ALWAYS make a backup of any file you are going to edit so that if something like this happens you can revert.  just copy the file like this
```
cp file1 file1.bkp
```  
The bkp can be anything that you can remember to mean that it is a backup.

On to your issue!

First, lets reset your xorg.conf file.  In a terminal type
```
nvidia-xconfig
```
That will make Nvidia-settings create a good xorg.conf file to work with.

Next, you said you installed the nvidia driver.  Were there two available?  If so, choose the one that is NOT 177, as it has given a lot of people grief for some reason.  I use the 133 (or something like that) and it solved the same issue you seem to be having.

---

