---
title: "migrating /home to new install"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by edzell on 2010-11-23
I've scanned various threads in the forums about partitioning and migrating /home to fresh installs but am still a mite confused about how to handle this.

I'm still relatively new to Linux/Ubuntu/Mint. Running Mint 9, contemplating a move up to Mint 10. I think a fresh install is to be preferred over a literal upgrade. My quandary is how best to handle my home & data files. I have a Data folder within /home; no problem there, I just copy & paste into the new install. But what about the rest of /home? Presumably it includes some other application data & software configurations I don't want to lose. But on the other hand if I copy & paste it, won't some of it be in conflict with some aspects of the new install?

I've seen advice to keep /home on a separate partition but don't see how that would help. Surely conflicts could still arise? I think I've even seen comments that this is a bad idea. How do most folks handle these issues when moving to a new release?

---

### Post by dFlyer on 2010-11-23
When I update I usually just tar the directories I want to keep out of my home folder and than just untar then after the install is complete.

---

### Post by Zzl1xndd on 2010-11-23
For the most part copying and pasting should be fine (just ensure you get all the hidden folders as well). 

This will copy over all the config files for any of the programs you are using. If you do a clean install you will still need to reinstall your applications, however once done it should pull all your settings from the config files.

I use a separate home partition so when I reinstall I don't have to copy anything over its already there. So far I have had no issues with this configuration.

---

### Post by lobralleo on 2010-11-23
In the past, I used to just copy the whole /home/myself/ directory someplace else (an external hard drive or the like) and copy it back after reinstall.

However, based on my personal experience, I would definitely recommend the separate /home partition: this way, you can mess with your system without the risk of compromising your personal data - and the other way around, of course! :)
I have been using this configuration for several years and it saved me several times.

As a rule of thumb, it should be enough to dedicate about 10-20 GB to the root (/) partition, up to 2 GB to swap and the remaining of your hard drive to /home.

---

