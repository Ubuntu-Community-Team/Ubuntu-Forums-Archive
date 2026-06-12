---
title: "windows shares &amp; printer problem"
date: 2005-08-24
forum: Networking &amp; Wireless
---

### Post by soonindallas on 2005-08-24
hi all,  it was all working yesterday...

I have a Win XP box and a laptop with Ubuntu, a WLAN router/gateway linked to a cable modem.  On the Ubuntu laptop I use samba to access windows shares, and printing througn samba to a shared printer on the XP box worked fine until yesterday.

Today I noticed that I could not print to the printer on the XP box: Administration > Printers > properties for that printer gives me an error: NT_STATUS_UNSUCCESSFUL

In addition, and contrary to symptoms described in another recent thread, that my windows shares are today inaccessible: I cannot navigate to them with nautilus.  Places > Connect to server fails, in Network the workgroup is listed but trying to browse it also fails.

Each box can ping the other, both have internet access.

Since yesterday the only change I have made to the Ubuntu setup was to accept an update proposed by synaptic this morning.  I made no changes to the windows shares or permissions.

As for others I have found samba documentation to be hermetic.  Can anyone show me where to start troubleshooting this, or point me to a solution ?  For example, what might make the windows box invisible to gnome/nautilus ?

thanks

Peter

---

### Post by s_p_a_r_k_y on 2005-08-24
for debuggins we return to the grand command line.

type this 
[code]smbclient -L name_of_windows_box -U useraccount_on_windows_box
it'll ask you for a password and you supply it. It should list all shares on it. If not, then it seems as if the problem is on the Windows Box. Any firewalls?

if You can't do the above command try this 
telnet IP_address_of_windows 139
mine says this

telnet 192.168.0.19 139
Trying 192.168.0.19...
Connected to 192.168.0.19.
Escape character is '^]'.
which means it connected successfully. If yours times out, then again its a problem with connecting to that port on the windows machine

---

### Post by soonindallas on 2005-08-24
thanks for the suggestion.  when I type

peter@ubuntu:~$ smbclient -L windows_box -U my_account

I get:

timeout connecting to 82.101.8.43:445
timeout connecting to 82.101.8.43:139
Error connecting to 82.101.8.43 (Operation already in progress)
Connection to windows_box failed

which is wierd: I don't have anything configured in 82.101...

where might this come from ?

otherwise telnet to this box succeeds.

---

### Post by s_p_a_r_k_y on 2005-08-24
what about smbclient -L IPADDRESS -U win_user

---

### Post by soonindallas on 2005-08-25
[QUOTE=soonindallas]thanks for the suggestion.  when I type

peter@ubuntu:~$ smbclient -L windows_box -U my_account

I get:

timeout connecting to 82.101.8.43:445
timeout connecting to 82.101.8.43:139
Error connecting to 82.101.8.43 (Operation already in progress)
Connection to windows_box failed

which is wierd: I don't have anything configured in 82.101...

where might this come from ?

otherwise telnet to this box succeeds.[/QUOTE]
 [QUOTE=s_p_a_r_k_y]what about smbclient -L IPADDRESS -U win_user[/QUOTE]

here's what i get:

```
peter@ubuntu:~$ smbclient -L 192.168.0.5 -U peter
Password:
Domain=[ISABELLE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        My Documents    Disk
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        Printer         Printer   CutePDF Writer
        Canoni560       Printer   Canoni560
session request to 192.168.0.5 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[ISABELLE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------


```

it looks like the disk and the printer shares are visible to smbclient... the canon is the printer that worked yesterday and gave the error I described above.

what do you think ?  and thanks for your help.

---

### Post by soonindallas on 2005-08-25
[QUOTE=soonindallas]here's what i get:

```
peter@ubuntu:~$ smbclient -L 192.168.0.5 -U peter
Password:
Domain=[ISABELLE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        My Documents    Disk
        IPC$            IPC       Remote IPC
        print$          Disk      Printer Drivers
        Printer         Printer   CutePDF Writer
        Canoni560       Printer   Canoni560
session request to 192.168.0.5 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[ISABELLE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------


```

it looks like the disk and the printer shares are visible to smbclient... the canon is the printer that worked yesterday and gave the error I described above.

what do you think ?  and thanks for your help.[/QUOTE]
 I looked at this similar thread: [http://ubuntuforums.org/showthread.php?t=55207](http://ubuntuforums.org/showthread.php?t=55207)
and could reproduce some of the steps, but not the fix:

restarting samba allos me to perform smbclient -L 127.0.0.1
whereas before the restart I get:
peter@ubuntu:~$ smbclient -L 127.0.0.1
Error connecting to 127.0.0.1 (Connection refused)
Connection to 127.0.0.1 failed

performing "smbclient -L netbios_name_of_windows_box" fails.
"peter@ubuntu:~$ smbclient -L 192.168.0.5" wih or without "-U user" prompts me for a password, then lists successfully the shares, then:

"session request to 192.168.0.5 failed (Called name not present)"; server, workgroup information is not reported for the target box.

Here's the curious part: from my XP box, I can access my (Ubuntu) laptop shares perfectly!

---

### Post by s_p_a_r_k_y on 2005-08-25
take a look at this

"peter@ubuntu:~$ smbclient -L windows_box -U my_account

I get:

timeout connecting to 82.101.8.43:445
timeout connecting to 82.101.8.43:139"

If your windows_box's IP is 192.168.0.5 then why when you do smbclient -L windows_box does it try connecting to 82.101.8.43? THat seems like its your external interface or something is wrong.

Check you /etc/hosts file to look for an entry of windows_box and also look in /etc/samba/smb.conf

and check your name resolve order, mine is commented out so I'm not sure what the default it, but you may want to have it like this

 name resolve order = bcast lmhosts host wins 

so that it looks on the local network first

---

### Post by soonindallas on 2005-08-25
[QUOTE=s_p_a_r_k_y]take a look at this

"peter@ubuntu:~$ smbclient -L windows_box -U my_account

I get:

timeout connecting to 82.101.8.43:445
timeout connecting to 82.101.8.43:139"

If your windows_box's IP is 192.168.0.5 then why when you do smbclient -L windows_box does it try connecting to 82.101.8.43? THat seems like its your external interface or something is wrong.

Check you /etc/hosts file to look for an entry of windows_box and also look in /etc/samba/smb.conf

and check your name resolve order, mine is commented out so I'm not sure what the default it, but you may want to have it like this

 name resolve order = bcast lmhosts host wins 

so that it looks on the local network first[/QUOTE]
 thanks sparky: that's the track I've been exploring - incorrect nam resolution on the lan.

I discovered I can ping the XP box from the Ubuntu laptop by IP but not by name.  Pinging the Ubuntu box from the XP box works by IP *and* by name, so there's a problem with name resolution on the LAN for Ubuntu.  Internet host name resolution works fine -- I can ping [www.yahoo.com](www.yahoo.com) from the Ubuntu box.  I guess the gateway is passing that resolution task to the IPS's DNS and correctly passing that resolution back to Ubuntu.

My resolution order is commented out.  I'll try reversing it.

---

### Post by soonindallas on 2005-08-25
wierdness...

reversed the order of name resolution and restarted samba - didn't seem to change anything.

I rebooted and browsing of shares on the XP box now works!

I did notice after the reboot that the my NIC is back to eth0 and my wireless connection back to eth1... didn't touch anything tho'.

however what you refer to as netbios resolution is still not working:  where do I go from here ?

---

### Post by s_p_a_r_k_y on 2005-08-25
so now you can type in smb://windows_boxen and it connects? If so then the netbios name is being resolved correctly

---

### Post by soonindallas on 2005-08-25
[QUOTE=s_p_a_r_k_y]so now you can type in smb://windows_boxen and it connects? If so then the netbios name is being resolved correctly[/QUOTE]
 well, what you type is what I see in the sexy gnome GUI navigator-type explorer thing.

from the command line I type smbclient //isabelle/my_xp_share and I'm in the share!

can't ping the darned box by name, though. I did see your contribution to another thread on that, thanks.

cheers!

Peter

---

### Post by s_p_a_r_k_y on 2005-08-25
you wont be able to ping it by name from Linux. Linux looks up things in the host file or DNS but not using samba. If you want to ping it by host stick it into the /etc/hosts file, then that'll work. Unlike windows, samba is not integrated in the operating system, and thus runs on top of Linux. Therefore old utilities like ping and traceroute and other command line tools don't use netbios to look for hosts

---

### Post by soonindallas on 2005-08-25
[QUOTE=s_p_a_r_k_y]you wont be able to ping it by name from Linux. Linux looks up things in the host file or DNS but not using samba. If you want to ping it by host stick it into the /etc/hosts file, then that'll work. Unlike windows, samba is not integrated in the operating system, and thus runs on top of Linux. Therefore old utilities like ping and traceroute and other command line tools don't use netbios to look for hosts[/QUOTE]
 got it.  thanks for your help dude.

---

