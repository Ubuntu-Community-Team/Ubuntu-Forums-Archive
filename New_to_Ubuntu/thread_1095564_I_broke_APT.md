---
title: "I broke APT"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by DBrocks on 2009-03-13
Well here's the deal
I decided to give the  network manager nagios a try, an installed it via apt-get install nagios3

However, I decided after playing around, i wanted fresh config files, so I deleted /etc/nagios3/*. Then I went to apt-get remove nagios3, and it says this:

```
The following packages will be REMOVED:
  nagios3
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 3969kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 42156 files and directories currently installed.)
Removing nagios3 ...
 * There is no configuration file for Nagios 3.
invoke-rc.d: initscript nagios3, action "stop" failed.
Processing triggers for man-db ...
```

Since it cant stop it, it cant remove it, and I cant get the new version. Any ideas?

---

### Post by DBrocks on 2009-03-13
Yay! I figured it out

```
aptitude purge nagios3
```
Then a normal apt-get got it reinstalled. Man that was so stupid of me :D

---

### Post by 73ckn797 on 2009-03-19
Just a question. I assume that by deleting the directory, that the apt remove command could not find what it was looking for. The "purge" command apparently ignored what could not be found and did the rest of the stuff by default. Does this sound correct?

---

### Post by DBrocks on 2009-03-19
Well, now that you ask: when I tried to run apt-get remove, It tried to run the stop command. However, the stop command was linked to a script I deleted. So, It couldn't find the script, and it wouldn't kill the process, and so it would fail. I just "touched" the conf file, and it seemed to work again. Then apt-get remove --purge worked.

---

### Post by 73ckn797 on 2009-03-19
I asked because one time I executed a remove command but still had lingering issues. The purge command completely eliminated whatever was left "hanging" around causing conflicts and/or residual effects.

---

### Post by DBrocks on 2009-03-19
I see. Apt is fantastic. I absolutely love it... Except for when it breaks. But usually when it breaks, it's a somewhat simple fix.

---

### Post by 73ckn797 on 2009-03-19
HaHa! Most of my Ubuntu problems are self inflicted.

---

