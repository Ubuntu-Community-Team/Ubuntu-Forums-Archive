---
title: "Cannot Connect to Shared Drive on Windows Server 2012 R2"
date: 2015-02-03
forum: Networking &amp; Wireless
---

### Post by glauzex on 2015-02-03
Hi, currently I'm working as an IT Staff responsible for migrating several PC into Ubuntu 14.04 LTS
My problem is I can't connect my Ubuntu to my shared drive on Windows Server 2012 R2

I've googled for this topic a little while ago and find out that I supposed to this:

1. Open "File Manager"
2. Click "Connect to Server"
3. And then enter my server Address >> smb://[myhostname-in-uppercase]/[drive-letter]

The problem is everytime I try to connect my Ubuntu always shows a message saying either "Connection Timed Out" or "Connection Refused"

I've double checked everything, every PC in my office had no problem regarding this problem (since they used Windows 7)

Was I supposed to enter my server IP Address as the hostname? Like this >> smb://xxx.xxx.x.xx
or like this >> smb://WIN-HOSTNAME/F ??

I tried to look at my server configuration, and I don't see any settings that block specific PC connection, because I just did a fresh install on this computer...

Help me, since I can't find any other solution for this problem...

---

### Post by bab1 on 2015-02-03
> **glauzex said:**
> Hi, currently I'm working as an IT Staff responsible for migrating several PC into Ubuntu 14.04 LTS
My problem is I can't connect my Ubuntu to my shared drive on Windows Server 2012 R2

I've googled for this topic a little while ago and find out that I supposed to this:

1. Open "File Manager"
2. Click "Connect to Server"
3. And then enter my server Address >> smb://[myhostname-in-uppercase]/[drive-letter]

The problem is everytime I try to connect my Ubuntu always shows a message saying either "Connection Timed Out" or "Connection Refused"

I've double checked everything, every PC in my office had no problem regarding this problem (since they used Windows 7)

Was I supposed to enter my server IP Address as the hostname? Like this >> smb://xxx.xxx.x.xx
or like this >> smb://WIN-HOSTNAME/F ??

I tried to look at my server configuration, and I don't see any settings that block specific PC connection, because I just did a fresh install on this computer...

Help me, since I can't find any other solution for this problem...
Files (actually it's Nautilus) uses either UPPER or lower case names or the server's IP address.  You should use this format however; smb://server_name/share-name or smb://<IP Address/share_name.  If you use the server name it ultimately is the NETBIOS NAME.  This may or may not be the servers Linux hostname.  The share name is whatever the administrator named the share.  You can see the shares available with this command.```
smbtree
```

You can also diagnose problems with that command by adding debug to it.  Post the output of this so we can help you```
smbtree -d3
``` 

Post this output using the [noparse]```
 
```[/noparse] blocks.  You can use the [SIZE=6]**#**[/SIZE] icon when using the **Advanced Reply** editor.  This preserves the fixed width font, making it easier to read.

---

### Post by gordintoronto on 2015-02-04
I use a very different approach. I run the file manager, click on Network. Sometimes I can double-click on the computer name, then a share name, sometimes I double-click "Windows Network" first.

---

