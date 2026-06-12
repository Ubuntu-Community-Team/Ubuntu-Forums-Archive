---
title: "sbackup and SSD issue?"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-07-16
Hi Ubuntu Community:

[COLOR="Green"]**I'm running 10.04LTS with / on an SSD and /home on a separate HD. The SSD has 64Gb.**[/COLOR]

I've got another Ubuntu machine in my home network that I had planned to use to backup the 10.04LTS machine weekly.

So, I set up sbackup and used the "use a remote directory (SSH or FTP)" option on the Destination tab of sbackup to achieve my goal of backing up my 10.04 LTS machine on the other Ubuntu machine.

First, I set up ssh using instructions at: [COLOR="Blue"]**[https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html]("https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html")**[/COLOR]

After ticking the "use a remote directory (SSH or FTP)" I specified:

[COLOR="Red"]**ssh://CamilleSmith:PaSSWorD@192.168.1.67/home/CamilleSmith/BACKUP**[/COLOR]

Of course, I created /home/CamilleSmith/Backup on the backup machine.

After doing all of this, I chose "Backup Now!" button to see how things worked.

[COLOR="Green"]**sbackup overwrote my operating system on / on my 10.04 machine.**[/COLOR]  ](*,)

(I was really happy that I put /home on another hard disk... all of my settings and data were untouched.)

[COLOR="Red"]**How did I go wrong? Does sbackup first write things to / and them ship them off to the remote directory??? **[/COLOR]

Thanks!
Phil Smith de Duluthistan, GA

---

