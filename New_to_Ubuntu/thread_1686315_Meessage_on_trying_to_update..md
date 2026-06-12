---
title: "Meessage on trying to update."
date: 2011-02-12
forum: New to Ubuntu
---

### Post by bvpainter on 2011-02-12
When I try to do an update I get the following message. Can anyone tell me simply how to correct these errors, short of re-installing. My updates appear to work, though.

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 04EED3E377741834 Launchpad GeoD
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 15A8576D6E46FCAD Launchpad Realtime Sunlight Wallpaper
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>

---

### Post by NightwishFan on 2011-02-12
That is just the key the verifies the identity of the packages. Not being verified there should be no problems in practice, but the nature of how this came into being or how to fix is beyond me at the moment. I will check if there is a command to re-load the gpg keys.

Update: This fixes the issue apparently:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=802156](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=802156)

---

### Post by bvpainter on 2011-02-12
This seems to have worked:
sudo rm -r /var/lib/apt/lists
sudo mkdir -p /var/lib/apt/lists/partial
sudo aptitude update

Thanks.

---

