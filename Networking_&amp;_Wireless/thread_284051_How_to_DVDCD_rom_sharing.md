---
title: "How to DVD/CD rom sharing?"
date: 2006-10-25
forum: Networking &amp; Wireless
---

### Post by teckfatt on 2006-10-25
Anyone know how to share the DVD/CD-ROM for the purpose of read and write(burn)?

I only have a DVD burner on one of my Desktop computer, and all the computers is running Dapper. 

I want to burn DVD directly from the computer I using(where doen't have DVD burner), by using the CD/DVD Creator (Places=>CD/DVD Creator). So anyone know how to mount and share the DVD burner on other computer??

thank you

---

### Post by matthewstory on 2006-10-25
you could try NFS:

sudo aptitude install nfs-user-server

Then set up the /ext/exports file to export your cd rom drive, and set up /etc/hosts.allow and /etc/hosts.deny to allow connections only from your other two boxes.  

Then mount the drive on the other two machines:

sudo mount <ip of machine with drive>:/path/to/share/

That'll get you as far as read access, no guarentee on the write access, though i guess it might work.

---

