---
title: "nvidia error"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by furoido on 2010-05-13
Recently upgraded to 10.04. Got no sound, upgrades give me partial error messages, and I think its related to this:

E: nvidia-kernel-common: subprocess installed post-installation script returned error exit status 1

Can anyone give me a very clear, step-by-step guide on how to resolve this? 

Thanks!

---

### Post by furoido on 2010-05-14
Recently upgraded to 10.04. Got no sound, upgrades give me partial error messages similar to this one:

E: nvidia-kernel-common: subprocess installed post-installation script returned error exit status 1

Seems I need to install new drivers/kernel?

Can anyone give me a very clear, step-by-step guide on how to do so?

Thanks!

---

### Post by cariboo on 2010-05-14
It sounds like your upgrade didn't finish properly. Start in recovery mode, once at the menu select drop to root prompt with networking. Once at the prompt type:

```
apt-get -f install
```

once the above command has finished type:

```
aptitude update && aptitude safe-upgrade
```

this should hopefully finish the upgrade.

---

### Post by cariboo on 2010-05-14
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by furoido on 2010-05-14
Jut tried and seems problem is still there:

dpkg: error processing nvidia-kernel-common (--remove)
subprocess installed pre-removal script returned error exit status 127
update-re.d: warning: /etc/init.d/nvidia.kernel missing LSB information

and then a whole load of information, followed by:

dpkg:error while cleaning up:
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing: nvidia-kernel-common
E: sub-process /usr/bin/dpkg returned error code (1)

---

### Post by -humanaut- on 2010-05-14
try running "dpkg --reconfigure -a" in a terminal I'd suggest a clean install at this point though. It might be easier because in my experience with upgrades if one things broken the next thing is just a fix away.

---

### Post by Soul-Sing on 2010-05-14
this thread may be helpful: [https://answers.edge.launchpad.net/ubuntu/+question/41235](https://answers.edge.launchpad.net/ubuntu/+question/41235)

---

### Post by furoido on 2010-05-15
andrew@andrew-desktop:~$ dpkg --reconfigure -a
dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by Soul-Sing on 2010-05-15
a ```
sudo dpkg --reconfigure -a
```isn't the solution in this case.

---

### Post by furoido on 2010-05-15
leoquant,
thanks...sorry to be dumb, but what is the solution?!

---

### Post by Soul-Sing on 2010-05-15
```
sudo -i
```
```
rm -rf /var/lib/dpkg/info/nvidia-kernel-common.*
```
```
apt-get remove  nvidia-kernel-common
```
```
apt-get install  nvidia-kernel-common
```

close terminal, new terminal:
```
sudo apt-get update
```

---

### Post by furoido on 2010-05-15
pkg: warning: files list file for package `nvidia-kernel-common' missing, assuming package has no files currently installed.
(Reading database ... 191610 files and directories currently installed.)
Removing nvidia-kernel-common ...
root@andrew-desktop:~# apt-get install  nvidia-kernel-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-kernel-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-kernel-common has no installation candidate

---

### Post by furoido on 2010-05-15
Seems to be working!! Thanks guys!

---

### Post by Soul-Sing on 2010-05-15
Great, well done :KS

---

