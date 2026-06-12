---
title: "'Install' icon appears in menu"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by justpete on 2009-04-13
System > Administration after checking pre-release updates in the repositories setting window of synaptic.

Hover tip says 'Install this system permanently to your hard disk'.  Never saw this one before.  But I did allow update to the kernels having a -14 at the end over the -11 versions previously loaded.

Does this icon refer to permanently installing the new kernels?

Obviously new to ubuntu but didn't see this icon after intial install to existing second partition on eeePC 1000HE.

Tried search but install is kinda ubiquitous and I didn't find anything particularly relevant.

FYI, I'd added the remastersys repository earlier but didn't get it to work until I checked the unsupported updates option in the repositories window but after the update with the remastersys icons appearing in the system > administration menu, the install icon did not.

TIA,
Pete

---

### Post by juancarlospaco on 2009-04-13
**sudo apt-get purge ubiquity**

---

### Post by justpete on 2009-04-13
> **juancarlospaco said:**
> **sudo apt-get purge ubiquity**

Had figured out it had something to do with ubiquity but am not sure exactly what it is ubiquity is or does.  It appears to have been exercised, loaded, whatever with the remastersys packages as their installation dinked with quite a bit of system files including the kernel, or so it looked at the time.  And ubiquity does show up in synaptic so purge as root it is.  Thanks very much.

---

### Post by justpete on 2009-04-13
> **juancarlospaco said:**
> **sudo apt-get purge ubiquity**

And here's the terminal dialog after the command was issued:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  casper libntfs10 libdiscover2 libdebian-installer4 squashfs-tools xresprobe
  discover user-setup ubiquity-casper rdate localechooser-data os-prober
  ntfsprogs ubiquity-ubuntu-artwork libdebconfclient0 discover-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  remastersys* ubiquity* ubiquity-frontend-gtk*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 10.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 129811 files and directories currently installed.)
Removing remastersys ...
Purging configuration files for remastersys ...
Removing ubiquity ...
Purging configuration files for ubiquity ...
Removing ubiquity-frontend-gtk ...
Processing triggers for man-db ...

Remastersys and Restore Grub icons now missing as well from the system > administration menu.  Apparently remastersys does a lot more than I thought.  Hmmmm.  Will have to learn how to use partimage instead, probably safer.

Thanks again,
Pete

---

### Post by justpete on 2009-04-13
> **juancarlospaco said:**
> **sudo apt-get purge ubiquity**

The packages, ubiquity-ubuntu-artwork v1.10.10 and ubiquity-casper v1.152 remain installed after the purge per a search for ubiquity in synaptic.

fwiw,
Pete

---

