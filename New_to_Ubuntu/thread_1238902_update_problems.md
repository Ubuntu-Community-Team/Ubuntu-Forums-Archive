---
title: "update problems"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by gidrdunv11 on 2009-08-12
Here are the error messages I get when I try to update. Any help woul be much appreciated.

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://apt.freegeek.org](http://apt.freegeek.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0261FE3D0875A635

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://web.freegeek.org](http://web.freegeek.org) freegeek Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0261FE3D0875A635

W: Failed to fetch [http://web.freegeek.org/dists/freegeek/Release](http://web.freegeek.org/dists/freegeek/Release)  

W: Failed to fetch [http://apt.freegeek.org/ubuntu/dists/dapper/Release](http://apt.freegeek.org/ubuntu/dists/dapper/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by RedSingularity on 2009-08-13
Go to System>Admin>Software Sorces.  In there go to third party software and remove the lines that have **freegeek.org** in them.  Should be maybe 2 lines.  Then try the update again.

---

### Post by mthalis on 2009-08-13
[http://ubuntuforums.org/showthread.php?t=1236282](http://ubuntuforums.org/showthread.php?t=1236282)

---

### Post by kansasnoob on 2009-08-13
Please, tell me you're not still running Dapper.

---

### Post by colau on 2009-08-17
Problem:P
sudo apt-get update
```

Hit http://backintime.le-web.org stable/main Packages                                                                       
Fetched 814B in 27s (30B/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0D3C959DB2035A6
W: GPG error: http://ppa.launchpad.net jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 638ABCA0FA3A1271
W: GPG error: http://packages.medibuntu.org jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

```

---

### Post by jherskow on 2009-08-27
hi im a total newbie, and im getting some problems when i try to update:
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://medibuntu.sos-sts.com jaunty Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release  

W: Failed to fetch http://medibuntu.sos-sts.com/repo/dists/jaunty/free/binary-i386/Packages.bz2  Sub-process bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

any help?

---

