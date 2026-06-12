---
title: "autofs issues with ubuntu client and redhat server"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by yzf600 on 2008-11-13
I'm running Ubuntu 8.10 here at my company. They just switched over from RedHat NIS authenticaion+autofs to openLDAP 2.3. 

I was able to switch over to authenticate with the LDAP server, but now my automounts don't work. 

Here is what "sudo /etc/inid.d/autofs status" shows:

```

Configured Mount Points:
------------------------
/usr/sbin/automount --timeout=300 /apa yp auto.designs -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock 
/usr/sbin/automount --timeout=300 /homes yp auto.home -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock 
/usr/sbin/automount --timeout=300 /designs yp auto.designs -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock 

```

What is wrong here is the "yp" part. Apparently, autofs isn't getting any info about the mounts, so it defaults to "yp". 

I saw in the autofs script the command it runs to get the mounts from LDAP: /usr/lib/autofs/autofs-ldap-auto-master. Here is the output from that command:

```

/net -hosts          -rw,intr
/apa auto.designs    -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/homes auto.home       -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/designs auto.designs    -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock

```


So I tried an experiment. I copied one of the automount commands and ran it by hand as sudo with "ldap" instead of "yp". Nothing. I did get this in the syslog:

```

Nov 13 11:21:42 yzf600 automount[12005]: lookup(ldap): query failed for (objectclass=nisObject): Invalid DN syntax
Nov 13 11:21:42 yzf600 automount[12005]: lookup(ldap): query failed for (objectclass=automount): Invalid DN syntax

```

Google doesn't turn up much for that error message. 

Can anyone help me debug this further? Thanks

---

### Post by upengan78 on 2009-08-03
Hello,
were you able to get automount working with ubuntu? I am having the same issue as you mentioned. It will be great if you can provide help!

Appreciate your help

Thanks

---

### Post by yzf600 on 2009-08-03
In our particular NFS mount system, there are "virtual" mounts like /tools /homes. Under those is where the individual mounts are done. 

If I remember correctly, Ubuntu autofs wasn't getting these "virtual" mounts correctly from the RedHat server. I had to create a /etc/auto.master on my Ubuntu client and define what they were:


```

/homes ldap:nisMapName=auto.home,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/designs ldap:nisMapName=auto.designs,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/home ldap:nisMapName=auto.home,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/tools ldap:nisMapName=auto.tools,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/homes2 ldap:nisMapName=auto.tools2,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/test ldap:nisMapName=auto.test,dc=mydept,dc=company,dc=com -rw,intr,soft,quota,noatime,rsize=8192,wsize=8192,tcp,nolock
/layout ldap:nisMapName=auto.layout,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/regression ldap:nisMapName=auto.regression,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock

```

---

### Post by upengan78 on 2009-08-03
> **yzf600 said:**
> In our particular NFS mount system, there are "virtual" mounts like /tools /homes. Under those is where the individual mounts are done. 
 
If I remember correctly, Ubuntu autofs wasn't getting these "virtual" mounts correctly from the RedHat server. I had to create a /etc/auto.master on my Ubuntu client and define what they were:
 
 
```

/homes ldap:nisMapName=auto.home,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/designs ldap:nisMapName=auto.designs,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/home ldap:nisMapName=auto.home,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/tools ldap:nisMapName=auto.tools,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/homes2 ldap:nisMapName=auto.tools2,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/test ldap:nisMapName=auto.test,dc=mydept,dc=company,dc=com -rw,intr,soft,quota,noatime,rsize=8192,wsize=8192,tcp,nolock
/layout ldap:nisMapName=auto.layout,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock
/regression ldap:nisMapName=auto.regression,dc=mydept,dc=company,dc=com -rw,intr,soft,noquota,noatime,rsize=8192,wsize=8192,tcp,nolock

```
 
Thank you very much for your quick response, appreciate it!!!
 
Do you have anything in /etc/default/autofs ? and also is /etc/init.d/autofs as origianl or changed. I configured my auto.master looking at yours but the users home directory does not get mounted.:(

---

