---
title: "Samba Newbie Question"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by platoniciedeal on 2006-11-24
I am sure this is asked a lot but I could not find an answer on Google: I have Samba set up on a network with Edgy and two XP Machines. The Edgy box can see itself and the other two and logon to the share through SMB4K. THe XP boxes can see the Edgy machine but have do not get a chance to Logon. No password prompt is offered.

My .conf file:

[global]
interfaces = 192.168.0.1/24 127.0.0.1/8
security = share
wins support = yes
dns proxy = no

[homes]
read only = no

[CARTOONS]
path = /media/hdc1/CARTOONS
guest ok = yes

[MUSIC]
path = /media/hdc1/Music
guest ok = yes

What have I done wrong?

---

### Post by x64Jimbo on 2006-11-24
Did you follow the instructions [here?]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29")
That'll work well for read-only network shares. If you want r/w, go to the instructions immediately below that section.

---

### Post by platoniciedeal on 2006-11-26
I did follow the instructions but forgot to allow external connections in Firestarter. Thanks for the suggestion.

---

### Post by ac7ss on 2006-11-30
> **x64Jimbo said:**
> Did you follow the instructions [here?]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_share_public_folders_with_read_only_permission_.28Authentication.3DNo.29")
That'll work well for read-only network shares. If you want r/w, go to the instructions immediately below that section.

Thank you for that link.. Lots of good newbie info there!

---

