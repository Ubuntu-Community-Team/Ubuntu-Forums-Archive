---
title: "Unable to get valid context for &lt;user&gt;"
date: 2018-05-17
forum: Networking &amp; Wireless
---

### Post by rsteinmetz70112 on 2018-05-17
Whenever I login into one of my machines I get two messages I shouldn't.
```

*** System restart required ***
Unable to get valid context for <user>
```

I always get the system restart message, even immediately after a restart.

Looking at /var/run/reboot-required I see it was date stamped very recently.
I aslo see /var/run/reboot-required.pkgs has a list of packages

```
# cat /var/run/reboot-required.pkgs
libssl1.0.0
libssl1.0.0
linux-base
linux-image-4.4.0-124-generic
linux-base
linux-base
libssl1.0.0
linux-image-4.4.0-124-generic
linux-base

```

It seems this should get cleared after a restart, but it apparently isn't
I have reinstalled all of the packages listed just to make sure they were installed correctly and they re-installed without error. THat's probably the reason they are duplicated.

Looking into the "Unable to get valid context for <user>"  It seems to be related to selinux and ssl. I reinstalled selinux also with no error.

Lookig at other posts I find ran some other recommended commands 

```
#  semanage login -l
#
# semanage user -l

                Labeling   MLS/       MLS/
SELinux User    Prefix     MCS Level  MCS Range                      SELinux Roles

root            user       s0         s0-s0:c0.c255                  staff_r sysadm_r system_r
staff_u         user       s0         s0-s0:c0.c255                  staff_r sysadm_r
sysadm_u        user       s0         s0-s0:c0.c255                  sysadm_r
system_u        user       s0         s0-s0:c0.c255                  system_r
unconfined_u    user       s0         s0-s0:c0.c255                  system_r unconfined_r
user_u          user       s0         s0                             user_r
```

I don't know what I'm looking at here.
Some reports indicate users can't login in with ssl, but I've been able to use Putty and ssl to login without problems.

looking into selinux it looks like the default mapping od SElinux users to login users are not present. But I probably don't uinderstand what shoul dbe there.

```
# semanage login -a -s thelma  user_u
libsemanage.dbase_llist_query: could not query record value
OSError: Error
```

Even more to the point I'm not sure why I need selinux. I don't directly use it it;s just always been there. I assukmed it was needed by some other package but testing remove
```
 # apt-get remove selinux
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  selinux selinux-policy-ubuntu
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 37.1 MB disk space will be freed.
Do you want to continue? [Y/n]
```

Can I just remove it?

---

### Post by rsteinmetz70112 on 2018-05-23
OK I've removed Selinux. I am still getting the  "Unable to get valid context for <user>"  error on every login.
 running sestatus I get a message that my system seems to think selinux is still installed.

```
~# sestatus
SELinux status:                 enabled
SELinuxfs mount:                /sys/fs/selinux
SELinux root directory:         /etc/selinux
Loaded policy name:             targeted
Current mode:                   permissive
Mode from config file:          error (No such file or directory)
Policy MLS status:              enabled
Policy deny_unknown status:     allowed
Max kernel policy version:      30
```

/etc/selinuc doesn't exist  but /sys/fs/selinux does and contains

```
# ls -ld *
-rw-rw-rw-.  1 root root    0 May 22 19:16 access
dr-xr-xr-x.  2 root root    0 May 22 19:16 avc
dr-xr-xr-x.  2 root root    0 May 22 19:16 booleans
-rw-r--r--.  1 root root    0 May 22 19:16 checkreqprot
dr-xr-xr-x. 79 root root    0 May 22 19:16 class
--w-------.  1 root root    0 May 22 19:16 commit_pending_bools
-rw-rw-rw-.  1 root root    0 May 22 19:16 context
-rw-rw-rw-.  1 root root    0 May 22 19:16 create
-r--r--r--.  1 root root    0 May 22 19:16 deny_unknown
--w-------.  1 root root    0 May 22 19:16 disable
-rw-r--r--.  1 root root    0 May 22 19:16 enforce
dr-xr-xr-x.  2 root root    0 May 22 19:16 initial_contexts
-rw-------.  1 root root    0 May 22 19:16 load
-rw-rw-rw-.  1 root root    0 May 22 19:16 member
-r--r--r--.  1 root root    0 May 22 19:16 mls
crw-rw-rw-.  1 root root 1, 3 May 22 19:16 null
-r--r--r--.  1 root root    0 May 22 19:16 policy
dr-xr-xr-x.  2 root root    0 May 22 19:16 policy_capabilities
-r--r--r--.  1 root root    0 May 22 19:16 policyvers
-r--r--r--.  1 root root    0 May 22 19:16 reject_unknown
-rw-rw-rw-.  1 root root    0 May 22 19:16 relabel
-r--r--r--.  1 root root    0 May 22 19:16 status
-rw-rw-rw-.  1 root root    0 May 22 19:16 user

```

---

### Post by rsteinmetz70112 on 2018-05-24
I removed SElinux them autoremoved its related packages. This particular problem went away. Still can't figure out how it got installed in the first place. After the removea and purge /etc/selinus and /sys/fs/selinux were left behind. I'm trying to figure out if anything will break if I remove them. It doesn't seem likely but you never know.

---

### Post by cheaberlin on 2019-01-04
Does anyone think this was the solution to the initial question?  I have been looking to solve this same issue  but don't want to remove SELinux.... so don't think this was "SOLVED".

---

### Post by QIII on 2019-01-04
Hello!

It was solved in the opinion of the OP, who marked it solved.

If you would like to start a new thread with your own question, please do so.  Tagging on to an old thread marked solved is not likely to get anyone's attention.

Cheers!

---

