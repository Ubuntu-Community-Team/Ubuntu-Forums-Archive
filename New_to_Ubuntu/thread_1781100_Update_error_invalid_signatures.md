---
title: "Update error: invalid signatures"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by maqtanim on 2011-06-13
For couple of days, I am getting the following message after updating Ubuntu 10.04.
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

It seems that some repository is down. Currently I am using Main Server as the source. I've tried with some other servers also, but with no luck. 

Does anyone have any suggestion?

---

### Post by wildmanne39 on 2011-06-13
> **maqtanim said:**
> For couple of days, I am getting the following message after updating Ubuntu 10.04.
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

It seems that some repository is down. Currently I am using Main Server as the source. I've tried with some other servers also, but with no luck. 

Does anyone have any suggestion?
Hi try this
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 048A1684108A879C
```you may have to get rid of the old key first.

---

### Post by maqtanim on 2011-06-13
The command did not work. :( 

BTW, how to get rid of old key?

---

### Post by maqtanim on 2011-06-13
Well... I am getting a notice in my notification area like the attached screen-shot.

---

### Post by Stray Wolf on 2011-06-13
I've been having the same problem in Lucid.  I ran:
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Result:
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
Then ran:
sudo apt-get update
Result (error only):
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

This has been happening for about a week.  Still looking for an effective solution. Once I find one I'll post here unless someone beats me to it.

---

### Post by jynyl on 2011-09-20
Similar problem here;
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) natty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by philinux on 2011-09-20
> **jynyl said:**
> Similar problem here;
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) natty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Hi,

Read this first post. You'll then be able to fix yours.
[http://ubuntuforums.org/showthread.php?t=1221323](http://ubuntuforums.org/showthread.php?t=1221323)

---

### Post by sadaruwan12 on 2011-09-20
Read this how to delete the GPG key

[Click Here]("https://weblion.psu.edu/trac/weblion/wiki/DeleteGpgKey")

To rectify your problem read this

[Click Here]("http://systembash.com/content/apt-get-update-gpg-key-errors-and-fix/")

---

