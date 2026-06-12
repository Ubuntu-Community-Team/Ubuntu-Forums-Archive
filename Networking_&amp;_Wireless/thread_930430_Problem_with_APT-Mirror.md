---
title: "Problem with APT-Mirror"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by Thomy23 on 2008-09-26
Hello guys


Im having a problem with my locally installed apt-mirror. I'm mirroring about 30gb of data, and the highest throughput i get is 500kb/s, the lowest 20kb/s. As the server is on my LAN, this isn't a net problem. Has anybody an idea what this can be?

My mirror.conf looks like this:

```


############ config ##################
#
#set base_path    /var/mirror
#
# if you change the base path you must create the directories below with write privlages
#
#set mirror_path  $base_path/mirror
#set skel_path    $base_path/skel
#set var_path     $base_path/var
#set cleanscript $var_path/clean.sh
#set defaultarch  <running host architecture>
set nthreads     20
set _tilde 0
#
############# end config ##############

```


Greets Thomy

---

