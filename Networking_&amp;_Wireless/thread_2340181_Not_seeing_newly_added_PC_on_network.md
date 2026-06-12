---
title: "Not seeing newly added PC on network"
date: 2016-10-16
forum: Networking &amp; Wireless
---

### Post by exsheeple on 2016-10-16
Hello.  Just added a PC running Ubuntu 16.04 to a wired network.  I can see the other 2 PC's on the network but not the 3rd.  Is there anything I need to do to add this PC to the network or to allow it to be viewable?

---

### Post by TheFu on 2016-10-16
Which protocols do you want to support?
"Viewable" on the network can mean many different things.
What are the other 2 PCs running? If Windows, then you probably want a CIFS server, though I'd rather see you use sftp/scp/ssh instead (putty/winscp are the clients). These are much more secure when configured properly.

---

### Post by exsheeple on 2016-10-17
Good question! Ultimately I want to be able to access and share the files from one PC to another but I can't seem to find or access the network

---

### Post by TheFu on 2016-10-17
> **exsheeple said:**
> Good question! Ultimately I want to be able to access and share the files from one PC to another but I can't seem to find or access the network

And what are the answers to all the questions?  Hard to help without some info.

---

### Post by exsheeple on 2016-10-17
> **TheFu said:**
> Which protocols do you want to support?

What are the other 2 PCs running?

Not sure of the protocol other than file sharing.

All PC's are running Ubuntu 16.04

---

### Post by SeijiSensei on 2016-10-17
Probably you need to share a folder on the machine using Windows.  Right click on a folder and choose Share from the menu.

---

### Post by exsheeple on 2016-10-17
I am not using any Windows machine on this network. The machine that is doing the sharing is a Ubuntu machine

---

### Post by Morbius1 on 2016-10-17
From the machine you cannot see from the other two run these commands and post the output:
```
testparm -s
```
```
net usershare info --long
```
That way the folks that offer to help you will know how you are set up.

---

### Post by TheFu on 2016-10-17
There are thousands of protocols.
For file sharing there are probably 50.
On Unix systems, the **best** way to share files on a LAN is through NFS. There are many reasons for this and there are a few caveats. It is a 1-trick pony and a little more complex to accomplish than .... 

The quickest way setup something secure and move files around is to use **ssh** + **sftp** or **scp** or **rsync**.  ssh is how unix admins control systems remotely (10 inches or 26k miles).  If you install openssh-server onto each of these systems, then you get scp and sftp for free.  At that point, you can connect using almost any Linux file manager with sftp://192.x.x.x/ or the sftp://hostname.local (if avahi is running).  Some file managers want ssh://192.x.x.x/ (which is technically incorrect, since ssh isn't a file transfer protocol).  

Also, if you install an ssh server, which is what I'm suggesting, then it would be smart to install fail2ban (the default config is fine) and then you can setup secure file access over the internet. sftp/scp are considered to be secure enough for internet file access, provided ssh-keys are used, not passwords.

The other responses assume you are using Windows and while they are correct, testparms and Samba is NOT the best answer unless Windows is involved. Pretty sure they would agree on that.

If you want to get NFS working, we can help there too, it will just take longer since it is unlikely the network/systems are all setup in the best way needed for NFS to work well.  To get started: [http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

---

### Post by Morbius1 on 2016-10-17
>  The other responses assume you are using Windows and while they are  correct, testparms and Samba is NOT the best answer unless Windows is  involved. Pretty sure they would agree on that.
** Nope, I'm assuming he's using samba in an all Linux network.
** There are no absolutes in linux so there is no such thing as "is NOT the best answer"
** And as a side note          SeijiSensei's advice is still valid even though he was thinking Windows by changing one word into three:
> Right click on a folder and choose [COLOR=#006400]**Local Network Share**[/COLOR] from the menu.         
I suspect the OP is using system-config-samba however so it's best not to muddy the waters.

---

### Post by TheFu on 2016-10-17
I can agree that "best" is highly subjective and not necessarily the "easiest" or "most commonly used" solution.

---

### Post by exsheeple on 2016-10-18
```
testparm -s
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE

# Global parameters
[global]
    server string = %h server (Samba, Ubuntu)
    server role = standalone server
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    idmap config * : backend = tdb


[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


```
net usershare info --long
```
mkdir failed on directory /var/run/samba/msg.lock: Permission denied
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.



This was from the PC that could access the network.  Even though Im not sharing from this PC, would I still need to enable sharing to access a network?

---

### Post by Morbius1 on 2016-10-18
> **exsheeple said:**
> Hello.  Just added a PC running Ubuntu 16.04 to a wired network.  I can see the other 2 PC's on the network but not the 3rd.  Is there anything I need to do to add this PC to the network or to allow it to be viewable?
To which I responded:
> **Morbius1 said:**
> From the machine you cannot see from the other two run these commands and post the output:
```
testparm -s
```
```
net usershare info --long
```
That way the folks that offer to help you will know how you are set up.
So I don't know what this means:
>  This was from the PC that could access the network.  Even though Im not  sharing from this PC, would I still need to enable sharing to access a  network?         

On this error message:
> mkdir failed on directory /var/run/samba/msg.lock: Permission denied
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


You are either not a member of the sambashare group or you have not installed samba.

I would follow TheFu's sage advice.  

[COLOR=#0000cd]*Setting up samba takes less that 5 minutes ..... Let me state that more  precisely .... Setting up samba in an all Linux network takes less than 5  minutes and bypasses all the Microsoft-specific "stuff" usually  associated with one that has Windows in the mix. If I combine this topic with your other one about system-config-samba you have been working on this far too long. SSH as TheFu suggested seems like a better bet for you.*[/COLOR]

---

### Post by exsheeple on 2016-10-18
Sorry for the confusion and my noodness. The "mkdir failed...." error was received on the PC that cant access the network. 

The [COLOR=#0000cd]*system-config-samba *[/COLOR] topic was resolved weeks ago but I did not mark it resolved until now....thanks for reminding me [**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144")

---

### Post by roadrawts on 2016-11-08
Was able to ssh to other laptop on my lan until I had to reinstall Ubuntu 16.04 on it.  I am trying to ssh from my laptop to it targeted to another user account but get "permission denied, try again.  I can ping it ok.  When I ssh to an account set up for me on that machine I don't get an error but I seem to stay on my local machine.  If I exit the terminal it states that it has closed the connection.  Don't understand what's wrong.

---

### Post by roadrawts on 2016-11-08
Also, that laptop does not appear when click on the Network icon from the desktop.

---

