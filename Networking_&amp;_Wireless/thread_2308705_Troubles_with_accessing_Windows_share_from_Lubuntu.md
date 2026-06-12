---
title: "Troubles with accessing Windows share from Lubuntu"
date: 2016-01-05
forum: Networking &amp; Wireless
---

### Post by Anzial on 2016-01-05
Hi there, (L)ubuntu newbie here. I need help troubleshooting Lubuntu installation which can no longer access the windows 8.1 share properly. 

So here's setup: I run virtualbox on Windows8.1 with Lubuntu 15.04 guest (can't upgrade to 15.10 since there's not enough space). I had it on for over a year, starting with 14.04 LTS. At the beginning with a little bit of googling, I figured out how to access a windows share on my host using PCManFM. I also installed samba to share Lubuntu folders with the host, too. 

Yesterday I've installed partial updates and since then the windows share access got borked. While Lubuntu can still access the files, read and write new ones, I can't MODIFY anything after it has been written. So I can write a bunch of files from Lubuntu to Windows share but I can no longer change them after that. I make any changes and the resulting file is emptied out. Basically, Lubuntu can write but can't change/update/modify files.

I figure it has something to do with the way Lubuntu is accessing ntfs windows share but I can't figure out why it would change so suddenly after an update, because until that moment everything was working just fine. 

I'd really appreciate some suggestions and ideas. I went through list of changes in the update and didn't find anything there suspect. I even installed a fresh Lubuntu 15.10 but it has the same issue. I guess I might try installing the older one but updates will prolly screw something up again. 

Just to clarify - I didn't change any permissions on Windows share or Lubuntu, user rights are the same but files can longer be modified. I also tried Virtualbox Share Folder thing but it's not showing up in Lubuntu either (LinuxAdditions are installed). Manual mount for vboxsf is giving me errors, too.

EDIT: Solved, kinda. I made a workaround (which I probably should have done from the beginning but I'm a newbie, live and learn lol). I've mounted the windows share permanently through CIFS and fstab, previously each reboot I had to remount manually. Seems to be working so far.

---

