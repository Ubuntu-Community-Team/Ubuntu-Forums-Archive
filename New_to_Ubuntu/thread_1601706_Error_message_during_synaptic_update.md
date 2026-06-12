---
title: "Error message during synaptic update"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by skyjacker on 2010-10-20
How can I correct this error message??
 "A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by plucky on 2010-10-20
> **skyjacker said:**
> How can I correct this error message??
 "A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Look [Here](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/59304)

Good Luck

---

### Post by robert shearer on 2010-10-20
Try, in a terminal...
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```

then..
```
sudo apt-get update
```

and 
```
sudo apt-get upgrade
```


references...
[http://ubuntuforums.org/showthread.php?t=1589807](http://ubuntuforums.org/showthread.php?t=1589807)
[http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html](http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html)

---

### Post by skyjacker on 2010-10-20
> **robert shearer said:**
> Try, in a terminal...
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192
```

then..
```
sudo apt-get update
```

and 
```
sudo apt-get upgrade
```


references...
[http://ubuntuforums.org/showthread.php?t=1589807](http://ubuntuforums.org/showthread.php?t=1589807)
[http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html](http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html)
Worked like a charm.... Thanks

---

