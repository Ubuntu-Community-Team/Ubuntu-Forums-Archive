---
title: "Samba,WinBind Woes"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by tstrowd on 2006-11-11
Can anyone tell me how to overcome this error when trying to install samba and Winbind?

Terminal:
default@AMDK62-500:~$ sudo apt-get install krb5-user libpam-krb5
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  krb5-user: Depends: libkrb53 (= 1.3.6-4) but 1.3.6-4ubuntu0.1 is to be installed
             Depends: libkadm55 (= 1.3.6-4) but 1.3.6-4ubuntu0.1 is to be installed
E: Broken packages


Yes i'm trying to set up an Active directory client with this Ubuntu box.

---

