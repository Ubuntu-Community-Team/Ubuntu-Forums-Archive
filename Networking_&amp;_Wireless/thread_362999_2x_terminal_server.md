---
title: "2x terminal server"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by michael.fries on 2007-02-16
I have been trying to install 2x terminal server.  Not really all that experience, so I am having a little trouble at the Nx formums, so I thought I would try asking here.

Basically, I have done the following:

1.  downloaded tarball
2.  tar -xvzf 2xterminalserver-1.5.0-61.tar.gz 
3.  sudo /usr/NX/bin/nxsetup --install

From step 3, the following was provided:

[INDENT][INDENT]NX> 700 Autodetected system 'debian'
NX> 700 Install log is '/usr/NX/var/log/install'
NX> 700 Creating configuration in '/usr/NX/etc/node.cfg'
NX> 700 Cannot start statistics:
NX> 709 Production of statistics is disabled for this server
NX> 708 Not starting the NX statistics daemons
NX> 700 WARNING: Cannot find a systemwide initialization login shell initialization file;
NX> 700 WARNING: The following line won't be automatically executed upon login:
NX> 700 if ( -r /usr/NX/scripts/nxenv.csh ) then
NX> 700   source /usr/NX/scripts/nxenv.csh
NX> 700 endif
NX> 700 Inspecting local CUPS environment
NX> 700 Generating entries in '/usr/NX/etc/node.cfg' file
NX> 700 Installation of NX server was completed with warnings.
NX> 700 Please review the install log '/usr/NX/var/log/install'
NX> 700 for further details.
NX> 700
NX> 700 Showing file '/usr/NX/share/documents/server/install-notices':

Creating Users

Starting from version 1.5.0 NX is configured to allow access from
any system user, as long as to the user are given valid credentials
for the SSH login. NX provides an alternate authorization method,
allowing system administrators to determine to which users is given
access to the NX functionalities. This works by implementing a se-
paration between the system password and the NX password, so that,
for example, it is possible to disallow remote access to the system
by any other means except NX and use the NX tools to implement ef-
fective accounting of the system resources used by the user.

To activate the NX user and password DB, you will have to edit the
server.cfg configuration file, or run the NX System Management Tool
in order to set the ENABLE_PASSWORD_DB key to 1. Please refer to
the NX System Administrator's Guide for further information on how
to control the access to your NX system.
NX> 700 Bye

Not sure what those warnings mean.  I am also unsure how I actually use it.  I can't find an item in the drop down menus, and I don't know what the command is to actually get this thing running.  Eventually, I want to use this to connect to my ubuntu machine from an xp box.  

I have to admit, that I seem to have been spoiled by the friendly, detailed, step by step instructions that I have found on the UBUNTU forums, and I find the 2x forums fairly daunting.

Anyway, does anybody have any recommendations?

Thanks,
Mike

---

