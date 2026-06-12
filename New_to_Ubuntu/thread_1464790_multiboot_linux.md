---
title: "multiboot linux"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by raj_vet on 2010-04-28
Hi all wonderful people, 

I want to have multiple linux distros on my system. I am new to linux, though I have been using ubuntu, linuxmint for some time. I am just a casual user. I want to have mandriva, linux mint, ubuntu and puppy linux. Dont ask why, I just want to have these.

These are my requirements:
1. I do not want these partitions to share home folder as I plan to use only one distro for my data.

2. I have read quite a few articles on partitioning and at the risk of sounding not-so-bright they stop making sense to me after first few paragraphs. So I have realized I ll need spoon fed tutorial or short instructions that make sense to "me".

3. I want to be able to select boot option at boot time.

4. though I have linux mint installed on my system. I want to do things from the start. I have tried installing puppy linux on same system but I screwed up somewhere so it didnt give me the option to boot into puppy at boot time. Thats why I want to do it from start.

---

### Post by oldfred on 2010-04-28
While this is now older it shows the planning you have to do to boot multiple systems. Grub2 does not like chainbooting but any installs that use old grub probably should be chainbooted from grub2.
chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

Multiboot with multiple partitions and separate data:
[http://ubuntuforums.org/showthread.php?t=1443814](http://ubuntuforums.org/showthread.php?t=1443814)

Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

