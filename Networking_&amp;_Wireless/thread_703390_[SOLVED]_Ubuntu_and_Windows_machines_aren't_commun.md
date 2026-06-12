---
title: "[SOLVED] Ubuntu and Windows machines aren't communicating!"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by cyclingman on 2008-02-21
Basically, I can't see my windows (XP - home) shared folders from Ubuntu, nor can I see the Ubuntu shared folder from windows.

Here is the problem for each:

Ubuntu to windows - Places > Network > Windows Network > mshome, and I get the following message:
> The folder contents could not be displayed. Sorry, couldn't display all the contents of "Windows Network: mshome".

Windows to Ubuntu - My Network places > none of my Ubuntu shared folders appear. However - My Network Places > View workgroup computers > I can see my Ubuntu Samba 3.0.26a, but when I try to access it (double click) I get:
> (Ubuntu computer name)server (samba Ubuntu) is  not accessble. You might not have permission

I don't have any firewall on my Ubuntu, and I tried turning off Windows firewall on my Windows. I can see that this is a common problem, yet when looking around, I can't see a clear answer - I don't know much about networking, so could replies be explained for dummies XD.

Thank you in advanced

---

### Post by Bucky Ball on 2008-02-21
I know this could sound obvious, stoopid and naive, but have you got some 'common ground' for swapping files between Windows and Linux (Ubuntu) in the form of a fat32 partition (Ubuntu can read from NTFS but doesn't write so good ... yet - fat16/32 is fine, and possibly others)?

Linux uses ext3 file system and I think I am right in saying you won't be able to read a file system of this kind from Windows, although you may be able to see the physical drive in Disk Management or whatever in Windows or the LAN. These drives (or partitions) won't be visible as Windows can't read this file system (that I am aware of).

Bit outta left field and you may have been here already but never know, it is computing after all. :)

---

### Post by Bucky Ball on 2008-02-21
Sorry, now I figure you are networking two computers. Basically, the same applies.

If your Ubuntu machine is all on ext3 file system drives, Windows won't see much on your LAN.

Odd thing is, Ubuntu machine should see Windows drives and partitions, unless they are formtatted in something other than NTFS or FAT.

As for shared folders, again, think I'd be right in saying that system is not going to happen (not quite like networking a Vista and an XP machine).

Having said that, some workaround might be possible and out there already.

Incidentally, you know you are getting a connection through your router, if that is what you're using? Can both machines get online for instance? What signs show the network is working at all (LAN that is)?

---

### Post by Iowan on 2008-02-21
I've read threads with similar problems that got solved by installing **smbfs** - although I don't remember installing **smbfs** I have a working Samba server.

---

### Post by cyclingman on 2008-02-22
Thanks for the replies. I know its possable, because along time ago, when I first got Ubuntu I could share fine. Then, I don't know why, it gave me the message. Also, if I set up another network on a seperate windows machine, I can also see the wourkgroup, yet get the same error message from my Ubuntu machine, this leads me to believe its a problem with my Ubuntu machine, not windows.

Thanks, I will look into smbfs!

---

### Post by Iowan on 2008-02-22
> **cyclingman said:**
> ... I can see my Ubuntu Samba 3.0.26a, but when I try to access it (double click) I get:...
Windows username is the same as Ubuntu and Samba username?
Might need to post **smb.conf**.
 One quick check would be to change to **security=share**

---

### Post by cyclingman on 2008-02-22
Erm, thats a fairly good point - they might not be. I'll upload my smb.conf and change it to shared, to see what happens. Thanks.

P.S it will be attatched in the next post. I will also try and find the two usernames (I'm a bit confused)

---

### Post by cyclingman on 2008-02-22
wo, wo, wo. Something very strange has just happened;

lets call windows 1: CP1, windows 2: CP2 and Ubuntu 1: CP3

I just logged on, and from CP1 I can see CP3, but visa versa i get the error message that I saw before (could not display ...). From CP3 I can see a separate workgroup which was set up by CP2??

This is weird, because yesterday, nothing was working, and now half is. I haven't changed any settings yet. Never the less, here's the smb.conf file attached.

---

### Post by rickyjones on 2008-02-22
> **Bucky Ball said:**
> Sorry, now I figure you are networking two computers. Basically, the same applies.

If your Ubuntu machine is all on ext3 file system drives, Windows won't see much on your LAN.

Odd thing is, Ubuntu machine should see Windows drives and partitions, unless they are formtatted in something other than NTFS or FAT.

As for shared folders, again, think I'd be right in saying that system is not going to happen (not quite like networking a Vista and an XP machine).

Having said that, some workaround might be possible and out there already.

Incidentally, you know you are getting a connection through your router, if that is what you're using? Can both machines get online for instance? What signs show the network is working at all (LAN that is)?

I just want to interject and correct this post.

Networking does NOT care about what the filesystem is on either end system. When I connect to my Ubuntu server via Windows I'm connecting using the SMB protocol - it doesn't care what the underlying filesystem is. The networking protocols translate this information into network traffic which is then translated again on the other side of the connection.

Now, if you wish to share files between the two systems you'll need to ensure that you have SAMBA installed on the Linux computer. To make things easier you'll want to make sure that both systems (Windows and Linux) are using the same username and password. You'll also want to make sure that all computers are participating in the same workgroup.

Here is a very simple /etc/samba/smb.conf file that might be able to help you get started:
```

# Samba config file created using SWAT
# from 192.168.0.95 (192.168.0.95)
# Date: 2007/10/20 18:46:48

[global]
        workgroup = ZZPERFORMANCE
        server string = %h server (Samba, Ubuntu)
        security = SHARE
        encrypt passwords = No
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[html]
        path = /data/http
        admin users = richard
        read only = No
        guest ok = Yes

```

In the above example file the "share" is "html" and it is sharing the directory "/data/http". Also in this example I have it configured so that you do not need to provide a valid username/password to access the share. Of course, you'll also want to ensure that the folder being shared has permissions that allow this (I chmodded that folder as 777 for ease of use).

If you wish to connect to a share on your Windows computer from Linux then first and foremost you need to make sure that the folder is shared. If you are using Windows XP I recommend using "Simple File Sharing" to make it a little easier. This basically enables Guest access via the network to the folders that you have shared.

If you don't share at least one folder then it'll be difficult to connect to the Windows PC from the Linux PC. I have seen this from experience.

I hope this information helps point you in the correct direction.

Thanks,

-Richard

---

### Post by cyclingman on 2008-02-22
Thanks for all your help, I can now confirm that this has been solved:

I created another workgroup on one of my windows machines, and gave it a different name. Then I made sure that all other systems had the same workgroup name (includeing my Ubuntu by opening the smb.conf file). And then it just worked, no problems.

So I presume it was something to do with how the original workgroup was set up. If you have the same problem, try and making a new workgroup, and ensure all system have the same name. 

Thanks for all the help, you wonderful Ubuntu people!

---

### Post by Iowan on 2008-02-22
> **cyclingman said:**
> Thanks for all your help, I can now confirm that this has been solved:
GREAT!!! Remember to mark it [SOLVED] (under Thread Tools).

---

