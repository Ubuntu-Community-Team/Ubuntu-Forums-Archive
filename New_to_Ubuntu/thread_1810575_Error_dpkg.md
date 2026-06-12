---
title: "Error dpkg"
date: 2011-07-23
forum: New to Ubuntu
---

### Post by William111 on 2011-07-23
Hi,

When i want to install the **OpenLDAP** server daemon  	**slapd** and **ldap-utils** with the command sudo apt-get install slapd ldap-utils, i got the following output

Preconfiguring packages ...
Unquoted string "pm" may clash with future reserved word at /usr/share/perl5/Deb                                                    conf/Element/Noninteractive/Boolean.pm line 5, <GEN1> line 1.
Can't locate object method "new" via package "Debconf::Element::Noninteractive::                                                    Boolean" (perhaps you forgot to load "Debconf::Element::Noninteractive::Boolean"                                                    ?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN1> line 1.
(Reading database ... 52208 files and directories currently installed.)
Unpacking slapd (from .../slapd_2.4.23-6ubuntu6_amd64.deb) ...
Unquoted string "pm" may clash with future reserved word at /usr/share/perl5/Deb                                                    conf/Element/Noninteractive/Boolean.pm line 5, <GEN1> line 2.
Can't locate object method "new" via package "Debconf::Element::Noninteractive::                                                    Boolean" (perhaps you forgot to load "Debconf::Element::Noninteractive::Boolean"                                                    ?) at /usr/share/perl5/Debconf/FrontEnd.pm line 68, <GEN1> line 2.
dpkg: error processing /var/cache/apt/archives/slapd_2.4.23-6ubuntu6_amd64.deb (                                                    --unpack):
 subprocess new pre-installation script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/slapd_2.4.23-6ubuntu6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I don't know what to do. :sad: I am a newbie. Please can anyone help me?

With regards, William111

---

### Post by gmargo on 2011-07-23
I suspect one of your Debconf perl files got corrupted somehow.

Try checking the MD5 sums of these files with:
```

$ cd /
$ md5sum -c /var/lib/dpkg/info/debconf.md5sums

```

---

### Post by William111 on 2011-08-14
Hi,
 
Sorry that i reply only now.
I checked th MD5 sums. You were right. The output is as follows:
```
md5sum: WARNING: 1 of 145 computed checksums did NOT match

```
What do i have to do next?
 
With regards, William

---

### Post by gmargo on 2011-08-14
You just have to manually replace that one corrupted file.

1. Download the debconf package.
```

sudo apt-get -d --reinstall install debconf

```
Alternatively you could download it with the browser from [http://packages.ubuntu.com/natty/all/debconf/download](http://packages.ubuntu.com/natty/all/debconf/download)

2. Extract the contents of the package to a temporary location.  This assumes the 11.04 Natty version of **debconf** package.  Adjust the filename if using a different version.
```

mkdir /tmp/debconf.temp
cd /tmp/debconf.temp
sudo dpkg-deb -x /var/cache/apt/archives/debconf_1.5.36ubuntu4_all.deb .

```3. Replace corrupted file.  You don't say which file it was (see the md5sum output to find out which).  For example, if it is the Noninteractive/Boolean.pm file, you would do this:
```

sudo cp -p usr/share/perl5/Debconf/Element/Noninteractive/Boolean.pm /usr/share/perl5/Debconf/Element/Noninteractive/Boolean.pm

```

---

### Post by William111 on 2011-08-15
Hi Gmargo,

Hurray, your solution is adequate. Thank you very much. So the only cause is to reinstall debconf. After that i downloaded from 'natty' slapd and installed it (because i removed it before) and it has succeeded. Once again thank you very much.

With regards, William

---

