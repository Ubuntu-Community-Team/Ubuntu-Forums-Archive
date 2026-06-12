---
title: "ethernet card disconnecting"
date: 2023-08-11
forum: Networking &amp; Wireless
---

### Post by patwashere on 2023-08-11
[COLOR=#000000][FONT=Arial]Symptom:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Usually, when I am not active on the system, I will notice my Plex server is no longer reachable after some time.  Try to connect via xrdp, nothing, ping the IP for the box and get no reply.   Going directly to the PC and moving the mouse to wake the screen, I am presented with the logon dialog.  I enter my pwd and press enter.   I am then presented with a blank screen where I need to ctrl-alt-delete or alt-prtscr REISUB to get the box to reboot.  When it&#8217;s rebooted it works fine while I am on the box.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]My setup.  HP m01-f1 PC, Intel i3-10100 cpu, 16gb memory,  1TB m.2ssd, running Ubuntu 22.04 LTS fresh install, all patched up to 22.04.3. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I have installed:[/FONT][/COLOR]

[LIST]
[*]Plex server
[*]XRDP - used to rdp from Windows.  I don&#8217;t have a dedicated monitor for this Ubuntu box so use RDP to get access to the box.
[*]Private Internet VPN connected using split tunneling to allow Chrome to use the vpn and plex server to not use the vpn.
[/LIST]


[COLOR=#000000][FONT=Arial]Logs under the important tab show:[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Image removed :)[/FONT][/COLOR]

```

[COLOR=#000000][FONT=Arial]07:13:02 kernel: Syncing filesystems and block devices - timed out, issuing SIGKILL to PID 28349.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]07:13:00 kernel: r8169 0000:04:00.0 enp4s0: rtl_eriar_cond == 1 (loop: 100, delay: 100).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]07:12:21 systemd: Failed unmounting /mnt/nas/plex.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]07:12:18 kernel: r8169 0000:04:00.0 enp4s0: rtl_eriar_cond == 1 (loop: 100, delay: 100).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]07:12:05 gdm3: Gdm: Failed to contact accountsservice: Error calling StartServiceByName for org.freedesktop.Accounts: Transaction for accounts-daemon.service/start is destructive[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](systemd-fsck@dev-disk-by\x2duuid-84DE\x2d8FF9.service has 'stop' job queued, but 'start' is included in transaction).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]07:11:56 kernel: r8169 0000:04:00.0 enp4s0: rtl_eriar_cond == 1 (loop: 100, delay: 100).[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]07:10:22 gdm-session-wor: gkr-pam: unable to locate daemon control file[/FONT][/COLOR]

```
[COLOR=#000000][FONT=Arial]I first suspected that the NIC was bad so I ordered a cheap card from Amazon to replace the onboard Realtek card.  I did not think about the chipset and the new card is also a Realtek chipset.  The network is set up to a dedicated IP address.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]I have tried googling.  I have tried to use the r8168-dkms drivers in place of the built-in r8169.  But I am not sure that&#8217;s taken hold.  I followed the instructions from the first answer from this [/FONT][/COLOR][[COLOR=#1155CC][FONT=Arial]https://askubuntu.com/questions/1327697/ubuntu-20-04-ethernet-r8168[/FONT][/COLOR]]("https://askubuntu.com/questions/1327697/ubuntu-20-04-ethernet-r8168")[COLOR=#000000][FONT=Arial]  I did not try the second answer yet as it seems more in-depth.  After following the first suggestion last night.  My box was again unresponsive to the network this morning. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Should I consider getting another PCI card, this time have it be an intel chip set?   If so, can anyone suggest a good, inexpensive card?[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Where do I start digging?

[/FONT][/COLOR]The results of the wirelss-info script:

[https://pastebin.com/JPEeG7j8](https://pastebin.com/JPEeG7j8)
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by TheFu on 2023-08-11
First, please don't post images when text will do.  Save my bandwidth.

I've never seen the log tool you are using.  I'd use 
```
egrep -i 'warn|err' /var/logs/syslog*
```
as my first pass looking for issues.  
I'd also check the **dmesg** log.

Eventually, these text files are going away, so now is the time to get used to the very excellent **journalctl** log tool.  It really is excellent.  Some of my notes:
```
  journalctl -xe            # See errors for last service, with eXtra information
  journalctl -b -1          # See prior boot log
  journalctl -b -3          # See 3 boot logs ago
  journalctl -b             # See current boot logs
  journalctl --list-boots   # See how many prior boots are available
  sudo journalctl -k        # See current kernel logs

  journalctl --since=today
  journalctl -S today       # See logs for today, from midnight, yesterday/tomorrow
  journalctl -xe -S today   # See errors for today, from midnight today

  sudo journalctl /usr/bin/anacron # logs for a specific executable (full path is required)
  journalctl UNIT=snap.lxd.activate # get messages for a specific systemd unit file
  journalctl -u nfs-kernel-server.service   # Unit file/service
  journalctl -u nfs-server.service -S -2h   # Unit file/service in the last 2 hrs

  sudo journalctl -S -1h    # See logs for last 1 hour m/w == minutes/weeks

  sudo journalctl _PID=751  # find logs for a specific PID
  sudo journalctl _UID=1000 # find logs for a specific user
  journalctl -p 0           # emergency
                1           # alert
                2           # critical
 ....
                6           # info
                7           # debug

# Cleanup
  journalctl --disk-usage   # See log file disk use
  sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.
  sudo journalctl --vacuum-time=10d     # Drop logs, over 10 days old

```

Whenever posting terminal output, **please**, _please_, *please*, use forum code tags so the columns line up. We are used to seeing it and know exactly where to look.

I've had issues with realtek and marvell NICs, but they generally work, until it becomes flaky then after a few weeks, it dies.  I go out of my way to get well-known, well-supported, Intel NICs. Not all of the Intel NICS are equal.  The v219 and v217 seem to have more issues than others. Don't know why.  Some of the newer 2.5Gbps Intel NICs had/have issues with Linux. My last motherboard purchase specifically avoided them last November because there were still Intel driver problems being reported in Ubuntu installs with the new chips and Intel was denying any problems.  I haven't seen any in some time, so perhaps that is all solved?  IDK. i225V NICs: [https://askubuntu.com/questions/1288787/intel-i225v-2-5g-ethernet-card-drivers-not-working-ubuntu-20-04](https://askubuntu.com/questions/1288787/intel-i225v-2-5g-ethernet-card-drivers-not-working-ubuntu-20-04)

Has it always been flaky with your system or is this something new?

Have you tried a different switch port?
Have you tried a different CAT 5e (or better) cable?
Try the easy, cheap, stuff first.

I wouldn't bother with xrdp.  Learn to use, love, **ssh**.  restarting any service over ssh is a basic knowledge thing.  You can use **ssh -X** to run remote programs on another system, but having the output displayed in a window on the workstation you are sitting at.

When using Linux, never expect any addon to work unless you specifically look up the chip it uses and KNOW the kernel driver is included.  Think about the time you've wasted on this issue. Makes paying $20 more for supported hardware a bargain.  When I first started, I was cheap and would try to save $3.  Then after 20 yrs troubleshooting some issue, even if there was a solution, it didn't "just work" with the next upgrade.  I chose JFS for a file system to get journaling before any other file systems could really do it.  Had to build the kernel special to get JFS support.  But when I had a boot problem, the floppy/CDROM didn't support JFS and I was screwed.  Eventually, a new OS came that supported Ext3 which had journaling, so I wiped the file system and started fresh with ext3.  That's when I stopped buying the cheapest stuff - and while I'm not completely sane yet, I do have fewer insane episodes.  ;)

---

### Post by patwashere on 2023-08-11
Ok Image removed and used the code tag.  thanks for the guidance.

My issue happened again just now when I went to get the logs you requested.  So the box has been rebooted.

Here is grep from the syslog from about 3am this morning.  The whole thing was too large for pastebin.

[https://pastebin.com/BtvpZWnz](https://pastebin.com/BtvpZWnz)

I will look into the dmesg log.  is that something you'd like posted here?

Sorry I am a gui type of guy.  am familiar with SSH, but only use it when i have too ;)

This issue started when I rebuilt my OS.   I ignorantly upgraded from 22.x  to 23.4 and hit a lot of bugs, so I reset back to 22.04 LTS fresh install along side the broken 23.4 and a windows partition.  that's when i started to get the NIC disconnects.   Since then I have reinstalled 22.04 2 times still keeping the other Ubuntu 23.04 and windows partitions (tipple boot options).  the most recent I installed 22.04 wiping the disk clean and only having ubuntu on it.  that's where i am today with the NIC issues persisting.   I'd like to call out that I do not know for sure that the NIC is causing the issue.   It's just the thing I notice that the network stops responding.  This might be a symptom of something else. 

Thanks for your help. 

--pat

---

### Post by patwashere on 2023-08-11
thanks for the [COLOR=#000000][FONT=&amp]journalctl tip.  checking that out too.  will double check the wiring stuff.  prior to the reinstall of ubuntu it was working flawlessly . [/FONT][/COLOR]

---

### Post by herickwilke on 2023-08-15
Experiencing the exact same issue after Ubuntu update some days ago. It was not happening before, never happened before to be more specific. Here go the only log I have. 

11:16:47 kernel: r8169 0000:04:00.0 enp4s0: rtl_eriar_cond == 1 (loop: 100, delay: 100).

Seems to be related to driver r8169. My connection keeps blocked until I run rmmod r8169; modprobe r8169. Then, my Ethernet disconnects and I can go back to navigate again using Wi-Fi. Rebooting the system is the only way to solve the problem.
 
It happens almost everyday, normally when I'm making use of a huge download, or attending to some meeting on Google Meet.

---

### Post by patwashere on 2023-08-15
I went ahead and ordered a new intel based ethernet card.   I installed it yesterday, reinstalled Ubuntu and only installed plex server, set it up to see the media files on the nas and let it run that way.  was up for 24 hours without a crash.  So this morning I went ahead and installed the vpn and other apps needed and it's been running fine for 10 hours now.  no crashes.

here is the card i used.

[https://www.amazon.com/dp/B0B5632FPZ?psc=1&ref=ppx_yo2ov_dt_b_product_details](https://www.amazon.com/dp/B0B5632FPZ?psc=1&ref=ppx_yo2ov_dt_b_product_details)

---

### Post by patwashere on 2023-08-16
up for 3 days now with the nic replaced with the one above.

---

