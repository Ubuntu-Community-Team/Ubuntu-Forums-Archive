---
title: "unable to update :("
date: 2011-05-08
forum: New to Ubuntu
---

### Post by neil_1 on 2011-05-08
my update manager dosnt seem to get any updates :(
```

Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

```
then i hit run this action now,and i get this error
```

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ae.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  

W: Failed to fetch http://ae.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  

W: Failed to fetch http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

its been like this for a week or so now .

---

### Post by Not unique on 2011-05-08
Try going to  SYSTEM-ADMINISTRATION-SOFTWARE SOURCES  and check that everything is OK and what is ticked then go to the first tab and check your  DOWNLOAD FROM  box select it and try  OTHER  then SELECT BEST SERVER  it might help and shouldn't harm but maybe its your AUTHENTICATION KEYS ? or PPA's if the sources you are downloading from (PPA's) ?  Can you send some more info?

Try what is said on the below web page (ASSUMING YOU ARE USING UBUNTU10.10(MAVERICK)):

[http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html](http://www.ubuntugeek.com/fix-for-gpg-error-httpextras-ubuntu-com-maverick-release.html)

Or this one is for Ubuntu 10.04:

[http://ubuntuforums.org/showthread.php?t=1480604](http://ubuntuforums.org/showthread.php?t=1480604)

---

### Post by Not unique on 2011-05-09
Any more info did anything help??

---

### Post by neil_1 on 2011-05-11
Yes , changing the server for download did help , i get the updates at startup (i can install them fine) but i also get the false error message as in op !

---

### Post by 3177 on 2011-05-11
check to make sure your passwords right.

---

### Post by neil_1 on 2011-05-11
yeah my passwords are fine as well
now i updated the software sources , but i got this error
```
Failed to fetch
http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz
404 Not Found
Some index files failed to download
```

---

### Post by sikander3786 on 2011-05-11
> **neil_1 said:**
> yeah my passwords are fine as well
now i updated the software sources , but i got this error
```
Failed to fetch
http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz
404 Not Found
Some index files failed to download
```
There is not much we can do for the 404 errors. They mean that the destination servers are not replying. The only way to get rid of the problem is do disable the respective PPA for time being and update.

Go to Software Center > Edit > Software Sources > Other Software tab and disable the offensive repository.

---

### Post by alphacrucis2 on 2011-05-11
> **neil_1 said:**
> yeah my passwords are fine as well
now i updated the software sources , but i got this error
```
Failed to fetch
http://ppa.launchpad.net/user/ppa-name/ubuntu/dists/lucid/main/binary-amd64/Packages.gz
404 Not Found
Some index files failed to download
```


Looks like an example of a ppa name where ppa-name is meant to be replaced by the actual name of the ppa. Did you manually add this ppa and forget to type in the actual ppa name you were intending?

---

### Post by 3177 on 2011-05-11
are you using 10.04.3?

---

### Post by neil_1 on 2011-05-11
> **sikander3786 said:**
> There is not much we can do for the 404 errors. They mean that the destination servers are not replying. The only way to get rid of the problem is do disable the respective PPA for time being and update.

Go to Software Center > Edit > Software Sources > Other Software tab and disable the offensive repository.
i'll delete that ppa then :)
> **alphacrucis2 said:**
> Looks like an example of a ppa name where ppa-name is meant to be replaced by the actual name of the ppa. Did you manually add this ppa and forget to type in the actual ppa name you were intending?
no i didnt add any ppa :/
> **3177 said:**
> are you using 10.04.3?
10.04.1

---

