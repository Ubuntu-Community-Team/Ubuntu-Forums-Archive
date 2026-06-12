---
title: "Problem mounting windows file share"
date: 2011-08-29
forum: New to Ubuntu
---

### Post by ee08 on 2011-08-29
I am trying to install matlab from a windows file share server following the instructions below:

[LIST]
[*]su to root.
     % **su**
[*]Make a directory for mounting the distribution#** mkdir -p /mnt/licensed.dist**
[*] Mount the distribution with SMB:
     # **mount -t smbfs -o username=PRINCETON*\\<netID>* //files.princeton.edu/Licensed /mnt/licensed.dist**
[LIST]
[*]All one line, no line breaks
[*]Replace *<netID>* with your Princeton netID
[*]You will be prompted for a password.  Please enter your Princeton Windows password.
[*]If the command does not work, you might not have SMB mount support installed.
[*]**NOTE: As of Red Hat Enterprise Linux 5 and Fedora releases, use 'cifs' instead of 'smbfs' as the -t parameter above.**
[/LIST]
 
[*]Run the Matlab installation
     **# /mnt/licensed.dist/Products/Matlab/R2011a/Unix/install****_wrapper.sh**
[/LIST]
However, when I try the mount it returns the mount usage and the return value is 1 and the mount doesn't work. Any ideas?
Sincerely,
David

---

### Post by gnometorule on 2011-08-29
I haven't done this, but was curious and googled around. Here is how it a similar situation is described by your West Coast competitor:

[https://techcommons.stanford.edu/topics/miscellaneous/mounting-active-directory-windows-cifs-file-share-ubuntu-linux](https://techcommons.stanford.edu/topics/miscellaneous/mounting-active-directory-windows-cifs-file-share-ubuntu-linux)

The more interesting part is if you follow the link on that page back to the ubuntu forums. It appears that 'smfbs' is a package you need to install separately (it also appears it is sort of obsolete and replaced by another program, but you need to of course follow your instructions). So suggestions:

(1) install smfbs
(2) make sure you issue this command being in the right directory, if the dir you made isn't at root.
(3) have a look a the articles for safety.
(4) as -o lists options separated by comma, look closely if you're not missing one (you set UID, passwd, link - is that really not separated by commans?)

Gl.

---

### Post by ee08 on 2011-08-29
Thanks for the reply. I had  already installed smbfs, but i realized that i needed to add \mnt\licensed.dist to the end, so when I do the following:

mount -t smbfs -o username=PRINCETON\\deis //files.princeton.edu/Licensed/mnt/licensed.dist /mnt/licensed.dist

it returns:

mount error(20): Not a directory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

I get the same error when I do cifs instead of smbfs.
-David

---

### Post by ee08 on 2011-08-29
Okay, I think I found the problem, on the website I couldn't tell that there was a space between **//files.princeton.edu/Licensed **and** /mnt/licensed.dist**, now it seems to be okay, I'll try to see if the rest works. Thanks again for your help.

---

