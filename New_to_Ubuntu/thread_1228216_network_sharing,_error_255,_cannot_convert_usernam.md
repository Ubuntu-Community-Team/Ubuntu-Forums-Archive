---
title: "network sharing, error 255, cannot convert username to SID"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by The Boogster on 2009-07-31
Have gone over to Ubuntu from windows and loving it. Have only one problem at the moment which I have`not been able to solve. When right clicking to share a folder I get requested to install sharing services, I have samba4 installed and running. It takes off samba4 and installs samba. I then get told, on right clicking to share " net usershare returned error 255, net usershare add cannot convert username eveyone to a SID. Logon failure. I must admit my head is spinning from trying to work this out. I have a desktop (jaunty) and a laptop running mint. Can see both in network places but cannot access any files on either due to not being able to create a share on desktop. Desktop is wired to router and laptop is wireless. Any help would be much appreciated. I have found the forums amazing in there help and have learnt loads but this one has stumped me so I thought time to register. Thanks in advance everyone

---

### Post by Liolikas on 2009-07-31
[http://ubuntuforums.org/archive/index.php/t-1140216.html](http://ubuntuforums.org/archive/index.php/t-1140216.html)

---

### Post by The Boogster on 2009-07-31
> **Liolikas said:**
> [http://ubuntuforums.org/archive/index.php/t-1140216.html](http://ubuntuforums.org/archive/index.php/t-1140216.html)
Thanks for reply. Have tried this but problem I get is this. If i install samba4 and then try to share it tells me to install services and removes samba4 and installs samba, which I don`t really understand. Tried to follow advice in thread but just got a list of unknown parameters and unable to locate username. Does this make any sense to you or am I just digging a big hole and not seeing the picture!!
Thanks again for reply

---

### Post by Liolikas on 2009-07-31
I personally use pure-ftpd and sshd. maybe try them too.

---

### Post by The Boogster on 2009-07-31
i will thanks for advice. Will still keep trying to solve this though. I don`t like mysteries that I can`t solve. Hah Hah. Take it easy and will come back with any developments

---

### Post by Liolikas on 2009-07-31
eveyone you do not have user eveyone?
Mistype in config file?

---

### Post by The Boogster on 2009-07-31
will check con.f file. need to be tomorrow now. cheers and will post tomorrow.

---

### Post by The Boogster on 2009-08-01
Typo was in my post not the con.f file, sorry. Have set up sshd and working fine. Thanks for that. Will continue to mess about with the other problem to see if I can resolve it.

---

### Post by jmstern on 2009-12-23
Not sure what happened with my network, but I could ping IPs, but got an error when attempting to map a Ubuntu share from Winders XP machine.  After reading an earlier post regarding LMHOSTS file, smacked my forehead, recreated the LMHOSTS for my network, and SHAZAM.

---

