---
title: "Can't access my network drives anymore"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by kamil212 on 2006-11-19
Everything was working fine until today.
I'm running Ubuntu 6.06 on my desktop comp and have a couple of WinXP machines around the house plus a Win2003 server.
I have network drives set up but when I try to access them it either freezes up or defaults to my home directory.  When I browse the Windows Networks from scratch it gives me an error: The folder contents could not be displayed.

I have no idea how to even get started on trying to figure this out.
I restarted everything (desk,server,router)
I added a switch between my router and my desk but I thought everything worked fine afterwards.  I'll try and take it out tomorrow but if that doesn't do it (I don't see what it would have anything to do with it) then I'm lost. 
Thanks in advance for any suggestions.

EDIT: It is my switch, WHY!?!?!
How can adding a switch mess up just the network browsing and not anything else (I still have my IP and shared printers)

---

### Post by hal10000 on 2006-11-19
Don't panic, you won't get lost.

I assume that your WinServer shares work with Windows clients if you login to your domain/workgroup. 
First, open a xterm and try:
```
smbclient -N -L servername
```
where "servername means the name of your Win2003 Server.

You shold see something like:
```

Anonymous login successful
Domain=[RUBY-TEAM] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        share           Disk      Datengrab
        IPC$            IPC       IPC Service (compaq server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (compaq server (Samba, Ubuntu))
Anonymous login successful
Domain=[RUBY-TEAM] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Server               Comment
        ---------            -------
        compaq               compaq server (Samba, Ubuntu)
        NEO                  neo server (Samba, Ubuntu)

        Workgroup            Master
        ---------            -------
        RUBY-TEAM            NEO

```
Of course the names of your servers, Workgroup etc. will differ.

Second, open nautilus File Manager, type [COLOR="Red"]<CTRL>+<L>[/COLOR] and type in [COLOR="Red"]smb://username@servername[/COLOR] (username@server means an existing user on your Windows-Server)

If it works, you will now see the shares on your server. You can now add a bookmark in your nautilus file-manager, so you can access the smbshares by clicking on that bookmark. But this procedure is only appropriate for non-permanent access to your shares.
If you like to have permanent access to your winshares, then you should install the smbfs package [COLOR="Red"]sudo apt-get install smbfs[/COLOR] and make a post here so I can help you to get it work.

So long

---

### Post by kamil212 on 2006-11-19
Thanks, but it didn't do anything
```
kamdreoni@64bitch:~$ smbclient -N -L server
Anonymous login successful
Domain=[MSHOME] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003 5.2]

        Sharename       Type      Comment
        ---------       ----      -------
Error returning browse list: NT_STATUS_ACCESS_DENIED
Anonymous login successful
Domain=[MSHOME] OS=[Windows Server 2003 3790 Service Pack 1] Server=[Windows Server 2003 5.2]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```

Strange thing is that I can print fine off of the shared printer on the server. (so I can see/connect to a shared printer but not drive)

---

### Post by hal10000 on 2006-11-19
Maybe if you Windows Server acts as a Domain Controller you must check the Domain Security Policy and de-activate the "Always secured connection" policy.

---

### Post by kamil212 on 2006-11-20
%$#&%#!&#%!&#!](*,) 

It's my switch!
How?
I just add a switch between my router and desktop and the network shares crap  out. Everything else works fine. I restarted everything, including the router. 
Any suggestions?
(static IP on the desktop)
I use the switch to hook up a little print server to share my printers and external usb drives.

---

### Post by kamil212 on 2006-11-21
bump???

---

