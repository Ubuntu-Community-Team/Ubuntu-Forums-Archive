---
title: "can't install pkgs in jaunty"
date: 2010-03-11
forum: New to Ubuntu
---

### Post by navaneethan on 2010-03-11
root@nava-laptop:~# aptitude install sun-java6-jre sun-java6-jdk sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  gsfonts-x11{a} java-common{a} odbcinst1debian1{a} sun-java6-bin 
  sun-java6-jdk sun-java6-jre unixodbc{a} 
0 packages upgraded, 7 newly installed, 0 to remove and 275 not upgraded.
Need to get 54.5MB of archives. After unpacking 161MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main java-common 0.30ubuntu4
  403 Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse sun-java6-jre 6-16-0ubuntu1.9.04
  403 Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main odbcinst1debian1 2.2.11-16build3
  403 Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main unixodbc 2.2.11-16build3
  403 Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse sun-java6-bin 6-16-0ubuntu1.9.04
  403 Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty-updates/multiverse sun-java6-jdk 6-16-0ubuntu1.9.04
  403 Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main gsfonts-x11 0.21
  403 Forbidden
E: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.30ubuntu4_all.deb:](http://in.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.30ubuntu4_all.deb:) 403 Forbidden
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

root@nava-laptop:~# sudo aptitude install g++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  g++ g++-4.3{a} libstdc++6-4.3-dev{a} 
0 packages upgraded, 3 newly installed, 0 to remove and 275 not upgraded.
Need to get 5520kB of archives. After unpacking 19.1MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main libstdc++6-4.3-dev 4.3.3-5ubuntu4
  403 Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main g++-4.3 4.3.3-5ubuntu4
  403 Forbidden
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) jaunty/main g++ 4:4.3.3-1ubuntu1
  403 Forbidden
E: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb:](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/libstdc++6-4.3-dev_4.3.3-5ubuntu4_i386.deb:) 403 Forbidden
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done



here doesn't install :-) what happened in my jaunty?? how to do?

---

### Post by 3rdalbum on 2010-03-11
Use System > Administration > Software Sources to change to a different mirror.

---

### Post by leclerc65 on 2010-03-11
... or add 'sudo' in front of your command . Software installations require 'root' privilege.

---

### Post by plucky on 2010-03-11
> **leclerc65 said:**
> ... or add 'sudo' in front of your command . Software installations require 'root' privilege.

The OP was in super user mode.Note the prompt > root@nava-laptop:~#

---

### Post by sandyd on 2010-03-11
u behind firewall or proxy? if u are, the firewall or proxy may be blocking acess to the repositories. if thats the case, you might want to try apt-p2p or another repository.

---

