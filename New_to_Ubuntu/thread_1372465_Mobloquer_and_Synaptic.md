---
title: "Mobloquer and Synaptic"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by punkdrummer09 on 2010-01-04
I can't open synaptic after installing Mobloquer. I two different errors while trying to open synaptic, which are:

[B]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

and


**This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.**

I also wouldn't mind just removing mobloquer, but it doesn't let me do that either. If anyone could help, I would greatly appreciate it. Thank you.



-Eric

---

### Post by arochester on 2010-01-04
It's telling you what to do.

First close everything - Synaptic, Aptitude etc.

Then open a Terminal and input: sudo dpkg --configure -a

Try again

---

### Post by jre on 2010-01-04
> **punkdrummer09 said:**
> I can't open synaptic after installing Mobloquer. I two different errors while trying to open synaptic, which are:

[B]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

This **might** be, because you aborted the installation process, when you were asked some debconf questions. Please see [this link]("https://help.ubuntu.com/community/MoBlock#I%20tried%20to%20install%20MoBlock%20but%20I%27m%20stuck%20on%20a%20screen%20with%20a%20Moblock%20warning") for more information.


> **punkdrummer09 said:**
> 
**This usually means that another package management application (like apt-get or aptitude) is already running. Please close that application first.**

Well, this is your real problem. If you can't find any open instance of synaptic/aptitude/apt-get/dpkg, then you can scan your running processes. Type in console
```
ps aux|grep -E "dpkg|apt"
```
This will give you all running processes that contain either "dpkg" or "apt".
Here I get
```
root      2246  0.0  0.0   8176   516 ?        Ss   18:54   0:01 /usr/lib/laptop-net/ifd /usr/share/laptop-net/link-change eth0
root     **10080** 25.2  2.2 122296 45432 pts/2    Sl+  21:02   0:01 aptitude
jens     10088  0.0  0.0   7284   868 pts/3    S+   21:02   0:00 grep -E dpkg|apt
```
See, Ive got a running "aptitude" process with the process id 10080. (Also note that the first process in my example is of no interest - it just contains the word "l**apt**op".)
Now I kill the aptitude process with
```
sudo kill 10080
```
and everything should work as desired.

Good luck!
jre

---

### Post by punkdrummer09 on 2010-01-04
To arochester: when I sudo dpkg --configure -a, it takes me to Configuring blockcontrol in the terminal, and I'm not to sure what to do from there.  I just unchecked everything for now.
 
To jre: I killed the process and synaptic works  again.


I completely removed mobloquer via Synaptic though. Thanks guys, I appreciate it. I will try to install it correctly at a later time. Thanks again.



-Eric

---

### Post by jre on 2010-01-04
> **punkdrummer09 said:**
> To arochester: when I sudo dpkg --configure -a, it takes me to Configuring blockcontrol in the terminal, and I'm not to sure what to do from there.  I just unchecked everything for now.

Well, in that case I am quite sure, that you just have to go through the debconf questions. Just confirm every question (as it is explained in the link that I gave you), the defaults should be ok for you.

---

### Post by punkdrummer09 on 2010-01-05
Ok thank you.

---

