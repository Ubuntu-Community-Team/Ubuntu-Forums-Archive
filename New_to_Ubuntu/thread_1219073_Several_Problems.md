---
title: "Several Problems"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by Dr.iCe on 2009-07-21
1st; well i installed Wine with DX and alot of other plugins and stuff.. i dl'ed SteamInstall.msi using Terminal but when i try to do:
```
wine start steaminstall.msi
```
what happens is that Wine pops up (and a msiexec console) but after like 2 seconds wine just shutsdown :S
i havent experienced any problems using IE or Notepad or anything else on Wine..

i dont know if this helps but i past it in anyways:
```
drice@drice-laptop:~$ wine start steaminstall.msi
fixme:exec:SHELL_execute flags ignored: 0x00000500
drice@drice-laptop:~$ fixme:advapi:SetEntriesInAclA 1 0x33f79c (nil) 0x33f7d4
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f788 (nil) 0x33f7d0
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetEntriesInAclA 1 0x33f7a8 (nil) 0x33f7f0
fixme:advapi:SetSecurityInfo stub
fixme:sfc:SfcIsKeyProtected ((nil), (null)) stub
fixme:advapi:RegisterEventSourceA ((null),"MsiInstaller"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MsiInstaller"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x33f558,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x1307d0,(nil)): stub
err:eventlog:ReportEventW L"=====================================================\r\nException code: C0000005 ACCESS_VIOLATION\r\nFunction: 0x0\r\n=====================================================\r\n\r\nRegisters:\r\nEAX:00000000  EBX:004BEF2D  ECX:0033F594  EDX:00000031  ESI:0033F71C  EDI:00000000\r\nCS:EIP:0073:00000000 "...
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dba29e8, overlapped 0x7dba29cc): stub

```


2nd; when i try to watch Youtube videos it says that my Flash player might be outdated and all that so yeah i did an update but it still wont work :S (tried several times)..

3rd; so well i installed VLC to watch my videos, listen to music etc. etc. but when i try to open a DVD using VLC nothing happens (and i mean NOTHING)

hope to get some fast and good answers on fixing this, all of them are very important things i HAVE TO fix if not i need to move back to Windows (i know people have worked stuff like that out and i DONT want to go back to Vista or Win7 crap)

---

### Post by txapelgorri on 2009-07-21
Hi:

New to Ubuntu?, patience please, don't threat us switching to Windows again ;)

1) Wine works fine. Some programs like the one you have mention are a little hard to get them work properly. Some years ago, I get it working for playing Half Life, but it took me some time configuring it, so don't be tough with wine. My recomendation is to take a look at this: [http://appdb.winehq.org/](http://appdb.winehq.org/) there you can find more info about specific apps that run (or not) under wine. The one that you have mentioned: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1554)

2) Try to install flashplugin-nonfree package, via Package Manager. Maybe Youtube needs Adobe's plugin, and any other plugin doesn't work fine.

3) To try to debug the VLC issue...when you insert your disc, does it appear in the Desktop?, if so, try opening it with Totem movie player and tell us what happens.

Cheers, Ibon.

---

### Post by moody_mark on 2009-07-21
Hi, first thing id try is rather than try to run things via wine try using a linux alternative (i.e. like you are trying VLC)

The first thing I always do after installing ubuntu on any machine is to go into "Applications --> Add / Remove" and then search for "restricted" make sure your drop down under "show:" is selected the "All Available applications". Select the "ubuntu restricted extras" and then install that.

Make sure you have installed those extra packages and then report back to let us know how you get on

---

### Post by Dr.iCe on 2009-07-21
i cant find ANY solution to my steam problem (almost seems like i am the only one ever having it, i think it may be a problem with msiexec or something)... :,(

and for the other suggestions; ill take a look as soon as i am done downloading the packages i am currently doing :P

---

### Post by jeppewinther on 2009-07-21
For what it's worth, the Steam application is buggy, but it does run, and the games work more or less fine. And since it is one of those highprofile applications, there are a ton of Howtos out there to get it in working order, that link provided above would be a good starting point.

---

### Post by Dr.iCe on 2009-07-21
> **moody_mark said:**
> Hi, first thing id try is rather than try to run things via wine try using a linux alternative (i.e. like you are trying VLC)

The first thing I always do after installing ubuntu on any machine is to go into "Applications --> Add / Remove" and then search for "restricted" make sure your drop down under "show:" is selected the "All Available applications". Select the "ubuntu restricted extras" and then install that.

Make sure you have installed those extra packages and then report back to let us know how you get on
i installed The linux VLC and yes i try to find a linux alternative (only thing i will run on wine is Steam), i have a IRC Linux client, i got an Linux SVN etc. ;D

---

### Post by Dr.iCe on 2009-07-21
none of the things for Steam you have told me works :S
please look at my describition of the problem...

---

### Post by jeppewinther on 2009-07-21
[https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam)

---

### Post by Dr.iCe on 2009-07-21
> **jeppewinther said:**
> [https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/InstallingSteam)
1st, that didnt help me anything at all, no chance that would help me either..

but well i dropped the .msi and got the old .exe file.. and that went way smoother and its installed problem now is that it wont update and after some time gives me an error that it cant fine steam.dll

---

### Post by Dr.iCe on 2009-07-21
just me bumping for help

---

### Post by devildoc5 on 2009-07-21
I don't use Wine myself but just out of curiosity does it have permissions to access the modem/ethernet/wireless to be able to check for the update you are looking for?

---

