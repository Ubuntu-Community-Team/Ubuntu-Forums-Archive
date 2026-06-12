---
title: "Apt-get upgrade problem"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by vasilis-london on 2010-10-05
I receive the following:

```
-Kubuntu:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 libgtlcore0.7 : Depends: libllvm2.7 but it is not installed
 libopenctl0.7 : Depends: libllvm2.7 but it is not installed
 libopenshiva0.7 : Depends: libllvm2.7 but it is not installed
E: Unmet dependencies. Try using -f.
```

And then:

```
-Kubuntu:~$ sudo apt-get install libllvm2.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  libllvm2.7
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
38 not fully installed or removed.
Need to get 0B/5,169kB of archives.
After this operation, 13.2MB of additional disk space will be used.
(Reading database ... 95325 files and directories currently installed.)
Unpacking libllvm2.7 (from .../libllvm2.7_2.7-5ubuntu2_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: data error'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libllvm2.7_2.7-5ubuntu2_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libllvm2.7_2.7-5ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Is there anything I can do?

---

### Post by arochester on 2010-10-05
> You might want to run &#8216;apt-get -f install&#8217; to correct these.

Have you tried running: sudo apt-get -f install ?

---

### Post by emoguitarist06 on 2010-10-05
Precisely just run what the terminal is asking you to run

```
sudo apt-get -f install
```

---

