---
title: "Problems connecting to Server?"
date: 2018-01-24
forum: Networking &amp; Wireless
---

### Post by aniside on 2018-01-24
Hey everyone,

First time poster, so sorry in advance if this gets sloppy.

So I am a Network Administration student and I'm not exactly sure what we were doing in class today, but I'm pretty sure we were just trying to connect to one of the servers at our school. I could only partially follow our instructor because he was flying through all the steps. I know I messed some code(?) up because when I use nslookup for any site, there is no response. The only thing that responds is a nslookup for 8.8.8.8

Some of the things I type may be completely useless to what we were trying to do. That being said, here we go:

We downloaded bind9, apache 2, php, mariadb-php and something else. We're using Lubuntu, not sure which version off the top of my head.

For today, i think we were only using bind9.

So, we edited our connection to connect to our gateway and my own address.

Then we went into the terminal and used: 


```
sudo nano /etc/bind/named.conf.local

```

Made a zone(?) that i have as:


```
zone ""name".fur" {
type master;[INDENT=2]file /etc/bind/"name".fur.db
allow-transfer {"our dns";};
allow-update {"our dns";};
[/INDENT]
 };

```

Then we went to:


```
sudo nano /etc/bind/named.conf.local
```


Edited this to:


```
options {[INDENT]directory "/var/cache/bind";

//some text here
forwarders {
[Red box]8.8.8.8;8.8.4.4
};

//some more text

dnssec-validation auto;

auth-nxdomain no;     # conform to RFC1035
listen-on-v4 { any; };
listen-on-v6 { any; };
[/INDENT]
 };

```
After that, i really don't know. Any help would be appreciated~

---

### Post by TheFu on 2018-01-24
Welcome to the forums.

What was the task to be completed?

Running BIND without using a chroot is dangerous.  Had a system running BIND that got hacked.  Since then, I decided to pay professionals to handle my public DNS needs.

nslookup has been deprecated for a while.  'dig' is the normal command used to query name servers.

Most people here don't run BIND.  The Ubuntu release being used could be important, since network controls have changed every major release.

Whenever posting code here, please use *code tags*.  Adv-Reply (#).

Use the 'history' command to see everything you typed.  If there is a command you don't want in the history, just lead with a space and it won't be saved.

Linux/Unix has a very steep learning curve even when you already understand networking.  Keep at it. Try hard. Ask the Prof for help and do the reading BEFORE the class so the material isn't brand new when the explanation comes.

---

