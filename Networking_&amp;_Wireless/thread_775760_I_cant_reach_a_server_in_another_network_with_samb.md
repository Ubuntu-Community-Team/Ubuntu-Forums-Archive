---
title: "I cant reach a server in another network with samba!!!"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by pifo77 on 2008-04-30
Hi! Im new at Ubuntu Hardy, though, Ive been able to set up my laptop pretty well with the help of so many posts about everything in the web, I see all the multimedia and I can see all the pcs an access all the saherd folders in my subnet BUT ...

The problem I have is I have to access a windows server in another subnet, and I don know how to do that!!!! My lap is in the subnet 190.12.33.X and the server is in the 172.24.27.X subnet, my gateway leads me to the server, I have a correct ping response

What can I do??? :confused:

Any help will be appreciated:grin:

---

### Post by Pomble on 2008-04-30
Are both subnets using the same WINS server?

They need to be, in order to allow browsing.  See: [http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-samba-network-browsing.html]("http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/ref-guide/s1-samba-network-browsing.html")

More on this at: [http://brneurosci.org/linuxsetup38.html]("http://brneurosci.org/linuxsetup38.html")

Hope this is of help.

---

### Post by fhmanas on 2008-04-30
Well, if you can ping your destination ip of yopur Win machine, you can open nautilus and go directly to the machine 'smb://xx.xx.xx.xx', hopefully, this will open the machine for you for sharing.

---

### Post by pifo77 on 2008-05-02
Thanks! I'll try both methods and let you know what happened?

=)

---

### Post by pifo77 on 2008-05-02
Its working!!! \\:D/

The nautilus solution helped, the problem was that my windows 2003 server only allowed direct connections with the complete network path:

'smb://xx.xx.xx.xx/mysharedfolder'

Thanks a lot!!!

:-D

---

