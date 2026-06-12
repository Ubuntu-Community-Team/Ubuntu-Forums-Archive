---
title: "Wireless Broadcom driver resets System time:  Very Odd"
date: 2015-05-26
forum: Networking &amp; Wireless
---

### Post by mchain on 2015-05-26
Just installed 14.04.2 LTS on a SanDisk Cruzer 16GB Flash drive a couple of days ago.  

Used a live cd, wired cat6 connection, removed power cables for the windows system drive and secondary drive, and was able to set ext3/ext4 file system with a swap file space of 3.0 GB.  Ran the broadcom driver install with NETGEAR N3100 usb.  Installation was successful.  System was brought up-do-date during the CAT6 install, and wireless appears to be working well, as I am on the forum using 14.04.2 LTS right now.

Reason for installing to an USB drive is simple:  Dual-booting is not an option.  Nor is installing on another available HDD within the system.

Startup of the system with the USB drive will result in a time advance of exactly six hours over actual time here.  Restart of the system will result in a change of twelve hours, sometimes showing that the system is on the next day if the current day is less than twelve hours away from moving to the next day.

Checking the system BIOS will reveal the time change has already occurred as it has already initialized the USB drive.  

Workaround is to re-enter BIOS and reset time to current time, but this works only some of the time.  The twelve hour jump came off a system USB restart.

System is a HP-Compaq DX2300 mini-tower business model for home use, Pentium D 2.8 GHz, 3.0 GB RAM, and the two hdd's for windows.  

This is odd that the system time would reset to different hours each time the Cruzer is used, but the time remains correct when Windows is run.

Only account currently set up is the admin account.  The time/day applet does **not** have the normal admin password request/block in the window as I've seen in previous versions of Ubuntu in the past.

Obviously, if the system time is incorrect when connecting wirelessly, it has an impact on whether the router will accept the connection.  I've had to clear the wireless connection settings once so far, and re-enter the same credentials again to get connected.  

The question is, why is the usb resetting the system time on boot?  What diagnostics should I run in terminal to help resolve this issue?

---

### Post by mchain on 2015-05-28
I forgot to provide lsusb output.  Sorry.

                        ```
jacob@jacob-HP-Compaq-dx2300-Microtower:~$ lsusb 

 Bus 001 Device 006: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231] 
 Bus 001 Device 003: ID 0781:5575 SanDisk Corp.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 003: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
 Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 002: ID 03f0:1104 Hewlett-Packard DeskJet 959c 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 


```

Note:  Two days ago, wireless connection via NETGEAR was not working:  LIne for Netgear under lsusb was Bus 001 Device **7**.  Maybe that is why it wouldn't connect?

Anyway, connection is live and this is the current lsusb output.

---

### Post by wildmanne39 on 2015-05-28
Why do you think the broadcom driver is causing the issue? 
Thanks

---

### Post by mchain on 2015-05-29
Hi Wild Man,

Thank you for replying.

Because the issue of system time change was not present or evident before installing the broadcom package.  I used the CAT6 (wired) method to install the broadcom driver for NETGEAR.  I did not see any time changes during several reboots or shutdowns while using a wired connection.  

Scenario always begins with Ubuntu USB cold boot:

If the system is shutdown, and the Ubuntu USB is pulled, the system is powered on, Windows will consistently show it is exactly six hours behind the UTC time zone I've set here.  If Windows is shutdown and Ubuntu USB is booted as a cold start, then the UTC time zone will show it exactly six hours ahead of local time.

Since the time zone is set to automatically update, within three minutes it will show the correct time when running 14.04.2 LTS. 

If I check the time in system BIOS, and thus blocking a system boot, it will show the +/- six hour change has already occurred in either scenario.  Workaround for Windows is to enter BIOS and set the system time 6 hours ahead to the correct time and then allow CMOS to save the settings and reboot.

If Ubuntu is not run, then the system time does not change, and remains accurate.  

An issue such as this one is one reason I have for not dual-booting as an issue such as this one cannot be foreseen ahead of time.

Other than this one thing, Ubuntu runs well on this system.  It boots to desktop within 45 seconds and shuts down in about 5 seconds.

My feeling is that this should not be happening, tho.  Thanks.

---

### Post by wildmanne39 on 2015-05-29
Reboot your computer and as soon as the time changes run this command:
```
sudo tail -n200 /var/log/syslog
sudo tail -n200 /var/log/kern.log
```
paste the output here:
[http://pastebin.com/]("http://pastebin.com/")
then post the link back here.
Hopefully someone will take a look but if not I will later today when I have time.
Thanks

---

### Post by mchain on 2015-05-29
@ Wild Man,

Off to work atm.  Will get the requested logs as soon as able.  Link will be provided in following post.

-mchain

---

### Post by mchain on 2015-05-31
[http://pastebin.com/paYUVfv5](http://pastebin.com/paYUVfv5)  SysLog
[http://pastebin.com/5c7H2k1J](http://pastebin.com/5c7H2k1J)  kernelLog 1
[http://pastebin.com/eviVNYzt](http://pastebin.com/eviVNYzt)   kernelLog 2

Only reason for splitting kernel log was it apparently was too big. 

Did have difficulty connecting to network, had to reset modem/router and manually set computer system time as it would not automatically update to the correct time.  You will see the logs show the current time to be five hours **behind** the correct local time here.

A relevant detail left out in first post: I was watching the broadcom install as it was running in terminal.  There was a line that stated the kernel was [COLOR=#ff0000]"tainted"[/COLOR].  Don't know what that meant so forgot to mention it in the first post.

This was my first try using pastebin, so learning curve is involved.  gedit apparently is a little different in operation than notepad; so possible some of the syslog wound up in the kernellog paste and thus made too large to save to the bin.

Hope this helps.  Thanks.

---

### Post by mchain on 2015-06-01
Software Updater reported an update for Ubuntu base, so this was installed on Sunday.

Now system time does not change, but will monitor over time and report back if it reverts to reported odd behavior.

Did notice that ubuntu base install has caused the web data stream to stop completely if adobe shockwave is run and it crashes.  Workaround is to restart system and avoid running shockwave; similar issue reported at Linux Mint forums but never got support for this issue over there.  Moved over to Ubuntu as I've gotten much better support here.

The only change to the system is the new Ubuntu base install.

Before ubuntu base was installed, time issue was present, network connectivity issue was present, but now neither is an issue.  Only new issue is the one where the usb dongle is connected but no data stream is available.  So the new base install (which was somehow omitted in original install) fixed two issues only to bring in a third.

A second Ubuntu base install came in today (Monday) so that was installed also.

---

### Post by wildmanne39 on 2015-06-01
Glad it is working by whatever means necessary.

---

### Post by mchain on 2015-06-01
Well, thank you.

So a third Ubuntu base update came in just now.  This one had to do with secure sockets.  Related possibly to issue at hand?

Second Ubuntu base update killed both the local network and internet connections, just so you know.

But the issue with the local system time is now gone, apparently since I was missing the first Ubuntu base install.  I now have a window with the option to select four different options not present before.  Once the first one was put in, system time is stable.

:KS

---

### Post by wildmanne39 on 2015-06-01
Glad the time reset issue is resolved! If you have not done so already start a new thread for the wifi issue and run the wireless script in my signature and post the results in that thread by clicking on # and pasting the contents of the file between them.
Thanks

---

### Post by mchain on 2015-06-03
Not really.

Workaround to title topic still must be applied:  Enter BIOS and manually adjust system time before booting windows so it (Windows) does not think the system time is five hours ahead of local time.

If Ubuntu is booted from USB, then system time will have to be adjusted manually five hours ahead to local time; it is set back five hours.

Anyway, wireless script has been run and a new topic established.  A tar.gz file was generated also.

Thanks.

---

### Post by mchain on 2015-07-30
Fixed wireless connectivity issue in Ubuntu LTS, so now time/date is correct when logging onto account as wireless set to automatically connect on boot.

But issue with Windows time/date is still present:  Five hours ahead on boot unless care is taken to reset system time in BIOS before booting into Windows after shutting down Ubuntu on usb stick.

Why does this issue happen at all?  Does anyone know?

Is issue present on an internal hdd partitioned to Windows/Ubuntu dual-boot?

---

