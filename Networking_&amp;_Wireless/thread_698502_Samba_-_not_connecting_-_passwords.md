---
title: "Samba - not connecting - passwords?"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by zoomiest on 2008-02-16
I have been pulling my hair out with Samba... I am on the newest version... of everything...

When I do a smbclient -L [host] I get
[INDENT]Domain=[SOLOMON] OS=[Unix] Server=[Samba 3.0.26a]
tree connect failed: NT_STATUS_ACCESS_DENIED
allan@Solomon:/$ [/INDENT]

I CAN connect from another machine, with smbclient //hostname/username (but what then? I just get a smb: prompt... not commands work...)

When I run a testparm I get weird things...
[INDENT]Load smb config files from /etc/samba/smb.conf
Can't find include file /home/samba/etc/smb.conf.
Processing section "[family]"
Processing section "[laura]"
Processing section "[daniela]"
Processing section "[allan]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE[/INDENT]

My two questions are: 
1. Why can't I see my shares graphically on other machines?
2. what is the smb.conf that SHOULD be in /home/samba/etc/ ? (I went their and made the directories for it... but Samba doesn't seem to be making its own smb.conf file.)

Here is my /etc/samba/smb.conf 
```
[global]
        workgroup = COM-CENTER
        server string = %h Samba Server (Ubuntu)
        interfaces = lo, eth0
        bind interfaces only = Yes
        obey pam restrictions = Yes
        passdb backend = tdbsam
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = cups
        dns proxy = No
        wins support = Yes
        panic action = /usr/share/samba/panic-action %d
        comment = Home Directories
        invalid users = root
        valid users = %S
        read only = No
        create mask = 0775
        directory mask = 0775
        printing = cups
        print command = 
        lpq command = %p
        lprm command = 
        browseable = No
        include = /home/samba/etc/smb.conf.

[family]
        comment = Shared Family folders
        path = /home/family
        create mask = 0766
        guest ok = Yes
        browseable = Yes

[laura]
        comment = User's home directory
        path = /home/%U
        valid users = %U, root

[daniela]
        comment = User's home directory
        path = /home/%U
        valid users = %U, root

[allan]
        comment = User's home directory
        path = /home/%U
        valid users = %U, root

[printers]
        comment = All Printers
        path = /var/spool/samba
        read only = Yes
        create mask = 0700
        printable = Yes

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
        read only = Yes
        browseable = Yes
 
```

How does that look? 

In a Feb 2006 [Tutorial]("http://http://www.linuxforums.org/servers/howto:_fileserver_with_samba_and_printserver_with_cups.html") I read, it said that if you get the NT_STATUS_LOGON FAILURE message, then either 
[INDENT]1. Check that the smb.conf file has you in the correct workgroup
2. Check your samba passwords and which password file it use[/INDENT]s.

... so any help where Samba 3.0.26a keeps its passwords would be great.

Any help at all would... temp me to name my first child after you...

I am on Ubuntu 7.10 Gutsy

---

### Post by lnx4me on 2008-02-16
Okay I see a few things in the config file that doesn't really add up.
the invalid user = root but you have specified root in your share definitions. I also see that you are using an include statement in the global setting and I wonder about that. Since it is creating an error when you run testparam. The DOMAIN solomon does not add up to what is specified in the WORKGROUP line.
Start by removing the include line first
then remove the user root in your share definitions
then rerun testparm.
the restart samba.

---

### Post by zoomiest on 2008-02-16
1. I took out the include reference, and it is now not showing up in the testparam output... but what was it good for, anyway... don't I need it?

2. I took out the word root of the share references... and nothing is different. I still get
```
Domain=[SOLOMON] OS=[Unix] Server=[Samba 3.0.26a]
tree connect failed: NT_STATUS_ACCESS_DENIED
```
... and Samba is still not broadcasting its shares to the network (I can see the machine, but not the shares. I just get the the NT_STATUS... message.

---

### Post by lnx4me on 2008-02-16
Do you have a copy of the original smb.conf file? It looks like to me in the Global section you need to remove the comment-homes and everything below it in the Global Section only. Your printer definitons and your shares look ok.

---

### Post by lnx4me on 2008-02-16
What are the other machines your browsing from?

---

### Post by zoomiest on 2008-02-18
INX4ME, thanks... Your comment about cutting off everything from the home comment, sparked revision - I just brought back the original smb.conf and only edited the minimum, and **it now works**.

To compare. Here is near-original smb.conf with only a couple minor edits.
```

[global]
   workgroup = COM-CENTER 
   server string = %h Server (Samba, Ubuntu)
   wins support = noS.
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *passwd:*password\supdated\ssuccessfully* .
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

[homes]
   comment = Home Directories
   browseable = yes 
   valid users = %S

[family]
path = /home/family
comment = Shared Family folders
guest ok = yes
create mode = 0766
browseable = yes
public = yes
read only = no

[laura]
comment = User's home directory
path = /home/%U
read only = no
valid users = %U

[daniela]
comment = User's home directory
path = /home/%U
read only = no
valid users = %U

[allan]
comment = User's home directory
path = /home/%U
read only = no
valid users = %U


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no


```

In answer to your question, I have been browsing the network with a WinXP computer, and a couple of Linux desktops, using SMB4K (kde CIF/smb browser)

Now I just have to fine tune the user permissions thing... Everything seems to be shared wide open in the network. 
My plan is to look toy with the smb.conf, and linux permissions... any other suggestions?

---

### Post by Iowan on 2008-02-18
Since it's working, make a copy for disaster protection (name it smb.conf.bak - or something equally catchy). The **browseable = yes** is what makes the shares appear wide-open.  You shouldn't be able to *access* one of the files in someone else's directory (except as root).
Seems like my smb.conf builds home directories for each user without needing to specifically set up shares.
[http://it.samba.org/samba/docs/man/manpages-3/smb.conf.5.html]("http://it.samba.org/samba/docs/man/manpages-3/smb.conf.5.html") Look under **The [homes] section**

BTW, "wins support = noS." doesn't look kosher.

---

### Post by lnx4me on 2008-02-18
Well,
 You dont really need to specify home user definitions. By default the homes section uncommented would allow only the user to logon the nix box to the home section of the tree. Specifying security=user and uncommenting the homes section would have been all thats required here. Except it appears in this case the family has a share all users can access. the samba by example complete book is posted to the internet. It has a lot of examples and goes through setting up the smb.conf file. I dont use nix boxes with GUI's I prefer the good old fashion it works method. I dont use swat and in the 40-50 so far file servers I've built. most of the time people try to over complicate what they are trying to do. I highly recommend reading the Samba by example for anyone wishing to use the smb protocol in a mixed OS enviroment.

Also as Iowan stated the wins support =noS. isn't right. You should fix it. 

BTW your welcome. I dont want you to name a child after me, I have 4 teenagers I am attempting to give away. Just take one of them and I'll call it even.
:lolflag:

Dont forget to close the thread

---

### Post by msinkm on 2008-02-18
I don't know if you checked this or not, but did you set your ubuntu firewall correctly?  I was having similar problems, but it just turned out that I had to permit smb traffic on both machines with firestarter.

Hope this helps

---

