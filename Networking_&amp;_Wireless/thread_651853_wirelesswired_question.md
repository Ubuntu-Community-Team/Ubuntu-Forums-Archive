---
title: "wireless/wired question"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by digga on 2007-12-28
i have a linksys wireless router w/a wired connection to my main pc running 7.10. i have my laptop running windows that uses the wireless connection. i was wondering if i could transfer files from the windows machine to the linux machine.

basically i want to transfer all my mp3's from the laptop to the linux machine. can this be done w/o any major headaches?

---

### Post by carverj on 2007-12-28
> i have a linksys wireless router w/a wired connection to my main pc running 7.10. i have my laptop running windows that uses the wireless connection. i was wondering if i could transfer files from the windows machine to the linux machine.

basically i want to transfer all my mp3's from the laptop to the linux machine. can this be done w/o any major headaches?

Hi there,
               Can you ping the IP address of the linux box?
If so, you need to setup samba sharing or CIFS on the linux box, which will allow you to share with Windows.

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server)

Have fun mate!!
:)

---

### Post by digga on 2007-12-28
i think i just installed samba the other day. i havent tried to ping this box yet. 

hopefully this will all work out.

edit:

i plugged the external hdd into the windows machine and shared the drive. it showed up after i installed samba on the linux box. i am copying files as i type this right now. not that bad a deal really.

---

