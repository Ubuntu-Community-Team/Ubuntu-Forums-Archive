---
title: "update-motd issues"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Tux.Ice on 2009-03-06
I installed packages landscpae-client landscape-common update-motd

but, whenever I login, I don't see my motd changed with the system specs.

---

### Post by kevdog on 2009-03-07
Do you have a link for this particular program?

---

### Post by adult swim on 2009-03-07
is cron handling your update-motd?

---

### Post by dannyboy79 on 2010-04-28
i am also in the same boat. if I try to run update-motd isn't not even installed on the system in an up-to-date lucid install. i do however see a folder within 
/etc/
named
update-motd.d
within this folder are these:
00-header     20-cpu-checker        91-release-upgrade  99-footer
10-help-text  90-updates-available  98-reboot-required
but when i ssh into this server nothing is displayed. 

am i suppose to do something to activate the message of the day? I don't find it anywhere within /etc/cron.*  anywhere in any cron. folder.
my end goal is to try to get mythtv-status to run when i login into ssh session on the mythtv server. any help would be appreciated.

---

