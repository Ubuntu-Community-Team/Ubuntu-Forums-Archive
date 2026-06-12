---
title: "Ubuntu won't update."
date: 2009-07-09
forum: New to Ubuntu
---

### Post by LinuxFox on 2009-07-09
I went to apply new updates on Ubuntu 8.04, and it's not letting me update.  Instead I get an error, and it won't update.  Can someone please help me fix this problem?  If it helps, I attached a screenshot of the window.

---

### Post by Elfy on 2009-07-09
Looks like you have run out of room - do ```
df -h
```

See if the root drive is at 100% - you cna remove the apt cache for the moment to deal with what you are trying to do - but I would suggest that you look into expanding the partition as it will happen again

```
sudo apt-get clean
```

---

### Post by Paqman on 2009-07-09
How much space have you got left on your drive? Go to System > Admin > System Monitor to check.

---

### Post by LinuxFox on 2009-07-09
> **Paqman said:**
> How much space have you got left on your drive? Go to System > Admin > System Monitor to check.Oddly enough, 0 bytes.  I don't understand why since my home folder says I have 2.2 GB left.  Unless there's a way to clean out where update .debs download to.  Though, I'm also using an external hard drive to store larger files.

Thanks forestpixie, but it didn't seem to work for me.  I'd like to expand my partition, but I don't know how.  Also I don't want to risk anything unless I can back-up my stuff.  Plus I installed using Wubi, it hasn't given me problems until now.

---

### Post by Elfy on 2009-07-09
What didn't work - the clean command? The df -h command

If your root drive is full, which appears to be the case then you need to make i bigger - not quite so easy with Wubi.

---

### Post by LinuxFox on 2009-07-09
> **forestpixie said:**
> What didn't work - the clean command? The df -h command

If your root drive is full, which appears to be the case then you need to make i bigger - not quite so easy with Wubi.The clean command, it still says 0 bytes after using it, and I still got the same error installing.

Slightly off-topic, but somewhat related, I had problems installing from Synaptic earlier and getting an error.  Is this also related to my problem?

---

### Post by Elfy on 2009-07-09
aah - ok - nothing to clean out so no space will be released.

Yes - this would be related to synaptic not wanting to work.

This link is for the resizing of the virtual disk - possibly paqman knows more about resizing wubi - I'm afraid I have only played with it once a while ago.

---

### Post by Paqman on 2009-07-09
> **forestpixie said:**
> possibly paqman knows more about resizing wubi - I'm afraid I have only played with it once a while ago.

Sure, but there's a bit of a catch-22 here.

You can use [LVPM]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?") to resize Wubi's virtual disks, but to do that you need to have LVPM installed!

Some things you could try:
[LIST]
[*]Reboot. This will empty out /tmp and possibly create enough room
[*]Empty your trash, and the trash of all other users
[*]sudo apt-get clean && sudo apt-get autoremove
[*]Open up the disk usage tool as root (gksu baobab) and hunt around for any suspicious looking big files.
[*]Do you run an automated backup or other scripts? Check they haven't gobbled up your disk.
[*]If that doesn't work, temporarily remove a big app like Open Office
[/LIST]

---

### Post by LinuxFox on 2009-07-09
> **Paqman said:**
> Sure, but there's a bit of a catch-22 here.

You can use [LVPM]("https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?") to resize Wubi's virtual disks, but to do that you need to have LVPM installed!

Some things you could try:
[LIST]
[*]Reboot. This will empty out /tmp and possibly create enough room
[*]Empty your trash, and the trash of all other users
[*]sudo apt-get clean && sudo apt-get autoremove
[*]Open up the disk usage tool as root (gksu baobab) and hunt around for any suspicious looking big files.
[*]Do you run an automated backup or other scripts? Check they haven't gobbled up your disk.
[*]If that doesn't work, temporarily remove a big app like Open Office
[/LIST]Thanks, I tried some of those tips, and I successfully installed Automake (I did a synaptic file I needed as a test).

But something still confuses me.  I'm looking at the System Monitor, and  under "System Status" it says 0 bytes availble, while under the "File Systems" tab, it still says Root has 2.4 GB availible with 1.3 GB used.  Is there any reason for this?

Edit: I just tried updating, and it's a success!  Thanks, now I'm able to use the package manager and updates again.

---

