---
title: "why is sudo apt-get upgrade installing KDE stuff?"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by switch10 on 2010-01-06
I'm using GNOME with no KDE apps at all.  This is what it has downloaded so far:
```
Get:24 http://us.archive.ubuntu.com karmic-backports/main kdelibs5-data 4:4.3.4-0ubuntu1~karmic2 [2,580kB]                   
Get:25 http://us.archive.ubuntu.com karmic-backports/main kdelibs5 4:4.3.4-0ubuntu1~karmic2 [7,023kB]                        
Get:26 http://us.archive.ubuntu.com karmic-backports/main kde-icons-oxygen 4:4.3.4-0ubuntu1~karmic1 [18.7MB]
```

18.7MB is a big file for something I'm not going to use.  What is going on here?

---

### Post by switch10 on 2010-01-06
Here are the other ones:

```
Get:27 http://us.archive.ubuntu.com karmic-backports/main libknotificationitem1 4:4.3.3-0ubuntu1~+karmic1 [28.1kB]           
Get:28 http://us.archive.ubuntu.com karmic-backports/main kdebase-runtime 4:4.3.4-0ubuntu1~karmic1 [1,437kB]                 
Get:29 http://us.archive.ubuntu.com karmic-backports/main kdebase-runtime-bin-kde4 4:4.3.4-0ubuntu1~karmic1 [50.6kB]         
Get:30 http://us.archive.ubuntu.com karmic-backports/main kdebase-runtime-data-common 4:4.3.4-0ubuntu1~karmic1 [305kB]       
Get:31 http://us.archive.ubuntu.com karmic-backports/main kdebase-runtime-data 4:4.3.4-0ubuntu1~karmic1 [4,099kB]            
Get:32 http://us.archive.ubuntu.com karmic-backports/main khelpcenter4 4:4.3.4-0ubuntu1~karmic1 [1,737kB] 
```

---

### Post by bodhi.zazen on 2010-01-06
Are you sure you do not have KDE apps ?

Run ```
dpkg -l | grep kdde
```

---

### Post by mvalviar on 2010-01-06
> **bodhi.zazen said:**
> Are you sure you do not have KDE apps ?

Run ```
dpkg -l | grep kdde
```


Edit: ```
dpkg -l|grep kde
```

---

### Post by mocoloco on 2010-01-06
You could also just select one of the packages for removal, say kdelibs5, in synaptic or with apt-get remove and see what other apps depend on it.

---

### Post by switch10 on 2010-01-06
> **mvalviar said:**
> Edit: ```
dpkg -l|grep kde
```

It looks like the only ones I have installed are the ones that apt-get upgrade just installed...

```
ii  kde-icons-oxygen                      4:4.3.4-0ubuntu1~karmic1                   Oxygen icon theme for KDE 4
ii  kdebase-runtime                       4:4.3.4-0ubuntu1~karmic1                   runtime components from the official KDE 4 r
ii  kdebase-runtime-bin-kde4              4:4.3.4-0ubuntu1~karmic1                   core binaries for the KDE 4 base runtime mod
ii  kdebase-runtime-data                  4:4.3.4-0ubuntu1~karmic1                   shared data files for the KDE 4 base runtime
ii  kdebase-runtime-data-common           4:4.3.4-0ubuntu1~karmic1                   shared data files for the KDE 4 base runtime
ii  kdelibs-bin                           4:4.3.4-0ubuntu1~karmic2                   executables for all KDE 4 core applications
ii  kdelibs5                              4:4.3.4-0ubuntu1~karmic2                   core libraries for all KDE 4 applications
ii  kdelibs5-data                         4:4.3.4-0ubuntu1~karmic2                   core shared data for all KDE 4 applications

```

Should I just remove these??

thanks for the help..

Dave

---

### Post by philinux on 2010-01-06
Try this instead.

```
dpkg -l|grep KDE
```

---

### Post by slakkie on 2010-01-06
You have some apps which rely on it...

apt-cache rdepends <package name>

Otherwise:

```

sudo aptitude -s markauto $(dpkg -l|grep kde | grep "^ii" | awk '{print $2}')

```

Remove the -s if you actually want to run the command.

This will mark all kde packages as auto, if they are a dependency, they are not removed, if they don't have any dependencies, they will be removed.

---

### Post by switch10 on 2010-01-06
hmm.  I guess I will keep them then.  k9copy is a KDE app.  I didn't know that.

thanks for the help everyone.

---

### Post by mocoloco on 2010-01-06
> **switch10 said:**
> hmm.  I guess I will keep them then.  k9copy is a KDE app.  I didn't know that.

thanks for the help everyone.

Really?  The K in **K**9copy didn't give it away? :D

---

### Post by garryknight on 2010-01-06
K9copy? I thought it was for cloning dogs... ;)

---

