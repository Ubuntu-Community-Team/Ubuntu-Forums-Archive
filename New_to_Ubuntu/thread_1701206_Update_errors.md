---
title: "Update errors"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by BigBaka on 2011-03-06
Hi, I'm running 10.04 Lucid. 

My update process generally seems to work, but whenever I update the package manager there are numerous items which fail. At the end of the check package process I get this error message. Is any of it important? Why is it doing this?

```

W: GPG error: http://archive.getdeb.net lucid-getdeb Release: The following signatures were invalid: BADSIG A8A515F046D7E7CF GetDeb Archive Automatic Signing Key <archive@getdeb.net>
W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B43C851B1572604
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://ppa.launchpad.net/ubuntugis/ubuntugis-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Regards,
BB

---

### Post by ikt on 2011-03-06
> **BigBaka said:**
> Hi, I'm running 10.04 Lucid. 

My update process generally seems to work, but whenever I update the package manager there are numerous items which fail. At the end of the check package process I get this error message. Is any of it important? Why is it doing this?

When you update your system, your update manager uses a file called sources.list to find where to go to get updates, if your sources.list points to places that require a key to get into, and you don't have that key it will error.

> **BigBaka said:**
> 
W: GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures were invalid: BADSIG A8A515F046D7E7CF GetDeb Archive Automatic Signing Key <archive@getdeb.net>
W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Suggests that you have a key but it is wrong, the actual problem is that the repo is dead, so you will need to remove it.


> **BigBaka said:**
> 
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0B43C851B1572604
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release](http://archive.canonical.com/ubuntu/dists/lucid/Release)  

No key to get the contents.

You can get the key by typing this in terminal:

sudo apt-key adv --recv-key --keyserver keyserver.ubuntu.com 0B43C851B1572604

> **BigBaka said:**
> 
W: Failed to fetch [http://ppa.launchpad.net/ubuntugis/ubuntugis-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/ubuntugis/ubuntugis-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
[/CODE]

Says that there is no files at that location, so the address in the sources.list is wrong. 

[https://launchpad.net/~ubuntugis/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~ubuntugis/+archive/ppa?field.series_filter=lucid)

Has the right address.

You can update your sources.list manually, information here:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

or head into:

System > Admin > Synaptic > Settings > repositories, and click on Other Software, and remove the matching lines.

But a quick warning, if you remove a line from 'other software', make sure you know what that line updates before removing it.

For example I have a line in other software for opera, and if I remove that line then I won't receive any updates for opera.

---

