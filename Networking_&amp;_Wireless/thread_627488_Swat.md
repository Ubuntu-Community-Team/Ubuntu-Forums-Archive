---
title: "Swat"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by bazzieb on 2007-11-30
Hi There, i have installed SWAT and can access the web page [http://localhost:901](http://localhost:901) but when i click on any of the editing links it gives me a "404 File not found" error. Any suggestions please??

---

### Post by Jumpmasterrt on 2007-12-02
did you give your root a password so that you can access all of SWAT?

Before you try and run SWAT you need to:
```
sudo passwd root
```

---

### Post by Jumpmasterrt on 2007-12-04
Ok, let's start from the beginning...

1. You have to install BOTH inetd and swat.
2. Give root a password (done)
3. edit the /etc/inetd.conf file and remove the #<off># from:
```
#<off># swat  stream  tcp  nowait.400  root\

/usr/sbin/tcpd  /isr/sbin/swat
```

4. Save file and restart the inetd daemon with
```
# /etc/init.d/inetd restart
```

Now start the [http://localhost:901](http://localhost:901) and you should see 8 boxes.  I uninstalled mine so I can't give you a screen shot.

---

### Post by marco75 on 2008-02-05
I'm also trying to get samba & swat working. I don't understand why they are disabled by default after you install them -- oh don't tell me, it's 'security' -- that's like taking the wheels off your car so you won't have an accident.

Hrmh. Okay, let's start:

I'm using gutsy on a dual boot machine.
The other OS, XP x64, can network with another XP x32 machine on the same network, they can read and delete each other's files.

I'm trying to transition to Ubuntu. I go to Places > Network and I can see the HOME workgroup.
I can see the folders & files that are shared, but when I try to open or copy one, it says I don't have read permissions.

I have installed samba and openbsd-inetd (netkit-inetd wasn't available) as well as swat packages. [http://localhost:901](http://localhost:901) doesn't get me anything, though.

/etc/inetd.conf

#<off># netbios-ssn	stream	tcp	nowait	root	/usr/sbin/tcpd	/usr/sbin/smbd
swat		stream	tcp	nowait.400	root	/usr/sbin/tcpd	/usr/sbin/swat

When I try to restart:

# /etc/init.d/inetd restart
bash: /etc/init.d/inetd: No such file or directory

Since there's no other GUI in Ubuntu for configuring samba (it should really have one -- Windows does) I would like to enable swat.

Thanks for reading.

---

### Post by jetsam on 2008-02-05
Marco, you can restart inetd with:
```
sudo /etc/init.d/openbsd-inetd restart
```

I'm sure I didn't need to mess with inetd when I installed swat.  It came in as a dependency with the swat package and correctly configured.  I think what you've done mimics the right configuration, though, so hopefully it should work.  

The 404 errors from post #1 are because the samba-doc package isn't installed.  

You may be digging yourself in deeper than you need to.  I'm pretty sure that if you can see the files in Nautilus-->Places-->Network, the read permission problem is on the Windows side.  Check the permissions by right clicking on the files in Windows and make sure everyone is allowed to read the file.

---

### Post by marco75 on 2008-02-05
Thank you for your rapid response.

> **jetsam said:**
> You may be digging yourself in deeper than you need to.  I'm pretty sure that if you can see the files in Nautilus-->Places-->Network, the read permission problem is on the Windows side.  Check the permissions by right clicking on the files in Windows and make sure everyone is allowed to read the file.

I would think, since when both machines boot into XP, they can read/write their shares just fine, that they are configured correctly.

On the XP x32 box, I turned off simple file sharing, then right-click on a share, left-click Sharing and Security...

(o) Share this folder

Share name: Downloads
Comment: <blank>
User limit: (o) Maximum allowed

To set permissions for users who access this folder over the network, click Permissions

Another dialog: Share Permissions

Group or user names: Everyone
Permissions for Everyone -- Allow -- Deny
Full Control -- [ ] -- [ ]
Change -- [v] -- [ ]
Read -- [v] -- [ ]

Shouldn't that be sufficient?
I don't see what I could to open up the XP x32 even more.

The username is the same on all three OS installations. Perhaps Ubuntu is just not sending the correct username to XP? Perhaps it's attempting to gain access as 'guest' or 'nobody'? How would I tell?
The guest account on XP is disabled, by the way.

I'm sitting at the wrong machine in the moment, I'll sent my /etc/smb.conf with my next post.

---

### Post by jetsam on 2008-02-06
I believe Nautilus does use the guest account, and I'm not sure of a way to get it not to.  Still, it doesn't seem to cause issues with an XP PC I have even though it has the guest account turned off.     I just checked this by creating a file from Nautilus and then checking it's ownership under properties-->security-->advanced on the xp machine.  If you've got your guest account more stridently locked out somehow, I suppose that could explain the problem.  

Also, check some of the files themselves below the share folder...  make sure they are inheriting permissions correctly or are otherwise set to be modifiable.

**Edited to add**:  I think XP pro is much more serious about disabling its guest account than XP home.  What I said above was on XP Media Center Edition.  

You might try file-->connect to server from the Nautilus menu.  You'll have to enter the server information manually, but there's a field for user name.

---

