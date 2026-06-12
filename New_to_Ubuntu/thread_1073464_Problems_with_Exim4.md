---
title: "Problems with Exim4"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by Oliverkat on 2009-02-18
I have been unable to download any new packages because of problems with Exim4.The message I get is:

E: exim4-config: subprocess post-installation script returned error exit status 20
E: exim4-base: dependency problems - leaving unconfigured
E: exim4-daemon-light: dependency problems - leaving unconfigured
E: exim4: dependency problems - leaving unconfigured
E: bsd-mailx: dependency problems - leaving unconfigured
E: mailx: dependency problems - leaving unconfigured

What can I do to sort it out?

Oops! It's on Intrepid

---

### Post by brian_p on 2009-02-18
> **Oliverkat said:**
> 

What can I do to sort it out?

In a terminal:

```
sudo apt-get update
```

and

```
sudo apt-get -f install
```

are worth a try.

---

### Post by Oliverkat on 2009-02-18
> **brian_p said:**
> In a terminal:

```
sudo apt-get update
```

and

```
sudo apt-get -f install
```

are worth a try.

Thanks Brian. Just get more of the same:

Setting up exim4-config (4.69-5ubuntu2) ... 
dpkg: error processing exim4-config (--configure): 
 subprocess post-installation script returned error exit status 20 
dpkg: dependency problems prevent configuration of exim4-base: 
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however: 
  Package exim4-config is not configured yet. 
  Package exim4-config-2 is not installed. 
  Package exim4-config which provides exim4-config-2 is not configured yet. 
dpkg: error processing exim4-base (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of exim4-daemon-light: 
 exim4-daemon-light depends on exim4-base (>= 4.69); however: 
  Package exim4-base is not configured yet. 
dpkg: error processing exim4-daemon-light (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of exim4: 
 exim4 depends on exim4-base (>= 4.69); however: 
  Package exim4-base is not configured yet. 
 exim4 depends on exim4-daemon-light | exim4-daemon-heavy | exim4-No apport report written because the error message indicates its a followup error from a previous failure. 
            No apport report written because the error message indicates its a followup error from a previous failure. 
                                      No apport report written because MaxReports is reached already 
                    No apport report written because MaxReports is reached already 
  No apport report written because MaxReports is reached already 
                                                                daemon-custom; however: 
  Package exim4-daemon-light is not configured yet. 
  Package exim4-daemon-heavy is not installed. 
  Package exim4-daemon-custom is not installed. 
dpkg: error processing exim4 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of bsd-mailx: 
 bsd-mailx depends on exim4 | mail-transport-agent; however: 
  Package exim4 is not configured yet. 
  Package mail-transport-agent is not installed. 
  Package exim4-daemon-light which provides mail-transport-agent is not configured yet. 
dpkg: error processing bsd-mailx (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of mailx: 
 mailx depends on bsd-mailx; however: 
  Package bsd-mailx is not configured yet. 
dpkg: error processing mailx (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 exim4-config 
 exim4-base 
 exim4-daemon-light 
 exim4 
 bsd-mailx 
 mailx 
E: Sub-process /usr/bin/dpkg returned an error code (1) 

:(

---

### Post by brian_p on 2009-02-18
> **Oliverkat said:**
> Thanks Brian. Just get more of the same:

Setting up exim4-config (4.69-5ubuntu2) ... 
dpkg: error processing exim4-config (--configure): 
 subprocess post-installation script returned error exit status 20 
dpkg: dependency problems prevent configuration of exim4-base: 


The problem appears to be with exim4-config but I do know not its cause.

Something drastic - but not harmful:

```
sudo apt-get -s remove --purge exim4 exim4-config
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get install exim4
```

mailx can be installed if this is successful.

---

### Post by Oliverkat on 2009-02-18
> **brian_p said:**
> The problem appears to be with exim4-config but I do know not its cause.

Something drastic - but not harmful:

```
sudo apt-get -s remove --purge exim4 exim4-config
```

```
sudo apt-get dist-upgrade
```

```
sudo apt-get install exim4
```

mailx can be installed if this is successful.

Thanks again Brian. It all started well enough, but the second bit of code evinced the following reply:

Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Calculating upgrade... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
6 not fully installed or removed. 
After this operation, 0B of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Setting up exim4-config (4.69-5ubuntu2) ... 
dpkg: error processing exim4-config (--configure): 
 subprocess post-installation script returned error exit status 20 
dpkg: dependency problems prevent configuration of exim4-base: 
 exim4-base depends on exim4-config (>= 4.30) | exim4-config-2; however: 
  Package exim4-config is not configured yet. 
  Package exim4-config-2 is not installed. 
  Package exim4-config which provides exim4-config-2 is not configured yet. 
dpkg: error processing exim4-base (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of exim4-daemon-light: 
 exim4-daemon-light depends on exim4-base (>= 4.69); however: 
  Package exim4-base is not configured yet. 
dpkg: error processing exim4-daemon-light (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of exim4: 
 exim4 depends on exim4-base (>= 4.69); however: 
  Package exim4-base is not configured yet. 
 exim4 depends on exim4-daemon-light | exim4-daemon-heavy | exim4-No apport report written because the error message indicates its a followup error from a previous failure. 
            No apport report written because the error message indicates its a followup error from a previous failure. 
                                      No apport report written because MaxReports is reached already 
                    No apport report written because MaxReports is reached already 
  No apport report written because MaxReports is reached already 
                                                                daemon-custom; however: 
  Package exim4-daemon-light is not configured yet. 
  Package exim4-daemon-heavy is not installed. 
  Package exim4-daemon-custom is not installed. 
dpkg: error processing exim4 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of bsd-mailx: 
 bsd-mailx depends on exim4 | mail-transport-agent; however: 
  Package exim4 is not configured yet. 
  Package mail-transport-agent is not installed. 
  Package exim4-daemon-light which provides mail-transport-agent is not configured yet. 
dpkg: error processing bsd-mailx (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of mailx: 
 mailx depends on bsd-mailx; however: 
  Package bsd-mailx is not configured yet. 
dpkg: error processing mailx (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 exim4-config 
 exim4-base 
 exim4-daemon-light 
 exim4 
 bsd-mailx 
 mailx 
E: Sub-process /usr/bin/dpkg returned an error code (1) 

:(

---

### Post by brian_p on 2009-02-18
> **Oliverkat said:**
> Thanks again Brian. It all started well enough, but the second bit of code evinced the following reply:

Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Calculating upgrade... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

It's ok up to here. You have no packages to upgrade.

> 6 not fully installed or removed.
After this operation, 0B of additional disk space will be used. 
Do you want to continue [Y/n]? y 

This looks like the exim4 packages have not been first removed from the system. This is what I get:

```
brian@laptop:/var/cache/apt/archives$ sudo apt-get remove --purge exim4 exim4-config
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  at* bsd-mailx* exim4* exim4-base* exim4-config* exim4-daemon-light* mailx*
0 upgraded, 0 newly installed, 7 to remove and 3 not upgraded.
After this operation, 4346kB disk space will be freed.
Do you want to continue [Y/n]?
```

---

### Post by Oliverkat on 2009-02-18
Quote:
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
This looks like the exim4 packages have not been first removed from the system. 

It certainly looks that way. Have you any suggestions as to how I should go about removing them?

---

### Post by brian_p on 2009-02-19
> **Oliverkat said:**
> 

It certainly looks that way. Have you any suggestions as to how I should go about removing them?

I have given the command twice! Posts #4 and #6.

---

### Post by Oliverkat on 2009-02-19
> **brian_p said:**
> I have given the command twice! Posts #4 and #6.

Using the command again gets the same result again!

It seems to be catch 22 - it can't remove it because of dependency problems, and it can't re-install it because it's still there

---

### Post by brian_p on 2009-02-19
> **Oliverkat said:**
> Using the command again gets the same result again!

It seems to be catch 22 - it can't remove it because of dependency problems, and it can't re-install it because it's still there

This is outside my experience! Removing packages shouldn't be so hard. You could try with the package manager (synaptic) or

```
sudo dpkg -r package_name

```

---

### Post by Oliverkat on 2009-02-19
> **brian_p said:**
> This is outside my experience! Removing packages shouldn't be so hard. You could try with the package manager (synaptic) or

```
sudo dpkg -r package_name

```

If it's outside your experience there's no hope for me :)

I removed the (apparently) offending items with dpkg, but subsequent attempts to use dpkg to re-install in various ways brought the same old response. I have previously tried synaptic and apt-get with similar responses

Thanks for your help

Ted

---

