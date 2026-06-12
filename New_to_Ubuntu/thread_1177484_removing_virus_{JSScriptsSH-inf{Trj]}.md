---
title: "removing virus {JS:ScriptsSH-inf{Trj]}"
date: 2009-06-03
forum: New to Ubuntu
---

### Post by Patrickgpg on 2009-06-03
A scan for viruses found {JS:ScriptsSH-inf[Trj]} in my /var/lib/clamav/daily-inc/daily.nbh file.  Using AVAST!, but was unable to remove it by any normal means.  How do I remove the virus? Thanks - patrickgpg [A Newbie]

---

### Post by Ocxic on 2009-06-03
Delete the file...

sudo rm /var/lib/clamav/daily-inc/daily.nbh

---

### Post by Patrickgpg on 2009-06-03
Ocxic:  Thanks! Your command removed the virus! - patrickgpg

---

### Post by Sir Jasper on 2009-06-03
Hi,

In W98SE I use both Avast and ClamWin. There is a recent problem where Avast detects a virus when Clamwin updates. Avast say it is not a False Positive and ClamWin need to fix it. 

So, the problem may return. If it does I do not believe, after reading about it in the Avast Forum, that it is a pain rather than real problem.

In 'buntu I only use Avast so I've only seen this (assuming it's the same problem) using W98SE.

My regards

---

### Post by albinootje on 2009-06-03
> **Patrickgpg said:**
> A scan for viruses found {JS:ScriptsSH-inf[Trj]} in my /var/lib/clamav/daily-inc/daily.nbh file.  Using AVAST!, but was unable to remove it by any normal means.  How do I remove the virus? Thanks - patrickgpg [A Newbie]

A virus in your clamav anti-virus database ? What a coincidence.. 
Which "intelligent" anti-virus software did discover that ?

Is your clamav based anti-virus software still running OK ?

---

