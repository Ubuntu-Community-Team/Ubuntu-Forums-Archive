---
title: "Help need to on connect to server !"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by kartook on 2010-02-25
Hi 

Most of the time i need to connect windows  share . 

I Added 2 images one for default another one how i want .. 


Thanks for the help in advance 

k~

---

### Post by GrammatonCleric on 2010-02-25
Howdy,

So are you trying to access/mount a Windows share on your home PC or a share within a corp environment connected to an Active Directory?  As to FTP do you have the site info for the FTP server(s). 

-GC

---

### Post by kartook on 2010-02-25
> **GrammatonCleric said:**
> Howdy,

So are you trying to access/mount a Windows share on your home PC or a share within a corp environment connected to an Active Directory?  As to FTP do you have the site info for the FTP server(s). 

-GC


Windows share within a corp environment connected PC 's only iam going to Access 

Yes this is all in member of  an Active Directory .

I am Domain Admin .Most of the time i was check the Share Folders and coping from one server to another server . 

Ex: SRV-TEST-01 to SRV-TEST-10 ( Both are Windows servers )

I dont care about FTP . its very rare use .

Just if i open Connect to server that  should **windows share **as default option .thats all i need :)

Thanks 

K~

---

### Post by rustutzman on 2010-02-25
I'm not real sure what you're asking but this is how I do it on my office network.

**Server:** Server Name
**Share:**  If you're and admin you can use C$ or the actual folder name.
**Folder:** I leave blank
**User Name:** username
**Domain:** domain name

check the add bookmark if you will be using it often.

Russ

---

### Post by ScottinSoCal on 2010-02-25
I switched my work computer to Ubuntu 9.10, in a Windows network with Active Directory Services. I used Likewise-open to log in through the ADS, then configured it to automatically mount the network drives on boot-up. There's a thread in the networking section that talks about an issue I had when I followed the directions from this site. On the final step, it had me link the Samba and Likewise-open password files, and that broke everything. I had to unlink it to get it working again.

Make sure your logon ID/password to your local machine is the same as your ADS logon ID/password. It simplifies things.

---

### Post by ScottinSoCal on 2010-02-25
Here's the thread:

[http://ubuntuforums.org/showthread.php?t=1397745](http://ubuntuforums.org/showthread.php?t=1397745)

---

### Post by kartook on 2010-02-27
Hey guys 

If i open connect to server shortcut that should look like this ..how can ? .

I am know how to connect and use and all ...

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=148177&stc=1&thumb=1&d=1267091014[/IMG]

Question : How to make default connect to server as windows share ? .How to edit ? file path ? and how to edit ?

---

### Post by cariboo on 2010-02-27
Do you see the shares you are trying to connect to when you go Places->Network->Workgroup->server->share?

---

