---
title: "[Karmic] Some kind of repository error when attempting to install Pidgin"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by becim on 2009-11-02
I'm using a clean install of the final release of Karmic. I have tried from Software Center, Terminal, Synaptic, and .deb packages. I have installed other things like Celestia, Blender, and Songbird with no problems at all but Pidgin refuses to install.

Here is what it looks like from Terminal after "sudo apt-get install pidgin" and my password:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pidgin: Depends: pidgin-data (< 1:2.6.2-z) but 1:2.6.3-1~getdeb1 is to be installed
E: Broken packages
```

and from Software Center:
```
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.
```

For my software sources, I have main, universe, restricted, and multiverse all checked. My brother installed from the same disc as I did and he is not having this problem. Does anyone know what is going on?

---

### Post by Locke_99GS on 2009-11-02
Do ```
sudo apt-get remove pidgin pidgin-data
```
then try installing Pidgin again
```
sudo apt-get install pidgin
```

It look like at one time you had installed (or tried to) a getdeb package. This confuses apt-* services sometimes when the getdeb version is greater than the repo version. I had a similar issue.

---

### Post by becim on 2009-11-02
> **Locke_99GS said:**
> Do ```
sudo apt-get remove pidgin pidgin-data
```then try installing Pidgin again
```
sudo apt-get install pidgin
```It look like at one time you had installed (or tried to) a getdeb package. This confuses apt-* services sometimes when the getdeb version is greater than the repo version. I had a similar issue.

Ah! Thank you, that worked perfectly! ;) I really appreciate your help

---

### Post by Locke_99GS on 2009-11-02
> **becim said:**
> Ah! Thank you, that worked perfectly! ;) I really appreciate your help

Not a problem, glad I could help.

---

