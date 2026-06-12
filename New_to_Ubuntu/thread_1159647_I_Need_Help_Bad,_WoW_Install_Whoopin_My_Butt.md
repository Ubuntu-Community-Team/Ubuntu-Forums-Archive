---
title: "I Need Help Bad, WoW Install Whoopin My Butt"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by Jishen on 2009-05-14
So I Need Someone To Go Through And Explain How To Install WoW (DVD) On Ubuntu Jaunty As If They Were Speaking To An 8 Year Old. Ive Tried  Everything And Im Getting Frustrated. Ive Mounted The Disk Unhide And Copied It To The HD. When I Try To Install Via The Install.exe File It Tells Me It Cant Find The File, And When I Try To Install As They Told Me To On The WoW Community Page Using The Terminal It Gives Me This

chad@chad-laptop:~$ cd /home/chad/.wine/drive_c/wowinstallfiles/
[email]chad@chad-laptop:~/.wine[/email]/drive_c/wowinstallfiles$ wine Install.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:service:EnumServicesStatusW 0x127c20 type=30 state=3 (nil) 0 0x87e798 0x87e7a4 0x87e7a0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x87e5a8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x127a50,(nil)): stub
wine: could not load L"C:\\windows\\system32\\Install.exe": Module not found

Pleeeease Help.

---

### Post by anewguy on 2009-05-14
Did you also post this back in the WoW and games forums here?  That would probably be your best bet for getting help.

Dave :)

---

### Post by Jishen on 2009-05-14
thanks anewguy

---

### Post by AndThenWhat on 2009-05-14
Looks like something is missing from your /.wine/drive_c/windows/system32 folder called "Install.exe"

---

