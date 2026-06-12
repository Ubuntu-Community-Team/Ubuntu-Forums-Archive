---
title: "How can I do stuff as root!?"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by the-new-x on 2011-08-14
OK, so here's the deal, every time I try to mount my external hard drive, Ubuntu keeps telling me that I do not have sufficient permissions and keeps telling me some stuff about FUSE or something like that, and other times I just want to do anything with Ubuntu, and it starts telling me that I should be root. So I guess that you have already figured out that I want to know how I can become the root, any help would be greatly appreciated, and thank you in advance!

---

### Post by haqking on 2011-08-14
> **the-new-x said:**
> OK, so here's the deal, every time I try to mount my external hard drive, Ubuntu keeps telling me that I do not have sufficient permissions and keeps telling me some stuff about FUSE or something like that, and other times I just want to do anything with Ubuntu, and it starts telling me that I should be root. So I guess that you have already figured out that I want to know how I can become the root, any help would be greatly appreciated, and thank you in advance!


root is disabled by default in Ubuntu and you should have no need to enable it.

see here

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

everything that requires root priveleges is done using sudo or gksudo in graphical apps

---

### Post by the-new-x on 2011-08-14
> **haqking said:**
> root is disabled by default in Ubuntu and you should have no need to enable it.

see here

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

everything that requires root priveleges is done using sudo.
Yes, but I would like to use a GUI interface (like Disk Utility) in order to mount and unmount and change partitions and labels to my HDDs. So is there a way to become root, or have root privileges, cause to be honest, I want to see what lies in the root folder as well. ;)
And thanks for the reply!

---

### Post by haqking on 2011-08-14
> **the-new-x said:**
> Yes, but I would like to use a GUI interface (like Disk Utility) in order to mount and unmount and change partitions and labels to my HDDs. So is there a way to become root, or have root privileges, cause to be honest, I want to see what lies in the root folder as well. ;)
And thanks for the reply!


like i said see above link

Root is not enabled and you dont need root.

you do admin tasks as sudo or graphical apps gksudo as outlined in the above link

---

### Post by babakott on 2011-08-14
___

---

### Post by coffeecat on 2011-08-14
> **the-new-x said:**
> Yes, but I would like to use a GUI interface (like Disk Utility) in order to mount and unmount and change partitions and labels to my HDDs.

Those GUI applications that require root privileges for certain tasks will prompt you for your password when that is needed. Disk Utility is as good an example as any. When you ask it to create or re-format a partition, it will ask you for your password. Easy!


> **the-new-x said:**
>  So is there a way to become root, or have root privileges, cause to be honest, I want to see what lies in the root folder as well. ;)

Read the link haqking posted and, believe me, the contents of /root are very boring. :wink:

---

### Post by SavageWolf on 2011-08-14
**DON'T FOLLOW BABAKOTT'S INSTRUCTIONS, IT'S A SECURITY FLAW** thingy.

Anyway, Disk Utility and the like should prompt you for your password when they start (In a grey box thing), if they don't, uh, reply or something.

---

### Post by the-new-x on 2011-08-14
> **coffeecat said:**
> Those GUI applications that require root privileges for certain tasks will prompt you for your password when that is needed. Disk Utility is as good an example as any. When you ask it to create or re-format a partition, it will ask you for your password. Easy!




Read the link haqking posted and, believe me, the contents of /root are very boring. :wink:
but it is not  asking me for a password, which is driving me crazy... But the MoutManager works fine to mount and unmount drives, but i think that it lacks some options (or I haven't found them yet), which is the real reason I am asking this question

---

### Post by the-new-x on 2011-08-14
> **SavageWolf said:**
> **DON'T FOLLOW BABAKOTT'S INSTRUCTIONS, IT'S A SECURITY FLAW** thingy.

Anyway, Disk Utility and the like should prompt you for your password when they start (In a grey box thing), if they don't, uh, reply or something.
Some programs like MountManager do ask me about the password, but Disk Utility doesn't!

---

### Post by Frogs Hair on 2011-08-14
GUI applications that require elevated permissions will display a password prompt if that option is included . In Nautilus you can look in the file system but , to remove or change items from those folders requires the su , sudo , or gksu command .

---

### Post by coffeecat on 2011-08-14
> **babakott said:**
> Root is not enabled, however you CAN enable it. But its not recommended. To enable it you can type 

@babakott, before you are tempted to tell someone how to enable the root password again, please read this first:

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

Although haqking's RootSudo link does provide those details, it puts this in context and outlines the potential problems, which you have not done. You might want to read that link as well.

> **babakott said:**
> Give root a password and log in as root.

<snip>

I haven't done this in Ubuntu, but I am fairly sure it will work.

If you mean login graphically, then it won't work in Ubuntu, and telling someone how to make it work in Ubuntu is a total no-no here. And quite rightly, imo.

---

### Post by haqking on 2011-08-14
> **babakott said:**
> Root is not enabled, however you CAN enable it. But its not recommended. To enable it you can type 
```
<snip>
```Give root a password and log in as root. Keep in mind if you do this, you can destroy your system if you fat finger the wrong command.

I haven't done this in Ubuntu, but I am fairly sure it will work.

enabling of Root is not supported and circumvents Canonicals security model.

---

### Post by the-new-x on 2011-08-14
> **haqking said:**
> like i said see above link

Root is not enabled and you dont need root.

you do admin tasks as sudo or graphical apps gksudo as outlined in the above link
I read the link, and now I fully understand, which leaves me with 1 question, what is the best alternative, this is the error code I am getting from Disk Utility every time I try to do anything with my HDD or SD card:

From SD:
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/mmcblk0p1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


From HDD:

What the H*ll, it worked without an error with the HDD, it always gave me this error when I try to mount or unmount the HDD, but this time it didn't, I guess the problem is solved, **somehow**!

---

### Post by the-new-x on 2011-08-14
> **haqking said:**
> like i said see above link

Root is not enabled and you dont need root.

you do admin tasks as sudo or graphical apps gksudo as outlined in the above link
I read all of that page, and now I understand it, thanks again for the link!

---

### Post by the-new-x on 2011-08-14
> **SavageWolf said:**
> **DON'T FOLLOW BABAKOTT'S INSTRUCTIONS, IT'S A SECURITY FLAW** thingy.

Anyway, Disk Utility and the like should prompt you for your password when they start (In a grey box thing), if they don't, uh, reply or something.
Will not do, cause I read the link, and now I understand!

---

### Post by babakott on 2011-08-14
Read the rules, didnt know I wasnt supposed to tell folks how too. Sorry.

---

### Post by coffeecat on 2011-08-14
> **the-new-x said:**
> but it is not  asking me for a password, which is driving me crazy...

> **the-new-x said:**
> Some programs like MountManager do ask me about the password, but Disk Utility doesn't!

Please re-read my post.

> **coffeecat said:**
> Disk Utility is as good an example as any. [SIZE="4"]When you ask it to create or re-format a partition[/SIZE], it will ask you for your password. Easy!

Works for me! :wink:

---

### Post by haqking on 2011-08-14
> **babakott said:**
> Its not a security flaw. It is adding a password to root to enable it. And do you think it will make his system explode or something? I think you may be overreacting a bit.

as said already if your read the thread and the link provided.

Enabling root in Ubuntu is not supported and circumvents Canonical security model.

Read the CoC also

---

### Post by the-new-x on 2011-08-14
So I guess problem somehow solved, and now I know a little bit more about ubuntu thank you haqking for the link, really helpful, and thanks to all the others who took the time to read and reply as well, again thank you!
-A still happy Ubuntu user...:D

---

### Post by haqking on 2011-08-14
> **the-new-x said:**
> So I guess problem somehow solved, and now I know a little bit more about ubuntu thank you haqking for the link, really helpful, and thanks to all the others who took the time to read and reply as well, again thank you!
-A still happy Ubuntu user...:D

you are welcome.

remember to use the thread tools to mark thread as solved

cheers

---

### Post by the-new-x on 2011-08-14
> **haqking said:**
> you are welcome.

remember to use the thread tools to mark thread as solved

cheers
Will do!

---

### Post by Elfy on 2011-08-14
There should be no need to set a root password to enable su. 

That said there is - apparently - sometimes a need, never found it personally. 

[This is this forum staff policy on root - more we are concerned with logging is a root. ]("http://ubuntuforums.org/showthread.php?t=1486138")

> Thus the intent of the policy is we prefer if people educate new users re: permissions, etc, etc, rather then simply instruct them to set a root pw.

Personally if I'm off to do a lot of things I will use sudo -i

---

