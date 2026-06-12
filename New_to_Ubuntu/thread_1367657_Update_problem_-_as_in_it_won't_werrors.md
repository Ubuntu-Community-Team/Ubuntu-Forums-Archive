---
title: "Update problem - as in it won't w/errors"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by eddski on 2009-12-29
I I cannot update Ubuntu and I keep getting an error. i thought it was because of the connection at work, but at home it does the same thing. Below is the error that pops up:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


any suggestions? As I have no idea.

---

### Post by tom.swartz07 on 2009-12-29
> **eddski said:**
> I I cannot update Ubuntu and I keep getting an error. i thought it was because of the connection at work, but at home it does the same thing. Below is the error that pops up:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


any suggestions? As I have no idea.

You can solve it in one command. Seriously.
Download this script: [http://dl.getdropbox.com/u/1115768/launchpad-update.tar.gz](http://dl.getdropbox.com/u/1115768/launchpad-update.tar.gz)
Extract the script from the archive by right clicking –> extract
Move it to your home folder if it’s not already there.
Open a terminal and type: -
sudo ./launchpad-update
5. That’s it!

---

### Post by eddski on 2009-12-30
thanks, but I get another error after running "sudo ./launchpad-update":

Release: jaunty
Please Wait...
cat: keyss: No such file or directory
rm: cannot remove `keyss': No such file or directory

---

