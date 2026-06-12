---
title: "Can't install or remove Samba"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by sequimbob on 2013-09-07
I have looked through all the posts and can't find my problem.  I want to set up a network between my windows 7 computer and my ubuntu 12.04.  
I was trying to load SAMBA.  I am running ubuntu 12.04.  Went to the Software center and found SAMBA, clicked on Install.  It seemed to install with no errors. Then I stopped samba with "sudo /etc/init.d/samba stop". It returned "sudo: /etc/init.d/samba: command not found". I thought that the installation may have had a problem so I tried to remove SAMBA from the Software Center.  I got the following message:
```
"Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of winbind4:
 winbind4 depends on samba4 (= 4.0.0~alpha18.dfsg1-4ubuntu2); however:
  Package samba4 is not configured yet.
dpkg: error processing winbind4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 samba4
 winbind4
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of winbind4:
 winbind4 depends on samba4 (= 4.0.0~alpha18.dfsg1-4ubuntu2); however:
  Package samba4 is not configured yet.
dpkg: error processing winbind4 (--configure):
 dependency problems - leaving unconfigured."
Softwar Center now shows Samba as not installed and shows the install button.

I clicked on the install button and it tried but failed with the following errors:
nstallArchives() failed: Selecting previously unselected package libuser1.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 385586 files and directories currently installed.)
Unpacking libuser1 (from .../libuser1_1%3a0.56.9.dfsg.1-1.2ubuntu2_amd64.deb) ...
Selecting previously unselected package python-libuser.
Unpacking python-libuser (from .../python-libuser_1%3a0.56.9.dfsg.1-1.2ubuntu2_amd64.deb) ...
Selecting previously unselected package system-config-samba.
Unpacking system-config-samba (from .../system-config-samba_1.2.63-0ubuntu5_all.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of winbind4:
 winbind4 depends on samba4 (= 4.0.0~alpha18.dfsg1-4ubuntu2); however:
  Package samba4 is not configured yet.
dpkg: error processing winbind4 (--configure):
 dependency problems - leaving unconfigured
Setting up libuser1 (1:0.56.9.dfsg.1-1.2ubuntu2) ...
No apport report written because the error message indicates its a followup error from a previous failure.
Setting up python-libuser (1:0.56.9.dfsg.1-1.2ubuntu2) ...
Setting up system-config-samba (1.2.63-0ubuntu5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Processing triggers for python-central ...
Errors were encountered while processing:
 samba4
 winbind4
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of winbind4:
 winbind4 depends on samba4 (= 4.0.0~alpha18.dfsg1-4ubuntu2); however:
  Package samba4 is not configured yet.
dpkg: error processing winbind4 (--configure):
 dependency problems - leaving unconfigured"

I then tried the following:
bob@Bobs-HP:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
samba set to manually installed.
The following packages were automatically installed and are no longer required:
  libxml-sax-perl libdrm-nouveau2 libxml-sax-expat-perl libxcb-dri2-0
  libxml-parser-perl linux-headers-3.2.0-49 libxml-libxml-lazybuilder-perl
  language-pack-kde-zh-hans-base firefox-globalmenu
  libxml-namespacesupport-perl libxml-libxml-perl firefox-locale-zh-hans
  unity-2d-spread linux-headers-3.5.0-36-generic libmethod-autoload-perl
  libxrandr-ltsq2 linux-headers-3.5.0-23-generic language-pack-kde-en
  linux-headers-3.5.0-23 linux-headers-3.5.0-36 libxml-sax-base-perl
  kde-l10n-engb libuniversal-require-perl libxvmc1 language-pack-zh-hans-base
  kde-l10n-zhcn language-pack-zh-hans language-pack-kde-zh-hans
  linux-headers-3.2.0-49-generic language-pack-kde-en-base libllvm3.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of winbind4:
 winbind4 depends on samba4 (= 4.0.0~alpha18.dfsg1-4ubuntu2); however:
  Package samba4 is not configured yet.
dpkg: error processing winbind4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 samba4
 winbind4
E: Sub-process /usr/bin/dpkg returned an error code (1)
bob@Bobs-HP:~$ 

I also tried Sudo apt-get build-dep samba. This resulted in the following:
bob@Bobs-HP:~$ sudo apt-get build-dep samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up samba4 (4.0.0~alpha18.dfsg1-4ubuntu2) ...
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
ERROR: Invalid smb.conf
/var/lib/dpkg/info/samba4.postinst: 14: /var/lib/dpkg/info/samba4.postinst: /usr/share/samba/setoption.pl: Permission denied
dpkg: error processing samba4 (--configure):
 subprocess installed post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of winbind4:
 winbind4 depends on samba4 (= 4.0.0~alpha18.dfsg1-4ubuntu2); however:
  Package samba4 is not configured yet.
dpkg: error processing winbind4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 samba4
 winbind4
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies
bob@Bobs-HP:~$"
```

 

At this point I am completely confused.  It seems that previous installation failed and will not let the app be removed or re-installed. Is there some way to forcibly remove all traces of SAMBA and start fresh?  Or any other ideas.

---

### Post by TheFu on 2013-09-07
TL;DR.

Samba requires manual configuration to work. Look in /etc/samba/ for the config files.  You'll need to read something to get this working. Samba setup is non-trivial, but not hard, IME.  I've never used samba4. That version is relatively new and I just haven't had the time or need to switch from the 15+ yr old way that Samba worked before.
 
Samba is the name of the package, but the services have different names.  smbd and nmbd.

**sudo apt-get purge samba4**
That should clean it up, but check the config files to ensure /etc/samba gets wiped too.

---

### Post by sequimbob on 2013-09-09
Thanks, I did the sudo apt-get purge samba4 and it went through fine but I still have the folder /etc/samba.  When you say check the config files, just what are you referring to and where are they located? (I am fairly new to Ubuntu and slowly learning) Can I just delete the folder? Thanks again for your help. I really aprreciate this forum.

---

### Post by TheFu on 2013-09-09
> **sequimbob said:**
> Thanks, I did the sudo apt-get purge samba4 and it went through fine but I still have the folder /etc/samba.  When you say check the config files, just what are you referring to and where are they located? (I am fairly new to Ubuntu and slowly learning) Can I just delete the folder? Thanks again for your help. I really aprreciate this forum.

Yes, if you have completely removed (purged) the samba and samba4 packages, then you can safely run ....

```
sudo rm -rf /etc/samba
```
with out worry.

Then I'd suggest locatiing a Samba4 howto (if you **need** an Active directly replacement only) or just install the older samba package and follow a more conventional how-to for that.

You will need to manually edit config files located in  .... guess where? ....   /etc/samba .... for it to work. You'll want to follow a guide, not just "wing it."  The settings can seem complex and it is easy to forget. There are HUGE security aspects to those settings.  

Just because something works, that doesn't mean it is secure. - I need to add that to my signature.

---

### Post by carl4926 on 2013-09-09
This might interest
[http://www.youtube.com/watch?v=-wUfzdiE4m8](http://www.youtube.com/watch?v=-wUfzdiE4m8)

---

### Post by TheFu on 2013-09-09
.

---

### Post by bab1 on 2013-09-09
> **TheFu said:**
> .

Sometimes it is better to say nothing 

+1 

I understand and I agree!

---

### Post by sequimbob on 2013-09-14
Thanks to THEFU samba is now working. I re purged samba and then did a apt-get install samba and now it seems to be working.  Don't know what the problem was with the first install.  I sure do appreciate all the help and thanks to others who answered.

---

### Post by 1976MrEMan on 2014-05-05
I'm running 12.04 Precise and have been trying for a week now to share files with my Windows 7 laptop. After trying unsuccessfully to set it up myself the first time, I began googling walkthroughs. EVERY single walkthrough was useless! Then I tried following walkthroughs to completely remove samba. Once that was done I couldn't install samba 3.6.3. Now that that is fixed, I have no option to share files or folders when I right-click them in the GUI folders. I've tried checking to see if I am missing packages, thinking I had removed something necessary. If I try to install the necessary packages in terminal, it tells me that they are already installed, but they aren't. This has been the absolute biggest waste of time in my entire life. Why can't they just fix samba instead of making us jump through hoops, turn in circles, hop on one foot, and sacrifice goats? My beautiful install of 12.04 that I spent a LOT of time setting up just the way I wanted it is RUINED!

Now that my rant is out of the way, can anybody tell me how to reset all the necessary packages by either command or removing/reinstalling them? And also, if even possible, can somebody tell me what the RIGHT way to install samba 3.6.3? Preferably without hitting even more brick walls? Because I'm at such a loss here that I may have to tuck my tail between my legs and trudge back to Windows....

---

