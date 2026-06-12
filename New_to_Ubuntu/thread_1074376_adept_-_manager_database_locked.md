---
title: "adept - manager database locked"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by openworld on 2009-02-19
when i tried to open adept-manager this is the message i got 

Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude).
Would you like to attempt to resolve this problem? No will enter read-only mode and Cancel to quit and resolve this issue yourself.

on clicking yes , it simply crashed .... 
it's a problem from last couple of weeks, and i seriously need a access to repository now .... please reply asap 

the repository i am using is the one available in my college LAN

---

### Post by stumbleUpon on 2009-02-19
> **openworld said:**
> Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude)

The problem is clearly mentioned -- there is another process accessing the packaging system database.

See if there is another adept process running and kill it. In a terminal

```
killall adept
```

should do the job.

A simple restart of the machine will also kill any running processes -- either adept, apt-get, aptitude or synaptic

---

### Post by openworld on 2009-02-19
i have done it some 15-20 times
i am having this problem from last few weeks 

even then to be sure i tried using killall adept but it says " no process killed" :(

---

### Post by stumbleUpon on 2009-02-19
See if adept is running. Type in a terminal

```
ps -ef | grep adept
```

If you spot an adept process running, make a note of its process ID and then in a terminal

```
kill -9 AdeptProcessID
```

AdeptProcessID is the process ID, i.e., a number.

---

### Post by openworld on 2009-02-19
i tried above command and it shows ID of previous try to access adept 
then also i tried the ids' 
but the terminal crashed

---

### Post by stumbleUpon on 2009-02-19
kill all instances of adept

If you find that the terminal is crashing, go to a virtual console (Alt + Ctrl + F1) and then do the same (ps -ef | grep adept) and kill all adept processes

can you open synaptic...? can you install something with apt-get or aptitude...?

---

### Post by HavocXphere on 2009-02-19
sudo dpkg --configure -a

seems to have done the trick in the past.

---

### Post by openworld on 2009-02-19
no sudo apt-get is not working 

1 tell me how to get out of the virtual console ....... i mean to get back my GUI desktop

2 how to become root( to get all the privilages) to make dpkg work 



can this adept problem be because of viruses, what i mean to say is that i had installed wine earlier for running wordweb dictionary and had virus(trojan) in my windows hdd which creates newfolder.exe in every directory , so might be that must have got activated through wine 

but now i have removed wine from my comp

can't understand anything , whats happening

---

### Post by stumbleUpon on 2009-02-20
Ctrl + Alt + F7 gets you back to GUI desktop

sudo gives you root permissions. To go to the root account, you do 
```
sudo su
```

I dont know about viruses. Sorry.

---

### Post by HavocXphere on 2009-02-20
> **openworld said:**
> can this adept problem be because of viruses, what i mean to say is that i had installed wine earlier for running wordweb dictionary and had virus(trojan) in my windows hdd which creates newfolder.exe in every directory , so might be that must have got activated through wine
The chances of it being a virus are very very small.

As for the wine issue, you can relax. The wine environment is like a fish in a fishbowl...it can't get out and if it does then its not going to survive out of the water. Your windows programs can't run outside of wine, and windows viruses can't either....they are windows programs too after all.

---

### Post by openworld on 2009-02-20
actually what i am thinking is that it might have got activated when wine was running 

as now my every directory contains a file directory_name.exe , which is a trojan horse symptoms

---

### Post by openworld on 2009-02-20
hey dpkg worked 
can u please tell me what does it actually do 

and how come few other programs also got installed with it like wine and wordweb pro

---

