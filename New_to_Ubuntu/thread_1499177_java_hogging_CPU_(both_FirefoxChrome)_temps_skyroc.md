---
title: "java hogging CPU (both Firefox/Chrome) temps skyrocket"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by UbuNoob001 on 2010-06-01
Hi all, I am new to linux and ubuntu 10.04_64

I am currently running Firefox and Chrome, however I am getting the same problem with both. When opening a site with Java usage, i have terrible CPU hogging and battery usage (battery life goes from 2+ hrs to 30 min max). Also CPU temps go from 49 to 69 deg with fan on constantly

output of top before Java site loading: ```
$ top

top - 15:40:36 up 10 min,  2 users,  load average: 1.04, 0.67, 0.33
Tasks: 164 total,   3 running, 161 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.8%us,  1.0%sy,  0.0%ni, 97.5%id,  0.0%wa,  0.3%hi,  0.3%si,  0.0%st
Mem:   3052112k total,   983876k used,  2068236k free,    44744k buffers
Swap:  4022264k total,        0k used,  4022264k free,   427704k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1171 root      20   0  163m  31m  13m S    1  1.1   0:37.26 Xorg               
    4 root      20   0     0    0    0 S    1  0.0   0:00.21 ksoftirqd/0        
    7 root      20   0     0    0    0 S    0  0.0   0:00.38 ksoftirqd/1        
 1549 administ  20   0  199m  12m 9540 S    0  0.4   0:00.21 notify-osd         
 1763 administ  20   0  525m 103m  29m S    0  3.5   0:20.62 firefox-bin        
 1809 administ  20   0 70944  12m 9156 R    0  0.4   0:01.95 npviewer.bin       
 1831 administ  20   0  293m  17m  12m S    0  0.6   0:01.51 gnome-terminal     
```and after:    ```
$ top

top - 15:41:51 up 11 min,  2 users,  load average: 1.10, 0.77, 0.39
Tasks: 165 total,   3 running, 162 sleeping,   0 stopped,   0 zombie
Cpu(s): 54.8%us,  2.6%sy,  0.0%ni, 41.6%id,  0.0%wa,  1.0%hi,  0.0%si,  0.0%st
Mem:   3052112k total,  1304184k used,  1747928k free,    45140k buffers
Swap:  4022264k total,        0k used,  4022264k free,   488432k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1896 administ  20   0 1286m 267m  18m S  100  9.0   0:44.80 java               
 1171 root      20   0  173m  31m  13m S    6  1.1   0:42.93 Xorg               
 1763 administ  20   0  554m 104m  29m S    3  3.5   0:30.17 firefox-bin        
 1809 administ  20   0 70944  12m 9156 S    2  0.4   0:03.03 npviewer.bin       
 1831 administ  20   0  309m  17m  12m S    2  0.6   0:02.55 gnome-terminal     
 1423 administ  20   0  319m  34m 8612 S    1  1.1   0:09.78 compiz   
```any help would be greatly appreciated.

---

### Post by lovinglinux on 2010-06-01
Does it happen with all sites or just a particular one?

Are you sure is Java and not Javascript? This problem is not uncommon with some web sites with bad javascript. I would recommend installing [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722/) for Firefox and block scripts for third-party sites, even for allowed sites.

---

### Post by Shpongle on 2010-06-01
+1 yea no script is really a must for the web , try run firefox / chromium form the command line eg type firefox  to start firefox. and use it as normal and it will say if there are any problems when loading the page . paste back the output if any

---

### Post by dummy910 on 2010-06-01
i will endorse here as well, the **no script** ad-on... it's **[COLOR=red]a must have [/COLOR]**for any mozilla based browser.    **[http://noscript.net/](http://noscript.net/)**

---

### Post by stoogiebuncho on 2010-06-01
I had the same problem.

In order to fix it, I had to install the Sun version of Java (instead of the open-source version that is installed by default).

To install, put this in a terminal:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

Next, you have to tell Ubuntu to use the Sun Java instead of the other one:
```
sudo update-java-alternatives -s java-6-sun
```

You'll need to restart firefox, but it should be fixed.

---

### Post by harto on 2010-06-21
> **stoogiebuncho said:**
> 
In order to fix it, I had to install the Sun version of Java (instead of the open-source version that is installed by default).
Next, you have to tell Ubuntu to use the Sun Java instead of the other one:

Those packages did install fine, but when attempting the 2nd command, I get errors like this:

```
~$ sudo update-java-alternatives -s java-6-sun
update-alternatives: error: no alternatives for appletviewer.
update-alternatives: error: no alternatives for apt.
update-alternatives: error: no alternatives for extcheck.
.
.
.

```and this...

```
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/extcheck
.
.
.

```
[B]
EDIT: DESPITE ONLY OUTPUT BEING THESE ERRORS IT WORKED! THANKS A LOT! :)[/B]

---

### Post by philinux on 2010-06-21
```
sudo update-alternatives --config java
```

It's this bug by the way.

[https://bugs.launchpad.net/bugs/551328](https://bugs.launchpad.net/bugs/551328)

---

