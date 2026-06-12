---
title: "Getting Samba to work"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by mrstevegross on 2008-05-15
I am trying to get Samba (server) set up on Ubuntu. I am using the directions found on:

  [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

I installed the samba server (sudo apt-get install smbfs). That went fine.

Then I went to the network settings. The instructions tell me to enter some stuff for both "host settings" and "windows networking". There are options available for host settings, but nothing appears under the general tab for "windows networking."

Is there somewhere else I should be looking for those settings?

Thanks,
--Steve

---

### Post by mrstevegross on 2008-05-15
BTW, this is ubuntu 8.04. I see that in earlier versions of Ubuntu the windows config was under system -> admin -> share folders. In 8.04, it apperas to be nowhere!

Thanks,
--Steve

---

### Post by jetsam on 2008-05-15
I just took a stab at this question in post # 6 of this [thread]("http://ubuntuforums.org/showthread.php?t=794576").  

Hope it helps...

---

### Post by cb951303 on 2008-05-15
```
 sudo apt-get install system-config-samba 
```

System > Administration > Samba

---

### Post by mrstevegross on 2008-05-15
> **cb951303 said:**
> ```
 sudo apt-get install system-config-samba 
```

System > Administration > Samba

Ok, I installed system-config-samba and ran the above command. However, it crashed! It created a window that said "spawning samba"; then it closed that window and alerted me to a system crash.

???

--Steve

---

### Post by jetsam on 2008-05-15
There's a bug report on that in Launchpad  [here]("https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/224599").

This is pasted from a solution suggested there:
> In the Traceback,txt I see
SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory

So, I did

sudo touch /etc/libuser.conf

and now the tool starts.........


---

### Post by mrstevegross on 2008-05-15
> **jetsam said:**
> There's a bug report on that in Launchpad  [here]("https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/224599").

This is pasted from a solution suggested there:

Ok, I got the samba config to run and set up a share. However! It is stilled not visible on my XP network browser.

I took a look at the Samba server settings, and it is indeed using the correct workgroup ('mshome').

Any ideas? (This is Ubuntu-via-VirtualBox, BTW).

Thanks,
--Steve

---

### Post by cb951303 on 2008-05-16
you should add your user to the samba group

also in samba manager make sure "visible" is checked for your shared directory ;)

---

### Post by Iowan on 2008-05-16
[This]("http://ubuntuforums.org/showthread.php?t=789444") help at all?

---

