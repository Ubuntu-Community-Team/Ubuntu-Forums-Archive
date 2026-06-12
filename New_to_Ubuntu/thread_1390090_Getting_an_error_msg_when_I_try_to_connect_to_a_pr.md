---
title: "Getting an error msg when I try to connect to a printer shared by Cups 1.3.9"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by henriquelm on 2010-01-25
Hello there guys, I'm getting this error message ("Cannot connect to network printer, error 0x000006d1") when I try to connect a Windows Vista client pc to a printer shared by a Ubuntu Server running Cups 1.3.9. Ubuntu Server 8.10 won't let me upgrade cups to a newer version.

Do you guys have a clue if this problem is related to Cups or to the Windows client pc?

:???:

---

### Post by cariboo on 2010-01-25
Have you got share printers connected to this sytem enabled? to check open the cups web interface, and check under Adminstration. I'm running Karmic, so the interface is a little different, but the functionality is the same. See screen shot.

---

### Post by henriquelm on 2010-01-26
> **cariboo907 said:**
> Have you got share printers connected to this sytem enabled? to check open the cups web interface, and check under Adminstration. I'm running Karmic, so the interface is a little different, but the functionality is the same. See screen shot.

I don't have this option enabled, but Cup's shared printers have been working with Windows XP clients without this option. Also the printers are already shared, but maybe by a different method. I will enable this option and see if it fixes the problem.

Thanks

---

### Post by Mugatu on 2010-09-09
I just had this error on a Server 2008 R2 machine.  I don't know if this will help you or not, but this is what I did to fix it:

Start --> Run --> gpedit.msc --> OK

Computer Configuration --> Administrative Templates --> Printers --> Always render print jobs on the server --> right-click --> Edit --> Disabled --> OK

---

### Post by TrinitronX on 2013-03-02
> **Mugatu said:**
> I just had this error on a Server 2008 R2 machine. I don't know if this will help you or not, but this is what I did to fix it:

Start --> Run --> gpedit.msc --> OK

Computer Configuration --> Administrative Templates --> Printers --> Always render print jobs on the server --> right-click --> Edit --> Disabled --> OK

OMG!!! THANK YOU FOR THIS!! I've been working on getting a printer share via samba+cups working for weeks now, and this fixed it!

For posterity (because I really hope nobody ever has to struggle with this again):

I kept getting various errors such as these hideously unhelpful ones:

"windows cannot connect to the printer 0x000006d1"
"Cannot install printer. The print processor does not exist."
"There are no Print Processors"

[SIZE=3]**Reason for Problem:**[/SIZE]

Samba only supports 'winprint' [Print Processor]("http://technet.microsoft.com/en-us/library/cc976744.aspx") and 'RAW' Data Type.  HP printer I was trying to install had a custom print processor: '[FONT=courier new]hpzpplhn.dll[/FONT]', and kept complaining about it.

[SIZE=3][B]Steps to fix:
[/B][/SIZE]

[LIST=1]
[*]I configured drivers for samba using [this guide]("http://blog.realcomputerguy.com/2011/10/cups-samba-64bit-driver-installation.html") ([and also this guide]("http://blog.encomiabile.it/2010/02/17/samba-cups-and-windows-32-64-bit-drivers/")) and running: ```
cupsaddsmb -a -v
```
[*](Optional) I installed [this windows update(KB2647753)]("http://support.microsoft.com/kb/2647753") (not sure if this was completely necessary, but could also fix other potential windows printing problems?)
[*]Deleted the offending printer from my system via: 
Start --> Run [Super+R] ```
printmanagement.msc
``` --> OK
Print Management --> Print Servers --> *(Local machine name)* --> Printers
Select printer, right click & delete!
[*]Deleted the related printer driver via *printmanagement.msc*
Print Management --> Print Servers --> *(Local machine name)* --> Drivers
Select the related printer driver, right click & delete!
[*]Start --> Run --> ```
gpedit.msc
``` --> OK
Computer Configuration --> Administrative Templates --> Printers --> Always render print jobs on the server --> right-click --> Edit --> **Disabled **--> OK
[*]Start --> Devices and Printers --> Add a printer --> Add network printer --> *Select printer shared via linux samba server* --> next..next..finish **SUCCESS!**
[/LIST]
[B]
Additional Troubleshooting Info


[/B]I ran into various permissions issues along the way. Make sure your [FONT=courier new]/etc/samba/smb.conf[/FONT] has these settings when you are trying to use **[FONT=courier new]cupsaddsmb[/FONT]**, or you are remotely adding printer drivers:

```

[global]

security = user
username map = /etc/samba/smbusers  # You may need to configure this to map your linux username to your windows one if they're different
load printers = yes
printing = cups
printcap name = cups

[printers]
        comment = All Printers
        browseable = yes
        path = /var/spool/samba
        printable = yes
        writeable = no
;       guest ok = no
;       read only = yes
        create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
        comment = Printer Drivers
        path = /etc/samba/drivers
        browseable = yes
        writeable = yes
        read only = no
        guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
        write list = root, @lpadmin  ## You may also need to explicitly add your usernames here if you have problems.  For Example: root, @lpadmin, linuxusername, windowsusername, Administrator)


```


[B][SIZE=3]Helpful commands to troubleshoot:[/SIZE]

rpcclient: [/B]Used to explore the samba shared printers, drivers, etc...
For help, run ```

rpcclient localhost -N
help
help <some-command>
adddriver --help
exit # exits out of rpcclient shell

```

create a tmp file with your samba credentials like this:```
echo -e 'username = your-username\npassword = your-password\ndomain = your-workgroup-name' >> /tmp/smbauth
```
```


#List all shared printers:
rpcclient localhost -N -A /tmp/smbauth -c 'enumprinters'
#List all drivers installed on server:
rpcclient localhost -N -A /tmp/smbauth -c 'enumdrivers'
#List all print processors/datatypes on server (right now samba only supports 'winprint' & 'RAW'):
rpcclient localhost -N -A /tmp/smbauth -c 'enumprocs' 
rpcclient localhost -N -A /tmp/smbauth -c 'enumprocdatatypes'

#Get info about your printer:
rpcclient localhost -N -A /tmp/smbauth -c 'getprinter your-printer-name'
#Get lots of info about your printer:
rpcclient localhost -N -A /tmp/smbauth -c 'getprinter your-printer-name 2'

#Get info about installed driver:
rpcclient localhost -N -A /tmp/smbauth -c 'getdriver your-driver-name'

```

Help for [FONT=courier new]*adddriver *[/FONT]command:
```


Usage: adddriver <Environment> \
        <Long Printer Name>:<Driver File Name>:<Data File Name>:\
        <Config File Name>:<Help File Name>:<Language Monitor Name>:\
        <Default Data Type>:<Comma Separated list of Files> \
        [version]
```

**smbclient**: Used to connect to samba shares, upload drivers, etc...

```

#Copy x64 driver files from windows to ~/mydrivers/ first
cd ~/mydrivers/
smbclient //localhost/print$ -N -A /tmp/smbauth -c "$(for f in $(ls -1 .); do echo "put /home/your-username/mydrivers/${f} x64/${f}; "; done)"
#Install a new driver (I tried manually installing Windows 7 x64 driver for HP PSC 1300 series in samba)
rpcclient localhost -N -A /tmp/smbauth -c 'adddriver "Windows x64" "psc-1300-series-driverhack:unidrv.dll:hpo1300t.gpd:unidrvui.dll:unidrv.hlp:LIDIL hpzlllhn:RAW:hpzevlhn.dll,hpzstlhn.dll,hpzuilhn.dll,hpz3rlhn.dll,hpzlalhn.dll,hpzsslhn.dll,hpo13x0t.gpd,hpz3clhn.ini,hpzsmlhn.gpd,hpz3mlhn.gpd,hpo1300t.xml,hpzsclhn.dtd,hpfres50.dll,hpfime50.dll,hpfiglhn.dll,hpzprlhn.dll,hpzlelhn.dll,unires.dll,stdnames.gpd,stddtype.gdl,stdschem.gdl,stdschmx.gdl"'
rpcclient localhost -N -A /tmp/smbauth -c 'setdriver psc-1300-series psc-1300-series-driverhack'

```

**printmanagement.msc**: Windows tool for administering print servers.

If you have allowed remote management in samba, you can add drivers more easily using this tool.  Just add your server by clicking: Print Servers --> right click --> Add/Remove Servers --> Browse --> Select Server --> Add to list --> Apply --> OK

To add drivers: Drivers --> right click --> Add Driver --> select arch (x64 or x86) --> next --> select manufacturer & printer model -->  next --> finish

**regedit.exe**: Edits windows registry (so we can look for the printer-related registry keys)

To see what your printer driver's settings are (these are what to input into the [FONT=courier new]*rpcclient -c'adddriver'*[/FONT] command) look under: 
(x64-bit): [FONT=courier new]HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows x64\Drivers\Version-3[/FONT]
(32-bit): [FONT=courier new]HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows NT x86\Drivers\Version-3[/FONT]

Installed Print Processors are under: [FONT=courier new]HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Environments\Windows x64\Print Processors[/FONT]

Print Monitors are under: [FONT=courier new]HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Print\Monitors[/FONT]

---

### Post by QIII on 2013-03-03
Thank you for sharing.  Everyone’s questions and answers are valuable.

If a thread has had no activity for about a year or more, it is best to start a new thread of your own. Not only will you be more likely to get a response, but things change so quickly in the software world that an old thread may cause you more trouble than it will help due to outdated information.

Please feel free to add a link to the original thread in your new one if you think it might be helpful.

Best wishes!

*Thread **closed.***

---

