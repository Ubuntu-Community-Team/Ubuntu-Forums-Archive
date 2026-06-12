---
title: "Synaptic update errors"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by Frau_Munitz on 2011-04-24
Hi, 
I'm not exactly a new user but a red triangle with an exclamation mark appears in my panel and I keep getting this errors when i try to check for updates:


W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://pr.archive.ubuntu.com](http://pr.archive.ubuntu.com) lucid-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 4874D3686E80C6B7 Launchpad PPA for Banshee Team

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 638ABCA0FA3A1271 Launchpad PPA for Telepathy
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 4874D3686E80C6B7 Launchpad PPA for Banshee Team
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG D45DF2E8FC91AE7E Launchpad PPA for Geza Kovacs
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG D45DF2E8FC91AE7E Launchpad PPA for Geza Kovacs
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E0319082F37F3AB0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release](http://archive.canonical.com/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/Release](http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release](http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release)  

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.

How can i fix this?

---

### Post by ivanovnegro on 2011-04-24
I would clean up your sources list, just smash all the PPAs out and then try to update again. If you have Maverick installed, I also see you have backports for Lucid, I think that can also cause problems and the packages that are showing a 404 error are definiteley to remove from your list.

---

### Post by Frau_Munitz on 2011-04-24
> **ivanovnegro said:**
> I would clean up your sources list, just smash all the PPAs out and then try to update again. If you have Maverick installed, I also see you have backports for Lucid, I think that can also cause problems and the packages that are showing a 404 error are definiteley to remove from your list.

How can I do this?
I think i need a step by step guide, I'm afraid of screwing up my computer :S

---

### Post by Old_Grey_Wolf on 2011-04-24
> **Frau_Munitz said:**
> How can I do this?
I think i need a step by step guide, I'm afraid of screwing up my computer :S

Before editing your sources list try enterring these commands in the terminal:```
gpg --keyserver keyserver.ubuntu.com --recv E0319082F37F3AB0
gpg --export --armor E0319082F37F3AB0 | sudo apt-key add -
```

Then try updating again. Post any errors you get.

---

### Post by sikander3786 on 2011-04-24
There are multiple errors in your output.

BADSIG means the gpg keys for the PPAs are corrupt/missing.

404 error means the PPA server is not responding.

Best option is to disable all the PPAs from Software Center > Edit > Software Sources > Other Software Tab as advised above. Then replace your existing sources.list with a new one as described here.

[http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html](http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html)

If you don't want to go this way, then please post the output of these commands.

```
cat /etc/apt/sources.list
```

```
ls -l /etc/apt/sources.list.d
```

---

### Post by Old_Grey_Wolf on 2011-04-24
sikander3786,

I am not sure about how the updates work.

OK, if I remove entries from the sources list file then I don't get errors anymore.

However, does it still check if there are updates that may be security related for those applications I have downloaded from those sources; because, they are not in my sources list?

If I have packages on my computer and eliminate the sources from the sources file, do I have a false sense of security because I think they are updated with patches when in reality they are not? I'm not getting any errors; therefore, everything must be fine, right?

Should I try to find a solution to why the updates do not work rather than hide the problem from myself, or am I hiding the problem from myself and I still get notified of security updates even if the ppa, etc., is not in my sources list?

---

### Post by Frau_Munitz on 2011-04-24
> **Old_Gray_Wolf said:**
> Before editing your sources list try enterring these commands in the terminal:```
gpg --keyserver keyserver.ubuntu.com --recv E0319082F37F3AB0
gpg --export --armor E0319082F37F3AB0 | sudo apt-key add -
```

Then try updating again. Post any errors you get.

I entered the code and got this:
[PHP]
verus@verus-laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv E0319082F37F3AB0
gpg: directory `/home/verus/.gnupg' created
gpg: new configuration file `/home/verus/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/verus/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/verus/.gnupg/secring.gpg' created
gpg: keyring `/home/verus/.gnupg/pubring.gpg' created
gpg: requesting key F37F3AB0 from hkp server keyserver.ubuntu.com
gpg: /home/verus/.gnupg/trustdb.gpg: trustdb created
gpg: key F37F3AB0: public key "Launchpad fixes for aprsd" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
verus@verus-laptop:~$ gpg --export --armor E0319082F37F3AB0 | sudo apt-key add -[sudo] password for verus: 
OK
verus@verus-laptop:~$ [/PHP]


Then tried to check for updates and got this:
[PHP]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://pr.archive.ubuntu.com lucid-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.canonical.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://archive.ubuntu.com maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.ubuntu.com maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 4874D3686E80C6B7 Launchpad PPA for Banshee Team

W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 638ABCA0FA3A1271 Launchpad PPA for Telepathy
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 4874D3686E80C6B7 Launchpad PPA for Banshee Team
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG D45DF2E8FC91AE7E Launchpad PPA for Geza Kovacs
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG D45DF2E8FC91AE7E Launchpad PPA for Geza Kovacs
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG E0319082F37F3AB0 Launchpad fixes for aprsd
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://ppa.launchpad.net/banshee-team/ppa/ubuntu/dists/maverick/Release  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/maverick/Release  

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/maverick-security/Release  

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/PHP]

---

### Post by Frau_Munitz on 2011-04-24
> **sikander3786 said:**
> There are multiple errors in your output.

BADSIG means the gpg keys for the PPAs are corrupt/missing.

404 error means the PPA server is not responding.

Best option is to disable all the PPAs from Software Center > Edit > Software Sources > Other Software Tab as advised above. Then replace your existing sources.list with a new one as described here.

[http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html](http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html)

If you don't want to go this way, then please post the output of these commands.

```
cat /etc/apt/sources.list
```

```
ls -l /etc/apt/sources.list.d
```

Under the first code i got this:
[HTML]
verus@verus-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://pr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://pr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository
deb http://ppa.launchpad.net/banshee-team/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/banshee-team/ppa/ubuntu maverick main
deb http://ppa.launchpad.net/telepathy/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu maverick main
verus@verus-laptop:~$ [/HTML]

Under the second:
[HTML]verus@verus-laptop:~$ ls -l /etc/apt/sources.list.d
total 136
-rw-r--r-- 1 root root 164 2011-04-24 09:08 banshee-team-banshee-unstable-maverick.list
-rw-r--r-- 1 root root 164 2011-04-20 19:43 banshee-team-banshee-unstable-maverick.list.save
-rw-r--r-- 1 root root  64 2010-10-13 16:26 banshee-team-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root 103 2011-02-04 22:28 banshee-team-ppa-lucid.list.save
-rw-r--r-- 1 root root 205 2011-04-24 09:08 banshee-team-ppa-maverick.list
-rw-r--r-- 1 root root 241 2011-04-20 19:43 banshee-team-ppa-maverick.list.save
-rw-r--r-- 1 root root  50 2011-04-24 09:08 dropbox.list
-rw-r--r-- 1 root root  50 2011-04-20 19:43 dropbox.list.save
-rw-r--r-- 1 root root 140 2011-04-24 09:08 gezakovacs-pdfocr-maverick.list
-rw-r--r-- 1 root root 134 2011-04-24 09:08 gezakovacs-ppa-maverick.list
-rw-r--r-- 1 root root 134 2011-04-20 19:43 gezakovacs-ppa-maverick.list.save
-rw-r--r-- 1 root root 176 2011-04-24 09:08 google-chrome.list
-rw-r--r-- 1 root root 176 2010-10-13 16:26 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 176 2011-04-20 19:43 google-chrome.list.save
-rw-r--r-- 1 root root 180 2011-04-24 09:08 google-talkplugin.list
-rw-r--r-- 1 root root 180 2010-10-13 16:26 google-talkplugin.list.distUpgrade
-rw-r--r-- 1 root root 180 2011-04-20 19:43 google-talkplugin.list.save
-rw-r--r-- 1 root root   0 2010-10-09 15:05 jayreading-ppa-lucid.list
-rw-r--r-- 1 root root  64 2010-10-09 15:05 jayreading-ppa-lucid.list.save
-rw-r--r-- 1 root root  61 2010-10-13 16:26 jayreding-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root 100 2011-02-04 22:28 jayreding-ppa-lucid.list.save
-rw-r--r-- 1 root root 100 2011-04-24 09:08 jayreding-ppa-maverick.list
-rw-r--r-- 1 root root 100 2011-04-20 19:43 jayreding-ppa-maverick.list.save
-rw-r--r-- 1 root root 180 2011-04-24 09:08 kamalmostafa-linux-kamal-mjgbacklight-maverick.list
-rw-r--r-- 1 root root 180 2011-04-20 19:43 kamalmostafa-linux-kamal-mjgbacklight-maverick.list.save
-rw-r--r-- 1 root root 175 2011-04-24 09:08 lucid-partner.list
-rw-r--r-- 1 root root 172 2010-10-13 16:26 lucid-partner.list.distUpgrade
-rw-r--r-- 1 root root 175 2011-04-20 19:43 lucid-partner.list.save
-rw-r--r-- 1 root root 148 2010-12-02 21:27 pidgin-ppa.list.save
-rw-r--r-- 1 root root  73 2011-04-24 09:08 skype.list
-rw-r--r-- 1 root root  73 2011-04-20 19:43 skype.list.save
-rw-r--r-- 1 root root  92 2011-04-24 09:08 tualatrix-ppa-maverick.list
-rw-r--r-- 1 root root  92 2011-04-20 19:43 tualatrix-ppa-maverick.list.save
-rw-r--r-- 1 root root   0 2010-10-09 15:05 user-ppa-name-lucid.list
-rw-r--r-- 1 root root  63 2010-10-09 15:05 user-ppa-name-lucid.list.save
-rw-r--r-- 1 root root   0 2010-10-09 15:05 user-ppa-nameppa-lucid.list
-rw-r--r-- 1 root root  66 2010-10-09 15:05 user-ppa-nameppa-lucid.list.save
verus@verus-laptop:~$ [/HTML]

---

### Post by sikander3786 on 2011-04-25
@ **Frau_Munitz**:

Go to Software Sources and disable the Skype PPAs that are returning a 404 error. There is not much we could do to correct this one.

Then go to Software Sources > Authentication Tab and delete these keys one by one.

16126D3A3E5C1192, 40976EAF437D05B5, 40976EAF437D05B5, 4874D3686E80C6B7, 638ABCA0FA3A1271, 4874D3686E80C6B7, D45DF2E8FC91AE7E, D45DF2E8FC91AE7E, 6AF0E1940624A220, 40976EAF437D05B5, 40976EAF437D05B5.

Now try to add the missing keys by running this command at once.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192 40976EAF437D05B5 40976EAF437D05B5 4874D3686E80C6B7 638ABCA0FA3A1271 4874D3686E80C6B7 D45DF2E8FC91AE7E D45DF2E8FC91AE7E 6AF0E1940624A220 40976EAF437D05B5 40976EAF437D05B5
```

If everything goes well, there shouldn't be errors. If some keys fail to add, we'll need to see the output of above command.

@ **Old_Gray_Wolf**:

The result of disabling the PPAs or any repositories is that you'll no longer be able to install/update any software from those but it is an easier fix. What I believe is most of the times these PPA updates result in package conflict or unstable system as they are "Testing PPAs" so the risk is same if you update or if you don't update your software. But it is my personal thought :-)

---

### Post by Frau_Munitz on 2011-04-30
> **sikander3786 said:**
> @ **Frau_Munitz**:

Go to Software Sources and disable the Skype PPAs that are returning a 404 error. There is not much we could do to correct this one.

Then go to Software Sources > Authentication Tab and delete these keys one by one.

16126D3A3E5C1192, 40976EAF437D05B5, 40976EAF437D05B5, 4874D3686E80C6B7, 638ABCA0FA3A1271, 4874D3686E80C6B7, D45DF2E8FC91AE7E, D45DF2E8FC91AE7E, 6AF0E1940624A220, 40976EAF437D05B5, 40976EAF437D05B5.

Now try to add the missing keys by running this command at once.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 16126D3A3E5C1192 40976EAF437D05B5 40976EAF437D05B5 4874D3686E80C6B7 638ABCA0FA3A1271 4874D3686E80C6B7 D45DF2E8FC91AE7E D45DF2E8FC91AE7E 6AF0E1940624A220 40976EAF437D05B5 40976EAF437D05B5
```

If everything goes well, there shouldn't be errors. If some keys fail to add, we'll need to see the output of above command.



Funny thing... last night I upgraded to Natty and the computer stopped giving errors. Guess it took care of it. Still I checked if the keys were there and they all seem to be removed. Thanks for the help anyway :)

---

