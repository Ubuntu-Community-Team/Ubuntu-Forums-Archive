---
title: "smb.conf in folder  /usr/share/samba"
date: 2014-12-27
forum: Networking &amp; Wireless
---

### Post by jamglefebvre on 2014-12-27
Please explain why there is _another_ version of  smb.conf in the /usr/share/samba folder ? ? ?

I have made modifications to the smb.conf file in  /etc/samba., everything seems to work OK. Do I need to worry about the other one ? ? ? 
                                       :confused:             
         
     

Thank you.

---

### Post by schragge on 2014-12-27
Most probably, it's just the default version shipped with the package that gets copied to /etc/samba/ on install. On next upgrade, it will notice your modifications and ask you if you want to preserve them or replace /etc/samba/smb.conf with the default one. This is handled by post-install script [/var/lib/dpkg/info/samba-common.postinst](http://anonscm.debian.org/cgit/pkg-samba/samba.git/tree/debian/samba-common.postinst)

---

### Post by jamglefebvre on 2014-12-27
**Thanks for the info. ** I looked at the script [/var/lib/dpkg/info/samba-common.postinst]("http://anonscm.debian.org/cgit/pkg-samba/samba.git/tree/debian/samba-common.postinst").  My Bash is beginner-intermediate: **aint gonna touch it !**

I recently moved from Ubuntu 12.04 to **X**ubuntu 14.04.  I had to reconfigure the samba files because my backups were corrupt.

Can you tell me _where_ I can learn about the installation process and how network configuration  files are generated ? ? ?

Best Regards
Michel

---

### Post by bab1 on 2014-12-27
> **jamglefebvre said:**
> ... how [are] network configuration  files are generated ? ? ?
What network configuration files are you referring to?  Samba or TCP/IP or ... ??

---

### Post by schragge on 2014-12-27
You can start from [Debian FAQ]("https://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.en.html#s-conffile") that contains some basic definitions. The subject of conffiles gets more throughly discussed in [this section]("http://debian-handbook.info/browse/stable/sect.package-meta-information.html#sect.conffiles") of The Debian Administrator's Handbook (the French version of it is [here]("http://debian-handbook.info/browse/fr-FR/stable/sect.package-meta-information.html#sect.conffiles")). All the gory details are in the Debian Policy Manual (esp. [Chapter 10]("https://www.debian.org/doc/debian-policy/ch-files.html#s-config-files") and [Appendix E]("https://www.debian.org/doc/debian-policy/ap-pkg-conffiles.html")), see also [Debian Wiki]("https://wiki.debian.org/DpkgConffileHandling"). Be aware that the last two sources are intended for package maintainers, not for the end users. Maybe other forum members may suggest more user-friendly introductory documentation.

---

### Post by bab1 on 2014-12-27
> **schragge said:**
> You can start from [Debian FAQ]("https://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.en.html#s-conffile") that contains some basic definitions. The subject of conffiles gets more throughly discussed in [this section]("http://debian-handbook.info/browse/stable/sect.package-meta-information.html#sect.conffiles") of The Debian Administrator's Handbook (the French version of it is [here]("http://debian-handbook.info/browse/fr-FR/stable/sect.package-meta-information.html#sect.conffiles")). All the gory details are in the Debian Policy Manual (esp. [Chapter 10]("https://www.debian.org/doc/debian-policy/ch-files.html#s-config-files") and [Appendix E]("https://www.debian.org/doc/debian-policy/ap-pkg-conffiles.html")), see also [Debian Wiki]("https://wiki.debian.org/DpkgConffileHandling"). Be aware that the last two sources are intended for package maintainers, not for the end users. Maybe other forum members may suggest more user-friendly introductory documentation.
All of the above appears to be for package maintainers.  Is the OP looking for package info or possibly only how to configure Samba or IP networking?

---

### Post by jamglefebvre on 2014-12-27
Schragge, 

I realize there are hundreds of files supporting samba, certainly the same for IP networking. I'm moderately familiar with the filesystem. Precisely today I would like to know where these config files reside.

Regards
Michel

---

### Post by schragge on 2014-12-28
Ah sorry, now I see I was answering the wrong question. The simplest way to find out what conffiles were installed by samba and where they are located is just
```
cat /var/lib/dpkg/info/*samba*.conffiles
```
Unfortunately, you won't see in the output conffiles that were generated on the fly by post-install scripts like */etc/samba/smb.conf* you were asking about. I do not know any good generic way to find them. You should just consult the documentation installed in /usr/share/doc/<package>/ directory. There often will be files like *README.Debian* and/or *NEWS.Debian* that may mention where the <package> in question installs its config files.

With the command outlined above you also won't see the name of the package. E.g. some conffiles for samba are actually installed by package *samba-common*. Besides, any files under */var/lib/dpkg/info* are internal dpkg implementation details and not guaranteed to stay there in the future. The official way to access this information as currently recommended by dpkg developers is
```
dpkg-query -Wf'\n${binary:Package}\n${Conffiles}\n' '*samba*'
```
This should work fine on trusty (14.04) or newer. On precise (12.04) it should be ${Package} instead of ${binary:Package}

Or just look them up in the section named **Conffiles:** in the output of *dpkg -s*. This should work on any Ubuntu release starting from warty (4.10):
```

dpkg -s `apt-cache pkgnames samba` 2>/dev/null|sed 's/^Package:/\n&/p;/^Conffiles:/,/^[^ ]/!d'

```

I'm specifying the package name like '*samba*' and `apt-cache pkgnames samba` respectively instead of just plain *samba* because samba config files may be scattered across several packages like samba-common and samba. Also note that *samba* in `apt-cache pkgnames samba` is a prefix package name starts with, so it's not quite the same as '*samba*' in dpkg-query, but rather like 'samba*' and won't match e.g. *python-samba*.

---

### Post by jamglefebvre on 2014-12-28
Schragge,

thank you for the info.

I'm going into @**digestion**@ mode for a while.

See you later.

Michel

---

