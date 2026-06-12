---
title: "Programs just STOP working"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by Cloud Wolf on 2009-03-29
Recently, I have encountered BIG problems with Ubuntu Intrepid. I run 8.10, and all of a sudden, for no reason whatsoever that I can gather, many apps stop working, most of them are ones that require full screen.
At first I thought it was just a problem with WINE, as I was trying to run several games, such as AirRivals, S4 League. These had all worked perfectly before.
But then I tried to run Savage XR/Savage 2. These are both linux clients, but these did not work either. The update manger started, but the game did not.
Then more recently I tried to run TvTime, a simple Tv viewer I downloaded from the Ubuntu repositories. That fails to load as well.
One more thing. With the games, The process are still running, and i have to kill them (the exes) from the system monitor.
I am at a total loss at what do do here.
Please help!

---

### Post by llamakc on 2009-03-29
If Desktop Effects is enabled, disable it and try running the programs again.

---

### Post by Cloud Wolf on 2009-03-29
I don't have any effects on for just that reason. So its not that :(

---

### Post by Kareeser on 2009-03-29
Try running the linux apps through the terminal. That will output any error messages for us to see.

---

### Post by llamakc on 2009-03-29
I would open the Terminal and run the program from there. See if any error appears. 

Also, when you check for the running processes (still running) in the Terminal with the command `ps -aux` please cut/paste that back here in this thread.

---

### Post by James M on 2009-03-29
> **Cloud Wolf said:**
> Recently, I have encountered BIG problems with Ubuntu Intrepid. I run 8.10, and all of a sudden, for no reason whatsoever that I can gather, many apps stop working, most of them are ones that require full screen.
At first I thought it was just a problem with WINE, as I was trying to run several games, such as AirRivals, S4 League. These had all worked perfectly before.
But then I tried to run Savage XR/Savage 2. These are both linux clients, but these did not work either. The update manger started, but the game did not.
Then more recently I tried to run TvTime, a simple Tv viewer I downloaded from the Ubuntu repositories. That fails to load as well.
One more thing. With the games, The process are still running, and i have to kill them (the exes) from the system monitor.
I am at a total loss at what do do here.
Please help!


Very odd. It could be Xorg.

---

### Post by Cloud Wolf on 2009-03-29
I tried running s4 league, and it came up with
```
jacob@UBUNTU-VAIO1:~$ '/home/jacob/Desktop/S4League.desktop' 
/home/jacob/Desktop/S4League.desktop: line 1: [Desktop: command not found
fixme:exec:SHELL_execute flags ignored: 0x00000500
/home/jacob/Desktop/S4League.desktop: line 6: Files/alaplaya/S4League: No such file or directory
jacob@UBUNTU-VAIO1:~$ fixme:shdocvw:PersistStreamInit_InitNew (0x14bca0)
fixme:shdocvw:navigate_url Unsupported args (Flags 0x33ed70:3; TargetFrameName 0x33ed60:8)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
fixme:iphlpapi:NotifyAddrChange (Handle 0x7daaaa08, overlapped 0x7daaa9ec): stub
err:mshtml:set_profile SetCurrentProfile failed: 80520015
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12fef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x14bd3c)->((null) 1 0x33d1f8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 25 2 0x33d20c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 26 2 0x33d20c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14bd3c)->(0x33d248)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d30c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33d39c)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:navigate_url Unsupported args (Flags 0x33eda0:3; TargetFrameName 0x33ed90:8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 29 2 0x33ea58 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x14bd3c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x33e9b0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x33e9b0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 26 2 0x33ea38 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 29 2 0x33ea48 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 28 2 0x33e9b0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14bd3c)->(0x33ea0c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x14bd3c)->(0xb7ea96d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 25 2 0x33e940 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 26 2 0x33e940 (nil))
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14ce58)->((nil))
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12fef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x14bd3c)->((null) 1 0x33d2fc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 25 2 0x33d310 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 26 2 0x33d310 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14bd3c)->(0x33d34c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d410 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33d4a0)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:navigate_url Unsupported args (Flags 0x33e9d0:3; TargetFrameName 0x33e9c0:8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 29 2 0x33ea58 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x14bd3c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x33e9b0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x33e9b0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 26 2 0x33ea38 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 29 2 0x33ea48 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 35 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 28 2 0x33e9b0 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14bd3c)->(0x33ea0c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x14bd3c)->(0xb7ea96d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 25 2 0x33e940 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 26 2 0x33e940 (nil))
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14ce40)->((nil))
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12fef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x14bd3c)->((null) 1 0x33d6fc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 25 2 0x33d710 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 26 2 0x33d710 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14bd3c)->(0x33d74c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d810 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x13c7888)->(L"" L"" 0 0x33d848)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 29 2 0x33ea58 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x14bd3c)
fixme:shdocvw:ClientSite_GetContainer (0x14bd3c)->(0x33ea0c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x14bd3c)->(0xb7ea96d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 25 2 0x33e940 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 26 2 0x33e940 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 28 2 0x33e9f8 (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d1-0000-0000-c000-000000000046} 67 0 0x33e21c 0x33e20c)
fixme:hlink:IHlink_fnSetMonikerReference (0x15c9070)->(0 0x15c90a8 (null))
fixme:hlink:IHlink_fnGetStringReference (0x15c9070) -> (1 (nil) 0x33e0f0)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14ce40)->((nil))
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12fef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x14bd3c)->((null) 1 0x33cc00 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 25 2 0x33cc14 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 26 2 0x33cc14 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x14bd3c)->(0x33cc50)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33cd14 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x15c9118)->(L"" L"" 0 0x33cd4c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 29 2 0x33ea58 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x14bd3c)
fixme:shdocvw:ClientSite_GetContainer (0x14bd3c)->(0x33ea0c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x14bd3c)->(0xb7ea96d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 25 2 0x33e940 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 26 2 0x33e940 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x14bd3c)->((null) 28 2 0x33e9f8 (nil))
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x14bca0)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14ce40)->((nil))
fixme:shdocvw:OleObject_Close (0x14bca0)->(1)
wine: Unhandled page fault on write access to 0x8106be2f at address 0x8000c9 (thread 0025), starting debugger...



```

the debugger never opens.

And when I put the command 'ps -aux' in, it comes up with
```
jacob@UBUNTU-VAIO1:~$ ps -aux
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1   2844  1688 ?        Ss   19:21   0:01 /sbin/init
root         2  0.0  0.0      0     0 ?        S<   19:21   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S<   19:21   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S<   19:21   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   19:21   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S<   19:21   0:00 [events/0]
root         7  0.0  0.0      0     0 ?        S<   19:21   0:00 [khelper]
root        41  0.0  0.0      0     0 ?        S<   19:21   0:00 [kblockd/0]
root        44  0.0  0.0      0     0 ?        S<   19:21   0:00 [kacpid]
root        45  0.0  0.0      0     0 ?        S<   19:21   0:00 [kacpi_notify]
root       120  0.0  0.0      0     0 ?        S<   19:21   0:00 [kseriod]
root       154  0.0  0.0      0     0 ?        S    19:21   0:00 [pdflush]
root       155  0.0  0.0      0     0 ?        S    19:21   0:00 [pdflush]
root       156  0.0  0.0      0     0 ?        S<   19:21   0:00 [kswapd0]
root       197  0.0  0.0      0     0 ?        S<   19:21   0:00 [aio/0]
root      1458  0.0  0.0      0     0 ?        S<   19:21   0:00 [ata/0]
root      1464  0.0  0.0      0     0 ?        S<   19:21   0:00 [ata_aux]
root      1467  0.0  0.0      0     0 ?        S<   19:21   0:00 [ksuspend_usbd]
root      1474  0.0  0.0      0     0 ?        S<   19:21   0:00 [khubd]
root      1482  0.0  0.0      0     0 ?        S<   19:21   0:00 [scsi_eh_0]
root      1488  0.0  0.0      0     0 ?        S<   19:21   0:01 [scsi_eh_1]
root      1500  0.0  0.0      0     0 ?        S<   19:21   0:00 [khpsbpkt]
root      2274  0.0  0.0      0     0 ?        S<   19:21   0:00 [knodemgrd_0]
root      2556  0.0  0.0      0     0 ?        S<   19:21   0:00 [kjournald]
root      2761  0.0  0.0   2536  1060 ?        S<s  19:21   0:00 /sbin/udevd --d
root      3050  0.0  0.0      0     0 ?        S<   19:21   0:00 [pccardd]
root      3117  0.0  0.0      0     0 ?        S<   19:21   0:00 [saa7134[0]]
dhcp      4304  0.0  0.0   2440   548 ?        S<s  19:21   0:00 dhclient3 -e IF
root      4417  0.0  0.0   3812   940 ?        Ss   19:21   0:00 /sbin/mount.ntf
root      4732  0.0  0.0   1716   508 tty4     Ss+  19:21   0:00 /sbin/getty 384
root      4733  0.0  0.0   1716   512 tty5     Ss+  19:21   0:00 /sbin/getty 384
root      4737  0.0  0.0   1716   512 tty2     Ss+  19:21   0:00 /sbin/getty 384
root      4738  0.0  0.0   1716   512 tty3     Ss+  19:21   0:00 /sbin/getty 384
root      4740  0.0  0.0   1716   504 tty6     Ss+  19:21   0:00 /sbin/getty 384
root      4908  0.0  0.0   2456  1348 ?        Ss   19:21   0:00 /usr/sbin/acpid
root      4940  0.0  0.0      0     0 ?        S<   19:21   0:00 [kondemand/0]
syslog    5021  0.0  0.0   1936   640 ?        Ss   19:21   0:00 /sbin/syslogd -
root      5078  0.0  0.0   1872   540 ?        S    19:21   0:00 /bin/dd bs 1 if
klog      5080  0.0  0.1   3436  2268 ?        Ss   19:21   0:00 /sbin/klogd -P
103       5102  0.0  0.0   2944  1392 ?        Ss   19:21   0:00 /usr/bin/dbus-d
root      5118  0.0  0.1   4580  1948 ?        Ss   19:21   0:00 /usr/sbin/Netwo
root      5132  0.0  0.0   3388  1164 ?        Ss   19:21   0:00 /usr/sbin/Netwo
root      5145  0.0  0.0   4112  1112 ?        Ss   19:21   0:00 /usr/bin/system
avahi     5174  0.0  0.0   2864  1456 ?        Ss   19:21   0:00 avahi-daemon: r
avahi     5175  0.0  0.0   2760   468 ?        Ss   19:21   0:00 avahi-daemon: c
root      5214  0.0  0.1   5920  2304 ?        Ss   19:21   0:00 /usr/sbin/cupsd
root      5250  0.0  0.0   1772   524 ?        S    19:21   0:00 /bin/sh /usr/bi
mysql     5292  0.0  1.0 127588 16988 ?        Sl   19:21   0:01 /usr/sbin/mysql
root      5294  0.0  0.0   1700   552 ?        S    19:21   0:00 logger -p daemo
ntp       5329  0.0  0.0   4136  1232 ?        S<s  19:21   0:00 /usr/sbin/ntpd
clamav    5494  0.0  0.0   3144  1212 ?        Ss   19:21   0:00 /usr/bin/freshc
root      5554  0.0  0.0   6528  1320 ?        Ss   19:21   0:00 /usr/sbin/nmbd
root      5556  0.0  0.1  10120  2332 ?        Ss   19:21   0:00 /usr/sbin/smbd
nobody    5563  0.0  0.0   2056   708 ?        S    19:21   0:00 /usr/sbin/tinyp
nobody    5564  0.0  0.0   2056   256 ?        S    19:21   0:00 /usr/sbin/tinyp
nobody    5567  0.0  0.0   2056   256 ?        S    19:21   0:00 /usr/sbin/tinyp
nobody    5568  0.0  0.0   2056   256 ?        S    19:21   0:00 /usr/sbin/tinyp
nobody    5569  0.0  0.0   2056   256 ?        S    19:21   0:00 /usr/sbin/tinyp
nobody    5570  0.0  0.0   2056   256 ?        S    19:21   0:00 /usr/sbin/tinyp
nobody    5571  0.0  0.0   2056   256 ?        S    19:21   0:00 /usr/sbin/tinyp
nobody    5572  0.0  0.0   2056   256 ?        S    19:21   0:00 /usr/sbin/tinyp
nobody    5573  0.0  0.0   2056   256 ?        S    19:21   0:00 /usr/sbin/tinyp
nobody    5574  0.0  0.0   2056   256 ?        S    19:21   0:00 /usr/sbin/tinyp
nobody    5575  0.0  0.0   2056   256 ?        S    19:21   0:00 /usr/sbin/tinyp
root      5588  0.0  0.0  10120  1064 ?        S    19:21   0:00 /usr/sbin/smbd
root      5589  0.0  0.0   8084  1300 ?        Ss   19:21   0:00 /usr/sbin/winbi
root      5605  0.0  0.0   8084  1060 ?        S    19:21   0:00 /usr/sbin/winbi
root      5664  0.0  0.0   2020   760 ?        Ss   19:21   0:00 /usr/sbin/dhcdb
107       5683  0.0  0.2   6256  4168 ?        Ss   19:21   0:00 /usr/sbin/hald
root      5686  0.0  0.1   7764  2340 ?        Ssl  19:21   0:00 /usr/sbin/conso
root      5748  0.0  0.0   3236  1084 ?        S    19:21   0:00 hald-runner
107       5768  0.0  0.0   2204   900 ?        S    19:21   0:00 hald-addon-acpi
root      5789  0.0  0.0   3300  1052 ?        S    19:21   0:00 hald-addon-inpu
root      5799  0.0  0.0   3304  1024 ?        S    19:21   0:00 hald-addon-stor
root      5808  0.0  0.0   3304  1040 ?        S    19:21   0:00 hald-addon-stor
root      5811  0.0  0.0   3304  1040 ?        S    19:21   0:00 hald-addon-stor
root      5866  0.0  0.0   3052  1220 ?        Ss   19:21   0:00 /usr/sbin/hcid
root      5875  0.0  0.0      0     0 ?        S<   19:21   0:00 [btaddconn]
root      5876  0.0  0.0      0     0 ?        S<   19:21   0:00 [btdelconn]
root      5887  0.0  0.0   2900  1016 ?        S    19:21   0:00 /usr/lib/blueto
root      5888  0.0  0.0   2964  1212 ?        S    19:21   0:00 /usr/lib/blueto
root      5891  0.0  0.0      0     0 ?        S<   19:21   0:00 [krfcommd]
root      5929  0.0  0.1  14080  1900 ?        Ss   19:21   0:00 /usr/sbin/gdm
root      5930  0.0  0.2  19216  4476 ?        S    19:21   0:00 /usr/sbin/gdm
daemon    5985  0.0  0.0   1984   420 ?        Ss   19:21   0:00 /usr/sbin/atd
root      5999  0.0  0.0   2104   892 ?        Ss   19:21   0:00 /usr/sbin/cron
root      6113  0.0  0.0   1716   512 tty1     Ss+  19:21   0:00 /sbin/getty 384
root      6867  2.2  2.0  40028 32524 tty7     Ss+  19:43   0:41 /usr/bin/X :0 -
jacob     6888  0.1  0.3   7648  4772 ?        S    20:02   0:00 /usr/lib/libgco
jacob     6890  0.0  0.1  14256  2064 ?        S    20:02   0:00 /usr/bin/gnome-
jacob     6891  0.0  0.4  28896  7572 ?        Ssl  20:02   0:00 x-session-manag
jacob     6992  0.0  0.4  22672  6288 ?        Ss   20:02   0:00 /usr/bin/seahor
jacob     7013  0.0  0.0   2700  1088 ?        Ss   20:02   0:00 dbus-daemon --f
jacob     7015  0.0  0.6  39584  9920 ?        Sl   20:02   0:00 gnome-settings-
jacob     7056  0.0  0.3  36660  5876 ?        Sl   20:02   0:00 /usr/bin/pulsea
jacob     7060  0.0  0.1   5676  2204 ?        S    20:02   0:00 /usr/lib/pulsea
jacob     7069  0.3  0.6  18668 10428 ?        S    20:02   0:02 /usr/bin/metaci
jacob     7072  0.6  1.5  52560 24284 ?        S    20:02   0:04 gnome-panel --s
jacob     7074  0.2  1.7  75004 27684 ?        S    20:02   0:01 nautilus --no-d
jacob     7082  0.1  0.1  15232  2556 ?        Ss   20:02   0:01 gnome-screensav
jacob     7084  0.0  0.2  23652  3204 ?        Ssl  20:02   0:00 /usr/lib/bonobo
jacob     7087  0.0  0.1   5380  2112 ?        S    20:02   0:00 /usr/lib/gvfs/g
jacob     7088  0.0  0.3  14660  5768 ?        S    20:02   0:00 bluetooth-apple
jacob     7096  0.0  0.1  29048  1888 ?        Ssl  20:02   0:00 /usr/lib/gvfs//
jacob     7098  0.0  0.8  38104 13104 ?        S    20:02   0:00 update-notifier
jacob     7102  0.0  0.6  54180 10396 ?        Sl   20:02   0:00 /usr/lib/evolut
jacob     7105  0.0  0.3  15664  5832 ?        S    20:02   0:00 tracker-applet
jacob     7108  0.1  0.5  29236  9256 ?        SNl  20:02   0:01 trackerd
jacob     7113  0.0  0.7  24188 12124 ?        S    20:02   0:00 python /usr/sha
jacob     7114  0.0  0.7  48852 11784 ?        S    20:02   0:00 nm-applet --sm-
jacob     7116  0.0  0.4  23100  7440 ?        Ss   20:02   0:00 gnome-power-man
jacob     7117  0.0  0.3  20692  4720 ?        Ss   20:02   0:00 /usr/lib/gnome-
jacob     7122  0.0  0.4  50556  6660 ?        Sl   20:02   0:00 /usr/lib/evolut
jacob     7126  0.0  0.6  38964  9792 ?        Sl   20:02   0:00 /usr/lib/evolut
jacob     7143  0.0  0.1  22048  2636 ?        S    20:02   0:00 /usr/lib/gvfs/g
jacob     7149  0.0  0.5  35172  9276 ?        S    20:02   0:00 /usr/lib/gnome-
jacob     7154  0.0  0.1   5380  2156 ?        S    20:02   0:00 /usr/lib/gvfs/g
jacob     7159  0.0  0.9  56636 14196 ?        Sl   20:02   0:00 /usr/lib/gnome-
jacob     7173  5.7  4.4 177268 69972 ?        Sl   20:02   0:36 /usr/lib/firefo
jacob     7221  3.5  2.1  51788 33824 ?        Sl   20:04   0:18 wish8.5 /usr/bi
jacob     7242  0.0  0.0      0     0 ?        Z    20:04   0:00 [xdg] <defunct>
jacob     7355 14.0  1.2  97320 19860 ?        Sl   20:13   0:00 gnome-terminal
jacob     7357  0.0  0.0   2796   752 ?        S    20:13   0:00 gnome-pty-helpe
jacob     7358  6.0  0.2   5780  3192 pts/0    Ss   20:13   0:00 bash
jacob     7375  0.0  0.0   2644  1004 pts/0    R+   20:13   0:00 ps -aux

```

That help? I don't understand it!

---

### Post by Cloud Wolf on 2009-03-29
P.s. What is Xorg?

---

### Post by James M on 2009-03-29
> **Cloud Wolf said:**
> P.s. What is Xorg?

Xorg is the window system on Linux. Its terrible but its what we have.

You say all apps are affected? 

Open a terminal and type in ```
firefox
```

Paste the output

---

### Post by rhcm123 on 2009-03-29
are you sure your graphics card can handle it? I was using desktop effects on my integrated chip in 8.04, and they ran (barely, albeit), and upon my upgrade to 8.10 xorg started sucking more power so i had to kill the desktop effects.

also, post the results of the following commands
```

sudo cat /var/log/Xorg.0.log | grep -i EE
sudo cat /var/log/Xorg.20.log | grep -i EE

```

---

### Post by James M on 2009-03-29
> **rhcm123 said:**
> are you sure your graphics card can handle it? I was using desktop effects on my integrated chip in 8.04, and they ran (barely, albeit), and upon my upgrade to 8.10 xorg started sucking more power so i had to kill the desktop effects.

also, post the results of the following commands
```

sudo cat /var/log/Xorg.0.log | grep -i EE
sudo cat /var/log/Xorg.20.log | grep -i EE

```

He stated earlier that he tried it without desktop effects.

---

### Post by Cloud Wolf on 2009-03-30
> **James M said:**
> Xorg is the window system on Linux. Its terrible but its what we have.

You say all apps are affected? 

Open a terminal and type in ```
firefox
```

Paste the output

I mentioned the programs I had problems with in the first post.
Firefox works fine.

---

### Post by Cloud Wolf on 2009-03-30
oh, and new thing.
I just downloaded avast! anti virus, and set it up and running last night.
It worked fine, scanned the entire system. it picked up a DAME virus in one of the system folders.dunno what that is.
Now Avast anti virus can be added to the list of programs that wont start up. it has just stopped. like the others mentioned.
"Linux, with a virus?" I hear you ask. "Impossible!"
I don't know, but it's a possibility.

---

### Post by James M on 2009-03-30
> **Cloud Wolf said:**
> oh, and new thing.
I just downloaded avast! anti virus, and set it up and running last night.
It worked fine, scanned the entire system. it picked up a DAME virus in one of the system folders.dunno what that is.
Now Avast anti virus can be added to the list of programs that wont start up. it has just stopped. like the others mentioned.
"Linux, with a virus?" I hear you ask. "Impossible!"
I don't know, but it's a possibility.

Very possible. Write down the directory to that file, boot into a live cd and remove that file from the harddrive WITH the live cd with the command as root (which you should be in a live CD):

rm /path/to/FILENAME

---

### Post by rhcm123 on 2009-03-30
> **Cloud Wolf said:**
> oh, and new thing.
I just downloaded avast! anti virus, and set it up and running last night.
It worked fine, scanned the entire system. it picked up a DAME virus in one of the system folders.dunno what that is.
Now Avast anti virus can be added to the list of programs that wont start up. it has just stopped. like the others mentioned.
"Linux, with a virus?" I hear you ask. "Impossible!"
I don't know, but it's a possibility.

did avast break it?

Also, the commands i asked for, plox.

---

### Post by llamakc on 2009-03-30
> **James M said:**
> Very possible. Write down the directory to that file, boot into a live cd and remove that file from the live cd with 

sudo rm -r /path/to/file

There is ZERO reason to use the recursive flag to remove a single file. That is bad advice.

---

### Post by kevmitch on 2009-03-30
I would also hesitate to remove files willy nilly just because some program tells you they're a "virus". What file is it? It sounds like [DAME]("http://wiw.org/~meta/vsum/view.php?vir=364") itself is not a virus, but an encryption algorithm used by viruses.

---

### Post by bodhi.zazen on 2009-03-30
> **James M said:**
> Very possible. Write down the directory to that file, boot into a live cd and remove that file from the live cd with 

sudo rm -r /path/to/file

I am sorry, but that is just bad advice.

First, there are viruses on Linux, they are very very rare and it is much more likely that this is a false positive.

Second, that advice will 'remove" a file on the CD, but accessing the hard drive is a bit more complex and involves mounting the partition first.

Third, please take are with the -r flag, more so since you really do not know what it is you are removing or why.

See also : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by Cloud Wolf on 2009-04-01
I don't really quite know what you are on about there :S

It also picked up a load of other stuff, but it closed before i could read any of it. :(

---

### Post by rhcm123 on 2009-04-02
> **Cloud Wolf said:**
> I don't really quite know what you are on about there :S

It also picked up a load of other stuff, but it closed before i could read any of it. :(

This is a command line app? Run this, and be sure to change "user" to your username:
```
the command > /home/user/Desktop/results.txt
```

open up results.txt to see the output

---

### Post by Cloud Wolf on 2009-04-05
nope. its all run through a GUI.
No command lines. :D

I decided to try AVG instead. Installed it easily, updated servers, scanned, and everything was clean. except for the fact it couldn't scan certain files (permission denied).

So I don't think its a virus after all.
And I ended up completely deleting the file that was meant to contain DAME. I couldn't quarantine it or anything, it wouldn't allow me, not even as root.

Any ideas of what is causing this problem then?

---

### Post by Peter09 on 2009-04-05
The fact that you had an unhandled page fault in wine could mean that its an H/W problem. Might be worth checking you hard disk and your memory.

---

### Post by Cloud Wolf on 2009-04-05
Err....right.
Now if you could translate that into me speak that would be great.
Basically, guide me through step by step?

---

### Post by EnglishSparrow on 2009-04-05
Do you get i/o errors?

---

### Post by Cloud Wolf on 2009-04-06
what are i/o errors?
if you mean error messages, no, I don't.

---

### Post by Peter09 on 2009-04-06
Force a disk check

```
sudo touch /forcefsck
```

[http://onlyubuntu.blogspot.com/2009/03/how-to-repair-corrupted-filesystem-in.html](http://onlyubuntu.blogspot.com/2009/03/how-to-repair-corrupted-filesystem-in.html)

---

### Post by Cloud Wolf on 2009-04-06
i do that....then it does nothing.
what now?

---

### Post by 3rdalbum on 2009-04-06
If Wine encounters a part of a Windows program that it doesn't understand, then Wine crashes and the window disappears. Wine may or may not report a page fault; this does not indicate bad RAM or a bad hard disk.

Virus programs tend to report a lot of false positives. When I used to have Windows, my father had installed Dreamweaver onto the Windows partition. One of the Javascripts used in Dreamweaver was reported to be a virus by one of those anti-virus programs; no, nothing had been infected, this was just an innocent Javascript that is part of Dreamweaver's "Actions" functionality.

---

### Post by Cloud Wolf on 2009-04-08
bump

---

