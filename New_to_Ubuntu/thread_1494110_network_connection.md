---
title: "network connection"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by ck_linux on 2010-05-26
[FONT=Courier New][SIZE=1]I am trying the whole week to access a windwos share from xubuntu 10.04.
Nothing found what helps so maybe someone can help me here.
I installed at the end: smbclient, samba, smbfs.
I do have a windows server which shares a 'share' called 'data'

I tried several ways, but noone seems to have a problem, so or I am missing something or did not configure something correctly. As I understand I did not need samba because I only want to access the 'shared directory' on the windows server.
I tried first with: 
smbclient -L //192.168.1.1/data 
the answer was hopeful

Enter user2's password: 
Domain=[W2000] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       Remote IPC
    D$              Disk      Default share
    print$          Disk      Printer Drivers
    SharedDocs      Disk      
    data            Disk      
    Windows (C)     Disk      
    ADMIN$          Disk      Remote Admin
    C$              Disk      Default share
    Printer         Printer   Microsoft Office Document Image Writer
session request to 192.168.1.1 failed (Called name not present)
session request to 192 failed (Called name not present)
Domain=[W2000] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------

So whatever I do I received error messages.
IF I still try to connect with:

$ smbclient  //192.168.1.1/data -U localadmin
Enter localadmin's password: 
Domain=[W2000] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]
smb: \> dir
NT_STATUS_ACCESS_DENIED listing \*

        54454 blocks of size 524288. 26623 blocks available
smb: \> exit


I am lost.
Can not find out WHAT I am missing or what I am doing wrong.
Forum does not help, google ... can not find a useful solution.
I tried the chat, but people are funny and answer: try a wire

Please let me know any suggestion which can give me a new idea how to proceed.
Thanks in advanced

[/SIZE][/FONT]

---

### Post by -humanaut- on 2010-05-26
Open your file manager and type smb://windows.ip.address into the address bar make sure your windows machine is actively scanning for your connection.

---

### Post by ck_linux on 2010-06-01
For anyone who follows the forums: this was not the solution.
smb://windows.ip.address is using smfs and if the commandline does not work, trying the Nautilus interface is useless.

If a solution is found I will update the forum.

If however anyone does have any suggestions, please add a quick note. Thanks !

---

### Post by ck_linux on 2010-06-06
great, absolutely great, nobody does have any idea!
I can't believe I am the only one with problem.

Ok see thread : **samba_smbfs ** for the continue story and hopefully the solution.
CK

---

### Post by anewguy on 2010-06-06
You shot yourself in the foot for support - -humanaut- posting was not offered as a solution, but rather as simply a test to see if the network was being scanned properly.  The tone of your response is what turns most volunteers away from trying to help.

My suggestion?  I would now try posting this in the networking and wireless forum:

[http://ubuntuforums.org/forumdisplay.php?f=336]("http://ubuntuforums.org/forumdisplay.php?f=336")


Best of luck.

Dave

---

