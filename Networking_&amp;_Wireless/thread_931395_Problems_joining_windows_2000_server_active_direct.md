---
title: "Problems joining windows 2000 server active directory"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by PardusLynx on 2008-09-27
First of all sorry about reposting this problem if a solution was already given somewhere in this forum but I coudln't find it...

I isntalled ubuntu 8.0.4 on my laptop and want to authenticate windows 2000 server active directory and access the shares including the ones requiring access privileges.

I tried several alternatives but none seem to work perfect. Everyone of them has a problem.

Howto here [http://ubuntuforums.org/showthread.php?t=91510](http://ubuntuforums.org/showthread.php?t=91510) ends uo with "No Logon Servers" problem. Even after that I can see users by "wbinfo -u", I can browse folders and access the ones weher access level set to "everyone" but for the ones access level is set to a specific user, for instance my linux user and windows server administrator, when I click on the folder it asks for password, workgroup etc and even when I enter them corrrectly it woudln't let me see what is inside the folder.

Any help is really appreciated. I really do want to prove that we can use linux as an alternative at work!

Thanks,

---

### Post by PardusLynx on 2008-10-07
Ok, I wanted to give another try with likewise-open. I set it up, finished all the steps to join the AD, everythign worked ok, I can open a session with DOMAIN\user. But when I try to connect to a share on the server it asks for my password! I type the password but it wouldn't let me see the folder contents. I even try the Administrator password but no way! 

Is there really a way to join in AD for ubuntu without problems? :x:x:x

---

### Post by likeWiseGuy on 2008-10-09
> **PardusLynx said:**
> Ok, I wanted to give another try with likewise-open. I set it up, finished all the steps to join the AD, everythign worked ok, I can open a session with DOMAIN\user. But when I try to connect to a share on the server it asks for my password! I type the password but it wouldn't let me see the folder contents. I even try the Administrator password but no way! 

Is there really a way to join in AD for ubuntu without problems? :x:x:x

When you say you want to connect to a share on the server, do you mean you are using samba? If so, that's a matter of configuring samba, not Likewise.

---

