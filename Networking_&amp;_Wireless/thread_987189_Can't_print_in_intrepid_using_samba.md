---
title: "Can't print in intrepid using samba"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by Virtual DarKness on 2008-11-19
Searched a lot in the forum and google but was not able to find a solution.. I've upgraded from ubuntu 8.04 to 8.10 (32bit) and everything works well but priting. 

I have a windows 98 pc with a shared printer on it and it always worked just fine from ubuntu but now is not longer working..

here are the errors from the log (/var/log/cups/error_log):

> E [19/Nov/2008:16:34:54 +0100] [Job 2] Connection failed: NT_STATUS_ACCESS_DENIED
E [19/Nov/2008:16:35:12 +0100] [Job 2] Connection failed: NT_STATUS_ACCESS_DENIED
E [19/Nov/2008:16:35:29 +0100] [Job 2] Connection failed: NT_STATUS_ACCESS_DENIED
E [19/Nov/2008:16:35:29 +0100] [Job 2] Unable to connect to CIFS host, will retry in 60 seconds...

I've also tried to remove cups + samba purging the config file so in theory my samba + cups config should be more or less as in a fresh installed intrepid.. (even job number has been reset as you can see ;))

After removing all the packages I installed "system-config-printer-gnome" and all its dependences but still getting the same errors reported above.

Thanks in advice for any help / tip.

Giovanni.

---

### Post by Virtual DarKness on 2008-11-20
Have found more information in order to better "debug" this problem..

I've done:
```
$ DEVICE_URI="smb://W98WG/P150/HP"
$ export DEVICE_URI
$ echo something | smbspool 99 me test 1 ""

```

and as output I've got:
> timeout connecting to 208.69.34.132:445
timeout connecting to 208.69.34.132:139
cli_start_connection: failed to connect to P150<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
ERROR: Connection failed: NT_STATUS_ACCESS_DENIED
ERROR: Unable to connect to CIFS host, will retry in 60 seconds...

Don't know where the 208.69.34.132 ip came from cause my win98 pc has 192.168.1.7 as ip (not dhcp) and it also has no firewall.

so it seems that it fails to resolve the correct ip.. I've also tried to change the workgroup name and the device_uri string but nothing changes :(

let me know if you have any idea about this, thanks.

bye,
Giovanni.

---

### Post by pqrs295 on 2008-11-20
Up to 70% Off, Hurry Sale Ends SoonAustralian Real Sheepskin Boots**[color=#c76200]Uggretailsale.com[/color]**Authentic ugg boots, crafted from 100% natural Australian merino sheepskin leather.**[color=#c76200]Uggretailsale.com[/color]****[color=#c76200][/color]**100% Genuine AustralianUgg BootsPay by Paypal, Non-tax, Hurry!**[color=#c76200]Uggretailsale.com[/color]**

---

### Post by superprash2003 on 2008-11-20
try connecting via ip instead of hostname.. also enter the full path of the printer like smb://x.x.x.x/printername .. are you able to access the windows 98 machine's shared files?

---

### Post by Virtual DarKness on 2008-11-21
now it works; I think it was something due to the printer / the windows configuration cause I didn't changed anything related to samba or cups..

I've tried printing from another computer with windows xp and then it installed some other drivers on that machine but it returned error that the cartridge was empty but it was not.. in fact after hitting "reset" on the printer it started printing the test page..

same thing then from linux except that I got some strange symbols instead of the image.. then after setting the printer to grayscale mode it worked :confused:

the strange thing is that when trying to print form linux in the past days, before I tested it with the other windows pc, I got no error both from windows nor from the printer ..

anyway, thanks for your help.

bye,
Giovanni.

---

### Post by mahasmb on 2008-12-22
I'm having this same problem, and I don't understand how you solved it. Please help.

---

### Post by Virtual DarKness on 2008-12-23
> **mahasmb said:**
> I'm having this same problem, and I don't understand how you solved it. Please help.


have you tried to print from a windows pc to check that all the cartridges are not empty or other similar problems that could prevent it from printing? Cause it seems to me that if an error happens it is just not shown through samba.. 

Also have you tried to do this from terminal:
```
$ DEVICE_URI="smb://<work group>/<pc>/<printer>"
$ export DEVICE_URI
$ echo something | smbspool 99 me test 1 ""
```

eventually post here the output to check if the problem is the same or there is something else..

bye,
Giovanni.

---

### Post by fewjr on 2008-12-23
I have a similar problem. My Wife's Vista computer has the shared printer connected to it. Her computer and my Ubuntu 8.10 computer are connected to the router via ethernet. I can print a test page fine, but I cannot print from any other applications, (pdf docs, webpage, etc.). 
Here is error_log:
[CODE]D [23/Dec/2008:12:35:52 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:35:52 -0500] Report: clients=1
D [23/Dec/2008:12:35:52 -0500] Report: jobs=2
D [23/Dec/2008:12:35:52 -0500] Report: jobs-active=0
D [23/Dec/2008:12:35:52 -0500] Report: printers=1
D [23/Dec/2008:12:35:52 -0500] Report: printers-implicit=0
D [23/Dec/2008:12:35:52 -0500] Report: stringpool-string-count=325
D [23/Dec/2008:12:35:52 -0500] Report: stringpool-alloc-bytes=9472
D [23/Dec/2008:12:35:52 -0500] Report: stringpool-total-bytes=6856
D [23/Dec/2008:12:35:52 -0500] cupsdCloseClient: 8
D [23/Dec/2008:12:35:52 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:35:52 -0500] cupsdReadClient: 8 POST / HTTP/1.1
D [23/Dec/2008:12:35:52 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:35:52 -0500] CUPS-Get-Printers
D [23/Dec/2008:12:35:52 -0500] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [23/Dec/2008:12:35:52 -0500] cupsdAcceptClient: 9 from localhost (Domain)
D [23/Dec/2008:12:35:52 -0500] cupsdCloseClient: 8
D [23/Dec/2008:12:35:52 -0500] cupsdReadClient: 9 GET /printers/Photosmart-c4200.ppd HTTP/1.1
D [23/Dec/2008:12:35:52 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:35:53 -0500] cupsdCloseClient: 9
D [23/Dec/2008:12:35:55 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:35:55 -0500] cupsdReadClient: 8 POST /printers/Photosmart-c4200 HTTP/1.1
D [23/Dec/2008:12:35:55 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:35:55 -0500] Print-Job ipp://localhost:631/printers/Photosmart-c4200
D [23/Dec/2008:12:35:55 -0500] [Job ???] Auto-typing file...
I [23/Dec/2008:12:35:55 -0500] [Job ???] Request file type is application/pdf.
E [23/Dec/2008:12:35:55 -0500] Print-Job: Unauthorized
D [23/Dec/2008:12:35:55 -0500] cupsdSendError: 8 code=401 (Unauthorized)
D [23/Dec/2008:12:35:55 -0500] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"
D [23/Dec/2008:12:35:55 -0500] cupsdCloseClient: 8
D [23/Dec/2008:12:36:21 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:36:21 -0500] cupsdAcceptClient: 9 from localhost (Domain)
D [23/Dec/2008:12:36:21 -0500] cupsdCloseClient: 8
D [23/Dec/2008:12:36:21 -0500] cupsdReadClient: 9 POST / HTTP/1.1
D [23/Dec/2008:12:36:21 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:36:21 -0500] CUPS-Get-Printers
D [23/Dec/2008:12:36:21 -0500] cupsdProcessIPPRequest: 9 status_code=0 (successful-ok)
D [23/Dec/2008:12:36:21 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:36:21 -0500] cupsdCloseClient: 9
D [23/Dec/2008:12:36:21 -0500] cupsdReadClient: 8 GET /printers/Photosmart-c4200.ppd HTTP/1.1
D [23/Dec/2008:12:36:21 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:36:22 -0500] cupsdCloseClient: 8
D [23/Dec/2008:12:36:23 -0500] cupsdAcceptClient: 8 from localhost (Domain)
D [23/Dec/2008:12:36:23 -0500] cupsdReadClient: 8 POST /printers/Photosmart-c4200 HTTP/1.1
D [23/Dec/2008:12:36:23 -0500] cupsdAuthorize: No authentication data provided.
D [23/Dec/2008:12:36:23 -0500] Print-Job ipp://localhost:631/printers/Photosmart-c4200
D [23/Dec/2008:12:36:23 -0500] [Job ???] Auto-typing file...
I [23/Dec/2008:12:36:23 -0500] [Job ???] Request file type is application/pdf.
E [23/Dec/2008:12:36:23 -0500] Print-Job: Unauthorized
D [23/Dec/2008:12:36:23 -0500] cupsdSendError: 8 code=401 (Unauthorized)
D [23/Dec/2008:12:36:23 -0500] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"
D [23/Dec/2008:12:36:24 -0500] cupsdCloseClient: 8[CODE]

Does anyone know what to make of this? I'm not sure.

Best Regards
fewjr

---

### Post by mahasmb on 2008-12-23
Yes, I can print from the Windows XP host computer just fine.

And here's my output:

```

maha@mahmaha@maha-desktop:~$ DEVICE_URI="smb://MSHOME/KURO/BrotherD"
maha@maha-desktop:~$ export DEVICE_URI
maha@maha-desktop:~$ echo something | smbspool 99 me test 1 ""
timeout connecting to 192.168.2.10:445
timeout connecting to 192.168.2.10:139
cli_start_connection: failed to connect to KURO<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
ERROR: Connection failed: NT_STATUS_ACCESS_DENIED
timeout connecting to 192.168.2.10:445
timeout connecting to 192.168.2.10:139
cli_start_connection: failed to connect to KURO<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
ERROR: Connection failed: NT_STATUS_ACCESS_DENIED
timeout connecting to 192.168.2.10:445
timeout connecting to 192.168.2.10:139
cli_start_connection: failed to connect to KURO<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
ERROR: Connection failed: NT_STATUS_ACCESS_DENIED
ERROR: Unable to connect to CIFS host, will retry in 60 seconds...
timeout connecting to 192.168.2.10:445
timeout connecting to 192.168.2.10:139
cli_start_connection: failed to connect to KURO<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
ERROR: Connection failed: NT_STATUS_ACCESS_DENIED
timeout connecting to 192.168.2.10:445
timeout connecting to 192.168.2.10:139
cli_start_connection: failed to connect to KURO<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
ERROR: Connection failed: NT_STATUS_ACCESS_DENIED
timeout connecting to 192.168.2.10:445
timeout connecting to 192.168.2.10:139
cli_start_connection: failed to connect to KURO<20> (0.0.0.0). Error NT_STATUS_ACCESS_DENIED
ERROR: Connection failed: NT_STATUS_ACCESS_DENIED
ERROR: Unable to connect to CIFS host, will retry in 60 seconds...


```

---

### Post by Virtual DarKness on 2008-12-26
> **mahasmb said:**
> Yes, I can print from the Windows XP host computer just fine.


I've tried it again and I'm getting the same error again now.. :confused::(

so it is no longer working for me too.. let me know if you find a solution.

bye,
Giovanni.

---

### Post by Virtual DarKness on 2008-12-27
@mahasmb & fewjr: do you have a fresh ubuntu intrepid install or did you dist upgrade?

I went from 8.04..

bye,
Giovanni.

---

### Post by fewjr on 2008-12-27
Virtual Darkness, 
I did not upgrade from 8.04.1. I installed fresh using an Intrepid AlternateCD. There was some kind of bug with my hardware that wouldn't allow me to install from the Livecd. I still can not print to my network printer. I tried the cups web interface, hplip, etc. I can only print a test page. I still need assistance. I don't seem to see anything else to try to fix it myself. Do you have any ideas? I was wondering if it would be a good idea to uninstall cups and hplip and start over. I am not sure what to try...I'm standing by. :)

fewjr

---

### Post by mahasmb on 2008-12-28
I did a fresh install from the CD I received from ShipIt from Canonical.

---

### Post by Virtual DarKness on 2008-12-30
> **fewjr said:**
> Do you have any ideas? I was wondering if it would be a good idea to uninstall cups and hplip and start over. I am not sure what to try...I'm standing by. :)

I tried to uninstall cups removing anlso the config files and reinstall it but nothing changed.. maybe it is a problem with samba or maybe it has something to do with apparmor .. anyway not sure the problem you have is the same I have cause I can't even print the test page.. As an alternative try to use the gimp-print drivers and play a bit with print settings (as I told you I once managed to make it works but now it doesn't works again..)

let me know..

bye,
Giovanni.

---

### Post by mahasmb on 2009-01-02
No luck yet.

---

### Post by nemilar on 2009-01-02
Are you able to print as root?

try

```
sudo gedit
```

and try printing something...


If that works... the best I can tell you at the moment is that I had a similar problem, took me a few weeks, and found a line to comment in one of the /etc/cups/ configuration files.   

If the above works for you, I'll dig deeper and see if I can come up with my old solution...

---

### Post by fewjr on 2009-01-02
nemilar,
I could not print from gedit myself. I do not remember if I opened gedit with gksudo or not. I don't think I did. There is a screenshot of it here:
[http://ubuntuforums.org/showthread.php?t=1018914&page=2](http://ubuntuforums.org/showthread.php?t=1018914&page=2)
I will try to sudo tomorrow when I get off work and post results. I can still only print a test page. This is really annoying. Hope there is a solution out there somewhere.

Thanks,
fewjr

---

### Post by fewjr on 2009-01-03
Nope....doesn't work. Heres a screenshot:
[http://i260.photobucket.com/albums/ii20/fewjr/screenshots/Screenshot-again.png](http://i260.photobucket.com/albums/ii20/fewjr/screenshots/Screenshot-again.png)

---

### Post by Virtual DarKness on 2009-01-06
Today I saw some updates to samba but was related to security issues.. anyway didn't tried it again yet..

bye,
Giovanni.

---

### Post by mahasmb on 2009-01-21
Still no luck with this at all...

---

### Post by kroylar on 2009-02-27
Apparently there is a problem in the samba name resolution.  When I try to print using smb://WORKGROUP/192.168.1.101/printer it works.  But when I use the windows name smb://WORKGROUP/BUBBA/printer it doesnt work.

I guess that means that it is a problem with the winbind daemon.  Maybe someone should file a bug report ;)

---

### Post by mahasmb on 2009-03-08
I still haven't been able to fix this. It's been months.

I got an error log:

```
D [08/Mar/2009:20:26:30 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:26:30 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:26:30 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:26:30 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:26:30 -0400] Get-Jobs ipp://localhost/jobs/
D [08/Mar/2009:20:26:30 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:30 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:26:30 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:26:30 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:26:30 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:26:30 -0400] Create-Printer-Subscription /
D [08/Mar/2009:20:26:30 -0400] cupsdCreateSubscription(con=0xb87c3e98(7), uri="/")
D [08/Mar/2009:20:26:30 -0400] pullmethod="ippget"
D [08/Mar/2009:20:26:30 -0400] notify-lease-duration=86400
D [08/Mar/2009:20:26:30 -0400] notify-time-interval=0
D [08/Mar/2009:20:26:30 -0400] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")
D [08/Mar/2009:20:26:30 -0400] Added subscription 54 for server
I [08/Mar/2009:20:26:30 -0400] Saving subscriptions.conf...
D [08/Mar/2009:20:26:30 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:30 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:26:31 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:26:31 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:26:31 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:26:31 -0400] Get-Notifications /
D [08/Mar/2009:20:26:31 -0400] cupsdIsAuthorized: requesting-user-name="maha"
D [08/Mar/2009:20:26:31 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:31 -0400] cupsdCloseClient: 7
E [08/Mar/2009:20:26:34 -0400] [Job 63] Connection failed: NT_STATUS_ACCESS_DENIED
E [08/Mar/2009:20:26:34 -0400] [Job 63] Unable to connect to CIFS host, will retry in 60 seconds...
I [08/Mar/2009:20:26:34 -0400] Saving subscriptions.conf...
D [08/Mar/2009:20:26:34 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:26:34 -0400] Get-Jobs ipp://localhost/jobs/
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:26:34 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:26:34 -0400] Get-Notifications /
D [08/Mar/2009:20:26:34 -0400] cupsdIsAuthorized: requesting-user-name="maha"
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:26:34 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:26:34 -0400] Get-Notifications /
D [08/Mar/2009:20:26:34 -0400] cupsdIsAuthorized: requesting-user-name="maha"
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdAcceptClient: 8 from localhost (Domain)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 8 POST / HTTP/1.1
E [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: Local authentication certificate not found!
D [08/Mar/2009:20:26:34 -0400] CUPS-Get-Printers
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 8 POST / HTTP/1.1
E [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: Local authentication certificate not found!
D [08/Mar/2009:20:26:34 -0400] CUPS-Get-Classes
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 8 GET /admin/conf/printers.conf HTTP/1.1
E [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: Local authentication certificate not found!
D [08/Mar/2009:20:26:34 -0400] cupsdIsAuthorized: username=""
D [08/Mar/2009:20:26:34 -0400] cupsdSendError: 8 code=401 (Unauthorized)
D [08/Mar/2009:20:26:34 -0400] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"
D [08/Mar/2009:20:26:34 -0400] cupsdCloseClient: 8
D [08/Mar/2009:20:26:34 -0400] cupsdAcceptClient: 8 from localhost (Domain)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 8 GET /admin/conf/printers.conf HTTP/1.1
D [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: Authorized as root using Local
D [08/Mar/2009:20:26:34 -0400] cupsdIsAuthorized: username="root"
D [08/Mar/2009:20:26:34 -0400] cupsdAcceptClient: 11 from localhost (Domain)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:26:34 -0400] Get-Notifications /
D [08/Mar/2009:20:26:34 -0400] cupsdIsAuthorized: requesting-user-name="maha"
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 8 POST / HTTP/1.1
D [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: Authorized as root using Local
D [08/Mar/2009:20:26:34 -0400] CUPS-Get-Default
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 12 POST / HTTP/1.1
E [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: Local authentication certificate not found!
D [08/Mar/2009:20:26:34 -0400] CUPS-Get-Printers
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 12 POST / HTTP/1.1
E [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: Local authentication certificate not found!
D [08/Mar/2009:20:26:34 -0400] CUPS-Get-Classes
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 12 GET /admin/conf/printers.conf HTTP/1.1
E [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: Local authentication certificate not found!
D [08/Mar/2009:20:26:34 -0400] cupsdIsAuthorized: username=""
D [08/Mar/2009:20:26:34 -0400] cupsdSendError: 12 code=401 (Unauthorized)
D [08/Mar/2009:20:26:34 -0400] cupsdSendHeader: WWW-Authenticate: Basic realm="CUPS"
D [08/Mar/2009:20:26:34 -0400] cupsdCloseClient: 12
D [08/Mar/2009:20:26:34 -0400] cupsdAcceptClient: 12 from localhost (Domain)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 12 GET /admin/conf/printers.conf HTTP/1.1
D [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: Authorized as root using Local
D [08/Mar/2009:20:26:34 -0400] cupsdIsAuthorized: username="root"
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: Authorized as root using Local
D [08/Mar/2009:20:26:34 -0400] CUPS-Get-Default
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:26:34 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:26:34 -0400] Get-Notifications /
D [08/Mar/2009:20:26:34 -0400] cupsdIsAuthorized: requesting-user-name="maha"
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:26:34 -0400] cupsdReadClient: 12 POST / HTTP/1.1
D [08/Mar/2009:20:26:34 -0400] cupsdAuthorize: Authorized as root using Local
D [08/Mar/2009:20:26:34 -0400] Get-Printer-Attributes ipp://localhost/printers/DCP7020-for-CUPS
D [08/Mar/2009:20:26:34 -0400] cupsdProcessIPPRequest: 12 status_code=0 (successful-ok)
D [08/Mar/2009:20:26:34 -0400] cupsdCloseClient: 11
D [08/Mar/2009:20:27:00 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:27:00 -0400] cupsdReadClient: 7 POST /printers/DCP7020-for-CUPS HTTP/1.1
D [08/Mar/2009:20:27:00 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:27:00 -0400] Print-Job ipp://localhost/printers/DCP7020-for-CUPS
D [08/Mar/2009:20:27:00 -0400] add_job: requesting-user-name="maha"
D [08/Mar/2009:20:27:00 -0400] Adding default job-sheets values "none,none"...
I [08/Mar/2009:20:27:00 -0400] [Job 65] Adding start banner page "none".
I [08/Mar/2009:20:27:00 -0400] Saving subscriptions.conf...
I [08/Mar/2009:20:27:00 -0400] [Job 65] Adding end banner page "none".
I [08/Mar/2009:20:27:00 -0400] [Job 65] File of type application/postscript queued by "maha".
D [08/Mar/2009:20:27:00 -0400] [Job 65] hold_until=0
I [08/Mar/2009:20:27:00 -0400] [Job 65] Queued on "DCP7020-for-CUPS" by "maha".
D [08/Mar/2009:20:27:00 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:27:00 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:27:00 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:27:00 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:27:00 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:27:00 -0400] Get-Jobs ipp://localhost/jobs/
D [08/Mar/2009:20:27:00 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:27:00 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:27:00 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:27:00 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:27:00 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:27:00 -0400] Get-Notifications /
D [08/Mar/2009:20:27:00 -0400] cupsdIsAuthorized: requesting-user-name="maha"
D [08/Mar/2009:20:27:00 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:27:00 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:27:00 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:27:00 -0400] Get-Job-Attributes ipp://localhost/jobs/65
D [08/Mar/2009:20:27:00 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:27:00 -0400] cupsdAcceptClient: 11 from localhost (Domain)
D [08/Mar/2009:20:27:00 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Mar/2009:20:27:00 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:27:00 -0400] Get-Notifications /
D [08/Mar/2009:20:27:00 -0400] cupsdIsAuthorized: requesting-user-name="maha"
D [08/Mar/2009:20:27:00 -0400] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Mar/2009:20:27:00 -0400] cupsdCloseClient: 11
D [08/Mar/2009:20:27:00 -0400] cupsdAcceptClient: 11 from localhost (Domain)
D [08/Mar/2009:20:27:00 -0400] cupsdReadClient: 11 POST / HTTP/1.1
D [08/Mar/2009:20:27:00 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:27:00 -0400] Get-Notifications /
D [08/Mar/2009:20:27:00 -0400] cupsdIsAuthorized: requesting-user-name="maha"
D [08/Mar/2009:20:27:00 -0400] cupsdProcessIPPRequest: 11 status_code=0 (successful-ok)
D [08/Mar/2009:20:27:00 -0400] cupsdAcceptClient: 13 from localhost (Domain)
D [08/Mar/2009:20:27:00 -0400] cupsdReadClient: 13 POST / HTTP/1.1
D [08/Mar/2009:20:27:00 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:27:00 -0400] Get-Notifications /
D [08/Mar/2009:20:27:00 -0400] cupsdIsAuthorized: requesting-user-name="maha"
D [08/Mar/2009:20:27:00 -0400] cupsdProcessIPPRequest: 13 status_code=0 (successful-ok)
D [08/Mar/2009:20:27:00 -0400] cupsdCloseClient: 13
D [08/Mar/2009:20:27:01 -0400] cupsdCloseClient: 11
D [08/Mar/2009:20:27:01 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:27:35 -0400] Report: clients=2
D [08/Mar/2009:20:27:35 -0400] Report: jobs=38
D [08/Mar/2009:20:27:35 -0400] Report: jobs-active=3
D [08/Mar/2009:20:27:35 -0400] Report: printers=3
D [08/Mar/2009:20:27:35 -0400] Report: printers-implicit=0
D [08/Mar/2009:20:27:35 -0400] Report: stringpool-string-count=2292
D [08/Mar/2009:20:27:35 -0400] Report: stringpool-alloc-bytes=9608
D [08/Mar/2009:20:27:35 -0400] Report: stringpool-total-bytes=50928
D [08/Mar/2009:20:27:50 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:27:50 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:27:50 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:27:50 -0400] Get-Job-Attributes ipp://localhost/jobs/64
D [08/Mar/2009:20:27:50 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:27:50 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:27:50 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:27:50 -0400] Get-Job-Attributes ipp://localhost/jobs/63
D [08/Mar/2009:20:27:50 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:27:50 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:27:50 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:27:50 -0400] Get-Job-Attributes ipp://localhost/jobs/65
D [08/Mar/2009:20:27:50 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:27:50 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:27:50 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:27:50 -0400] cupsdReadClient: 7 POST / HTTP/1.1
D [08/Mar/2009:20:27:50 -0400] cupsdAuthorize: No authentication data provided.
D [08/Mar/2009:20:27:50 -0400] Cancel-Subscription /
D [08/Mar/2009:20:27:50 -0400] cupsdIsAuthorized: requesting-user-name="maha"
I [08/Mar/2009:20:27:50 -0400] Saving subscriptions.conf...
D [08/Mar/2009:20:27:50 -0400] cupsdProcessIPPRequest: 7 status_code=0 (successful-ok)
D [08/Mar/2009:20:27:50 -0400] cupsdCloseClient: 7
D [08/Mar/2009:20:27:50 -0400] cupsdAcceptClient: 7 from localhost (Domain)
D [08/Mar/2009:20:27:50 -0400] cupsdReadClient: 7 GET /admin/log/error_log HTTP/1.1
D [08/Mar/2009:20:27:50 -0400] cupsdAuthorize: No authentication data provided.
```

---

### Post by talynpower on 2009-03-13
Ok, this is how I got mine to work. I went to the printer Administration>Printing then right clicked on the printer and selected properties and instead of using the name of the machine hosting the printer eg smb://WORKGROUP/RIMBALDI/HPLaserJ, i changed the name into the machines IP address ie smb://WORKGROUP/1xx.1xx.x.xx/HPLaserJ  worked like a charm!

Hope it helps someone...

---

### Post by JustinAlf on 2009-04-06
After almost 3 months of not being able to print, the IP address insert worked for me.  Why in the hell has this not been fixed yet?  It should not be this damn difficult to fix.

---

### Post by utillich on 2009-05-31
Inserting ip fixed it for me too, thanks.

---

### Post by dmizer on 2009-05-31
Try the 6th link in my sig to get name browsing to work.

---

### Post by Lucretia on 2009-06-14
Using the IP address doesn't fix it for me.

Same issue, "too many failed attempts". Using 8.10.

---

