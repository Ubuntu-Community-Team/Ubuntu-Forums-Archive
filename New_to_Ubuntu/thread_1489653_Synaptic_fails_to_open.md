---
title: "Synaptic fails to open"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by nnjond on 2010-05-21
Left confused by aborted Install

Hi, 
Can someone help me please? My prob it seems is that, Banshee didn't install properly and won't open. Synaptic Package Manager wont open and returns:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have failed to understand this advice But I ...

~$ sudo dpkg --configure -a
[sudo] password for nnjond: 
Setting up libgdata1.4-cil (1.4.0.2-3) ...
* Installing 14 assemblies from libgdata1.4-cil into Mono


This leads to nowhere and just hangs...

I'm hopping that someone just needs to spell out an obvious command to me that will enable me to open synaptic.

---

### Post by dFlyer on 2010-05-21
Don't know if this will help, but when I get a package that fails to install, I run 'sudo apt-get -f install' which usually fixes the problem.

---

### Post by nnjond on 2010-05-21
Thanks for your interest

~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
nnjond@nnjond-desktop:~$ 


.....?

---

### Post by Chesamo on 2010-05-21
> **nnjond said:**
> This leads to nowhere and just hangs...
You say it "just hangs". How long did you let it sit? Many processes in Linux have no in-progress output.

---

### Post by -humanaut- on 2010-05-21
sudo apt-get -f install

can install broken packages thats a fairly good way to break a system. sudo dpkg --reconfigure -a whats the output of that?

---

### Post by Chesamo on 2010-05-21
> **-humanaut- said:**
> sudo apt-get -f install

can install broken packages thats a fairly good way to break a system. sudo dpkg --reconfigure -a whats the output of that?
Might want to read the thread a little more carefully...
> **nnjond said:**
> ~$ sudo dpkg --configure -a
[sudo] password for nnjond: 
Setting up libgdata1.4-cil (1.4.0.2-3) ...
* Installing 14 assemblies from libgdata1.4-cil into Mono

This leads to nowhere and just hangs...

---

### Post by Sef on 2010-05-21
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure  -a' to correct the problem. 
E: _cache->open() failed, please report.

I have failed to understand this advice But I ...

~$ sudo dpkg --configure -a
[sudo] password for nnjond: 
Setting up libgdata1.4-cil (1.4.0.2-3) ...
* Installing 14 assemblies from libgdata1.4-cil into Mono


This leads to nowhere and just hangs...

How long have you waited?  Sometimes it takes a while for things to clear.

---

### Post by nnjond on 2010-05-21
I have waited many times, sometimes all day.

---

### Post by -humanaut- on 2010-05-21
Theres several dpkg --force options that could apply to this but those can be quite dangerous. Have you tried removing the program? and reinstalling.

---

### Post by nnjond on 2010-05-21
[QUOTE]Hi, 
Can someone help me please? My prob it seems is that, Banshee didn't install properly and won't open. Synaptic Package Manager wont open and returns:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

/QUOTE]

I dont know what my problem is or where the pkgs are

---

