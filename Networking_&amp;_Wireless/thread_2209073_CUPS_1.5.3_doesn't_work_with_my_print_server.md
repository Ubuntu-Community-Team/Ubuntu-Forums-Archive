---
title: "CUPS 1.5.3 doesn't work with my print server"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by srdjan-hrnjak on 2014-03-03
Computers with Ubuntu 12.04 and CUPS 1.5.3, doesn't work with my print server (U.S. Robotics ADSL 4-Port Router with Lexmark E120 attached). Printing test page displays error message: ```
Print file was not accepted.
```
Printer and print server still works on computers with Ubuntu 11.04 and CUPS 1.4.6. Printer works normally when it is connected directly on USB port of computers with Ubuntu 12.04.

---

### Post by tgalati4 on 2014-03-03
Look in /var/log/cups for errors in both your printer server and your client computer that sent the file.  Post any errors.

---

### Post by srdjan-hrnjak on 2014-03-03
error_log
```
E [04/Mar/2014:01:53:14 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [04/Mar/2014:01:53:15 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-2-Gray..' already exists
W [04/Mar/2014:01:53:15 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120-2' already exists
```

error_log.1.gz
```
E [03/Mar/2014:00:08:05 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
E [03/Mar/2014:02:14:04 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
E [03/Mar/2014:09:15:00 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [03/Mar/2014:20:59:36 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-LAN-Gray..' already exists
W [03/Mar/2014:20:59:36 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120-LAN' already exists
W [03/Mar/2014:20:59:36 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-LAN-Gray..' already exists
W [03/Mar/2014:20:59:36 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120-LAN' already exists
W [03/Mar/2014:20:59:36 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-LAN-Gray..' already exists
W [03/Mar/2014:20:59:36 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120-LAN' already exists
W [03/Mar/2014:21:05:43 +0100] Lexmark-E120-LAN: Printer does not provide REQUIRED printer-is-accepting-jobs attribute.
W [03/Mar/2014:21:05:43 +0100] Lexmark-E120-LAN: Printer does not provide REQUIRED printer-state-reasons attribute.
W [03/Mar/2014:21:05:43 +0100] Lexmark-E120-LAN: Printer does not support REQUIRED Validate-Job operation.
E [03/Mar/2014:21:05:43 +0100] [Job 1] Print file was not accepted.
W [03/Mar/2014:21:08:15 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-LAN-Gray..' already exists
W [03/Mar/2014:21:08:15 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120-LAN' already exists
W [03/Mar/2014:21:08:15 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-LAN-Gray..' already exists
W [03/Mar/2014:21:08:15 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120-LAN' already exists
W [03/Mar/2014:21:08:15 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-LAN-Gray..' already exists
W [03/Mar/2014:21:08:15 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120-LAN' already exists
W [03/Mar/2014:21:08:15 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-LAN-Gray..' already exists
W [03/Mar/2014:21:08:15 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120-LAN' already exists
W [03/Mar/2014:21:08:22 +0100] Lexmark-E120-LAN: Printer does not provide REQUIRED printer-is-accepting-jobs attribute.
W [03/Mar/2014:21:08:22 +0100] Lexmark-E120-LAN: Printer does not provide REQUIRED printer-state-reasons attribute.
W [03/Mar/2014:21:08:22 +0100] Lexmark-E120-LAN: Printer does not support REQUIRED Validate-Job operation.
E [03/Mar/2014:21:08:22 +0100] [Job 2] Print file was not accepted.
E [03/Mar/2014:21:09:47 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [03/Mar/2014:21:09:53 +0100] failed to CreateProfile: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
E [03/Mar/2014:21:12:03 +0100] [Job 3] Print file was not accepted.
W [03/Mar/2014:21:22:22 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:21:22:22 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:21:22:34 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:21:22:34 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:21:22:34 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:21:22:34 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:21:22:49 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-is-accepting-jobs attribute.
W [03/Mar/2014:21:22:49 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-state-reasons attribute.
W [03/Mar/2014:21:22:49 +0100] Lexmark-E120: Printer does not support REQUIRED Validate-Job operation.
E [03/Mar/2014:21:22:49 +0100] [Job 5] Print file was not accepted.
E [03/Mar/2014:21:28:00 +0100] [Job 5] Stopping unresponsive job!
W [03/Mar/2014:21:52:03 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-2-Gray..' already exists
W [03/Mar/2014:21:52:03 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120-2' already exists
E [03/Mar/2014:21:58:10 +0100] [Job 7] Invalid printer command "Clean".
E [03/Mar/2014:21:58:18 +0100] [Job 7] Job stopped due to filter errors; please consult the error_log file for details.
D [03/Mar/2014:21:58:18 +0100] [Job 7] The following messages were recorded from 21:58:10 to 21:58:17
D [03/Mar/2014:21:58:18 +0100] [Job 7] Adding start banner page "none".
D [03/Mar/2014:21:58:18 +0100] [Job 7] Adding end banner page "none".
D [03/Mar/2014:21:58:18 +0100] [Job 7] File of type application/vnd.cups-command queued by "sloter".
D [03/Mar/2014:21:58:18 +0100] [Job 7] hold_until=0
D [03/Mar/2014:21:58:18 +0100] [Job 7] Queued on "Lexmark-E120-2" by "sloter".
D [03/Mar/2014:21:58:18 +0100] [Job 7] job-sheets=none,none
D [03/Mar/2014:21:58:18 +0100] [Job 7] argv[0]="Lexmark-E120-2"
D [03/Mar/2014:21:58:18 +0100] [Job 7] argv[1]="7"
D [03/Mar/2014:21:58:18 +0100] [Job 7] argv[2]="sloter"
D [03/Mar/2014:21:58:18 +0100] [Job 7] argv[3]="Test Page"
D [03/Mar/2014:21:58:18 +0100] [Job 7] argv[4]="1"
D [03/Mar/2014:21:58:18 +0100] [Job 7] argv[5]="job-uuid=urn:uuid:1079b385-133e-3ef8-408d-b56219b7e6b4 job-originating-host-name=localhost time-at-creation=1393880290 time-at-processing=1393880290"
D [03/Mar/2014:21:58:18 +0100] [Job 7] argv[6]="/var/spool/cups/d00007-001"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[8]="HOME=/var/spool/cups/tmp"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[10]="SERVER_ADMIN=root@sloter"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[11]="SOFTWARE=CUPS/1.5.3"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[13]="USER=root"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[16]="IPP_PORT=631"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[17]="CHARSET=utf-8"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[18]="LANG=sr_RS.UTF-8"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[19]="PPD=/etc/cups/ppd/Lexmark-E120-2.ppd"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[20]="RIP_MAX_CACHE=128m"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[21]="CONTENT_TYPE=application/vnd.cups-command"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[22]="DEVICE_URI=usb://Lexmark/E120?serial=9958VK8"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[23]="PRINTER_INFO=Lexmark International Lexmark E120"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[24]="PRINTER_LOCATION=sloter"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[25]="PRINTER=Lexmark-E120-2"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[26]="PRINTER_STATE_REASONS=none"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[27]="CUPS_FILETYPE=document"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[28]="FINAL_CONTENT_TYPE=application/postscript"
D [03/Mar/2014:21:58:18 +0100] [Job 7] envp[29]="AUTH_I****"
D [03/Mar/2014:21:58:18 +0100] [Job 7] Started filter /usr/lib/cups/filter/commandtops (PID 5834)
D [03/Mar/2014:21:58:18 +0100] [Job 7] Started backend /usr/lib/cups/backend/usb (PID 5835)
D [03/Mar/2014:21:58:18 +0100] [Job 7] Printing on printer with URI: usb://Lexmark/E120?serial=9958VK8
D [03/Mar/2014:21:58:18 +0100] [Job 7] libusb_get_device_list=12
D [03/Mar/2014:21:58:18 +0100] [Job 7] Set job-printer-state-message to "Invalid printer command "Clean".", current level=ERROR
D [03/Mar/2014:21:58:18 +0100] [Job 7] STATE: +connecting-to-device
D [03/Mar/2014:21:58:18 +0100] [Job 7] STATE: -connecting-to-device
D [03/Mar/2014:21:58:18 +0100] [Job 7] Printer found with device ID: MANUFACTURER:Lexmark International;COMMAND SET:NPAP, PJL;MODEL:Lexmark E120;CLS:PRINTER;DES:Lexmark E120;CID:Lexmark_Internationa9D72;COMMENT:ECP1.0, LV_043D, LP_00CD, LF_003F; Device URI: usb://Lexmark/E120?serial=9958VK8
D [03/Mar/2014:21:58:18 +0100] [Job 7] Device protocol: 2
D [03/Mar/2014:21:58:18 +0100] [Job 7] Sending data to printer.
D [03/Mar/2014:21:58:18 +0100] [Job 7] Sent 0 bytes...
D [03/Mar/2014:21:58:18 +0100] [Job 7] Waiting for read thread to exit...
D [03/Mar/2014:21:58:18 +0100] [Job 7] Read thread still active, aborting the pending read...
D [03/Mar/2014:21:58:18 +0100] [Job 7] End of messages
D [03/Mar/2014:21:58:18 +0100] [Job 7] printer-state=3(idle)
D [03/Mar/2014:21:58:18 +0100] [Job 7] printer-state-message="Sending data to printer."
D [03/Mar/2014:21:58:18 +0100] [Job 7] printer-state-reasons=none
E [03/Mar/2014:22:03:02 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [03/Mar/2014:22:03:07 +0100] failed to CreateProfile: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
W [03/Mar/2014:22:12:19 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:12:19 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:12:19 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:12:19 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:12:19 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:12:19 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:12:27 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-is-accepting-jobs attribute.
W [03/Mar/2014:22:12:27 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-state-reasons attribute.
W [03/Mar/2014:22:12:27 +0100] Lexmark-E120: Printer does not support REQUIRED Validate-Job operation.
E [03/Mar/2014:22:12:27 +0100] [Job 10] Print file was not accepted.
W [03/Mar/2014:22:15:48 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:15:48 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:15:48 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:15:48 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:15:48 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:15:48 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:15:48 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:15:48 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:15:55 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-is-accepting-jobs attribute.
W [03/Mar/2014:22:15:55 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-state-reasons attribute.
W [03/Mar/2014:22:15:55 +0100] Lexmark-E120: Printer does not support REQUIRED Validate-Job operation.
E [03/Mar/2014:22:15:55 +0100] [Job 11] Print file was not accepted.
W [03/Mar/2014:22:16:21 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:16:21 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:16:21 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:16:21 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:17:30 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:17:30 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:27:56 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:27:56 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:27:56 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:27:56 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:27:56 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:27:56 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:27:56 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:27:56 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:28:13 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-is-accepting-jobs attribute.
W [03/Mar/2014:22:28:13 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-state-reasons attribute.
W [03/Mar/2014:22:28:13 +0100] Lexmark-E120: Printer does not support REQUIRED Validate-Job operation.
E [03/Mar/2014:22:28:13 +0100] [Job 12] Print file was not accepted.
W [03/Mar/2014:22:28:36 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:28:36 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
E [03/Mar/2014:22:28:40 +0100] [Job 12] Print file was not accepted.
W [03/Mar/2014:22:29:09 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:29:09 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:29:09 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:29:09 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:29:09 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:29:09 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:32:09 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:32:09 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:32:09 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:32:09 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:32:09 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:32:09 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:32:09 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:22:32:09 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:22:32:16 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-is-accepting-jobs attribute.
W [03/Mar/2014:22:32:16 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-state-reasons attribute.
W [03/Mar/2014:22:32:16 +0100] Lexmark-E120: Printer does not support REQUIRED Validate-Job operation.
E [03/Mar/2014:22:32:16 +0100] [Job 14] Print file was not accepted.
E [03/Mar/2014:23:01:23 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [03/Mar/2014:23:01:29 +0100] failed to CreateProfile: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
W [03/Mar/2014:23:05:02 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:23:05:02 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:23:05:02 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:23:05:02 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:23:05:02 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:23:05:02 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
E [03/Mar/2014:23:19:03 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [03/Mar/2014:23:19:36 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-is-accepting-jobs attribute.
W [03/Mar/2014:23:19:36 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-state-reasons attribute.
W [03/Mar/2014:23:19:36 +0100] Lexmark-E120: Printer does not support REQUIRED Validate-Job operation.
E [03/Mar/2014:23:19:36 +0100] [Job 16] Print file was not accepted.
E [03/Mar/2014:23:23:58 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [03/Mar/2014:23:24:02 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-is-accepting-jobs attribute.
W [03/Mar/2014:23:24:02 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-state-reasons attribute.
W [03/Mar/2014:23:24:02 +0100] Lexmark-E120: Printer does not support REQUIRED Validate-Job operation.
E [03/Mar/2014:23:24:02 +0100] [Job 16] Print file was not accepted.
W [03/Mar/2014:23:25:50 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:23:25:50 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:23:25:50 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:23:25:50 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:23:25:50 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:23:25:50 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
W [03/Mar/2014:23:25:50 +0100] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'Lexmark-E120-Gray..' already exists
W [03/Mar/2014:23:25:50 +0100] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-Lexmark-E120' already exists
E [03/Mar/2014:23:28:23 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [03/Mar/2014:23:29:08 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-is-accepting-jobs attribute.
W [03/Mar/2014:23:29:08 +0100] Lexmark-E120: Printer does not provide REQUIRED printer-state-reasons attribute.
W [03/Mar/2014:23:29:08 +0100] Lexmark-E120: Printer does not support REQUIRED Validate-Job operation.
E [03/Mar/2014:23:29:08 +0100] [Job 17] Print file was not accepted.
E [03/Mar/2014:23:34:27 +0100] [Job 17] Stopping unresponsive job!
E [04/Mar/2014:01:48:12 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
W [04/Mar/2014:01:48:17 +0100] failed to CreateProfile: org.freedesktop.DBus.Error.NoReply:Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

error_log.2.gz
```
E [02/Mar/2014:20:48:38 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
E [02/Mar/2014:21:01:43 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
E [02/Mar/2014:23:00:35 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
E [03/Mar/2014:00:03:03 +0100] Unknown directive SystemGroup on line 16 of /etc/cups/cupsd.conf.
```

---

### Post by srdjan-hrnjak on 2014-03-03
Found this: [HTML]https://bugs.launchpad.net/ubuntu/+source/cups/+bug/973270[/HTML] 
I replaced "http" in printer address with "ipp14" and now it works

---

### Post by tgalati4 on 2014-03-04
CUPS as all frameworks in linux is undergoing constant change.  I'm glad you found a work-around.  It is no fun to deal with regressions--something that was working just fine gets messed up with a newer version.

Glad you found the problem, because the error messages were of no help.

---

### Post by srdjan-hrnjak on 2014-03-05
It was helpful for me, in log I found error 
```
Printer does not provide REQUIRED printer-is-accepting-jobs attribute.
```
which I googled and found solution :)

---

