---
title: "Windows 10 not connecting to shared Ubuntu folder"
date: 2024-09-24
forum: Networking &amp; Wireless
---

### Post by madirisha on 2024-09-24
Hello,

I have been trying for many, many hours to access my samba drive from my Windows 10 client PC but to no avail. Admittedly, I am a total Linux noob and have been relying on the scattered online discussions on this topic to find a solution. I honestly believe at this point I have tried everything my brain can comprehend, but I just can't get it to work. Windows fails to map the network drive ("Windows cannot access \\[UbuntuServerIP]\home. Check the spelling of the name. Otherwise, there might be a problem with your network. To try to identify and resolve network problems, click Diagnose.")

The following thread gave me some inspiration: [https://ubuntuforums.org/showthread.php?t=2486949](https://ubuntuforums.org/showthread.php?t=2486949)

So I will list the output to these commands here:

testparm -s
```
Load smb config files from /etc/samba/smb.confLoaded services file OK.
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
        preferred master = Yes
        server role = standalone server
        server string = %h server (Samba, Ubuntu)
        unix password sync = Yes
        usershare allow guests = Yes
        wins support = Yes
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




[home]
        comment = Shared Folder
        guest ok = Yes
        path = /mnt/backup/home
        read only = No
```

net usershare info --long
```
net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.
```

hostname
```
threadripper
```

Anything you can do to help guide me towards a solution is greatly appreciated.

---

### Post by Morbius1 on 2024-09-24
You didn't state what version of Ubuntu you are using so I will assume it's the latest.

These are incidental but:

Install wsdd-server so Win10 can discover your Ubuntu server in explorer:
```
sudo apt install wsdd-server
```
You really don't need these options since Windows no longer uses them:
> preferred master = Yes
wins support = Yes
It don't think it will do any harm to keep them so this is just an FYI

The way samba works is that for an un-credentaled user the remote samba user will be declared a "Bad User" and converted to the "guest account" which is literally "nobody".

So the question is does "nobody" have access to the shared folder and the path to it:
```
ls -al /mnt/backup
```

---

### Post by madirisha on 2024-09-24
Hello Morbius1,

Thank you for taking the time to reply. I am still running on Ubuntu 20.04.6 LTS because there is software running on this server which is incompatible with later versions (for now).

sudo apt install wsdd-server gives the following output:
```
Reading package lists... DoneBuilding dependency tree
Reading state information... Done
E: Unable to locate package wsdd-server
```

ls -al /mnt/backup gives the following:
```
total 84
drwxrwxr-x 6 root  root        4096 Apr 19  2023 .
drwxr-xr-x 3 root  root        4096 Apr 12  2023 ..
drwxrwxr-x 4 root  root        4096 Apr  9  2023 fms
drwxrwxrwx 3 Stijn sharegroup  4096 Oct 27  2023 home
drwx------ 2 root  root       16384 Apr  9  2023 lost+found
-rw-r--r-- 1 root  root       47110 Apr 19  2023 master.zip
drwxr-xr-x 7 root  root        4096 Mar  4  2023 wsdd-master
```

Any ideas?

---

### Post by Morbius1 on 2024-09-24
> drwxrwxrwx 3 Stijn sharegroup  4096 Oct 27  2023 home
Well, "nobody" has access to the shared folder - in fact everyone does so that isn't the problem.

[I][COLOR="#0000CD"]Stijn looks odd - didn't think you could create a linux user with a capital letter in it ....

Just out of curiosity if you run the command:
```
id
```
Does it actually show Stijn or does it show stijn?
[/COLOR][/I]
Anyway, Linux permissions do not appear to be the problem so maybe it's a network ( non-Samba ) problem. Can Win10 ping the ubuntu server by it's ip address:
```
ping UbuntuServerIP
```
Or it's mDNS host hame:
```
ping threadripper.local /4
```

And are you allowing Samba through the firewall:
```
sudo ufw allow Samba
```

---

### Post by madirisha on 2024-09-24
Yeah I'm not sure why I decided to create the username with a capital 'S'. I believe the lower case ('stijn') also exists as a user on my server. Probably because that is also my client PC's username (whoami on Windows command line yields 'stijn') and I saw somewhere that using the same name on both client and server would solve the issue.

id gives the following:
```
uid=1000(stijn) gid=1000(stijn) groups=1000(stijn),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),117(lxd),1001(fmsadmin)
```

Pinging the IP works no problem.
Pinging threadripper does not: "Ping request could not find host threadripper.local. Please check the name and try again."

I believe I am allowing Samba through the firewall:
```
Skipping adding existing ruleSkipping adding existing rule (v6)
```

Thanks for your patience.

---

### Post by Morbius1 on 2024-09-24
>  Pinging threadripper does not: "Ping request could not find host threadripper.local. Please check the name and try again."
You have to have avahi-daemon installed on the Ubuntu machine so you might want to check that:
```
sudo apt install avahi-daemon
```
It's installed by default on Ubuntu desktop machines but not Ubuntu Server installs.

I'm skirting around the real issue here because I don't have a clue at the moment why this isn't working.

Samba configuration except from some superfluous stuff is OK, Linux permissions are OK, firewall set to allow, you can ping it by ip address.....

Some Windows 10 setups don't allow guest access as a client but you would get an error message on Win10 telling you that.

Could be an encryption issue ... I'm not sure.

If you change the share definition to this does it resolve anything:
```
[home]
        comment = Shared Folder
        guest ok = Yes
        path = /mnt/backup/home
        read only = No
        force user = stijn


```
Then restart smbd:
```
sudo service smbd restart
```

---

### Post by madirisha on 2024-09-24
avahi-daemon is installed:
```
Reading package lists... DoneBuilding dependency tree
Reading state information... Done
avahi-daemon is already the newest version (0.7-4ubuntu7.3).
0 upgraded, 0 newly installed, 0 to remove and 90 not upgraded.
```

Forcing user to 'stijn' did not change anything (nor did changing to 'Stijn').

What if the setup is ok on the Ubuntu side, but something is wrong on the Windows side? For example, I enabled network discovery so I don't understand why the device doesn't even show up in my Explorer. :???:

---

### Post by Morbius1 on 2024-09-24
Can you on the ubuntu machine access your own share?

If you run in a terminal:
```
nautilus smb://UbuntuServerIP/home
```
Or:
```
nautilus smb://threadripper.local/home
```
Can you connect?

---

### Post by madirisha on 2024-09-24
I just tried 'ping threadripper' from the Windows command prompt (no '.local'-suffix) and it started pinging a different IP. The server IP may change from time to time after a network connection interruption but it seems like Windows is saving the IP somewhere and trying a wrong one. Response: destination host unreachable.

---

### Post by madirisha on 2024-09-24
Sorry, hadn't seen your latest post yet. It seems this doesn't work:

```
Unable to init server: Could not connect: Connection refused

(org.gnome.Nautilus:26945): Gtk-WARNING **: 13:32:12.461: cannot open display:
```

Same output for both commands.

EDIT: I'm running these commands through SSH (putty) from my Windows client and NOT directly from the terminal. Not sure if that makes a difference.

---

### Post by Morbius1 on 2024-09-24
Now I'm really confused.

Are you running Ubuntu Desktop or Ubuntu Server?

Are you running either directly or are you using an ssh connection to connect to the machine?

Is this a standalone machine or are you using WSL in Windows?

---

### Post by madirisha on 2024-09-24
Sorry, as mentioned in my previous post (edited) I am running these commands from my Windows 10 client PC using Putty (SSH). Not directly from terminal.

---

### Post by madirisha on 2024-09-24
Same nautilus response when run from terminal. Might this be related to the fact that I'm working in tty2 (not 1)?

---

### Post by Morbius1 on 2024-09-24
If ssh works for you why not pursue an ssh solution. Something like WinSCP or SSHFS on Windows. You need to google all that as I've never needed to use it myself.

You have a lot of networking issues here and and I'm not convinced they are even samba related - at least not on a local LAN. If this is a local LAN issue.

---

### Post by madirisha on 2024-09-25
Ok, I will check that out. Thank you!

---

