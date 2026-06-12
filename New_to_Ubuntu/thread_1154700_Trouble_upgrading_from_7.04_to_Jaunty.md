---
title: "Trouble upgrading from 7.04 to Jaunty"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by epickert on 2009-05-10
Trying to upgrade from 7.04 to Jaunty, I cannot seem to get apt-get -d upgrade to do it from the terminal, even after "update". The GUI under System does not seem to find any new packages either. Should I be using aptitude?


My sources are:
main, universe, restricted and multiverse, according to the checkboxes on the Software Sources GUI.

Is there an easy command to access my sources list? Is that likely the problem?

---

### Post by pastalavista on 2009-05-10
You can only uprade in place from the immediately preceding release (ie. 8.10). My advice would be to back up your /home directory and do a clean install of 9.04. Then copy your backup into the new /home. If you create a separate /home partition when you install, it will be much easier to upgrade in the future. Then, you'd only have to format the / partition.

---

### Post by perpetualcacophany on 2009-05-10
Aren't the repos for 7.04 closed now? It's support has been ended since October. I would reccomend a fresh install after backing up your /home as well. If you are really using 7.04 then you definitely won't see the upgrade. If you just mistyped and you mean 8.04 then I would still suggest a new install. Upgrades tend to be buggy.

---

### Post by kansasnoob on 2009-05-10
Support for 7.04 dropped some time ago (nearly 8 months ago), so the only option is to download or otherwise acquire either 8.04.2, 8.10, or 9.04.

Actually 6.06 will still upgrade to 8.04.2 for about a month but it's a mess!

---

### Post by kansasnoob on 2009-05-10
> **pastalavista said:**
> You can only uprade in place from the immediately preceding release (ie. 8.10). My advice would be to back up your /home directory and do a clean install of 9.04. Then copy your backup into the new /home. If you create a separate /home partition when you install, it will be much easier to upgrade in the future. Then, you'd only have to format the / partition.

Good point!

Where 7.04 was not an LTS you'd have to upgrade to 7.10 - then 8.04 and onward! But I don't think that's even possible now!

---

### Post by k3lt01 on 2009-05-10
You can upgrade from 7.04 but it's lot of work and the downloads (4 separate upgrade downloads at least and alot of work with the sources.lists file) involved are way beyond what you would download with a new Cd and fresh install.

---

