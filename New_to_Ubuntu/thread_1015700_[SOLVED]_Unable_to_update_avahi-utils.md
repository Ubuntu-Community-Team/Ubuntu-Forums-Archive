---
title: "[SOLVED] Unable to update avahi-utils"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Joe Soap on 2008-12-19
I updated several packages with the update manager a while ago, but avahi-utils did not update successfully.

The error message reads:
```
E: /var/cache/apt/archives/avahi-utils_0.6.23-2ubuntu2.1_i386.deb:
 unable to stat `./usr/bin/avahi-resolve-address' 
(which I was about to install)
```

The screenshot below shows the complete output from the terminal:

Any ideas how to fix this?

---

### Post by Michael.Godawski on 2008-12-19
hey
It might be a bug so try to fill a bug report

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078)
[/LIST]
first check in launchpad if there is not a similar issue:

[LIST]
[*][https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)
[/LIST]
Which update options do you have selected? I mean in software sources > Updates?

---

### Post by Joe Soap on 2008-12-19
> **Michael.Godawski said:**
> 
Which update options do you have selected? I mean in software sources > Updates?

I've got intrepid-security, intrepid updates and intrepid proposed marked.

---

### Post by Kevbert on 2008-12-19
Try changing your server in Software Sources.

---

### Post by Michael.Godawski on 2008-12-19
> **Kevbert said:**
> Try changing your server in Software Sources.
yes, try this.
I haven't select the proposed, but I do not know how this could take effect on the installation or update of avahi-utils.

---

### Post by Joe Soap on 2008-12-19
I changed the server to "Main server" and tried again.  No luck, same error.

---

### Post by Kevbert on 2008-12-19
Please post the output of 
```
cat /etc/hosts
```

---

### Post by Joe Soap on 2008-12-19
```
~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	Andelain

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by Kevbert on 2008-12-19
What is your normal prompt, is it someusername@Andelain ? If not then the line 
```
127.0.1.1	Andelain
```
needs to be changed. Are you working behind a proxy ? (at college/university ?) - that could also be the problem.

---

### Post by Joe Soap on 2008-12-19
My computer's name is Andelain and my user name is alpha.

I'm using it from home - have another PC (intrepid) and a laptop (hoary) connected to the network.

---

### Post by Joe Soap on 2008-12-21
Found the problem - there were corrupt areas on my hard drive.  I booted with a live disk and ran fsck with the --rebuild-tree option.  On reboot from the hard drive, I was able to update avahi-utils without any problems.

---

