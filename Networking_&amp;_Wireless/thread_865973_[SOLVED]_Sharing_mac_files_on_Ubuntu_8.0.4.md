---
title: "[SOLVED] Sharing mac files on Ubuntu 8.0.4"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by amarkitanis on 2008-07-21
Although I've read one zillion things online and on this forums I haven't managed to find anything that gave me a right solution.



I have been able to view anything i share on my mac machines, through samba on the same network-configured machine (PC running both windows vista and ubuntu 8.04) with windows, and with each machine, windows is asking me to authenticate. 

In Ubuntu 8.04, I'm able to find the machines, I click on them, the shared directories are there, but whenever I click on the following message comes up, "The folder contents could not be displayed"
I've checked the permissions, and they're assigned to read and write for everyone. 

Is there anyway I can authenticate with the mac's credentials each time I try to access a mac machine so that i can wholly access the hard disk?

for example in windows, even if i have nothing shared on the mac, under the sharing pane, it will ask me to authenticate, if i authenticate as a user administrator on the mac, i will still be able to access the mac's hard disk etc.

any advice is greatly appreciated!

P.S viewing any shared folder under ubuntu, on the mac works perfectly okay! 

Thanks.
Andreas

---

### Post by amarkitanis on 2008-07-21
please if anyone knows anything id be very grateful, ive been trying to solve this forever and it's wasting my time. it's really really important to me. i dont wanna use ssh/ftp because i use it a lot.

thanks

---

### Post by decoherence on 2008-07-21
Bring up a Nautilus file manager window and under the View menu make sure "Location Bar" is enabled.

In the location bar type

smb://yourUserName@yourHostName

for instance "smb://amarkitanis@myMacintosh" or whatever.

If this works, then I think you've come across a known bug in Nautilus.

I also think you should reconsider using ssh to share from the Mac to Ubuntu. ssh connections through Nautilus behave identically to SMB connections (that is, you can browse around the file system in the normal way -- no command line needed) and in my experience they are more stable.

---

### Post by amarkitanis on 2008-07-21
err how can i ssh without a command line? using some kind of shh gui program?

---

### Post by amarkitanis on 2008-07-21
I tried smb://Andreas@192.168.0.101 which is the mac's local ip address and it doesn't complain but nothing pop ups and nothing is shown. 

isn't there any way to authenticate myself ?

thanks

---

### Post by decoherence on 2008-07-22
> err how can i ssh without a command line? using some kind of shh gui program?

connect the same way as you did with smb. Make sure Remote Login is enabled on the Mac, then

ssh://Andreas@192.168.0.101

or

sftp://Andreas@192.168.0.101

same difference...

> I tried smb://Andreas@192.168.0.101 which is the mac's local ip address and it doesn't complain but nothing pop ups and nothing is shown.

Perhaps old/incorrect account information is in the keyring? At the terminal type

seahorse

click on the Passwords tab and trash anything that looks suspicious (right click, delete key)

hope that helps,

---

### Post by amarkitanis on 2008-07-22
seahorse did the work! thank you! 

ok just a simple question 
what's considered safer? ssh/sftp or samba? I suppose ftp/sftp?

and also which one is considered to be faster and more efficient/effective/secure?


thanks :)

---

### Post by decoherence on 2008-07-22
> **amarkitanis said:**
> seahorse did the work! thank you! 

ok just a simple question 
what's considered safer? ssh/sftp or samba? I suppose ftp/sftp?

and also which one is considered to be faster and more efficient/effective/secure?


thanks :)

For speed, I would say FTP is the king since it has the lowest overhead. For the same reason it is also the least secure. All information sent over the network can be snooped, including the password you use to connect. FTP should only be used inside a local network or preferably not at all.

Samba varies, depending on how it is configured. I'm not an expert on OS X's Samba server configuration but I imagine if it had problems, we'd hear about them. (maybe i'm being naive)

SSH/SFTP route everything through the OpenSSL encryption layer, creating a secure tunnel for your data to move through. The continuous encryption/decryption incurs some overhead but on today's hardware it is not noticeable in most cases.

I prefer ssh because it's secure, easy to set up and will run on anything. I just wish OS X had support for SFTP connections in the Finder the way Nautilus does.

---

