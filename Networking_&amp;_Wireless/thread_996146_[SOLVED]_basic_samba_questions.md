---
title: "[SOLVED] basic samba questions"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by sparrowkc on 2008-11-28
I have a few questions about samba in Ubuntu.  How come none of the shares I create through the gui show up in /etc/samba/smb.conf?  I remember that you used to have to add users with smbpasswd before those usernames could be used to authenticate samba connections, what is it doing now?  Also, files written to my ubuntu machine over samba are owned by nobody and have permissions drwxr-xr-x, how can I change this?
Thanks,
-Mark

---

### Post by bab1 on 2008-11-28
> **sparrowkc said:**
> I have a few questions about samba in Ubuntu. 


> How come none of the shares I create through the gui show up in /etc/samba/smb.conf?
[COLOR="Blue"]**Nautilus (Gnome) uses the dbus interface (via gvfs) to talk to Samba (smbd).  The configuration is stored  at**[/COLOR]:```
[COLOR="Blue"]/var/lib/samba[/COLOR]
``` [COLOR="Blue"]**I believe Hardy's implementation is different that Intrepid's.  This further complicates the matter.**[/COLOR]

  
> I remember that you used to have to add users with smbpasswd before those usernames could be used to authenticate samba connections, what is it doing now? 
[COLOR="Blue"]**The smbpasswd command should still work.  The smb.conf file should still able to configure Samba.  The smbd still looks first to /etc/samba/smb.conf [COLOR="Red"]*before*[/COLOR] looking to the configuration files in /var/lib/samba. **[/COLOR]

> Also, files written to my ubuntu machine over samba are owned by nobody and have permissions drwxr-xr-x, how can I change this?
Thanks,
-Mark

[COLOR="Blue"][B]This can be controlled by the share settings in /etc/samba/smb.conf.  

What? You say they're not there.  Then add them to the file.  You can still manually configure the shares using /etc/samba/smb.conf.[/B][/COLOR]

---

### Post by sparrowkc on 2008-11-28
Thanks!

---

### Post by HDTimeshifter on 2008-11-28
I have been having a hell of a time trying to share my "documents" folder in Ubuntu.  I set it up as shared and gave all r/w and guest permissions, yet can not see it when I browse my network, Windows shares, Ubuntu PC in Nautilus.  However, I can see my other shared "downloads" folder as well as my shared printer in Nautilus, drilling through network as above.  I can also see "downloads" and shared printer in all my XP clients, including XP in Virtualbox, but still can't see the "documents" folder.  I just checked my /var/lib/samba/usershares folder and both documents and downloads files are identical.  The only thing I can think of is that documents is a default Ubuntu folder, while I created the downloads folder, yet they are both owned by me and have identical permissions.

If I change the smb.conf file in /etc, do I need to log out or do something to source it to recognize changes?  There is a line in there regarding the "documents" folder, but I think I put it in there at someone's direction on trying to get sharing to work.  Since there is no corresponding "downloads" line in there, I tried commenting it out to see if that was the problem.

---

### Post by Coreigh on 2008-11-28
Timeshifter

You probably need to restart the Samba daemon to have chages take effect
```
sudo /etc/init.d/samba restart
```

When you indicated that you granted permissions for your documents folder did you mean in Samba or folder permissions? You need both.

In the share definition in the smb.conf file you will need to make guests allowed and make the share writable and you will need to set the folder permissions to allow all to access. This will make your documents folder available to ANYONE who uses your computer!
```
sudo chmod 777 /home/<username>/documents
```
it is probably better to create a desinated folder for sharing, such as /usr/share/documents.

There are lots of example for pulic shares, do a google search for
> samba public share

---

### Post by HDTimeshifter on 2008-11-28
Hmm, strangeness...
I woke up my Vista laptop, refreshed it's Explorer window, which happened to be on the Ubuntu share, and wah lah - all of a sudden I can see my Ubuntu PC and the shared folders!  Well, I tried to view my Vista shares from Nautilus, but no such luck.  I guess the Ubuntu-Vista networking problems is one-sided.

By granting permissions, I meant sharing the folders from Nautilus.

Restarting the Samba daemon made the Documents folder visible in all clients.  Apparently the line in my smb.conf file for my documents folder that included file and directory masks = 077 and forcing user and group to nobody and nogroup was mucking things up.  I think I put that line in trying to get Vista-Ubuntu networking working.  My documents folder already had rwd permissions for all groups.  I'm ok with opening it up to any computer on my network since I'm the only user.  I want to be able to access (copy, delete, and backup from any computer on my network), whether it be a XP, Vista. or my Virtualbox XP guest.  I don't want to make a separate folder to share stuff - I want to be able to maintain documents here, access and move around and backup them from any computer on my network.  Bascially all the computers on my network will basically mirror this folder for sharing and backup.  If I turn off all permissions but owner, should I be able to maintain sharing, albeit requiring me to logon with the owner account when I access a share for the first time?  I only opened up all permissions, including guest, when I was trying to get Vista networking working.

---

### Post by bab1 on 2008-11-28
> my documents folder that included file and directory masks = 077 

This is wrong for sure.  This is not a mask but the actual octal settings.  I made that mistake many moons ago myself.  :D

[COLOR="Blue"]Edit: Regarding your Vista problems, the share authorization is one-way. Vista expects Samba to provide NTLMv2 credentials.  You can tell Samba to do that, but the defaults has always been off.[/COLOR]

---

### Post by Coreigh on 2008-11-28
> If I turn off all permissions but owner, should I be able to maintain sharing, albeit requiring me to logon with the owner account when I access a share for the first time?

I think that is correct but you'll just have to give it a try.

Cheers

---

