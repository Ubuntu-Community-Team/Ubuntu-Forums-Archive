---
title: "My Home Network"
date: 2005-04-15
forum: Networking &amp; Wireless
---

### Post by gabbman on 2005-04-15
I am trying to get access to my laptop running XP.  I have a clean install of Hoary 5.04.

I click on Places > Network Servers and the first window opens showing two icons, Ubuntu and Windows Network.  

I click on Windows Network, and the new windows shows two icons, mshome (my laptop) and mshome1 (my daughters computer).

I click on mshome (my laptop) and in the new window instead of seeing my Sony Vaio, I get the Ubuntu icon.

Now in Warty I was able to see my laptop and it's shared folder's including the printer.

What do I have to do to get this to work?  

On my origional install, I followed the directions in the Starter Guide, but it just did not work.

Please help free me from having to reinstall KDE again.

---

### Post by ijsje on 2005-04-16
> 
I click on mshome (my laptop) and in the new window instead of seeing my Sony Vaio, I get the Ubuntu icon.
 
 Now in Warty I was able to see my laptop and it's shared folder's including the printer.

You say you are "seeing the ubuntu icon", do you mean by that that you get a folder with no contents instead of a folder with the shares and printer?

> 
 I click on Windows Network, and the new windows shows two icons, mshome (my laptop) and mshome1 (my daughters computer).


Does the same problem occur when viewing your daughters computer?

---

### Post by gabbman on 2005-04-16
[QUOTE=ijsje]You say you are "seeing the ubuntu icon", do you mean by that that you get a folder with no contents instead of a folder with the shares and printer?



Does the same problem occur when viewing your daughters computer?[/QUOTE]
 
Yes the Ubuntu icon folder is empty.

Yes it is the same on the mshome1 icon.

---

### Post by ijsje on 2005-04-16
There are two things you can try:

**1)**
Are you running Samba?
If it's not running, you can start it from the command line with:[indent]sudo /etc/init.d/samba start
[/indent]**2)**
If that didn't work, you can try to get to the share using the command line:[indent]smbclient -L //mshome
[/indent]This should provide a list of shares, you can pick a share and issue the command:[indent]smbclient //mshome/sharename
[/indent]It will ask for a password (you can leave this empty).
You can type 'ls' to see a file listing.
It's not a solution, but it does help to locate the problem.

---

### Post by gabbman on 2005-04-16
gord@ubuntu:~$ sudo /etc/init.d/samba start
Password:
 * Starting Samba daemons..                                                                       [fail]
gord@ubuntu:~$ smbclient -L//mshome
Connection to mshome failed
gord@ubuntu:~$ smbclient //mshome/sharename
Connection to mshome failed
gord@ubuntu:~$


I don't know why the *starting Samba daemons... failed. 

That may be the issue.

---

### Post by ijsje on 2005-04-17
Have you edited or removed the samba config?
If you still got the original samba config you can put it back and try to start samba again. The samba config is located at /etc/samba/smb.conf

Samba could also fail to start because it's already started, try this:
[indent]sudo /etc/init.d/samba restart
[/indent]

---

### Post by gabbman on 2005-04-17
[QUOTE=ijsje]Have you edited or removed the samba config?
If you still got the original samba config you can put it back and try to start samba again. The samba config is located at /etc/samba/smb.conf

Samba could also fail to start because it's already started, try this:
[indent]sudo /etc/init.d/samba restart
[/indent][/QUOTE]
No I have not edited it.
Yes it restarted ok, but I still can not see the laptop.

Oddly, I can transfer files to and from the ubuntu box from the laptop running xp.

---

### Post by gabbman on 2005-04-21
Well all of this was because I recently upgraded my F-Secure firewall software on the laptop, and foolishly assumed it would maintain the old settings.
After a quick tweak, I am now sharing without incident, and also printing to my networked HP PSC1210 printer.

Thanks ijsje for putting up with my windows ignorance.

/me runs and burries head in sand. :)

---

### Post by ijsje on 2005-04-22
[QUOTE=gabbman]Well all of this was because I recently upgraded my F-Secure firewall software on the laptop, and foolishly assumed it would maintain the old settings.
After a quick tweak, I am now sharing without incident, and also printing to my networked HP PSC1210 printer.

Thanks ijsje for putting up with my windows ignorance.

/me runs and burries head in sand. :)[/QUOTE]

Great to see everything worked out, and thanks for lettings us know the problem.

---

### Post by Gnobody on 2005-04-22
I can't get Samba to start...  I tried deleting my smb.conf

---

### Post by ijsje on 2005-04-23
[QUOTE=Gnobody]I can't get Samba to start...  I tried deleting my smb.conf[/QUOTE]

Samba won't start without a configuration file.
Do you have a backup smb.conf you can put back?

Error messages are stored in the directory /var/log/samba/ , is there any usefull information in log.smbd ? If there is you can post it here, it's hard to locate the problem without some additional information.

---

