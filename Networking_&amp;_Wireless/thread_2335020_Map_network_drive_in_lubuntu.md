---
title: "Map network drive in lubuntu"
date: 2016-08-24
forum: Networking &amp; Wireless
---

### Post by rac75 on 2016-08-24
Hello all  

I have just started work in an organisation which uses an intranet accessed by wifi.  Staff provide their own laptops and mine uses lubuntu. 

I can access most things within the system but there is an smb:// shared network which I cannot connect to. I have tried various things (ie, posting the smb address in file manager and in nautilus, using the Connect to Server option within file manager) and have had no luck. Most of these options say that the connection has been rejected, sometimes that the address was not found. 

 The IT dept have had a look but aren't familiar with lubuntu.   Can anyone suggest what I could try? Is it possible that the system here is rejecting my connection because it doesn't recognise the OS? Is it worth persisting or should I just give up and accept I'm not going to be able to access it from here?   Any ideas much appreciated.

---

### Post by SeijiSensei on 2016-08-24
Let's start with the command-line program smbclient. Can you see the available shares on the server if you open a terminal and enter
```
smbclient -L server_name
```
It should try and connect with your current username and request your server password.  If you have a different username on the server, use "smbclient -U username -L server_name".  

If you don't have a copy of smbclient on your machine, you can install it with "sudo apt-get install smbclient".

---

### Post by rac75 on 2016-08-25
Thank you for the reply and apologies for my delay.

I have started the installation of smbclient (it may take some time, internet access here ranges from difficult through very slow to impossible) but once it's installed I'll try it and let you know how it goes.

R

---

### Post by rac75 on 2016-08-26
Just to say I haven't forgotten, I'm still trying with this. I couldn't get connected to install the prog yesterday - I'm not sure if the connection is blocked in some way or if our link to the outside world was just too slow. I will try from somewhere else over the weekend.

---

### Post by SeijiSensei on 2016-08-26
Insert your installation disc and use the Software Center to see if smbclient is there.  It's on a Kubuntu 14.04 image I had lying around.  Since smbclient isn't a KDE program, I'd imagine it comes with most flavors of Ubuntu.  Then you won't need the Internet.

---

### Post by rac75 on 2016-09-19
Hi all and sorry for the delay.

I couldn't find the installation disk (think I might have left it back at home when I moved here) - I did still have the iso but for some reason struggled to create a new disk, not sure what the issue is there.

However, I DID eventually manage to install the smbclient - after repeatedly faling to connect to the server from within the school, I did it from a public wifi spot - hurrah! 

However, the message I got when I tried the command above in SeijiSensei's post was Connection to fs.ish.local failed (Error NT_STATUS_UNSUCCESSFUL). Is this because my machine isn't seeing any servers at all? I tried both with the server_name and with the actual name of the server here but with no luck.

I appreciate all the help so far and will try talking again to the techies here.

---

### Post by SeijiSensei on 2016-09-19
Try using the server's IP address.  Any better?

---

### Post by rac75 on 2016-09-19
Thanks again. Not sure if it's better but it's different. I wasn't sure how to input the server address and so tried it with and without the http

This is what I've got
> 
school@rachel-Aspire-5535:~$ smbclient -U rachel -L 10.xx.xxx.xx
WARNING: The "null passwords" option is deprecated
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated

Enter rachel's password: 
session setup failed: NT_STATUS_INVALID_PARAMETER


school@rachel-Aspire-5535:~$ smbclient -U rachel -L [http://10.xx.xxx.xx]("http://10.20.130.32")
WARNING: The "null passwords" option is deprecated
Unknown parameter encountered: "password level"
Ignoring unknown parameter "password level"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated

Enter rachel's password:
Connection to http: failed (Error NT_STATUS_UNSUCCESSFUL)


school@rachel-Aspire-5535:~$ 


To clarify a bit, school is the user I created on this machine for use here; rachel is the username they created for me here on the network and all school systems.

---

### Post by SeijiSensei on 2016-09-20
> **rac75 said:**
> Thanks again. Not sure if it's better but it's different. I wasn't sure how to input the server address and so tried it with and without the http

Sorry.  I forgot that smbclient has a somewhat tricky syntax.  Try this:
```
smbclient -L server_name -I 10.x.x.x -U rachel
```

If that works, you can next try adding an entry to /etc/hosts like this:
```

10.x.x.x     server_name

```
Then try the command again without the "-I 10.x.x.x" item.

If that also works, then try the "smb://server_name/share" method you started out with.

---

### Post by rac75 on 2016-10-07
Many thanks again and apologies for the delay.

I have tried this (the first command) and I get to the point where it asks for rachel's password, but then, when I use the password, everything appears to stop. I get no error message, the CMD line doesn't reappear, nothing. This happens even when I input a deliberately incorrect password (ie with no incorrect password message) - perhaps it's doing something but I can't see what's happening.

For the time being, I must use one of the computers (Windows) in the school's computer classroom if I want to see the network. It's not ideal, as the machines take a while to boot up - but it's the only slution I have for now. 


Edited to add: If I leave it for long enough I get a "connection failed" with a timeout message.

---

