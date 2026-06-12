---
title: "Webcontentcontrol/dansguardian/firehol/tinyproxy won't uninstall!"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by diablo75 on 2009-01-17
So I downloaded a web filter (webcontentcontrol) for testing purposes (because I'd like to be able to recommend something like this to other ubuntu users I know who happen to be parents).  After trying it out for a little bit I decided it seemed worth while and did what I was looking for.  So now I want to uninstall it.

First I tried this:

```
user@userpc:~$ sudo dpkg -r webcontentcontrol
(Reading database ... 137435 files and directories currently installed.)
Removing webcontentcontrol ...
prerm remove|deconfigure called
Unconfiguring dansguardian+firehol+tinyproxy
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
 * Stopping Firewall firehol                                             [ OK ] 
Stopping tinyproxy: tinyproxy.
 * Stopping DansGuardian dansguardian                                    [ OK ] 
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
All OK! Everything was stopped
Running from /home/user
===>importing /usr/share/webcontentcontrol/backup.dgs.full
tar: /usr/share/webcontentcontrol/backup.dgs.full: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dpkg: error processing webcontentcontrol (--remove):
 subprocess pre-removal script returned error exit status 2
Errors were encountered while processing:
 webcontentcontrol
user@userpc:~$
```

Then I tried this:

```
user@userpc:/usr/share/webcontentcontrol$ ls
CustomApps.conf  reference  scripts  webcontentcontrol_GUI
zeke@zekepc:/usr/share/webcontentcontrol$ sudo aptitude purge firehol tinyproxy dansguardian
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  webcontentcontrol 
The following packages will be REMOVED:
  dansguardian{p} firehol{p} tinyproxy{p} 
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 3510kB will be freed.
The following packages have unmet dependencies:
  webcontentcontrol: Depends: firehol but it is not installable
                     Depends: tinyproxy but it is not installable
                     Depends: dansguardian but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
webcontentcontrol

Score is 121

Accept this solution? [Y/n/q/?] y
The following packages will be REMOVED:
  aggregate{u} clamav{u} clamav-base{u} clamav-freshclam{u} dansguardian{p} 
  firehol{p} gambas2-gb-form{u} gambas2-gb-form-dialog{u} gambas2-gb-gtk{u} 
  gambas2-gb-gui{u} gambas2-gb-qt{u} gambas2-gb-qt-kde{u} 
  gambas2-gb-qt-kde-html{u} gambas2-gb-settings{u} gambas2-runtime{u} 
  libclamav5{u} tinyproxy{p} webcontentcontrol{a} 
0 packages upgraded, 0 newly installed, 18 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 29.7MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 137501 files and directories currently installed.)
Removing aggregate ...
Removing webcontentcontrol ...
prerm remove|deconfigure called
Unconfiguring dansguardian+firehol+tinyproxy
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
 * Stopping Firewall firehol                                             [ OK ] 
Stopping tinyproxy: tinyproxy.
 * Stopping DansGuardian dansguardian                                    [ OK ] 
FireHol is stopped
TinyProxy is stopped
DansGuardian is stopped
All OK! Everything was stopped
Running from /
===>importing /usr/share/webcontentcontrol/backup.dgs.full
tar: /usr/share/webcontentcontrol/backup.dgs.full: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
dpkg: error processing webcontentcontrol (--remove):
 subprocess pre-removal script returned error exit status 2
Processing triggers for man-db ...
Errors were encountered while processing:
 webcontentcontrol
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

user@userpc:/usr/share/webcontentcontrol$
```

I've also tried doing this after running the deb package hoping it might recreate whatever file appears to be missing so it won't snag when I attempt to uninstall.  And that didn't work.

The reason I need to get this software off my computer so badly is because firehol is blocking inbound ports used for VNC connections.  So I can't remote into my own PC, and I would suspect I can't accept reverse VNC connections on 5900 either (something I NEED for the purposes of providing service to clients of mine).

I'm looking for anything from a work-around solution (edit config files for instance) to actually removing this damn software cleanly.  I was shocked to find there wasn't a single bug for webcontentcontrol on Launchpad till I posted one up there today.  Please help!

---

### Post by KIAaze on 2009-01-24
:)
Found this while looking through the unanswered questions here.
I guess it's solved then. ;)

In case somebody else has the same problem:
[https://bugs.launchpad.net/webcontentcontrol/+bug/318301](https://bugs.launchpad.net/webcontentcontrol/+bug/318301)

---

### Post by diablo75 on 2009-01-24
> **KIAaze said:**
> :)
Found this while looking through the unanswered questions here.
I guess it's solved then. ;)

In case somebody else has the same problem:
[https://bugs.launchpad.net/webcontentcontrol/+bug/318301](https://bugs.launchpad.net/webcontentcontrol/+bug/318301)

Yup, got it solved.  Sorry for the lack of updating this thread.

---

### Post by Rodroes on 2010-04-17
Hi,
first, sorry for my bad english. You can delete all files and directories related with webcontent control:

cd /
sudo find . -iname "webcontentcontrol" -exec rm {} \;
sudo find . -iname "webcontentcontrol" -exec rm -dfr {} \;

Then just run synaptic in system/admin and mark the webcontrol packet for uninstall. It worked for me and I hope it works for everyone.

---

