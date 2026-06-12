---
title: "clamav installation"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by Chough39 on 2010-01-19
I have re-installed ClamAV following a fresh installation of Ubuntu 9.10. Previously it worked well and there were no problems with the installation. However, it now refuses to configure   . The attached screen shots of the messages explain the situation I believe. As a newcomer to this operating system I would like some help please.

---

### Post by HermanAB on 2010-01-19
Uhmm, you can copy and paste from a terminal window.  Highlight the text with your mouse left button, then middle click where you want to paste the text.

I can't view your pictures on my dinky little netbook, sorry, but usually the reason for your woes is right there in the error messages.  Copy and paste an error message into [http://www.google/linux](http://www.google/linux) for an instant answer.

---

### Post by sisco311 on 2010-01-19
An application is accessing the /etc/passwd file. Close it, then run *sudo apt-get update*.

---

### Post by Chough39 on 2010-01-19
Thanks HermanAB, so I have learnt a bit more. Here is the information which you requested.

Chough39

E: clamav-base: subprocess installed post-installation script returned error exit status 1
E: clamav-freshclam: dependency problems - leaving unconfigured
E: clamav: dependency problems - leaving unconfigured


Preconfiguring packages ...
Selecting previously deselected package clamav-base.
(Reading database ... 140486 files and directories currently installed.)
Unpacking clamav-base (from .../clamav-base_0.95.3+dfsg-1ubuntu0.09.10_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.95.3+dfsg-1ubuntu0.09.10_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.95.3+dfsg-1ubuntu0.09.10_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up clamav-base (0.95.3+dfsg-1ubuntu0.09.10) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/clamav -g clamav -s /bin/false -u 114 clamav' returned error code 1. Exiting.
dpkg: error processing clamav-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.95.3+dfsg-1ubuntu0.09.10); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-base (0.95.3+dfsg-1ubuntu0.09.10) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/clamav -g clamav -s /bin/false -u 114 clamav' returned error code 1. Exiting.
dpkg: error processing clamav-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.95.3+dfsg-1ubuntu0.09.10); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav

---

### Post by Chough39 on 2010-01-19
Thanks HermanAB, so I have learnt a bit more. Here is the information which you requested.

Chough39

E: clamav-base: subprocess installed post-installation script returned error exit status 1
E: clamav-freshclam: dependency problems - leaving unconfigured
E: clamav: dependency problems - leaving unconfigured


Preconfiguring packages ...
Selecting previously deselected package clamav-base.
(Reading database ... 140486 files and directories currently installed.)
Unpacking clamav-base (from .../clamav-base_0.95.3+dfsg-1ubuntu0.09.10_all.deb) ...
Selecting previously deselected package clamav-freshclam.
Unpacking clamav-freshclam (from .../clamav-freshclam_0.95.3+dfsg-1ubuntu0.09.10_i386.deb) ...
Selecting previously deselected package clamav.
Unpacking clamav (from .../clamav_0.95.3+dfsg-1ubuntu0.09.10_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up clamav-base (0.95.3+dfsg-1ubuntu0.09.10) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/clamav -g clamav -s /bin/false -u 114 clamav' returned error code 1. Exiting.
dpkg: error processing clamav-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.95.3+dfsg-1ubuntu0.09.10); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-base (0.95.3+dfsg-1ubuntu0.09.10) ...
useradd: cannot lock /etc/passwd; try again later.
adduser: `/usr/sbin/useradd -d /var/lib/clamav -g clamav -s /bin/false -u 114 clamav' returned error code 1. Exiting.
dpkg: error processing clamav-base (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.95.3+dfsg-1ubuntu0.09.10); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		[[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8691333") 		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] 			[[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8691333")

---

### Post by jward3010 on 2010-01-19
Something to say about Ubuntu and viruses.

I wouldn't bother installing an anti-virus program on most Linux distributions unless you we're running a mail server and you we're trying to catch dodgy attachments heading towards Windows machines. Virus activity on Linux is such a minor issue that AV programs are rarely needed, they'll slow you down unecessarily.

---

### Post by Chough39 on 2010-01-19
I appreciate what you say, however it is good if one does not pass in Windows viruses to others using that system.

Thanks Chough39

---

### Post by lambengolmor on 2010-01-19
You can try

```
sudo dpkg --configure -a
```

and then try reinstalling clamav. Hope this helps.

---

### Post by Sir Jasper on 2010-01-19
Hi,

Just in case my comments may help.

I used to use the graphical version clamtk
To update it I typed into my terminal:
gksu clamtk
then went to help then update
I had to take care to load my saved settings before scanning.

I now use the Debian version of avast. Which scans [for me] about 6 times faster than clam and also has a significantly higher detection rate, but updates are full (not incemental as for clam versions) so it is best used with broadband. 

I use Wine, but for those´ buntu users who do not - then most Windows users need their own independent protection, because the ´buntu-user precautions will normally be as a drop in the ocean.

My regards

---

### Post by Chough39 on 2010-01-23
Many thanks for the help, the problem has now been solved.

Chough39

---

### Post by isthisyournacho on 2010-09-01
Can you post your fix please?

---

