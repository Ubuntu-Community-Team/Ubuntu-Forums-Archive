---
title: "Rsync from Computer NAME instead of IP?"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by StaticIp on 2009-06-26
I am running Ubuntu 32bit Jaunty and I have rsync setup to backup my files from my laptop to my server. Sometimes my laptop is plugged into the network and sometimes its just connected via wireless. Would it be possible to have rsync look for a computer name instead of an IP address?
 
Here is what rsync runs whenever I run "backup.sh"

sudo rsync --progress --size-only --delete -mrtXEpogI _@_::Documents /home/erik/Documents
sudo rsync --progress --size-only --delete -mrtXEpogI _@_::Music /home/erik/Music
sudo rsync --progress --remove-source-files --size-only -mrtXEpogI /home/erik/.saved/ _@_::Pictures
sudo rsync --progress --size-only --delete -mrtXEpogI _@_::Pictures /home/erik/Pictures
sudo rsync --progress --size-only -mrtXEpogI _@_::Videos /home/erik/Videos

---

### Post by nandemonai on 2009-06-26
> **StaticIp said:**
> I am running Ubuntu 32bit Jaunty and I have rsync setup to backup my files from my laptop to my server. Sometimes my laptop is plugged into the network and sometimes its just connected via wireless. Would it be possible to have rsync look for a computer name instead of an IP address?
 
Here is what rsync runs whenever I run "backup.sh"

sudo rsync --progress --size-only --delete -mrtXEpogI _@_::Documents /home/erik/Documents
sudo rsync --progress --size-only --delete -mrtXEpogI _@_::Music /home/erik/Music
sudo rsync --progress --remove-source-files --size-only -mrtXEpogI /home/erik/.saved/ _@_::Pictures
sudo rsync --progress --size-only --delete -mrtXEpogI _@_::Pictures /home/erik/Pictures
sudo rsync --progress --size-only -mrtXEpogI _@_::Videos /home/erik/Videos

It is possible but would require either DNS or manually editing the /etc/hosts file and adding a reference to point a name to a IP. For example:

```
192.168.1.10 hostname
```

Easiest thing to do would be use a static IP on said laptop (should be able to use the same IP for wired / wireless for your network provided you don't connect both interfaces at the same time) then set up a hosts reference on the other machine. 

Otherwise you're going to have to look into dynamic DNS / DHCP.

Hope that helps some.

---

### Post by sdennie on 2009-06-26
If both machines are running Ubuntu then you should have avahi running on both machines and so you already have dynamic DNS for the .local domain setup.  You will probably find that this works regardless of how the laptop is connected:

```

ping your_laptop_name.local

```

---

### Post by StaticIp on 2009-06-26
Great! Got everything up and running. Everything runs as expected.

---

