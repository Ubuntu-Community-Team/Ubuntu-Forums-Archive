---
title: "Connect ubuntu to Windows network"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by flamingdragon on 2007-11-02
I am trying to connect my Ubuntu machine to out Windows network. I have samba installed, and have been trying to configure it to allow access, but with no luck. I have followed several tips from these threads but currently nothing works. (At one point, my Ubuntu could access the windows computers, and at another point, the other way around, although I don't recall changing the config when that stopped working). 

Currently, the only thing that works is accessing the windows computers by typing IP addresses in, but I would prefer to be able to see them from the Windows network, and have them able to access my shares.


Anyone have any tips on configuring samba (and possibly network settings)? Or possibly a copy of a working samba configuration file?

I am using Ubuntu 7.10 (Gutsy), the windows computers are all Win-XP, and can access each other without any problems. I do not currently have Firestarter installed (having uninstalled it at some point trying to get access), but configuration tips for that would be welcome as well.

I apologise if this is too general, but I really have no idea what happened. (I have tried uninstalling and reinstalling samba, too, but couldn't even get the original config file)

---

### Post by froy02 on 2007-11-02
See this page for solution:

[http://ubuntuforums.org/showthread.php?t=598887](http://ubuntuforums.org/showthread.php?t=598887)

Froy

---

### Post by flamingdragon on 2007-11-02
Thanks for that, now the windows computers can access my Ubuntu. 

I still cannot access MSHOME (the network) from the Ubuntu, though. I can access the computers via the IP addresses, but I am curious about why I can't access the windows network through the link for that purpose..

I can see MSHOME, but I get the following error:
"Sorry, couldn't display all the contents of "Windows Network: mshome". "

Could it perhaps be that it can't resolve the name mshome? I get the same error trying to access the other computers by name

---

### Post by Innovator on 2007-11-02
That is the exact message that I've been getting, and was about to post a thread for.  Thanks in advanced to anyone willing to help us.

---

### Post by flamingdragon on 2007-11-02
After reading a bit more and making a few changes, I finally managed to have the connection visible both ways.

My smb.conf contains only the following

[global]

workgroup = mshome
netbios name = shaun-laptop
server string = %h server (Samba, Ubuntu)
security = SHARE
name resolve order = bcast hosts wins lmhosts
wins support = no

domain master = no
preferred master = Yes
local master = yes
os level = 65

And then a list of shares. It seems to work.

---

### Post by froy02 on 2007-11-02
Make sure you allow file sharing in Windows to see your windows shared files from ubuntu.  also sometimes you have to wait a while for the computers to sync. Click on places>network and they should show the computers and then you can browse them.

---

### Post by Innovator on 2007-11-03
I've been messing around so much with the smb.conf file to no avail.  Anyone know what exactly I should be doing in order for the changes to take effect (logging out and back in, etc.?)?  However, I have been able to connect to the network by typing in smb://ip address as suggested.  Thanks a lot for all the help so far!

---

### Post by flamingdragon on 2007-11-04
If you delete everything in the smb.conf file except the list of shares and just copy in the contents I posted (making necessary name changes), I think that should work - it did for me. Although technically i didn't delete anything - the file was already blank as samba kept erroring on reinstall. Still don't know why, but it works.

And the changes take effect if you type 
sudo /etc/rc.d/init.d/smb restart

There is another command to just reload the config but I can't remember it. Restarting samba only takes a few seconds anyway.

---

### Post by Innovator on 2007-11-04
I found out about that command you posted on a youtube video just last night, thanks for your efforts to help me nonevertheless.  I'll see what I can do about this the next time I get on my Ubuntu machine.

Edit:  I can see everything in mshome now, all I had to do was type that in the domain name section to the general tab in Network Settings.  Now I ssem to be having problems getting windows to see my shared files.  It's the same thing with VNC; Ubuntu can access Windows, but Windows can't access Ubuntu.

---

