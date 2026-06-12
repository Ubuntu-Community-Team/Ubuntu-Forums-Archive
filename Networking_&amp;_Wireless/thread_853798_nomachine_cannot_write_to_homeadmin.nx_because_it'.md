---
title: "nomachine cannot write to /home/admin/.nx because it's not writable."
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by RavUn on 2008-07-08
I'm trying to use nomachine and test it out on my two computers at home.  I try to log in and it connects and authenticates then tries to create a session but throws an error.  I checked the log and it says:
```

Jul  8 22:20:27 RavUn NXNODE-3.2.0-11[2949]: ERROR: NX> 596 ERROR: execution of last command failed [eC75901] Logger::log nxnode 2893
Jul  8 22:20:27 RavUn NXNODE-3.2.0-11[2949]: ERROR: NX> 596 last command: /bin/bash --login -c 'mkdir -p /home/ravun/.nx/C-RavUn-1002-654E835FC07EDA2562DC71AF878B275C' [eC75901] Logger::log nxnode 2893
Jul  8 22:20:27 RavUn NXNODE-3.2.0-11[2949]: ERROR: NX> 596 exit value: 1 [eC75901] Logger::log nxnode 2893
Jul  8 22:20:27 RavUn NXNODE-3.2.0-11[2949]: ERROR: NX> 596 stdout:  [eC75901] Logger::log nxnode 2893
Jul  8 22:20:27 RavUn NXNODE-3.2.0-11[2949]: ERROR: NX> 596 stderr: mkdir: cannot create directory `/home/ravun/.nx': Permission denied [eC75901] Logger::log nxnode 289Z

```

I took a look at the .nx folder and it's owned by root and I cannot change anything with it.  How'd this happen and how could I correct it?  I was hoping to use sudo and remove the folder (then create it again) but it says it cannot be removed because it's a directory.  I've been slowly working on this all day :P



*EDIT: Ok, I found out you type rm -rf to remove directories.  I did that and it works... I can start a session with my nomachine client.  Too bad nomachine froze... twice:(

---

