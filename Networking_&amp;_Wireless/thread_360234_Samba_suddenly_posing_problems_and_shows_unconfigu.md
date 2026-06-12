---
title: "Samba suddenly posing problems and shows unconfigured"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by keith11 on 2007-02-12
Samba was working fine for me after I installed it from the repositories. One day, while updating the repos and installing the updates, I started getting some errors about samba. Those errors are included in the output I have typed below:

root@linux:/# apt-get install samba 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up samba (3.0.22-1ubuntu4.1) ...
 * Starting Samba daemons...                                                                                                                          [fail] 
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gsambad:
 gsambad depends on samba; however:
  Package samba is not configured yet.
dpkg: error processing gsambad (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 samba
 gsambad
E: Sub-process /usr/bin/dpkg returned an error code (1)

What is going wrong here? Any ideas? Thanks.

---

### Post by ukripper on 2007-02-13
Samba seems to be already configured on your machine.

try removing it and installing it again use following

$ sudo apt-get remove samba


$ sudo apt-get install samba

I personally would not use root account but instead create another admin account and issue the above command in terminal.

---

### Post by keith11 on 2007-02-13
Thanks for the suggestions. I have been trying to do exactly the same as you suggested, but it didn't work. So I tried uninstalling samba and samba-common from the synaptic application manager. I figured out that somehow, during one of the upgrades the newer version of samba got corrupted. I know this becuase I kept on installing/uninstalling the newer version again and again and there was some problem in the installation/configuration files stored on my system, so I was going in circles. 

What I did then was uninstall samba (the later version) from synaptic application manager, forced the default/older versions of samba and samba-common (I had to force samba-common first becuase samba depended on samba-common) and installed those default versions of samba. The installation went fine. As soon as the installation of these versions was done I got a notification that updates were available for those versions of samba and samba-common. I went ahead and upgraded and fortunately this time, the installation of the upgrades went fine too. So finally, the problem is solved.:) Thanks for your help.

---

