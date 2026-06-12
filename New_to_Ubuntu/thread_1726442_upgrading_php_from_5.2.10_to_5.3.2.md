---
title: "upgrading php from 5.2.10 to 5.3.2"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by John kerr on 2011-04-11
Hi All,

Can someone tell me how to upgrade my server php from 5.2.10 to 5.3.2?

The sources list i find are for Ubuntu 9 and above and I'm on hardy main 8.02.

I'm planning to add in the sources list to my etc/apt/sources.list file so any help would be great.

Please help!!!!!!

john

---

### Post by adit on 2011-04-11
The package you want to install php5 (5.3.2) is not available for hardy (whatever repositories you add).
The only way is to upgrade your ubuntu to 10.10. Then you can install php5 (upto version 5.3.3).
Why do you want to use ubuntu hardy which reaches end of life at the end of April 2011.

---

### Post by John kerr on 2011-04-11
We've had it installed for 3 years so i've not just installed it.

I guess the only option will be to upgrade to 10.10.

---

### Post by SeijiSensei on 2011-04-11
No, there's another option. Download the source code from [www.php.net](www.php.net) and compile your own version. Before running the compilation, you need to get any required headers from the Ubuntu repositories with "sudo apt-get build-dep php5".  Those headers might be too old to compile 5.3.2, but you'll know right away after running ./configure.

---

