---
title: "Failure to connect to 127.0.0.1"
date: 2005-07-06
forum: Networking &amp; Wireless
---

### Post by geofff on 2005-07-06
I've been struggling to connect Ubuntu machine with 2 Windows machines. Ubuntu cannot be seen. Having searched the forum I've tried various fixes, and possibly caused more problems than I've solved. 

However I think I might be making progress. The How to install Samba at [http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/install.html) suggests trying $ testparm /etc/samba/smb.conf. This gives:
[PHP]geoff@fritz:~ $ testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[SharedDocs]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
# Global parameters
[global]
        netbios name = FRITZ_SMB_SERVER
        server string = %h
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\sp
assword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[homes]
        comment = Home Directories
        read only = No
        create mask = 0700
        directory mask = 0700

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[SharedDocs]
        path = /home/geoff/SharedDocs
        read only = No
        guest ok = Yes
        browseable = No[/PHP]

I'm not sure but I think this may be OK? 

However when I tried
$ sudo smbclient -L *computerhostname*
I get:
Error connecting to 127.0.0.1 (Connection refused)
Connection to fritz failed

Can someone tell me what I need to do to put this right. Thanks

Geofff

---

### Post by geofff on 2005-07-07
Anyone?

---

### Post by gruepig on 2005-07-07
[QUOTE=geofff]However when I tried
$ sudo smbclient -L *computerhostname*
I get:
Error connecting to 127.0.0.1 (Connection refused)
Connection to mycomputer failed

Can someone tell me what I need to do to put this right. Thanks

Geofff[/QUOTE]

127.0.0.1 is the IP of your loopback interface (which basically means it's the computer's way of refering to itself), so even if you could connect to 127.0.0.1, that wouldn't tell you much about whether your other computer could connect to it.  Try 'smbclient -L your_ip_address' (substituting in your IP address). If that doesn't work, check whether samba is running ('ps aux | grep samba'), whether it is listening on the network ('sudo lsof -i'), and whether you can telnet to the samba port ('telnet your_ip_address 139').

---

### Post by RJARRRPCGP on 2005-07-08
[QUOTE=geofff]
Error connecting to 127.0.0.1 (Connection refused)
[/QUOTE]

You can get that error message if the server isn't running or chose a port that the server isn't running on. Make sure that the server that you want to access, even if it's on the same PC you're using to browse the internet is running and that you chose the right port!!!

---

### Post by geofff on 2005-07-10
Thanks for the above. Results:

[PHP]geoff@fritz:~ $ smbclient -L 192.168.0.103
Error connecting to 192.168.0.103 (Connection refused)
Connection to 192.168.0.103 failed
geoff@fritz:~ $ ps aux | grep samba
geoff     8915  0.0  0.1   2948   576 pts/0    S+   11:09   0:00 grep samba
geoff@fritz:~ $ sudo lsof -i
Password:
COMMAND    PID   USER   FD   TYPE DEVICE SIZE NODE NAME
dhclient3 5910   root    4u  IPv4   8667       UDP *:bootpc
portmap   5929 daemon    3u  IPv4   8732       UDP localhost:sunrpc
portmap   5929 daemon    4u  IPv4   8733       TCP localhost:sunrpc (LISTEN)
master    7190   root   11u  IPv4  10712       TCP localhost:smtp (LISTEN)
master    7190   root   14u  IPv6  10716       TCP localhost:smtp (LISTEN)
gnome-cup 7630  geoff   20u  IPv4  13951       TCP localhost:32814->localhost:ipp (ESTABLISHED)
cupsd     8074 cupsys    0u  IPv4  13938       TCP localhost:ipp (LISTEN)
cupsd     8074 cupsys    5u  IPv4  13952       TCP localhost:ipp->localhost:32814 (ESTABLISHED)
firefox-b 8824  geoff   32u  IPv4  14650       TCP 192.168.0.103:33125->66.102.9.147:www (ESTABLISHED)
geoff@fritz:~ $ telnet 192.168.0.103 139
Trying 192.168.0.103...
telnet: Unable to connect to remote host: Connection refused[/PHP]

An interpretation of this would be very welcome! 

Re
[QUOTE=RJARRRPCGP] Make sure that the server that you want to access, even if it's on the same PC you're using to browse the internet is running and that you chose the right port!!![/QUOTE]

I'm not aware of setting a port and don't know where to find it or how to correct it if I have! 
TIA
Geoff

---

### Post by geofff on 2005-07-13
bump

---

### Post by gruepig on 2005-07-13
I think the samba process is actually smbd or nmbd, so I was wrong when I said to run 'ps aux | grep samba'.  Try 'ps aux | grep mbd' instead.  

Basically, the idea is to check your process table (ps = process) and see if you have any samba processes running.  Similarly, lsof lists open files (including sockets, which roughly correspond to network connections).  If you are running a samba server (in daemon mode), samba runs all the time, listening on port 139 waiting for a request.

If samba is running, I'd expect to see it listed in the output of lsof.  I'd also expect that when you telnet to port 139 you'd get a conclusion.  You should try 'ps aux | grep mbd' to be sure, but it looks to me like samba is not running.

You can likely start samba with 'sudo /etc/init.d/samba start' or through SWAT or other such tools.  Then use ps and lsof to see if samba is running.  You should also check the log files (maybe /var/log/samba/* or /var/log/daemon.log)  to see if any errors are reported.

---

### Post by hub on 2005-09-25
First check telnet 127.0.0.1.
if the answer is "unable to connect to remote host", you've got an issue (the same as mine!).
your problem in that case is not link to samba which should work properly (ps -aux | grep samba to check if it's running, sudo lsof -i to check if it's listening).

If you cannot connect your own host you won't be able to access swat (which use the address [http://localhost](http://localhost) sur le port 901).

In that case you have to find a solution to get rid of the strange error message. Then everything should work properly (smb.conf seemed to be correct)

I will search a solution for the "unable to connect to myself" problem and post the thread link on that thread.

---

