---
title: "official print server documentation is misleading?"
date: 2011-08-23
forum: New to Ubuntu
---

### Post by silverrope on 2011-08-23
Hi,
I am testing out a Lucid Lynx desktop to operate as a print server for my Windows and Ubuntu laptops in my home network. I have installed samba and looked at the official documentation,

[https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html](https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html)

It seems rather straightforward to set up a samba print server. But I am trying to understand the driver issues. The printers are attached to the ubuntu desktop with the proper linux drivers installed, i.e., I can print locally. Now, when a Windows client connects to the print share and tries to install the network printer (via Add Printer wizard), should it download windows drivers from the ubuntu server? If so, then do I have to install windows drivers into the ubuntu print share area for clients to download? Or should the client install drivers locally (from a CDROM for example)?

In either case, isn't the print server documentation misleading in making the print server setup to appear easier than it actually is? Or am I completely on the wrong track?

Sorry for the noobie questions.

---

### Post by mcduck on 2011-08-23
The computer(s) connecting to the print server shouldn't need any drivers at all, as it's only the server that directly communicates with the printer.

Edit:
If you need more functionality than what a basic Postscript printer has, you might actually need a driver on the Windows machine as well. In that case use the windows drivers that came with the printer and install them locally on the windows machine.

---

### Post by dave01945 on 2011-08-23
this post may be of use it shows the windows side of setting up aswell

[http://www.server-servers.com/ubuntu-print-server-windows-7/](http://www.server-servers.com/ubuntu-print-server-windows-7/)

they do recommend if you have a cd with drivers to use that

when i installed a print server on 2 linux machines both need the driver to work this caused me some problems as there was no 64bit driver for my printer :(

---

### Post by 3rdalbum on 2011-08-23
In my very ancient experience of Windows networking, I needed to install the printer driver on the clients and have them point to the server, and of course have a printer driver on the server too. This might have changed though - this was Windows 9x and NT.

---

### Post by silverrope on 2011-08-23
Well, I just followed the official documentation and it is clearly insufficient. Here is my situation. The print server is a ubuntu desktop with samba, the client is a Windows XP laptop.

On the client, when I activate the "Add Printer" wizard to install a network printer, it certainly finds the Ubuntu printers, no problem. When I click Next, I get the message "You are about to connect to a printer on UBUNTU, which will automatically install a print driver on your machine.... Do you want to continue?". I click Yes, then I get "The server for the printer does not have the correct printer driver installed. If you want to search for the proper driver, click OK.". After I click OK, I get a list of drivers (I guess these are included with XP?) or the button "Have Disk", which I assume it means I have to search for the driver from the CDROM.

So it seems I have to either install the driver locally or pull the driver from the ubuntu server (not mentioned in the doc). Since it is probably a pain to install a windows driver on the ubuntu share area, I just installed the driver locally. The tradeoff is that I have to manually install the drivers on every windows laptop!

---

### Post by JKyleOKC on 2011-08-23
I've run into a very similar situation when setting up printers for virtual machines running WinXP and Win2K, on my Xubuntu host. What I discovered was that, since my host runs the printer via CUPS (the default installation), I could choose **any** Windows print driver that generated PostScript output and it would work!

Since my printer is much more recent than the Windows systems to which I was trying to connect it (and consequently no drivers for it existed in the guest machines), that turned out to be the optimum solution for me. Hopefully it will work equally well for you. It appears that CUPS includes a PostScript interpreter, so that the Windows side needs only to generate a PostScript stream.

I used Samba initially to connect across my LAN, but then discovered that I could connect the printers using the IPP capability, which worked much better for me.

---

### Post by dave01945 on 2011-08-23
from what i can tell you need to add the drivers path in the smb.conf file under the section [print$] should look similar to this and change the path as appropriate to the location of the drivers
```

[print$]
comment = Printer Drivers
path = /etc/samba/drivers
browseable = yes
guest ok = no
read only = yes
write list = root
```

also have you checked the man pages 

```
man cupsaddsmb 
```

is a good place to start

---

### Post by silverrope on 2011-08-23
Ah, looking at cupsaddsmb, this looks like the way to go in order to install the print drivers on the samba server. However, I have no idea of the right path where the drivers should be located. But fortunately, there is an answer on the forum:

[http://ubuntuforums.org/showthread.php?t=279471](http://ubuntuforums.org/showthread.php?t=279471)

The drivers will eventually be placed in /var/lib/samba/printers which currently has a bunch of empty directories.

Thanks everyone for all the tips!

---

### Post by silverrope on 2011-08-24
OK I tried cupsaddsmb, but I am running into some trouble. I followed the man page:

1. I edited the smb.conf file according to instructions. testparm -s is below

```

[global]
    server string = S50 Ubuntu
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    username map = /etc/samba/smbusers
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    printcap name = cups
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    guest ok = Yes

[printers]
    comment = All Printers
    path = /var/spool/samba
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /etc/samba/drivers
    write list = root
    guest ok = No

[Backups]
    path = /media/files/Backups
    valid users = nobody
    read only = No
    create mask = 0755



```2. I downloaded the cups postscript drivers and microsoft drivers to the directory /usr/share/cups/drivers

3. I created a directory /etc/samba/drivers which I assume is where the drivers will be placed.

4. I ran the command sudo cupsaddsmb -a -v

The result is a running loop of errors:

```

Unable to copy Windows 2000 printer driver files (1)!
Running command: smbclient //localhost/print$ -N -A /tmp/0064c4e616cbf -c 'mkdir W32X86;put /tmp/0064c4e5e6da9 W32X86/BWBrother.ppd;put /usr/share/cups/drivers/ps5ui.dll W32X86/ps5ui.dll;put /usr/share/cups/drivers/pscript.hlp W32X86/pscript.hlp;put /usr/share/cups/drivers/pscript.ntf W32X86/pscript.ntf;put /usr/share/cups/drivers/pscript5.dll W32X86/pscript5.dll'
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.4.7]
tree connect failed: NT_STATUS_ACCESS_DENIED

```Any ideas on what to do next?

---

### Post by silverrope on 2011-08-25
Well, I guess the lack of response means that no one or very few have ever tried this, so I assume the best and probably only way to get Windows clients to print on a Ubuntu samba server is by installing the drivers on every Windows workstation then connecting to the network share. The writer of the following guide also seems to have reached the same conclusion:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch11_:_Sharing_Resources_with_Samba](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch11_:_Sharing_Resources_with_Samba)

---

### Post by mcduck on 2011-08-25
> **silverrope said:**
> Well, I guess the lack of response means that no one or very few have ever tried this, so I assume the best and probably only way to get Windows clients to print on a Ubuntu samba server is by installing the drivers on every Windows workstation then connecting to the network share. The writer of the following guide also seems to have reached the same conclusion:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch11_:_Sharing_Resources_with_Samba](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch11_:_Sharing_Resources_with_Samba)

To get them to *print* you only need the generic Postscript printer driver which should be included in Windows. Installing a printer-specific driver is only required if you want more than what Postscript can do. If it's worth the trouble or not depends pretty much on your printer and what kind of material you need to print.

---

### Post by silverrope on 2011-08-25
> **mcduck said:**
> To get them to *print* you only need the generic Postscript printer driver which should be included in Windows. Installing a printer-specific driver is only required if you want more than what Postscript can do. If it's worth the trouble or not depends pretty much on your printer and what kind of material you need to print.

Yes, but my original goal was not to install the driver locally (whether generic PS or printer-specific). I would prefer that the drivers are automatically delivered from server as that is what one would expect when one uses the "Add printer" wizard.

Anyway, I found the answer.

[http://geekyprojects.com/ubuntu/getting-windows-printer-drivers-from-cups/](http://geekyprojects.com/ubuntu/getting-windows-printer-drivers-from-cups/)

According to this tutorial, there are additional and slightly different details than what is written on the man page. I got cupsaddsmb to work so I now have the Samba server correctly delivering the generic PS drivers to Windows clients. 
:guitar:

Now if I can only figure out how to place and deliver the printer-specific drivers... :confused:
In any case the official ubuntu documentation is severely lacking! :sad:

---

