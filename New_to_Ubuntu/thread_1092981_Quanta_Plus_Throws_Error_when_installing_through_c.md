---
title: "Quanta Plus Throws Error when installing through console"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-03-11
When I run ```
sudo apt-get install quanta
``` I get the following messages about broken dependencies: ```
jeff@jeff-ubuntu:~$ sudo apt-get install quanta
[sudo] password for jeff: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  quanta: Depends: kfilereplace (= 4:3.5.10-0ubuntu1) but it is not going to be installed
          Depends: klinkstatus (= 4:3.5.10-0ubuntu1) but it is not going to be installed
E: Broken packages

```

Any idea how I can fix these so Quanta will install?

~Jeff

---

### Post by SunnyRabbiera on 2009-03-11
why dont you just do it with synaptic?

---

### Post by beastrace91 on 2009-03-11
Grr I should really try things before I come post about, I apt-get install the two files it was talking about and it works fine now.

~Jeff

---

