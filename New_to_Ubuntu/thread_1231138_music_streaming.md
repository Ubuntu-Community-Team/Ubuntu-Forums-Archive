---
title: "music streaming"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by coller_girl on 2009-08-04
how to stream music between a sansung v25 running windows xp, eeepc 701 4g running windows xp, and using my ubuntu 9.04 desktop machine as a media server, i want to be able too have my collection of ogg and mp3's play remotly from anywhere in the world my desktop machine is on a cat5 connection with dinamic ip from virgin media. 

the router is a buffalo model number i forget
my desktop doesnt have much ram 


im a noob sorry cant find anything relivent to my situation, i can provide more but not sure what info is needed other than connection speeds 2mbps though 11mbps as i'm upgrading my connection speed they are reliable.
i have no experiance of ssh

---

### Post by credobyte on 2009-08-04
[http://www.n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/](http://www.n00tz.net/2008/07/vlc-media-server-ubuntu-hardy/) - this should be enough for a while :)

---

### Post by INTENSETUX on 2009-08-04
Or try here , [http://www.simplifymedia.com/](http://www.simplifymedia.com/) , works on all platforms and a breeze to set up.

---

### Post by MrWES on 2009-08-04
> **coller_girl said:**
> how to stream music between a sansung v25 running windows xp, eeepc 701 4g running windows xp, and using my ubuntu 9.04 desktop machine as a media server, i want to be able too have my collection of ogg and mp3's play remotly from anywhere in the world my desktop machine is on a cat5 connection with dinamic ip from virgin media. 

the router is a buffalo model number i forget
my desktop doesnt have much ram 


im a noob sorry cant find anything relivent to my situation, i can provide more but not sure what info is needed other than connection speeds 2mbps though 11mbps as i'm upgrading my connection speed they are reliable.
i have no experiance of ssh

I'd look into mt-daapd shares (aka Firefly Media Server). It was originally developed by Apple, Inc. and is compatible with iTunes for Windows, Rhthymbox and Aramok for Ubuntu. It's in the repositories. I believe it runs on port 3689, so if you forwarded that port from your router to the mt-daapd server you should be able to connect over the internet. I run an mt-daapd on my home server, but I haven't tried connecting from the other side yet. I've attached a screenshot from Rhthymbox showing MyJukeBox media server. Neat thing is, my wife and also pick up the server on her Windows XP machine running iTunes.

Bill

```
sudo apt-get install mt-daapd
```
[http://www.fireflymediaserver.org/]("http://www.fireflymediaserver.org/")

---

### Post by YesSir on 2009-08-04
I love [***Subsonic***]("http://subsonic.sourceforge.net/"). Online demo [***here***]("http://gosubsonic.com/index.view").

---

### Post by coller_girl on 2009-08-05
> **INTENSETUX said:**
> Or try here , [http://www.simplifymedia.com/](http://www.simplifymedia.com/) , works on all platforms and a breeze to set up.


have been trying to set this up... its not working with me heres info on my eee






Application Build Number: 1406 (built 07-13-2009)
Application folder: C:/Program Files/Simplify Media (writable)
Disk availability:
 C: - Free space: 592,900,096 bytes
 E: - Free space: 1,013,563,392 bytes
iTunes Library Path: 
WMP Version: 11.0.5721.5260
Screen Name: thehumanthings
Host name: cutiepie
Location Name: eeepc_laptop
User Name: Sara 
Windows (32-bits) OS Version: Major=5 Minor=1 Build=2600 Platform=2, Version=Service Pack 3
Processor(s): 1 x Intel Architecture (level 6) CPU Model 13, Stepping 8
Processor Features: MMX SSE SSE2 
  Shared Folder(s):
     C:\Documents and Settings\Sara\My Documents\My Music
Network Scan Status: Success
Network Type: 0x1041 (hairpin = false)
Network Local: 192.168.11.3
NIC Addr: 00:15:AF:B2:9A:6E


Windows IP Configuration



        Host Name . . . . . . . . . . . . : cutiepie

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Media State . . . . . . . . . . . : Media disconnected

        Description . . . . . . . . . . . : Atheros L2 Fast Ethernet 10/100 Base-T Controller

        Physical Address. . . . . . . . . : 00-22-15-09-00-2F



Ethernet adapter Wireless Network Connection:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Atheros AR5007EG Wireless Network Adapter

        Physical Address. . . . . . . . . :

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : censored

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : ip censered

        DHCP Server . . . . . . . . . . . : ip censored in post

        DNS Servers . . . . . . . . . . . : censored

        Lease Obtained. . . . . . . . . . : 05 August 2009 12:57:07

        Lease Expires . . . . . . . . . . : 07 August 2009 12:57:07


PID    PPID    Thr    Pri    Name    Path
0    0    1    0    [System Process]    
4    0    65    8    System    
352    1948    2    8    AsTray.exe    C:\Program Files\Asus\EeePC ACPI\AsTray.exe
360    1948    3    8    AsAcpiSvr.exe    C:\Program Files\Asus\EeePC ACPI\AsAcpiSvr.exe
368    1948    4    8    RTHDCPL.exe    C:\WINDOWS\RTHDCPL.EXE
420    4    3    11    smss.exe    
440    1948    2    8    AsTray.exe    C:\WINDOWS\system32\AsTray.exe
444    1948    2    8    hkcmd.exe    C:\WINDOWS\system32\hkcmd.exe
468    1948    1    8    Belkinwcui.exe    C:\Program Files\Belkin\F5D7050v3\Belkinwcui.exe
472    1948    1    8    ctfmon.exe    C:\WINDOWS\system32\ctfmon.exe
484    420    12    13    csrss.exe    
508    420    18    13    winlogon.exe    
528    1948    20    8    msnmsgr.exe    C:\Program Files\Windows Live\Messenger\msnmsgr.exe
552    508    15    9    services.exe    
564    508    24    9    lsass.exe    
656    936    3    8    igfxsrvc.exe    C:\WINDOWS\system32\igfxsrvc.exe
684    1948    43    8    SimplifyMedia.exe    C:\Program Files\Simplify Media\SimplifyMedia.exe
936    552    15    8    svchost.exe    
996    552    8    8    svchost.exe    
1032    552    56    8    svchost.exe    
1104    552    6    8    svchost.exe    
1140    552    12    8    svchost.exe    
1192    1948    3    8    FirefoxPortable.exe    C:\Program Files\Apps\PortableApps\FirefoxPortable\FirefoxPortable.exe
1244    936    3    8    igfxext.exe    C:\WINDOWS\system32\igfxext.exe
1252    1948    13    8    pidgin.exe    C:\Program Files\Pidgin\pidgin.exe
1392    552    11    8    spoolsv.exe    
1464    552    4    8    svchost.exe    
1508    552    7    8    mDNSResponder.exe    
1572    552    6    8    svchost.exe    
1760    1336    1    8    PortableAppsPlatform.exe    C:\Program Files\Apps\PortableApps\PortableApps.com\PortableAppsPlatform.exe
1840    1192    8    8    firefox.exe    C:\Program Files\Apps\PortableApps\FirefoxPortable\App\firefox\firefox.exe
1948    1856    11    8    explorer.exe    C:\WINDOWS\Explorer.EXE
2068    552    5    8    alg.exe    
2364    552    8    8    svchost.exe

---

