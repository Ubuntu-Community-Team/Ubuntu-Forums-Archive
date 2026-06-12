---
title: "Time and Date Settings, Wrong Time"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by perito on 2011-04-29
I set my location correctly but it is displaying +2 hours from my correct time ... I can't understand from where is it getting this wrong information .. did the whole world decide to jump 2 extra hours today?

---

### Post by lmarmisa on 2011-04-29
Maybe you get a time conflict with other operating system of your computer:

[https://help.ubuntu.com/community/UbuntuTime#Multiple%20Boot%20Systems%20Time%20Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple%20Boot%20Systems%20Time%20Conflicts)

---

### Post by perito on 2011-04-29
I think you are right, since it started displaying wrong time in both OS (Ubuntu and Win7) after the installation of the new Ubuntu..

the weird problem is 

> #
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=no
VERBOSE=no
FSCKFIX=no

UTC = no ... it shouldn't display any wrong time .. should it ?

---

### Post by lmarmisa on 2011-04-29
Type this command and post here the result:

```

cat /etc/timezone

```

---

### Post by perito on 2011-04-29
> ubuntu@ubuntu-laptop:~$ cat /etc/timezone
Asia/Beirut


My City. Correct. Still wrong time.

---

### Post by lmarmisa on 2011-04-29
Please, type these commands now posting the results:

```

date
sudo ntpdate ntp.ubuntu.com
date

```

Check if the command ntpdate changes your time.

---

### Post by perito on 2011-04-29
> ubuntu@ubuntu-laptop:~$ sudo ntpdate ntp.ubuntu.com
29 Apr 19:28:28 ntpdate[3950]: no server suitable for synchronization found
ubuntu@ubuntu-laptop:~$ 


:(

it worked fine on the 10.10

---

### Post by lmarmisa on 2011-04-29
No problem with command ntpdate and Ubuntu 11.04 here:

```

luis@UB1104ENG:~$ sudo ntpdate ntp.ubuntu.com
[sudo] password for luis: 
29 Apr 15:34:41 ntpdate[1601]: adjust time server 91.189.94.4 offset 0.231734 sec
luis@UB1104ENG:~$

```This is the content of file /etc/default/rcS

```

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no

```I am running a stand alone Ubuntu 11.04 on a virtual machine. I did not change any parameter on the file /etc/default/rcS.

---

### Post by lmarmisa on 2011-04-29
Try other NTP servers. This is an example:

```

luis@UB1104ENG:~$ ping pool.ntp.org
PING pool.ntp.org (157.88.18.190) 56(84) bytes of data.
64 bytes from ns1.uva.es (157.88.18.190): icmp_req=1 ttl=245 time=82.7 ms
64 bytes from ns1.uva.es (157.88.18.190): icmp_req=2 ttl=245 time=59.7 ms
64 bytes from ns1.uva.es (157.88.18.190): icmp_req=3 ttl=245 time=54.5 ms
64 bytes from ns1.uva.es (157.88.18.190): icmp_req=4 ttl=245 time=63.6 ms
^C
--- pool.ntp.org ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3006ms
rtt min/avg/max/mdev = 54.528/65.174/82.774/10.665 ms
luis@UB1104ENG:~$ sudo ntpdate 157.88.18.190
29 Apr 15:47:36 ntpdate[1650]: adjust time server 157.88.18.190 offset 0.218851 sec
luis@UB1104ENG:~$

```

---

