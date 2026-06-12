---
title: "Transfering files between two users Linux/win xp"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by maksym on 2007-03-03
Hi,

I would like to transfer very large files (500+ mb) between two computers over the Internet. I run Ubuntu 6.10 another user runs windows XP. Could anyone suggest a good application to do this, preferably with resume support? 

FTP server is not acceptable since both computers are in LAN networks. 
I have tried skype but the speed seems to be VERY low - much lower than the actual speed of internet connection of both computers.

If this question was already answered in this forum - please redirect, as I could not find it.

Thank you!

---

### Post by Mr. C. on 2007-03-03
You say FTP is not acceptable, but your reason why isn't very clear.  FTP can be used anyplace, but firewalls need to be configured to allow FTP traffic.

Are one, or both of you firewalled in general?  What ports do you have access to ?  SSH?  HTTP?

Give a better description of your environments.

MrC

---

### Post by maksym on 2007-03-03
> **Mr. C. said:**
> You say FTP is not acceptable, but your reason why isn't very clear.  FTP can be used anyplace, but firewalls need to be configured to allow FTP traffic.

Are one, or both of you firewalled in general?  What ports do you have access to ?  SSH?  HTTP?

Give a better description of your environments.

MrC

Both computers are firewalled. Mine is behind my own hardware router firewall. Another computer is a part of a very large network and the firewall is setup by ISP. 
However the real problem is that the other user who needs to send files to me is a computer novice and in another country. I would deem next to impossible to  teach him how to setup an ftp and fight the firewall. So technically it might be possible but imagine teaching your grandma how to use ndiswrwapper, for example :)

---

### Post by Mr. C. on 2007-03-03
Ok, then, setup WebDav in an apache web server.  He can then drag-n-drop his file onto your website.

---

### Post by maksym on 2007-03-03
Thanks a lot, will try it

---

### Post by Tichondrius on 2007-03-04
> **Mr. C. said:**
> Ok, then, setup WebDav in an apache web server.  He can then drag-n-drop his file onto your website.

The two best protocols for file transfer over the internet (as opposed to a lan) are HTTP and SSH (which includes secure FTP). 

For HTTP, the sending computer must run HTTP server (e.g. apache), and the firewall must be configured to allow traffic on port 80. The receiving computer can then browse to the sender's IP address and get the file with the appropriate URL. If you want to send and receive in both directions, then both computers need to run a web server. Or you can use WebDAV like suggested above.

The other option which is easier and more secure, is to use SSH. Just install SSH server on Ubuntu (apt-get install ssh) and install SSH client on windows (download WinSCP), and then connect from the client to the IP address of the Ubuntu machine. This will allow you to transfer files using a file explorer interface in windows. Obviously you need to oopen the SSH port (22) in the firewall protecting your ubuntu machine.

---

### Post by Mr. C. on 2007-03-04
I wouldn't go that far.  SSH is the right choice when security is a concern.  It is not the right choice when security is not an issue and files are very large files (there is a significant penalty paid for the encryption layer).

There is a reason why HTTP and FTP are THE primary protocols for transferring a significant portion of general content.

OP - consider setting up YOUR system as the FTP server, and show the user how to use their browser to connect via browser.  

  [ftp://user](ftp://user) : password @ ftpserver/url-path

(remove spaces from above) 

Then, its all drag and drop.

On note of caution, the password above goes over an insecure net.  Be sure that there is no secure content on your site, and that you frequently monitor the server and change the password.

MrC

---

### Post by maksym on 2007-03-04
> **Mr. C. said:**
> I wouldn't go that far.  SSH is the right choice when security is a concern.  It is not the right choice when security is not an issue and files are very large files (there is a significant penalty paid for the encryption layer).

There is a reason why HTTP and FTP are THE primary protocols for transferring a significant portion of general content.

OP - consider setting up YOUR system as the FTP server, and show the user how to use their browser to connect via browser.  

  [ftp://user](ftp://user) : password @ ftpserver/url-path

(remove spaces from above) 

Then, its all drag and drop.

On note of caution, the password above goes over an insecure net.  Be sure that there is no secure content on your site, and that you frequently monitor the server and change the password.

MrC


yes, actually setting up my own ftp and than letting the user to upload files would probably the simplest. Let me see if I can get the port forwarding right in my router settings...

---

### Post by Mr. C. on 2007-03-04
> **maksym said:**
> yes, actually setting up my own ftp and than letting the user to upload files would probably the simplest. Let me see if I can get the port forwarding right in my router settings...

If you have trouble making the connection, be sure to learn about PASV.

MrC

---

