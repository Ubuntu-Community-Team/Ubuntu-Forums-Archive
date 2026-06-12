---
title: "how to access ubuntu from win xp"
date: 2005-07-09
forum: Networking &amp; Wireless
---

### Post by anbu on 2005-07-09
i am trying to access ubuntu shared folders from windows xp, where i can see ubuntu system. but its keep asking user/pass word but not able to use any user/pass associated with windows/ubuntu system.

have anyone done this things earlier? 

i am also trying to use this ubuntu systems as a webserver running php/my sql for development. how do i access and edit files on this server? for development?

help please.  :neutral:

---

### Post by cwaldbieser on 2005-07-09
There are lots of ways to do this, and with experience, you will find out which way is preferable to you:

1) Windows file sharing-- It sounds like you are trying this, but you don't have Ubuntu configured to give you write access to the shared folder.  This could be because you need to change your Samba configuration or the folder may actually have read-only permissions set.

2) FTP-- If you are not transferring sensetive information, most computers dating back to the stone age have some sort of FTP client.  The ubuntu repositories have no lack of FTP servers (just search for ftpd).

3) SSH-- You can use PuTTY and PSCP on Windows similarly to how you would use ssh (secure shell) and scp (secure copy) on UNIX based machines.  These methods are secure compared to vanilla FTP or telnet.  You need to run an ssh server on Ubuntu (look for sshd in the repositories).

---

### Post by jcs296 on 2005-07-09
I've gotten an ubuntu samba server to work, two of them in fact.  But I've had the same problem you do; i can mount the shares from other ubuntu boxes but not a windows machine.  For that one I can't help you, but post an answer if you figure it out.  

As for editing files; is the machine accessible with a keyboard, mouse and monitor? Or are you using it as a server with no way of directly connecting in? Because if you're using it as a server the standard way to connect is by running an ssh server on the ubuntu machine, and you can connect into it from windows with a program like Putty. you can even do your development work on windows and then copy (through scp/sftp) the files to the ubuntu machine; these are basically file transfer mechanisms that work through ssh without requiring anything bu the ssh server. And of course they are secure. You can find programs to support scp/sftp at the Putty website.

Hope this helps, and see ubuntuguide.org for setting up the SSH server (and samba too)

---

### Post by arosct on 2005-07-09
On your Windows, you could install cygwin. There you'll find some unix-utils portet to Windows. There is an ssh client, scp, sftp and lot of other useful things. You may install as well the X system to get access with all the GUI things to your Ubuntu.

---

### Post by kirsche on 2005-07-16
I have my samba running on a hoary system.
I can successful access all my shares from different OS (WXP, W2K, W2K3, MAC OS).
Can you see the shares (net view)?

---

### Post by DaZjorz on 2005-07-16
To help configure Samba, you can use Webmin ([www.webmin.com)](www.webmin.com)). You can install it as an RPM and then connect to your Ubuntu box, and check the settings for Samba. Webmin is very handy for configuration.

---

### Post by oneafrikan on 2005-07-20
kirsche

Can you describe how you got your Windows machine to play nicely with your Ubuntu box?

I've got the same problem as anbu - can see the Ubuntu share, but can't access it...

Something to do with having the same user names and passwords, and enabling Samba passwords to be encrypted I believe... ?

---

### Post by Dec on 2005-07-21
[QUOTE=oneafrikan]kirsche

Can you describe how you got your Windows machine to play nicely with your Ubuntu box?

I've got the same problem as anbu - can see the Ubuntu share, but can't access it...

Something to do with having the same user names and passwords, and enabling Samba passwords to be encrypted I believe... ?[/QUOTE]
 I having the same issue with samba.. I can not see my shared files in my linux box.. Could anybody please give us a sample of your configuration file for samba..

I already tried webmin and even got everything set to share level with guess account and still not access.

Any help?

---

