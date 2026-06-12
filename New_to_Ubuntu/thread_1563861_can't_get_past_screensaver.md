---
title: "can't get past screensaver"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by leeelson on 2010-08-29
After trying to update Pango (big mistake), when I reboot, I can't get past the screensaver. I can't seem to start X or any application. CTRL-ALT-Delete gives me the logout/shutdown options, but if I try to logout, I get "greeter application appears to be crashing...". I'm using an HP mini 110 running Ubuntu 8.04.

Suggestions?

---

### Post by leeelson on 2010-08-29
I've made some progress. Using ctrl-alt f1 I can log in. I've uninstalled the Pango files but that hasn't helped. startx gives the message:
"Server is already active..."

How can I get my normal gnome functions back?

---

### Post by leeelson on 2010-09-06
[FONT=Verdana]Still no progress. I've tried many iterations of removing and installing various packages (gdm, ubuntu-desktop). apt-get and aptitude both give script errors. A major problem seems to revolve around 
[/FONT][FONT=Verdana]fast-user-switch-applet

I've attached typical output at the end of this post. How can I force 
re-installation of "BROKEN" packages? Any suggestions out there? 
(Anybody out there?)[/FONT]

                  
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
The following packages are BROKEN:
  fast-user-switch-applet 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  fast-user-switch-applet: Depends: gdm but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
fast-user-switch-applet

Score is 119

Accept this solution? [Y/n/q/?] The following packages are unused and will be REMOVED:
  gnome-system-tools 
The following packages will be automatically REMOVED:
  fast-user-switch-applet 
The following packages will be REMOVED:
  fast-user-switch-applet 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 11.5MB will be freed.
Do you want to continue? [Y/n/?] Writing extended state information...
(Reading database ... 118156 files and directories currently installed.)
Removing fast-user-switch-applet ...
dpkg: error processing fast-user-switch-applet (--remove):
 subprocess pre-removal script returned error exit status 245
dpkg: gnome-system-tools: dependency problems, but removing anyway as you request:
 fast-user-switch-applet depends on gnome-system-tools; however:
  Package gnome-system-tools is to be removed.
Removing gnome-system-tools ...
dpkg: error processing gnome-system-tools (--remove):
 subprocess pre-removal script returned error exit status 245
Errors were encountered while processing:
 fast-user-switch-applet
 gnome-system-tools
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...
The following packages are unused and will be REMOVED:
  gnome-system-tools 
The following packages will be REMOVED:
  fast-user-switch-applet 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 11.5MB will be freed.
Do you want to continue? [Y/n/?] Writing extended state information...
(Reading database ... 118156 files and directories currently installed.)
Removing fast-user-switch-applet ...
dpkg: error processing fast-user-switch-applet (--remove):
 subprocess pre-removal script returned error exit status 245
dpkg: gnome-system-tools: dependency problems, but removing anyway as you request:
 fast-user-switch-applet depends on gnome-system-tools; however:
  Package gnome-system-tools is to be removed.
Removing gnome-system-tools ...
dpkg: error processing gnome-system-tools (--remove):
 subprocess pre-removal script returned error exit status 245
Errors were encountered while processing:
 fast-user-switch-applet
 gnome-system-tools
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Building tag database...

---

