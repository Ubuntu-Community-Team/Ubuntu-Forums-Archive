---
title: "Edimax print server"
date: 2007-09-06
forum: Networking &amp; Wireless
---

### Post by auralay on 2007-09-06
Greetings. I have a Dell Inspiron 510. It's 3 years old and as a confirmed DOS-head it has taken me that long to get the broadcom wireless card working on linux. Big THANKS to Ubunto docs.
I now have full functionality with Feisty, though it frequently hangs on booting.

Next stage is to use an Edimax PS-901print server.
The Unux install guide says:- 

***********************************************
You will need to perform the tasks below, logged in as the superuser (root).  To configure your Unix host for printing,

1.  Optionally, assign a name corresponding to the PrintSir’s IP address.  You can add this address to the /etc/hosts file, by adding a line such as:

203.66.191.186        pserver

2.  Create a spool directory for the printer in the same directory where spool directories are normally kept on the machine, such as /var/spool or /var/spool/lpd:

mkdir /var/spool/lpd/pserverd

chown daemon /var/spool/lpd/pserverd

chgrp daemon /var/spool/lpd/pserverd

chmod 775 /var/spool/lpd/pserverd

3.  Add an entry to the host’s /etc/printcap file, similar to the following:

printer-name:\

  :lp=:\

  :rm=203.66.191.186:\

  :rp=lpt1:\

  :lf=/var/spool/lpd/pserverd.log:\

  :sd=/var/spool/lpd/pserverd:\

  :mx#0:

Lines should be indented with tabs. More than one printer name can be used, with variants separated by vertical bars (name1|name2).

The rm= entry should correspond to the IP address you have assigned to the PrintSir. You can also use a host name if you have assigned one in the /etc/hosts file.

The sd= entry should correspond to the spool directory you created in the previous step.

The rp= entry should correspond to the port name of the remote printer. The values should be one of lpt1, lpt2 or lpt3 depends on the printer port.

The PrintSir should now be available for printing from your Unix host.
******************************************
Part 1 is optional so I can try later.

Part 2, the pserverd directory seemed to go ok, I could not see a /var/spool/lpd directory so I put it straight in the /var/spool/ directory.

Part 3, I cannot see a directory /etc/printcap.

Can anyone please tell me 
a) the equivalent directory in Fiesty
b) what are the commands to edit the file- expect I will have to use sudo in the command line terminal?

Thanks, JG.

---

### Post by auralay on 2007-09-12
Ok, I solved this.
I found I could install it simply as a network printer. Works like a charm!

---

