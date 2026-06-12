---
title: "APT giving  error"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by bipin.nag on 2009-09-04
whenever i use apt command it gives following error :

Reading package lists... Error!
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Dynamic MMap ran out of room. Please increase the size of APT::Cache-Limit. Current value: 25165824. (man 5 apt.conf)
E: Error occurred while processing gaffitter (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/ftp.tw.debian.org_debian_dists_lenny_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

---

### Post by drs305 on 2009-09-04
Added: Actually, I see you are trying to access a Debian repository. That could very well be the issue. Deselect it in your sources.list and then accomplish the following.

For MergeList problems, an easy way to reset the lists is to open Software Sources (not Synaptic), untick all the repositories in Ubuntu Software and the Third Party tabs, then reselect them and Reload. 

That should clear any erroneous lists and reload ones without error, assuming the error is not on that server or in your sources.list. If that doesn't clear it, post your sources.list

---

### Post by bipin.nag on 2009-09-08
yes that solved my problem
thank u very much

---

### Post by bin4ryninj4 on 2010-09-01
Thanx to drs305.  I was having the same problem, only when trying to add the Backtrack 4 packages.  I was about to just do a clean install but your advice works well.

---

### Post by ZazzyE on 2010-11-03
> **drs305 said:**
> Added: Actually, I see you are trying to access a Debian repository. That could very well be the issue. Deselect it in your sources.list and then accomplish the following.

For MergeList problems, an easy way to reset the lists is to open Software Sources (not Synaptic), untick all the repositories in Ubuntu Software and the Third Party tabs, then reselect them and Reload. 

That should clear any erroneous lists and reload ones without error, assuming the error is not on that server or in your sources.list. If that doesn't clear it, post your sources.list

So... what do you do if you're trying to include sources from other, compatible distributions?  

I've passed that apt limit, gone into /etc/apt/apt.conf.d/debconf70 to add a line of code that sets the default to 2x and 4x that limit, and... well, apt doesn't recognize the difference.

Here's the code I added at the end:
```
APT::Cache-Limit “201326592&#8243;; 
```

to this code in that file:
```
// Pre-configure all packages with debconf before they are installed.
// If you don't like it, comment it out.
DPkg::Pre-Install-Pkgs {"/usr/sbin/dpkg-preconfigure --apt || true";};
```

So, is there somewhere else that I need to change things?

---

