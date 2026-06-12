---
title: "Troubleshooting failed Ruby's installation (dpkg error)"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by frogo on 2011-08-06
Hi, 

I'm having problems installing ruby. I keep having this error message:

```
Selecting previously deselected package libruby1.8.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `linux-headers-2.6.34-020634-generic': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)

```2.6.34-020634-generic is indeed what I run on this machine. Does that suggest I may have to update/upgrade my kernel? That'd be bad...

many thanks 
f

---

### Post by wildmanne39 on 2011-08-06
Hi, try these two commands please:
```
dpkg --clean-avail
```
```
apt-get update
```
Thank you

---

### Post by frogo on 2011-08-06
> **wildmanne39 said:**
> Hi, try these two commands please:
```
dpkg --clean-avail
``````
apt-get update
```Thank you

Hi, I think you meant --clear-avail in the first one. I tried the suggestions and then to reinstall Ruby, either through apt-get (apt-get-install ruby-dev OR apt-get install ruby) or via Synaptic or again via the software center. All hang for a few secs at 55% of libruby1.8 and then fail with the same error message. 

thanks for the attempt nevertheless
f

EDIT: well, silly me, I doubt it has much to do with Ruby now. I tried installing a few random things and all break at a similar point with the same error, whether I clean dpkg and update apt or not...

---

### Post by Soul-Sing on 2011-08-07
close all -apt/dpkg/software centre.

```
gksudo nautilus
```
navigate to /var/lib/dpkg/info and deleting everything that has this name:linux-headers-2.6.34-020634-generic
(search-option right above)
close nautilus.
```
sudo apt-get -f install
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by frogo on 2011-08-07
> **leoquant said:**
> close all -apt/dpkg/software centre.

```
gksudo nautilus
```navigate to /var/lib/dpkg/info and deleting everything that has this name:linux-headers-2.6.34-020634-generic
(search-option right above)
close nautilus.
```
sudo apt-get -f install
``````
sudo apt-get update
``````
sudo apt-get upgrade
```


Oh yes that works (so far)! I could install Ruby just after the upgrade went through. I will still have to see whether it works and what happens when I restart the machine :) (If all goes well, I'll maerk as solved)

So for my understanding, did I just update and upgrade all my packages? I had never done so with this install because I was afraid of getting weird, breaking kernel updates (as in the past with other installs). 

I'm not sure I understand how the system becomes buggy overtime...

Many thanks to the two of you!

---

