---
title: "Please clarify user permissions."
date: 2010-07-03
forum: New to Ubuntu
---

### Post by spydeyrch on 2010-07-03
So, I have been using Ubuntu off and on since, if I remember correctly, 2005. But it wasn't until 9.04/9.10 that I dove back in because I wanted freedom from large corporations, amongst other reasons.

Currently I have a tri-boot system: Win7 Pro x64, Ubuntu 10.04 x64, and Mint 9 x64. I have always been and only been the only user on my systems, so I have never really needed to setup a multi-user system in Ubuntu or any of the other linux distros that I have used.......... except once and until now.

The one time that I setup a multi-user system was just for fun and was just for learning purposes. There were no actual other users. The question that I had back then and still have now is: in the user permissions, it seemed that even though I unchecked allowing access to certain things, the user would still have access to that item. So it seemed back then that the user permissions were not even useful. Oh, and I am not talking about read, write, execute permissions to a single file/folder. I am talking about group and user permissions: i.e. internet, printers, ethernet, modems, cd-rom, audio, microphone, etc. I believe that there is a whole list of the different groups in system -> admin -> users (forgive me if I am wrong, I am at work and so don't have access to my system to check everything. I am going off of just what I remember right now.)

I will give you an example: Lets say that for Joe, a normal user, I, as the only one with the ability to use root privileges, un-select the 'cd-rom' group under Joe's user account. (and again, due to being a work, it may not be a group but a privilege under just Joe's user account, correct me if I am wrong) I would assume that by doing this, Joe would not be able to read an CDs inserted into the CD-ROM nor be able to mount the CD-ROM, right? Yet for some reason he still can. Even after a reboot of the machine, verifying that the CD-ROM group/privilege is still un-checked under his user account, if we log into his account/desktop and insert a CD, it will still mount the CD and show it on his desktop.

Another example: If I un-check the 'ethernet' group/privilege under Joe's user account, I would assume that because network traffic routed through the NIC, that Joe would not be able to use the network nor go online and surf the internet. Yet he can. So I un-check the internet group/privilege and the ethernet one too. Yet he can still gain access to the internet by simply opening Firefox or what ever browser he chooses.

So it seems to me that the user privileges aren't really working. At least how I think that they should work. Again, this is based off of the one time that I experimineted with a multi-user system and it was back in 2006, so my memory might be a little faulty.

So that is why I need a little clarification. I am in the process of setting-up a multi-user system for a friend and his family and want to make sure that I get it right. They have little children that don't need access to certain things and older children that don't need access to certain other things. It isn't that we are worried that the kids are going to trash the system. I am not concerned about that at all. The parents just want to limit access to certain things. Such as internet access, hardware access, install programs access, etc., based upon which account is logged in. Hopefully that makes sense. 

Thanks for the clarification!

-Spydey :D

---

### Post by lkjoel on 2010-07-03
An administrator can do everything.
Everyone should be in the audio group (usually).
For the CD-ROM group, that is interesting.
Try putting "joe" without sudo.

---

