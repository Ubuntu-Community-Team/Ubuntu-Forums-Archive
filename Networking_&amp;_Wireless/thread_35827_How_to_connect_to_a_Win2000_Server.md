---
title: "How to connect to a Win2000 Server"
date: 2005-05-20
forum: Networking &amp; Wireless
---

### Post by Geronimo on 2005-05-20
Hi, I want to connect my pc (Kubuntu 5.04) to a Win200 Server. In My network there are some client (Win98) that connect themselves to the server using Uid, Pwd and Domain, for example Uid Direction, Pwd xxxxxx and Domain Corporate. They have some restriction on the shared directory on the server. The problem is that if I try to connect to the server with Kubuntu using the same Uid, Pwd and Domain, it doesen't connect. The strange is that if I try to connect with the administrator account and password it connect, but obviously wothout restriction.
What I have to do for connect my Kubuntu with a normal account on the server?
I think the server is a domain server.
Thanks

---

### Post by crmanski on 2005-05-20
Geronimo,
You do not really describe the error message you are getting when you try to connect so it is hard to say what it might be. To connect to my win2k servers in Konqueror you should only have to type something like...
smb://ServerName/ShareName
or
smb://IPAddress/lShareName

---

### Post by Geronimo on 2005-05-21
Thank you. Problem with case, in win98 typing "Forio" or "forio" is the same (it connect with Win200), in Linux no, so I typed Forio (instead of forio), now it work.
I have another problem, maybe you can help me.
In my network there is an Intel Print Server (192.168.1.10) with two Parallel (LPT1 and LPT2) and one Serial (COM1). I would like to print on the printer connected to LPT1, but I don't know how. Windows98 see this print server/port as \\Pr871dbc\PR_LPT1 but Kubuntu don't find it. I can see it if I type 192.168.1.10 but how to see the port (LPT1)? I tryed to type //192.268.1.10/LPT_1 but it find a binary files to download (???). I tryed to find a printer with the tool add printer, but without success. Maybe knowing the port number of the print server, but I don't know it, nothing on the manual about that.
Do you have any suggestion?
Thank you wery much.

---

### Post by crmanski on 2005-05-22
If in windows the printer is access via the UNC path: \\Pr871dbc\PR_LPT1 then you should be able to add the printer as a SMB/Windows printer.  If ubuntu does not see the hostname Pr871dbc then just try 192.168.1.10.  Also, you should check the manual and see if it runs a LPD queue or JetDirect interface and see if you can connect to LPT1 that way.  It is possible that it has a web interface.  Have you tried going to [http://192.168.1.10](http://192.168.1.10) to see what options you have?  What model is the print serve?

---

### Post by Geronimo on 2005-05-23
The print server is a discontinued product of intel.
[http://www.intel.com/support/netport/10100/index.htm](http://www.intel.com/support/netport/10100/index.htm)

In the lpt1 and lpt2 port there are attached two Hp Laserjet 4000.

I tryed via samba and via tcp without success.
In install printer tab, what I have to choose?
-add printer class
-add special printer

---

### Post by Geronimo on 2005-05-23
Sorry for the previous message, I tap accidentally enter:-)

The print server is a discontinued product of intel.
[http://www.intel.com/support/netport/10100/index.htm](http://www.intel.com/support/netport/10100/index.htm)

In the lpt1 and lpt2 port there are attached two Hp Laserjet 4000.

I tryed via samba and via tcp without success.
In install printer tab, what I have to choose?
-add printer class
-add special printer
   -local printer
   -..LPD remote
   -SMB (Windows)
   -TCP printer
   -IPP/HTTP CUPS
   -IPP (IPP/HTTP)
   -Other

-Printer class

I think the right is TCP printer, I tryed adding that type of printer with those setting:
192.168.1.10/pr_lpt1
192.168.1.10
smb://Pr871dbc/pr_lpt1

But without success. I tryed also using IPP, other and special printer with the above setting but nothing.
Maybe I miss or type something wrong.
Can you help me?
Thanks

---

### Post by Geronimo on 2005-05-23
Sorry again for this other post,

If in the navigator I do 192.168.1.10 I get into the configuration of the print server, but nothing of intresting, just change the IP and other unintresting (I think) things.

---

### Post by crmanski on 2005-05-23
It seems that from looking at the Manuals...
[ftp://download.intel.com/support/netport/10100/english.pdf](ftp://download.intel.com/support/netport/10100/english.pdf)
[ftp://download.intel.com/support/netport/10100/linux.pdf](ftp://download.intel.com/support/netport/10100/linux.pdf)

...that you have to setup a LPR/LPD printer and the queue needs to be called either LPT1_PASSTHRU, LPT2_PASSTHRU,or
COM1_PASSTHRU.

---

### Post by Geronimo on 2005-05-24
- Other printer type
-URL LPD://192.168.1.10/LPT1_PASSTHRU

Done.

Thank you very much, more easier than I thought. I saw that document but I don't read it carefully.

Thank you again for your patience, now I can replace the Win98 client with Linux:-)))

---

