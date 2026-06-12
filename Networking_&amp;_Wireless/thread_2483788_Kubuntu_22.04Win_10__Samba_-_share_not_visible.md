---
title: "Kubuntu 22.04/Win 10 / Samba - share not visible"
date: 2023-02-08
forum: Networking &amp; Wireless
---

### Post by oygle on 2023-02-08
On the Kubuntu side of things, this is what I have done..

> 
1.  sudo apt install -y samba

2.  mkdir ~/Public/Shared_Folder

3.  chmod 777 ~/Public/Shared_Folder

4.  kate /etc/samba/smb.conf

        Add these lines at the end

        [guest]
            # This share allows anonymous (guest) access
            # without authentication!
            path = /home/********/Public/Shared_Folder/
            browsable = yes
            read only = no
            guest ok = yes
            guest only = yes

        Save the file (needs pwd)

5.  Restart the samba server

        sudo service smbd restart


When I do the following command, it either shows it as okay or session closed

```
sudo systemctl status smbd
```

> &#9679; smbd.service - Samba SMB Daemon
     Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2023-02-09 14:02:08 AEDT; 43min ago
       Docs: man:smbd(8)
             man:samba(7)
             man:smb.conf(5)
    Process: 13624 ExecStartPre=/usr/share/samba/update-apparmor-samba-profile (code=exited, status=0/SUCCESS)
   Main PID: 13633 (smbd)
     Status: "smbd: ready to serve connections..."
      Tasks: 4 (limit: 9180)
     Memory: 8.9M
        CPU: 190ms
     CGroup: /system.slice/smbd.service
             &#9500;&#9472;13633 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;13635 /usr/sbin/smbd --foreground --no-process-group
             &#9500;&#9472;13636 /usr/sbin/smbd --foreground --no-process-group
             &#9492;&#9472;13637 /usr/lib/x86_64-linux-gnu/samba/samba-bgqd --ready-signal-fd=45 --parent-watch-fd=11 --debuglevel=0 -F

Feb 09 14:02:08 Inspiron-3542 systemd[1]: Starting Samba SMB Daemon...
Feb 09 14:02:08 Inspiron-3542 systemd[1]: Started Samba SMB Daemon.
Feb 09 14:05:39 Inspiron-3542 smbd[13699]: pam_unix(samba:session): session closed for user nobody
Feb 09 14:10:05 Inspiron-3542 smbd[13698]: pam_unix(samba:session): session closed for user nobody

I don't know what is closing the session ? One article suggested commenting out the following line.

>    map to guest = bad user

This post suggest a one liner to fix the 'nobody' problem - [https://stackoverflow.com/questions/70920783/windows-10-unable-to-connect-to-ubuntu-20-04-3-samba-server-0x80004005-unspecif/71127107#71127107](https://stackoverflow.com/questions/70920783/windows-10-unable-to-connect-to-ubuntu-20-04-3-samba-server-0x80004005-unspecif/71127107#71127107)

```
net usershare info --long
```

Nothing ??

```
testparm -s
```

> Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed

Server role: ROLE_STANDALONE

# Global parameters
[global]
        log file = /var/log/samba/log.%m
        logging = file
        map to guest = Bad User
        max log size = 1000
        obey pam restrictions = Yes
        pam password change = Yes
        panic action = /usr/share/samba/panic-action %d
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        passwd program = /usr/bin/passwd %u
        server role = standalone server
        server string = %h server (Samba, Ubuntu)
        unix password sync = Yes
        usershare allow guests = Yes
        idmap config * : backend = tdb


[printers]
        browseable = No
        comment = All Printers
        create mask = 0700
        path = /var/spool/samba
        printable = Yes


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers


[guest]
        guest ok = Yes
        guest only = Yes
        path = /home/********/Public/Shared_Folder/
        read only = No


If I browse the Network using Dolphin, under "Shared Folders (SMB) there is 'INSPIRON-3542' and 'guest' and 'print$' under that.

On the Win10 side of things, I have Enabled &#8220;network discovery&#8221; and &#8220;file and print sharing.&#8221;, and tried to "Add Network Location", but it fails with 'The folder you entered does not appear to be valid. Please choose another'. I have used

192.168.20.3  (IP of the Kubuntu box)
\\INSPIRON-3542\guest
\\INSPIRON-3542\Public\Shared_Folder

These 2 computers on the LAN are networked from a router. Win10 can actually see the router okay. The IP addresses are

Kubuntu 192.168.20.3
WIN10 192.168.20.2

I have been reading various posts here and on searching the internet. Just had a look in one of the samba log files

> [2023/02/09 15:02:43.079798,  0] ../../source3/smbd/service.c:168(chdir_current_service)
  chdir_current_service: vfs_ChDir(/home/********/Public/Shared_Folder) failed: Permission denied. Current token: uid=65534, gid=65534, 1 groups: 65534

---

### Post by oygle on 2023-02-09
Do I need this if all the samba traffic is only on a LAN ?

```
sudo ufw allow samba
```

From [https://ubuntu.com/server/docs/security-firewall](https://ubuntu.com/server/docs/security-firewall)

> * Similar to allowing traffic to a port, using an application profile is accomplished by entering:

sudo ufw allow Samba

Some details ..

```
sudo ufw app list
```

> Available applications:
  CUPS
  Samba
  
```
sudo ufw app info Samba
```

> Profile: Samba
Title: LanManager-like file and printer server for Unix
Description: The Samba software suite is a collection of programs that
implements the SMB/CIFS protocol for unix systems, allowing you to serve
files and printers to Windows, NT, OS/2 and DOS clients. This protocol is
sometimes also referred to as the LanManager or NetBIOS protocol.

Ports:
  137,138/udp
  139,445/tcp
  
```
cat /etc/ufw/applications.d/samba
```

> [Samba]
title=LanManager-like file and printer server for Unix
description=The Samba software suite is a collection of programs that implements the SMB/CIFS protocol for unix systems, allowing you to serve files and printers to Windows, NT, OS/2 and DOS clients. This protocol is sometimes also referred to as the LanManager or NetBIOS protocol.
ports=137,138/udp|139,445/tcp

---

### Post by Morbius1 on 2023-02-09
> [guest]
# This share allows anonymous (guest) access
# without authentication!
path = /home/********/Public/Shared_Folder/
browsable = yes
read only = no
guest ok = yes
guest only = yes


The Linux permissions of one's home directory is set to 750 in Ubuntu 22 meaning only the home folders owner can get access. To everyone else the Public folder and everything under it doesn't exist.

Easiest thing to do is to change your share definition to this:
> [guest]
# This share allows anonymous (guest) access
# without authentication!
path = /home/oygle/Public/Shared_Folder/
browsable = yes
read only = no
guest ok = yes
force user = oygle


Then restart smbd:
```
sudo service smbd restart
```

I've changed ******* as a user name with your Ubuntu name oygle for clarity.
I also removed the "guest only" parameter.

That will force the guest user to appear to be you - for this one share. That will remedy the Linux path permissions issue as well as the permissions of saved files from the client.

---

### Post by oygle on 2023-02-09
> **Morbius1 said:**
> ...{snip} ..

That will force the guest user to appear to be you - for this one share. That will remedy the Linux path permissions issue as well as the permissions of saved files from the client.

Thanks for that tip, it certainly fixed things up on the Kubuntu side of things for accessing. However the Win10 side still can't even 'see' the hostname or IP of the Kubuntu server. I found most of the documents had "Other LOcations" in the GUI file explorer. I use Dolphin and as soon as I installed Nautalis, I could see the Windows network.

---

### Post by Morbius1 on 2023-02-10
> However the Win10 side still can't even 'see' the hostname or IP of the Kubuntu server.
If you can't connect to the samba server using an ip address I would suggest the problem is the network not Samba. Perhaps your firewall?

Normally with Win10/11 I suggest installing the wsdd package in Linux. This enables Win10 to "discover" the samba server using the WS-Discovery mechanism Windows uses now. But there's a problem using that in KDE. It interferes with the native wsdd client in Dolphin.

Dolphin can "discover" a Win10 host using it's own wsdd client but when you install the wsdd package ( used by the server ) it disables the client in Dolphin. I have no idea why.

Win10/11 can also speak mDNS ( hostname with a .local attached at the end ) so you can also use this in Explorer:
```
\\INSPIRON-3542.local\guest
```

But all these methods eventual end up resolving to an ip address and if you can't do that directly .....

---

### Post by oygle on 2023-02-10
> **Morbius1 said:**
> If you can't connect to the samba server using an ip address I would suggest the problem is the network not Samba. Perhaps your firewall?

Some guides stated to do an "allow" to the firewall on Kubuntu, but I've held off on that because the UFW logs have no entries regarding that type of traffic.

> **Morbius1 said:**
> Normally with Win10/11 I suggest installing the wsdd package in Linux. This enables Win10 to "discover" the samba server using the WS-Discovery mechanism Windows uses now. But there's a problem using that in KDE. It interferes with the native wsdd client in Dolphin.

Dolphin can "discover" a Win10 host using it's own wsdd client but when you install the wsdd package ( used by the server ) it disables the client in Dolphin. I have no idea why.

I installed **wsdd** package, booted up WIN10, and now the file explorer in WIN10 can actually see itself PLUS INSPIRON-3542 (Kubuntu). It could only see itself for a while but then I made that netwrk 'private' on WIN10 and the Kubuntu computer was visible. 

> **Morbius1 said:**
> Win10/11 can also speak mDNS ( hostname with a .local attached at the end ) so you can also use this in Explorer:
```
\\INSPIRON-3542.local\guest
```

But all these methods eventual end up resolving to an ip address and if you can't do that directly .....

Thanks, I have tried so many 'combos' , but none work. But at least now with the Kubuntu computer visible, it gets a lot further on WIN10. I can even diagnose why it can't connect..

> file and print sharing resource (INSPIRON-3542) is online but isn't responding to connection attempts. Detected Detected 
 
The remote computer isn’t responding to connections on port 445, possibly due to firewall or security policy settings, or because it might be temporarily unavailable. Windows couldn’t find any problems with the firewall on your computer. 

I don't know why WIN10 thinks it is port 445 though, here is an entry from UFW.LOG

> Feb 11 12:29:35 Inspiron-3542 kernel: [] [UFW BLOCK] IN=enp7s0 OUT= MAC=************** SRC=192.168.20.4 DST=239.255.255.250 LEN=652 TOS=0x00 PREC=0x00 TTL=1 ID=60167 PROTO=UDP SPT=59645 DPT=3702 LEN=632

---

### Post by oygle on 2023-02-11
Have spent far too much time trying to get Samba to work with Windows 10/Kubuntu, so decided to use SSH/SFTP and was able to browse files on Kubuntu from Windows 10.

---

### Post by Morbius1 on 2023-02-11
I'm glad you found something that works for you.

This is more for comic relief but since I'm not a KDE user I decided to install Kubuntu 22.04 as a VBox guest to see what issue I would have in turning it into a Samba server for Win10/11.

So In Installed samba and wsdd.

I created a folder at /mnt/SMBPrivate and made my user the owner.

I created a share definition in smb.conf for that folder:
```
[Private]
        path = /mnt/SMBPrivate
        read only = No
        server smb encrypt = required
        valid users = tester
```
I made it slightly more complicated by forcing encrypted transport ( server smb encrypt = required ).

And added my user to the samba password database: sudo smbpasswd -a tester

You are using a firewall which I do not normally use and that did present an additional step.

When you install samba or cups or even ssh the package manager creates a firewall rule for those protocols but it's missing for wsdd. So just to be fancy I created one:
> tester@vkub2204:~$ cat /etc/ufw/applications.d/wsdd
[wsdd]
title=WSDD filewall rule
description = WSDD stuff
ports=3702/udp|5357/tcp

Then enabled the firewall: sudo ufw enable
And allowed wsdd: sudo ufw allow wsdd
And allowd samba: sudo ufw allow Samba

My Win10 machine can discover the Kubuntu samba server and it's Private share using WSD. To confirm I ran a command on the server to see how it was connecting:
> tester@vkub2204:~$ sudo smbstatus

Samba version 4.15.13-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing              
----------------------------------------------------------------------------------------------------------------------------------------
2278    tester       tester       2605:a601:a18d:9f00:9553:e005:f574:5bd5 (ipv6:2605:a601:a18d:9f00:9553:e005:f574:5bd5:50027) SMB3_11           partial(AES-128-GCM) partial(AES-128-CMAC)

Service      pid     Machine       Connected at                     Encryption   Signing     
---------------------------------------------------------------------------------------------
Private      2278    2605:a601:a18d:9f00:9553:e005:f574:5bd5 Sat Feb 11 07:59:40 AM 2023 EST  AES-128-GCM  AES-128-CMAC

Except for the time it took to install and update Kubuntu itself this whole process took maybe 15 minutes.

**[COLOR="#FF0000"]EDIT[/COLOR]**: I should note that doing this in reverse ( discovery then connection to a Win10 share from Dolphin ) is a problem. It's something KDE shares with Gnome. But that is to be expected since neither KDE or Gnome has a samba subject matter expert to guide them on how it needs to be done. A mount.cifs works of course since that's linux kernel based.

---

### Post by oygle on 2023-02-11
> **Morbius1 said:**
> This is more for comic relief but since I'm not a KDE user I decided to install Kubuntu 22.04 as a VBox guest to see what issue I would have in turning it into a Samba server for Win10/11.

So In Installed samba and wsdd...{SNIP}

That's quite some testing there. You are much more proficient with Samba/shares than me. I have to stick with what works now, the SSH/SFTP side of things.

Possibly why your WIN10 machine discovered/viewed the Kubuntu was the actual WIN10 ? By that I mean, in the many guides I read on Samba with Ubuntu/WIN10, I do not know what sort of a WIN10 setup people have, to get it to work. What parametsr/settings/config was already setup prior to the Samba install ?

The networking side of Windows hasn't improved since the days of Windows 95 it seems. At the best, it was very unstable/flakey yesterday for me. Network could be seen, then later couldn't, etc. The Kubuntu network side was stable. The laptop is refurbished, so I have no idea what the previous owner of the WIN10 had installed/setup. Now looking at wiping it and re-install from fresh, but can one purchase WIN10 Pro these days ?

Even when Windows couldn't see the Kubuntu box at all, either by hostname or IP, or share, I then used an SFTP client and it was able to see the Kubuntu box. So much for Windows explorer and the networking side of things. I did have the WIN10 firewall "ON", so it may have been the culprit ?  Yet if it was the SFTP client was able to view. I may turf Windows firewall and get McAfee.

---

### Post by Morbius1 on 2023-02-11
I would actually take exception to your assessment that Win10 isn't an improvement over Win95.

There is a world of difference between those 2 operating systems concerning SMB.

No more NetBIOS so no more name resolve order, master browsers, wins servers, ... all of the other flaky NetBIOS trauma that cased problems in the past.

It can use WS-Discovery to discover the Linux server. It can use mDNS ( avahi in Linux ) to connect to the server if you need to "map" it. None of this was possible in Win95.

EDIT: I do wish that Win10 had an SSH / SFTP client built into explorer however. You can "map" an ftp location but you can't map to sftp which makes no sense to me.

You can create an ssh connection in powershell but who does that.

---

### Post by oygle on 2023-02-11
> **Morbius1 said:**
> I would actually take exception to your assessment that Win10 isn't an improvement over Win95.

My perception was based on my experiences, which were a result of much frustration. Linux/Ubuntu networking simply works out of the box, with good security.

> **Morbius1 said:**
> 
EDIT: I do wish that Win10 had an SSH / SFTP client built into explorer however. You can "map" an ftp location but you can't map to sftp which makes no sense to me.


The Beyond Compare SFTP client showed more the true picture of network connections, whilst the Win10 explorer/networking wasn't able to.

---

### Post by oygle on 2023-02-12
> **Morbius1 said:**
> My Win10 machine can discover the Kubuntu samba server and it's Private share using WSD. To confirm I ran a command on the server to see how it was connecting:

Except for the time it took to install and update Kubuntu itself this whole process took maybe 15 minutes.

Do you have the full instructions documented please ? From start to finish.

---

### Post by Morbius1 on 2023-02-12
I thought that's what I did in Panel #8:

Um ... is this more complete:

Create a new folder to share and take possession of that folder:
```
sudo mkdir /mnt/SMBPrivate
sudo chown tester /mnt/SMBPrivate
```
Edit smb.conf and add a share definition for that folder:
```
sudo nano /etc/samba/smb.conf
```
Added the following to the bottom of the file:
```
[Private]
        path = /mnt/SMBPrivate
        read only = No
        server smb encrypt = required
        valid users = tester
```
Restarted the smb daemon:
```
sudo service smbd restart
```
Added my user to the samba password database:
```
sudo smbpasswd -a tester
```
Created a wsdd filewall rule:
```
sudo nano /etc/ufw/applications.d/wsdd
```
Added this to newly created file:
```
[wsdd]
title=WSDD filewall rule
description = WSDD stuff
ports=3702/udp|5357/tcp 

```
Did some firewall stuff:
```
sudo ufw enable
sudo ufw allow wsdd
sudo ufw allow Samba

```

That's pretty much it. Win10, Win11, MacOS, iOS can all discover and access my new Kubuntu Samba server.

Note: I used nano as the text editor but there's absolutely no reason you have to use it. It's been more than 20ish years since I've used KDE, couldn't remember what the editor was and if it still exists, so I used what I use on a server.

---

### Post by oygle on 2023-02-12
Thank you muchly, you did quite a number of steps that I didn't do. It's worth a try again, thanks. With KDE, I just use "Kate" for an editor.

---

### Post by oygle on 2023-02-13
> **Morbius1 said:**
> Um ... is this more complete:

It's more than complete, it is awesome. I basically used all the same commands and it worked on the WIN10 box immediately.

Only a few questions ..

1. What privileges did you have for user 'tester' prior to the user being added to Samba ?

2. For ```
sudo ufw allow Samba
```, I had to use lowercase

3. From the Win10 computer, it actually showed two shares. The one I created days ago , "guest" , and the one from your instructions - "Private". Some observations:

* I could simply go straight into the "guest" share created the other day, browse and open files
* I had to login with the "Private" share (which is understandable)

Actually the "guest" share had no entries in /etc/ufw/applications.d/wsdd

Here are the entries in /etc/samba/smb.conf

> [guest]
        # This share allows anonymous (guest) access
        # without authentication!
        path = /home/oygle/Public/Shared_Folder/
        browsable = yes
        read only = no
        guest ok = yes
        force user = oygle

[Private]
        path = /mnt/SMBPrivate
        read only = No
        server smb encrypt = required
        valid users = tester

It will be interesting to see if, in either of the Samba shares, I can traverse directories. ..Later, no I couldn't traverse directories using Beyond Compare as a Samba client, so that is good.

---

### Post by oygle on 2023-02-13
@Morbius1 - I have read many "how to's" about Linux/Win10 and Samba shares. Your guide at [https://ubuntuforums.org/showthread.php?t=2483788&p=14130598#post14130598](https://ubuntuforums.org/showthread.php?t=2483788&p=14130598#post14130598) was the only one that worked for me. Can I post your guide as a tutorial, giving you credit of course.  :)

---

### Post by Morbius1 on 2023-02-14
I don't see how I could stop you even if I did object.

---

### Post by oygle on 2023-02-14
> **Morbius1 said:**
> I don't see how I could stop you even if I did object.

Well, you did all the work.  :D

---

