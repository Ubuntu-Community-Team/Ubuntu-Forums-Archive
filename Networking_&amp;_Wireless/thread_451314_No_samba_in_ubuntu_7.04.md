---
title: "No samba in ubuntu 7.04"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by kanna1620 on 2007-05-22
Hi all!
I installed the Ubuntu 7.04 a few days before. And from then I tried a lot to get my computer visible over my LAN. But no system in my LAN can access my system. I tried to install and run samba server. But it did not work. I tried a lot. I read a lot of howto's with no use. I am undone. Please someone post the Howto for running the samba share please. Please someone please post.:(:(:(:(

---

### Post by JSThePatriot on 2007-05-22
> **kanna1620 said:**
> Hi all!
I installed the Ubuntu 7.04 a few days before. And from then I tried a lot to get my computer visible over my LAN. But no system in my LAN can access my system. I tried to install and run samba server. But it did not work. I tried a lot. I read a lot of howto's with no use. I am undone. Please someone post the Howto for running the samba share please. Please someone please post.:(:(:(:(

Hey,

I have samba running, and it really wasn't that hard. I hope the below works out for you.

Goto System > Administration > Shared Folders

Just by doing that Ubuntu then asked me if I wanted to install (probably after inputing my password) samba (install could mean activate/use). I agreed. (Possibly had to put in my password again), and I have samba shares.

I hope this helps you get going,
JS

---

### Post by JSThePatriot on 2007-05-22
This also may help you!

[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html](http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html)

This one actually should help you more.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

JS

---

### Post by kanna1620 on 2007-05-22
> **JSThePatriot said:**
> Hey,

I have samba running, and it really wasn't that hard. I hope the below works out for you.

Goto System > Administration > Shared Folders
JS
 Thanks for the quick response. I installed Samba in the same manner. But it is not working.

---

### Post by JSThePatriot on 2007-05-22
> **kanna1620 said:**
> Thanks for the quick response. I installed Samba in the same manner. But it is not working.

When you say it is not working what do you mean? (Explain further please, such as can you not access what you thought you should be able to from another machine?)

Have you checked to be sure the service is running?

Also as a side note my Samba has seemingly worked, and stopped working off and on. I am trying to run through all these settings with you at the same time to see what I can get working completely.

JS

---

### Post by JSThePatriot on 2007-05-22
Might want to take a peek at this thread, and watch it.

[http://ubuntuforums.org/showthread.php?t=449145](http://ubuntuforums.org/showthread.php?t=449145)

JS

---

### Post by lhuser on 2007-05-22
Have you installed all the samba stuff in Synaptic? Is there any dependency conflict?

---

### Post by JSThePatriot on 2007-05-22
Okay I got it... I am documenting and going to post it here now!! Give me just a few moments to get all the pieces together.

JS

---

### Post by JSThePatriot on 2007-05-22
Okay below is exactly how I performed my share and was able to get it to work. Let me know if that helps!

```
// Create a Shared Folder...GUI
System > Administration > Shared Folders

// Make a back up of your smb.conf
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf_backup

// Edit smb.conf File to setup proper sharing
gksudo gedit /etc/samba/smb.conf

// I am going to start from the top down. If these are
// in a different order then I am sorry.

// Scroll down until you see "####### Authentication #######"
After the comments set "; security = user" to "security = share"

// Scroll down a few lines
Set "; guest account = nobody" to "guest account = nobody"

// Now you scroll down until you see the share you are sharing
// in braces "[]" (Mine is [PublicShared]). Use the following to
// configure your settings. (Add as neccessary)
path = /home/username/PublicShared
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
guest ok = yes

// Save settings, and check the settings to be sure they are
// saved properly
sudo testparm

// Restart Samba to apply changes
sudo /etc/init.d/samba restart
```

If this doesn't work for you I would replace your smb.conf with the backup we made as follows.```
sudo cp /etc/samba/smb.conf_backup /etc/samba/smb.conf
```

I hope this helps,
JS

---

### Post by kanna1620 on 2007-05-23
> **JSThePatriot said:**
> Okay below is exactly how I performed my share and was able 

// Scroll down until you see "####### Authentication #######"
After the comments set "; security = user" to "security = share"


I hope this helps,
JS

Very very thanks . It worked great

---

### Post by JSThePatriot on 2007-05-24
> **kanna1620 said:**
> Very very thanks . It worked great

Excellent! Now I am going to link some people on this!
JS

---

