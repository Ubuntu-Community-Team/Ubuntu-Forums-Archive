---
title: "Why do I need to restart samba?"
date: 2015-02-18
forum: Networking &amp; Wireless
---

### Post by nhtrader on 2015-02-18
kubuntu 14.04.1 LTS x64
kde 4.13.3
Qt Version: 4.8.6
samba 4.1.6
smbd 4.1.6
nmbd 4.1.6


After I turn on my kubuntu PC (kubPC), I check samba with the following command:

$ ps aux|grep mbd
root      1844  0.0  0.0 191464  2860 ?        Ss   06:25   0:03 nmbd -D
root      6419  0.0  0.0 272732  7780 ?        Ss   13:35   0:00 smbd -F

So I assume that it is running. Then I go to a WinPC, and try to access the kubPC samba share, but I can't b/c I get an error message. 

Then I go back to the kubPC and use the following commands:
sudo su
service smbd restart
exit

Now I return to the WinPC and samba works. I get the login prompt for UserName and Password; enter data; and then I see all of the samba shares located on kubPC.

Why must I restart smbd after boot up? What's wrong?

---

### Post by TheFu on 2015-02-18
Does your Windows PC know how to reach the Ubuntu PC without using the IP address? Do you run DNS or have some other IP-to-hostname mapping on the Windows PC?  Broadcasts like Windows uses to locate other Windows PCs on the LAN is highly inefficient and not standard for Unix machines. The nmbd performs this task, but sometimes it takes a few minutes, I suppose.  

I modify the hosts file on Windows to find all my Linux PCs. [https://en.wikipedia.org/wiki/Hosts_%28file%29](https://en.wikipedia.org/wiki/Hosts_%28file%29) explains more about it.

---

### Post by nhtrader on 2015-02-18
> [COLOR=#000000]Does your Windows PC know how to reach the Ubuntu PC without using the IP address?[/COLOR]
Yes

> [COLOR=#000000]Do you run DNS or have some other IP-to-hostname mapping on the Windows PC? [/COLOR]
not that I'm aware of 

BTW, I tested this on windows using the following commands:
open command prompt
ping hostname <E>
reply from 10.10.10.10 bytes=32 time<1ms TTL=128


Just to be clear, it doesn't matter to me whether I use a hostname or ip address when using the FTP server. And to be clear, that is not my problem. My problem is that I can't transfer files on the local network when the server is set to use PASV. And when I disable PASV, I can use the FTP server locally but not externally.

---

### Post by bab1 on 2015-02-18
> **nhtrader said:**
> kubuntu 14.04.1 LTS x64
kde 4.13.3
Qt Version: 4.8.6
samba 4.1.6
smbd 4.1.6
nmbd 4.1.6


After I turn on my kubuntu PC (kubPC), I check samba with the following command:

$ ps aux|grep mbd
root      1844  0.0  0.0 191464  2860 ?        Ss   06:25   0:03 nmbd -D
root      6419  0.0  0.0 272732  7780 ?        Ss   13:35   0:00 smbd -F

This is not the proper response.  You should have 2 smbd and 1 nmbd daemons running.  Here is what I get from a 1 month old Samba v4.1.6 install
```
 ps aux|grep mbd
root       637  0.0  0.3 272692  7864 ?        Ss   16:17   0:00 smbd -F
root       663  0.0  0.1 272692  3904 ?        S    16:17   0:00 smbd -F
root      2236  0.0  0.1 191448  2560 ?        Ss   16:18   0:00 nmbd -D

```

```
smbd -V
Version 4.1.6-Ubuntu

```> 

So I assume that it is running. Then I go to a WinPC, and try to access the kubPC samba share, but I can't b/c I get an error message. 

Then I go back to the kubPC and use the following commands:
sudo su
service smbd restart
exit

Now I return to the WinPC and samba works. I get the login prompt for UserName and Password; enter data; and then I see all of the samba shares located on kubPC.

Why must I restart smbd after boot up? What's wrong?
How did you install Samba?  Hopefully you installed it via the repos.  How did you configure Samba on this host?

The reason for the 2 smbd daemons is that the first one forks and the copy is used by a user.  The next user gets another forked copy when there are multiple users.

---

### Post by bab1 on 2015-02-18
> **nhtrader said:**
> 
Just to be clear, it doesn't matter to me whether I use a hostname or ip address when using the FTP server. And to be clear, that is not my problem. My problem is that I can't transfer files on the local network when the server is set to use PASV. And when I disable PASV, I can use the FTP server locally but not externally.

What does this have to do with your Samba problem?

---

### Post by nhtrader on 2015-02-19
> Just to be clear, it doesn't matter to me whether I use a hostname or ip  address when using the FTP server. And to be clear, that is not my  problem. My problem is that I can't transfer files on the local network  when the server is set to use PASV. And when I disable PASV, I can use  the FTP server locally but not externally.
> What does this have to do with your Samba problem?

Sorry. My mistake. This was to be posted to a different discussion. This does not belong here.

As to the installation of samba, I performed a clean install of kubuntu 14.0.4.1 LTS with all known updates, then I manually installed the following pkgs using:

sudo apt-get samba samba-common
Then I modified the smb.conf

So when I turn on my kubPC and then go use my WinPCs....

The error message that I see on a WinXP is ...
\\kubPC\Share1 is not accessible. You might not have permission to use this network resource. 
Contact the administrator of this server to find out if you have access permissions.
The network path was not found.

The error message from Win7HP_64 SP1 is ...
Windows cannot acess \\kubPC\Share1 
Check the spelling of the name. Otherwise, there might be a problem with your network. To try to identify network problems, click Diagnose.
Error code:0x80004005
Unspecified Error

Then I go to the kubPC and I use the following command: sudo service smbd restart
Now I go back to the WinPCs and after I select the kubPC, the login window appears so that I can enter my kubPC username and password, and then samba server works perfectly.

---

### Post by nhtrader on 2015-02-20
I found the answer after an exhaustive iterative process of isolating various entries in my smb.conf

The culprit is the following line:

  bind interfaces only = yes

When this line is enabled, samba must be restarted after startup/boot. However if I eliminate this one line (disable it), samba works perfectly. I do not need to restart it.

Here is a copy of the globals that I'm using:

```
[GLOBAL]
workgroup = MYHOME
server string = %h server (Samba, Ubuntu)
log file = /var/log/samba/log.%m
max log size = 100000
syslog = 2
panic action = /usr/share/samba/panic-action %d
security = user
server role = standalone server
passdb backend = tdbsam
obey pam restrictions = yes
map to guest = bad user
   name resolve order = hosts lmhosts bcast
   dns proxy = no
   interfaces = 127.0.0.0/8 eth1
#   bind interfaces only = yes
   hosts allow = 127.0.0.1 10.10.10.

```

---

