---
title: "Rights issue and scripting issue"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by JackNBox on 2010-11-23
I have several problems I am trying to fix.  

Problem 1: When opening files via open office on a shared folder they open in read only mode unless I launch open office as root.  I am frequently going to this share and editing files.  I am setting this share up using a ncpmount command, the credentials are provided in this command. ie

sudo ncpmount - S server -A server.me.com -U user - P password - user /mnt/server 

which leads me to my second problem.

Problem 2: I would like to be able to have a script that I could just launch via nautilus to setup my ncpmounts and or to launch open office as root.  I installed the necessary nautilus plugin for this.  If I create a script ie A.sh and put the following line in the script.

sudo soffice -writer

If I type this in at the command line in runs fine.
If I run the script from the sh A.sh it runs fine.
If I right click on the script in nautilus it asks if I want to open it or run it.  If I run it it does nothing.

Thanks
Jack

---

### Post by cariboo on 2010-11-23
Are you using a netware server?

---

### Post by JackNBox on 2010-12-01
Yes I am connecting from ubuntu to a netware server using ncpmount.

---

### Post by SeijiSensei on 2010-12-01
> **JackNBox said:**
> Yes I am connecting from ubuntu to a netware server using ncpmount.

What are the permissions on /mnt/server before you mount the Netware share?  Try making them 0777 and see if that avoids the read-only problem.  That's obviously highly insecure from the Linux side, but NW will be enforcing rights on its end.  

If granting everyone full rights solves the permissions problem, you can consider cutting back if security on the Linux client matters.  For instance, you can create an "nwusers" group, put the relevant users in the group, then "chgrp nwusers /mnt/server; chmod g+rwx,o-rwx /mnt/server" will limit access to group members.  (I presume /mnt/server is owned by root?)

---

### Post by JackNBox on 2010-12-02
Yes, this fixed my main problem, I was doing a sudo on my ncpmount when I did not need to be doing this.  I think the rest I should be able to work out when I get some time and get back to this.

Thanks
Jack

---

