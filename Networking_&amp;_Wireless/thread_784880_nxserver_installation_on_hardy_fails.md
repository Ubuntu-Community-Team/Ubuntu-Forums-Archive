---
title: "nxserver installation on hardy fails"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by sperlyjinx on 2008-05-06
I'm trying to install nxserver version 3.2 and am running into issues.  I've succcessfully installed both nxclient & nxnode.  When I try to install nxserver, the following output is generated:

jgbaum@toro:~/downloads$ sudo dpkg -i nxserver_3.2.0-7_i386.deb 
(Reading database ... 126704 files and directories currently installed.)
Preparing to replace nxserver 3.2.0-7 (using nxserver_3.2.0-7_i386.deb) ...
Unpacking replacement nxserver ...
Setting up nxserver (3.2.0-7) ...
NX> 700 Installing: server at: Tue May 06 19:15:47 2008.
NX> 700 Autodetected system: debian.
NX> 700 Install log is: /usr/NX/var/log/install.
NX> 700 ERROR: Cannot set shell for user: nx to '/usr/NX/bin/nxserver'.
dpkg: error processing nxserver (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 nxserver


When I check the log in /usr/NX/var/log/install, here is the relavent info:

NX> 700 Installing: server at: Tue May 06 19:15:47 2008.
NX> 700 Autodetected system: debian.
NX> 700 Install log is: /usr/NX/var/log/install.
NX> 700 Running: adduser --system --disabled-password --home /usr/NX/home/nx nx.
NX> 700 Output: Warning: The home dir /usr/NX/home/nx you specified already exists.
Adding system user `nx' (UID 114) ...
Adding new user `nx' (UID 114) with group `nogroup' ...
adduser: Warning: The home directory `/usr/NX/home/nx' does not belong to the user you are curr
ently creating.
The home directory `/usr/NX/home/nx' already exists.  Not copying from `/etc/skel'..
NX> 700 Result: OK.
NX> 700 Running: usermod -p '*' nx .
NX> 700 Result: OK.
NX> 700 Command: echo '/usr/NX/bin/nxserver' | /usr/bin/chsh nx.
NX> 700 Your account has expired; please contact your system administrator
chsh: PAM authentication failed.
NX> 700 ERROR: Cannot set shell for user: nx to '/usr/NX/bin/nxserver'.
NX> 700 Running: userdel nx.
NX> 700 Result: OK.


This is on a clean install of hardy.  I've installed these programs on gutsy & then upgraded to hardy w/o a problem.  Anyone have any suggestions?

Thanks in advance.

-Jay

---

### Post by ltracy on 2008-05-07
I'm not sure what happened with your installation.  I just downloaded the .deb files and they installed without a problem for me.

---

### Post by sperlyjinx on 2008-05-09
OK, I've figured out a workaround.

[LIST=1]
[*]Comment out the "setShell" line (#2747) of the in the file: /usr/NX/scripts/setup/nxserver

[*]Run the command:
```
sudo /usr/NX/scripts/setup/nxserver --install
```You should receive no error messages.

[*]Set the shell manually in your /etc/passwd file by replacing the shell for the nx user with "/usr/NX/bin/nxserver".  After it's all said and done, it should look something like this:
```

nx:x:114:65534::/usr/NX/home/nx:/usr/NX/bin/nxserver

```
[/LIST]

Note that this is working for version 3.2.0-7 of nxserver.

---

### Post by garythree on 2008-05-24
This is probably due to SELinux. Disable SELinux and installation should succeed.

---

### Post by Endolith on 2008-09-06
> **garythree said:**
> This is probably due to SELinux. Disable SELinux and installation should succeed.

> **ltracy said:**
> I'm not sure what happened with your installation.  I just downloaded the .deb files and they installed without a problem for me.

ltracy, do you have SELinux disabled?

I don't think I have SELinux installed, but I think I do have apparmor installed.  I tried [disabling it]("https://help.ubuntu.com/community/AppArmor#Disable AppArmor framework") and installing nxserver, but got the same errors.

[sperlyjinx's solution]("http://ubuntuforums.org/showthread.php?t=784880#3") does work, though.

---

### Post by eclypse80 on 2009-03-11
It fails because the PAM module for chsh prompts you for your password, even as root, in order to change a shell of a user. 

I wanted to be able to install the .debs without modifying them, so this is what I've done:

1. Add /usr/NX/bin/nxserver to /etc/shells (Not sure if this step is even necessary)

```
 cat /etc/shells
# /etc/shells: valid login shells
/bin/csh
/bin/sh
/usr/bin/es
/usr/bin/ksh
/bin/ksh
/usr/bin/rc
/usr/bin/tcsh
/bin/tcsh
/usr/bin/esh
/bin/bash
/bin/rbash
/bin/ksh93
/usr/bin/screen
/usr/local/bin/tcsh
/usr/local/bin/bash
/usr/NX/bin/nxserver

```

2. Modify /etc/pam.d/chsh auth from 'required' to 'sufficient'

```
cat /etc/pam.d/chsh
#
# The PAM configuration file for the Shadow `chsh' service
#

# This will not allow a user to change their shell unless
# their current one is listed in /etc/shells. This keeps
# accounts with special shells from changing them.
auth       required   pam_shells.so

# The standard Unix authentication modules, used with
# NIS (man nsswitch) as well as normal /etc/passwd and
# /etc/shadow entries.
auth       sufficient   pam_unix.so nullok
account    required   pam_unix.so
session    required   pam_unix.so

```

3. Reinstall

The installer completes successfully, but now sets the default shell to /bin/false. Looking at the install logs, something is wrong with the format of the chsh command in the script, but this at least gets the installer to complete as far as dpkg is concerned.

```
NX> 700 Command: echo '/usr/NX/bin/nxserver' | /usr/bin/chsh nx.
NX> 700 Password: Changing the login shell for nx
Enter the new value, or press ENTER for the default
        Login Shell [/bin/false]: .
NX> 700 Result: OK.

```

4. Until I figure out the issue above, or submit a bug report to NX, Modify /etc/passwd for the nx user to set it's login shell to /usr/NX/bin/nxserver

---

