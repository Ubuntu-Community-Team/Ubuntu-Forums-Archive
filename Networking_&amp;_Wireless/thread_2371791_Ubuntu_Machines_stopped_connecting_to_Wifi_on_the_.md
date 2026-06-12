---
title: "Ubuntu Machines stopped connecting to Wifi on the same day!"
date: 2017-09-18
forum: Networking &amp; Wireless
---

### Post by josephmmorgan on 2017-09-18
For some reason, today, both of my Ubuntu 16.04 machines suddenly stopped connecting to WiFi.  I have several access points, and they won't connect to any of them though we've previously been using them for quite some time.  All my other stuff connects just fine with no issues (a few Windows boxes, several Apple devices, and several Android devices), so there is nothing wrong with the Wifi.

One machine is an ASUS G73SW with Intel Xeon and 16GB with an Atheros AR9285.  The other is an HP with AMD8 and 4GB with an Atheros AR9485.  Machines are totally different but both have Atheros just different model.

The machines "see" the Wifi.  That is, I can select them from the WiFi icon and switch between them.  They even show and say they are connected, but they are not.


[LIST]
[*]ifconfig does not show an IP address.
[*]ping to 8.8.8.8 gives me "Network is unreachable"
[*]Restarting network manager just completely shuts down the wifi altogether and I have to reboot to get at least that much back.
[*]route shows nothing (which explains the first two above)
[*]Reboot does not work to solve it.
[*]Deleting the wifi connections, rebooting, the connecting back to them doesn't solve it.
[/LIST]

No matter what I do, they behave exactly the same.  I suspect some kind of corruption, but don't know where to look or what to do to fix it.

---

### Post by wildmanne39 on 2017-09-18
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by josephmmorgan on 2017-09-18
I keep my machines pretty up to date and nothing updated.

```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

wireless-info.tar.gz attached.

[ATTACH]276768[/ATTACH]

---

### Post by wildmanne39 on 2017-09-18
I am having trouble opening the file will you please post it to pastebin like the first suggestion at the link with the script.

Thanks

---

### Post by josephmmorgan on 2017-09-18
I hate to be an idiot, but I've never used pastebin in my life... I have the site up and the text pasted there.  I gave it a name "JMUbuntuWirelessIssue"

What do I do now?  Note I have no account on there.

---

### Post by wildmanne39 on 2017-09-18
From the directions where you ran the script:
```
sudo apt install pastebinit
```
This will enable the wireless script to, upon your approval, upload the obtained data to pastebin while the script is running, creating at the same time a link to it in your terminal, permitting you to paste it to a forum thread.

Once that's done, download and run the [wireless info script]("https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info"), which will gather information to help diagnose your system. You can run it using this command:
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && \
chmod +x wireless-info && \
./wireless-info
```

Just post the link here that is created in the terminal.

---

### Post by josephmmorgan on 2017-09-18
[https://pastebin.com/W3ELGNf8](https://pastebin.com/W3ELGNf8)

---

### Post by wildmanne39 on 2017-09-18
Pleased do the following:

Open the file with your text editor, if you need more directions just ask:
```
sudo -H gedit /etc/NetworkManager/NetworkManager.conf
```
add lines
```
[device]
wifi.scan-rand-mac-address=0
```
Save and close file then reboot.

---

### Post by josephmmorgan on 2017-09-18
Done, but no resolution.  It still finds and says it is connected, but no route, no IP under ifconfig.

---

### Post by wildmanne39 on 2017-09-18
Please set your settings in network manger to match the screenshots, I believe you need this fix and the one in my previous post because kernel 4.10 has two bugs concerning networking.

Specifically it is the dns servers that will make it work but changing the other settings will give you a more stable connection.

Edit:

Reboot

Thanks

---

### Post by wildmanne39 on 2017-09-19
*Thread moved to **Networking & Wireless for better fit**.*

---

### Post by josephmmorgan on 2017-09-19
This seems to have made things worse.  Now it still "sees" the wireless networks, but now it cannot seem to connect to it.  That is, before, at least it *thought* it had connected, even though I'd have no IP and internet access.  Now, it is endlessly scanning. 

I'm going to revert those settings back to see if it at least gets back to the way it was.

---

### Post by wildmanne39 on 2017-09-19
It is possible something was entered incorrectly, for me to help, I need you to leave the settings and post a new wireless script file, then you can revert the changes if needed.

---

### Post by josephmmorgan on 2017-09-19
Ok.. so I reverted it back and at least got it back to the way it was.  I've changed only the "UNIFY-LR" network settings according to the screenshots, and then reran the script.

[http://paste.ubuntu.com/25570374/](http://paste.ubuntu.com/25570374/)

---

### Post by wildmanne39 on 2017-09-19
I will look at this more tomorrow, it is late here, someone else may stop in before I return.

---

### Post by josephmmorgan on 2017-09-19
Since this happened on more than one machine at approximately the same time, I took a look over the apt history logs on both.  The only thing I found in common (so far) that was installed on both is the linux-headers-generic 4.4.0.93.98.  linux-image-generic also updated on both, but one was to 4.4.0.93.98 and the other to 4.4.0.96.101.

Would these have anything to do with it?

---

### Post by wildmanne39 on 2017-09-19
Originally that was my first thought but the output from the script looks a lot different then it normally does when that is the cause but I think we should find out. Please do:
```
sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms
```
if it does not work reboot.

---

### Post by josephmmorgan on 2017-09-19
I can't tell if it did anything.. I'm still on the wire and will test wireless here in a second.  If it doesn't work, I'll reboot and try wireless again.  Will be back, but wanted you to see the output.

```
josephmmorgan@asus-G73Sw:~$ sudo apt install --reinstall linux-headers-$(uname sudo-r) build-essential
uname: extra operand ‘sudo-r’
Try 'uname --help' for more information.
[sudo] password for josephmmorgan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'linux-headers' can't be removed
The following packages were automatically installed and are no longer required:
  libaudclient2 libid3tag0 libimlib2 libxmmsclient6
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 4,758 B of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu xenial/main amd64 build-essential amd64 12.1ubuntu2 [4,758 B]
Fetched 4,758 B in 0s (25.9 kB/s)           
(Reading database ... 280108 files and directories currently installed.)
Preparing to unpack .../build-essential_12.1ubuntu2_amd64.deb ...
Unpacking build-essential (12.1ubuntu2) over (12.1ubuntu2) ...
Setting up build-essential (12.1ubuntu2) ...

```

---

### Post by wildmanne39 on 2017-09-19
I had to fix that command, I store commands in a file that I use all the time and that one got a little messed up, please run it now that I  edited the post.
Thanks

---

### Post by josephmmorgan on 2017-09-19
Ran it... here's the output.  Still doesn't immediately fix it.  I'll reboot to see if there is any improvement.  In the meantime.. here's the output.

```
josephmmorgan@asus-G73Sw:~$ sudo apt install --reinstall linux-headers-$(uname -r) build-essential dkms
[sudo] password for josephmmorgan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libaudclient2 libid3tag0 libimlib2 libxmmsclient6
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 3 reinstalled, 0 to remove and 0 not upgraded.
Need to get 4,758 B/786 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 build-essential amd64 12.1ubuntu2 [4,758 B]
Fetched 4,758 B in 0s (23.8 kB/s)           
(Reading database ... 280108 files and directories currently installed.)
Preparing to unpack .../build-essential_12.1ubuntu2_amd64.deb ...
Unpacking build-essential (12.1ubuntu2) over (12.1ubuntu2) ...
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11.3_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11.3) over (2.2.0.3-2ubuntu11.3) ...
Preparing to unpack .../linux-headers-4.10.0-35-generic_4.10.0-35.39~16.04.1_amd64.deb ...
Unpacking linux-headers-4.10.0-35-generic (4.10.0-35.39~16.04.1) over (4.10.0-35.39~16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up build-essential (12.1ubuntu2) ...
Setting up dkms (2.2.0.3-2ubuntu11.3) ...
Setting up linux-headers-4.10.0-35-generic (4.10.0-35.39~16.04.1) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.10.0-35-generic /boot/vmlinuz-4.10.0-35-generic
josephmmorgan@asus-G73Sw:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
josephmmorgan@asus-G73Sw:~$ ifconfig
enp5s0    Link encap:Ethernet  HWaddr bc:ae:c5:41:49:5a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3802 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1145 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:655288 (655.2 KB)  TX bytes:150980 (150.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2014 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2014 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:164745 (164.7 KB)  TX bytes:164745 (164.7 KB)

wlp3s0    Link encap:Ethernet  HWaddr 48:5d:60:c8:26:75  
          inet6 addr: fe80::9d61:e4ba:eb0d:b37c/64 Scope:Link
          inet6 addr: 2600:1700:520:c550:37d2:5f1c:eb02:46c0/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4050 errors:0 dropped:785 overruns:0 frame:0
          TX packets:142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:318831 (318.8 KB)  TX bytes:21408 (21.4 KB)
```


**[COLOR=#ff0000]*** Followup - Even after reboot, no joy.  Still not able to get IP or route via wireless.[/COLOR]**

---

### Post by wildmanne39 on 2017-09-19
You are running the 4.10 kernel not the 4.04 like I said this kernel has 2 bugs in it both of them should have been resolved by what I asked you to do already but I believe the extra image package for the kernel is missing, if it is we will install it but you will most likely have to change those settings back to what I had you change them to in the post last night. Please run the command and tell me or post what it says.
```
sudo dpkg -s linux-image-extra-4.10.0-35-generic | grep Status
```

---

### Post by josephmmorgan on 2017-09-19
I now even tried to hard-code an IP4... still no luck.

---

### Post by josephmmorgan on 2017-09-19
Not yet tested... Here is the output:

```
josephmmorgan@asus-G73Sw:~$ sudo dpkg -s linux-image-extra-4.10.0-35-generic | grep Status
[sudo] password for josephmmorgan: 
Status: install ok installed
```

Dropping off the wire and if that doesn't automatically work will reboot off the wire.  Will update after testing.

[B][COLOR=#ff0000]Update:  Still no wireless connection.  Same behavior.

[/COLOR][/B]Just in case it is helpful:

[http://paste.ubuntu.com/25573919/](http://paste.ubuntu.com/25573919/)[B][COLOR=#ff0000]

[/COLOR][/B]

---

### Post by wildmanne39 on 2017-09-19
Reboot your computer and as soon as it starts up start tapping the shift key and enter the grub menu and choose an older kernel that wifi worked on and hit enter.

---

### Post by wildmanne39 on 2017-09-19
I am going to get something to eat, if using an earlier kernel does not work post a fresh script from that kernel so we can see what is going on and please do not make any changes that you are not ask to make it makes it much more difficult to solve your issue.

Thanks

---

### Post by wildmanne39 on 2017-09-19
Did booting an earlier kernel work? your output shows your device is trying to connect to another network, I recommend setting your router to a fixed channel of 6 and not auto.

Has your network name always been all caps and with the dash mark? Ubuntu use to could not connect to an all capital name and special characters should not be used.

---

### Post by josephmmorgan on 2017-09-19
Nothing worked.  I rebooted to several earlier kernel versions, nothing worked.  I am also trying all of this on the other HP machine.. nothing working on that one either.

I'm not changing anything that I'm not changing back.  That is, I'm working through several suggestions from earlier in the thread on each changed configuration to see if there is any combination of them that might work.  So, I'll change network settings, try it, then change them back.  

If you mean UNIFY-LR, then yes, it has always been named that.  But, the ATT4mP7Pyf has always been named that as well.  The UNIFY-LR is relatively new, but if something was wrong with any of them, I suspect I'd have a broader problem.  Right now, only my Ubuntu boxes are affected.

[http://paste.ubuntu.com/25574809/](http://paste.ubuntu.com/25574809/)

---

### Post by wildmanne39 on 2017-09-19
I may see the issue, so many things are possible with the upgrade of the kernel.

Please do:
```
sudo dpkg-reconfigure resolvconf
```
and then answer 'Yes' to the "Prepare /etc/resolv.conf for dynamic updates?" question then reboot.

I started running a 101 fever 2 hours ago so I am not sure how long I can hold out, if someone else sees this thread and wants to jump in that would be great and I will go back to bed.

---

### Post by josephmmorgan on 2017-09-19
Still not solved.  Whatever mucked it up seems to have done so somewhat permanently.  That is, even older kernels didn't solve it, so I'm thinking there's a config file somewhere that changed and it doesn't matter what Kernel is in use.

Either way.. still no route and no IP - But... definitely don't stay on this if you're not well.  I can work off of a wire in the meantime.

```
josephmmorgan@asus-G73Sw:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
josephmmorgan@asus-G73Sw:~$ ifconfig
enp5s0    Link encap:Ethernet  HWaddr bc:ae:c5:41:49:5a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1568 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1568 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:117716 (117.7 KB)  TX bytes:117716 (117.7 KB)

wlp3s0    Link encap:Ethernet  HWaddr 48:5d:60:c8:26:75  
          inet6 addr: fe80::9d61:e4ba:eb0d:b37c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1084 errors:0 dropped:200 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91781 (91.7 KB)  TX bytes:13399 (13.3 KB)

```

---

### Post by wildmanne39 on 2017-09-19
I see when you ran the command to reinstall the kernel that it looked strange the way it showed it and compared it to 16.04 kernel, I am not sure if an upgrade to 16.04.1 added the 4.10  kernel which I do not think it did, I think it was done manually. Little changes can effect linux even though it does not effect windows or android devices because venders make drivers for those devices and linux volunteers have to backwards engineer the drivers to get them to work so compatibility is not always optimal. That is why changes like having an all cap network name or special characters can cause it to stop working. I am going to take a nap and see if I feel better when I wake up.

Good Luck, I hope someone stops by to help but we are down one of our best networking guru's at the moment he just took a month off for vacation.

---

### Post by josephmmorgan on 2017-09-19
I didn't intentionally reinstall the kernel.  I think it must have shown up in my Synaptic updates.  (So.. yes.. I did update, but it wasn't something I sat down with an express intent to do.)

What's interesting is that I tried the older Kernels, and that didn't solve it.  Logic follows, then, that there must be something the newer Kernel (or something else maybe) planted that is separate from the Kernel itself, or there is some way to revert *only* the driver, provided the driver is indeed the issue.

I don't think that I specified before the Kernel versions on the two:

ASUS - Linux 4.10.0-35-generic
HP - Linux 4.4.0-96-generic

In  both machines, I was able to reboot to Linux 4.4.0-93-Generic, which  indeed *was* the last working version, and it didn't work on either.   This is what makes me think it isn't the Kernel or the driver... OR... if it is, then  the newer Kernels planted something that *is not*  reverting when I boot to the earlier version.

Also, I didn't change a network to an all-cap name.  That network was there and my Ubuntu machines were working fine with it (The HP when on 4.4.0.93-Generic and the ASUS when it was on 4.4.0.96-Generic).  Additionally, the other access point, the "ATT4mP7Pyf" has neither all upper case nor a dash, and neither machine will work with that one any more.  The third access point, "mnlinkback" has all lower case and no dashes, and they no longer work with that one either.

Another interesting thing worth noting just in case it helps.  I have the three access points mentioned.  For some reason they seem to be "slaved" to the "UNIFY-LR" network.  As I initially explained, the computers act like they are connected (and indeed may be, but I never get an IP).  That is, they "say" they're connected to the "UNIFY-LR" network.  However, if I switch to either of the other two, the thing tries and tries, but never thinks it connects to the others.  Of course, the attempt eventually fails and the computer attempts other networks (?) until it lands again on the "UNIFY-LR" network, where it says it has connected to it.

So I deleted all wireless connections and shut down the computer.  Then restarted.  I added only the "ATT4mP7Pyf" connection (which is my provider's wireless.. direct to the router/modem).  It is able to detect that the connection needs a password and requests it, but then never makes the connection.   Then I add back "UNIFY-LR".  It asks for the password, and then "says" it is connected.

One more interesting thing.  On the ASUS computer, I keep switching from wired to wireless to test stuff.  Sometimes, when I reconnect the wire, it will say, "Successfully connected to UNIFY-LR" rather than "wired connection 1", which is what it typically says.  I actually have no idea if it was doing that before, but it is of course capturing my attention now.

---

### Post by josephmmorgan on 2017-09-25
*** NOTE - I've been out of town for 4 days and no update on this.  I'm  wondering, now, if there is any theory on why it still didn't work after  rebooting both machines back to 4.4.0-93-Generic. 

I'm adding more to think about.  On the HP, just out of curiosity, I  deleted the "UNIFY-LR" connection completely, then rebooted to  4.4.0.92-Generic.  I also created a new network, simply named "unify",  to which it at least will connect, but won't give me any IP or Internet  access.  It simply will not give an Internet connection with WIFI any  more.  This *was* working before on 4.4.0.92-Generic *and*  4.4.0.93-Generic.  I now have absolutely no doubt this has nothing to do  with the Kernel, as this HP machine has *never* run on the 4.10 Kernel.   Something external to the Kernel has affected these machines.   I'm  certain we're barking up the wrong tree.  We need to look elsewhere.

** Posting this as a reply to try to get some action on it.

---

### Post by josephmmorgan on 2017-09-27
I was searching Synaptic for anything to help with atheros, and I got to thinking... what if I re-install a much earlier Kernel, like 4.4.0.21 and boot to that?

---

### Post by jeremy31 on 2017-09-27
I would search recent updates for anything related to networking

---

### Post by josephmmorgan on 2017-09-27
What's the best way of doing that?  That is, I use Synaptic Package Manager, and everything is up to date.  Even from apt command line, everything appears to be up to date.

Is there some kind of deeper dive?

Or do you mean look at the history log and see what updated that might have been related to networking?   This I have done, and compared the history logs of the two affected machines.  The only thing in common was a Kernel update, but they were two different Kernels.  I was able to boot from the previous Kernels and that didn't solve it, so I suspect it isn't Kernel related.

---

### Post by wildmanne39 on 2017-09-27
I have seen about 4 users with the same issue and all of them had a kernel upgrade and are using one of the kernels that one of your machines is using but I have not found a solution, if I do I will post it here. 

At this time I do not know what is the solution.

---

### Post by josephmmorgan on 2017-09-27
What if we drive from my assumption that the Kernel may not be the real culprit?  That is, maybe some configuration somewhere changed (and I can kick my self for not having a file audit tool running).  I guess I couldn't hope for an easy way to find all network related config files?

---

### Post by wildmanne39 on 2017-09-27
I have looked at all the information from the script, it shows files and configuration of your router almost everything, we can run a few commands and get deeper results to look at for errors, not sure it will help. Reboot then run both of these commands as soon as your computer boots up and post the results here.
```
dmesg | egrep 'ath|firm|wlp|network|wpa'
```
```
sudo cat /var/log/syslog | grep -e ath -e firmware -e wlp -e wpa -e etwork | tail -n50
```

Thanks

---

### Post by josephmmorgan on 2017-09-27
```
josephmmorgan@asus-G73Sw:~$ dmesg | egrep 'ath|firm|wlp|network|wpa'
[    6.623177] systemd[1]: Started Trigger resolvconf update for networkd DNS.
[   21.156953] ath: phy0: Enable LNA combining
[   21.159472] ath: phy0: ASPM enabled: 0x42
[   21.159474] ath: EEPROM regdomain: 0x60
[   21.159474] ath: EEPROM indicates we should expect a direct regpair map
[   21.159476] ath: Country alpha2 being used: 00
[   21.159476] ath: Regpair used: 0x60
[   21.333115] ath9k 0000:03:00.0 wlp3s0: renamed from wlan0
[   26.628240] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   26.644440] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   27.677385] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   55.230417] wlp3s0: authenticate with f0:9f:c2:34:85:43
[   55.244170] wlp3s0: send auth to f0:9f:c2:34:85:43 (try 1/3)
[   55.247240] wlp3s0: authenticated
[   55.251456] wlp3s0: associate with f0:9f:c2:34:85:43 (try 1/3)
[   55.257974] wlp3s0: RX AssocResp from f0:9f:c2:34:85:43 (capab=0x431 status=0 aid=1)
[   55.258178] wlp3s0: associated
[   55.258226] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
josephmmorgan@asus-G73Sw:~$ sudo cat /var/log/syslog | grep -e ath -e firmware -e wlp -e wpa -e etwork | tail -n50
[sudo] password for josephmmorgan: 
Sep 27 20:45:58 asus-G73Sw NetworkManager[937]: <info>  [1506563158.4065] sup-iface[0xa96580,wlp3s0]: config: set interface ap_scan to 1
Sep 27 20:45:58 asus-G73Sw wpa_supplicant[1147]: wlp3s0: SME: Trying to authenticate with f0:9f:c2:34:85:43 (SSID='UNIFY-LR' freq=2437 MHz)
Sep 27 20:45:58 asus-G73Sw kernel: [   55.230417] wlp3s0: authenticate with f0:9f:c2:34:85:43
Sep 27 20:45:58 asus-G73Sw systemd[1810]: Reached target Paths.
Sep 27 20:45:58 asus-G73Sw NetworkManager[937]: <info>  [1506563158.4280] device (wlp3s0): supplicant interface state: inactive -> authenticating
Sep 27 20:45:58 asus-G73Sw kernel: [   55.244170] wlp3s0: send auth to f0:9f:c2:34:85:43 (try 1/3)
Sep 27 20:45:58 asus-G73Sw kernel: [   55.247240] wlp3s0: authenticated
Sep 27 20:45:58 asus-G73Sw wpa_supplicant[1147]: wlp3s0: Trying to associate with f0:9f:c2:34:85:43 (SSID='UNIFY-LR' freq=2437 MHz)
Sep 27 20:45:58 asus-G73Sw NetworkManager[937]: <info>  [1506563158.4362] device (wlp3s0): supplicant interface state: authenticating -> associating
Sep 27 20:45:58 asus-G73Sw kernel: [   55.251456] wlp3s0: associate with f0:9f:c2:34:85:43 (try 1/3)
Sep 27 20:45:58 asus-G73Sw wpa_supplicant[1147]: wlp3s0: Associated with f0:9f:c2:34:85:43
Sep 27 20:45:58 asus-G73Sw kernel: [   55.257974] wlp3s0: RX AssocResp from f0:9f:c2:34:85:43 (capab=0x431 status=0 aid=1)
Sep 27 20:45:58 asus-G73Sw kernel: [   55.258178] wlp3s0: associated
Sep 27 20:45:58 asus-G73Sw kernel: [   55.258226] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
Sep 27 20:45:58 asus-G73Sw NetworkManager[937]: <info>  [1506563158.4472] device (wlp3s0): supplicant interface state: associating -> 4-way handshake
Sep 27 20:45:58 asus-G73Sw wpa_supplicant[1147]: wlp3s0: WPA: Key negotiation completed with f0:9f:c2:34:85:43 [PTK=CCMP GTK=CCMP]
Sep 27 20:45:58 asus-G73Sw wpa_supplicant[1147]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to f0:9f:c2:34:85:43 completed [id=0 id_str=]
Sep 27 20:45:58 asus-G73Sw NetworkManager[937]: <info>  [1506563158.4599] device (wlp3s0): supplicant interface state: 4-way handshake -> completed
Sep 27 20:45:58 asus-G73Sw NetworkManager[937]: <info>  [1506563158.4600] device (wlp3s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'UNIFY-LR'.
Sep 27 20:45:58 asus-G73Sw NetworkManager[937]: <info>  [1506563158.4600] device (wlp3s0): state change: config -> ip-config (reason 'none') [50 70 0]
Sep 27 20:45:58 asus-G73Sw NetworkManager[937]: <info>  [1506563158.4604] dhcp4 (wlp3s0): activation: beginning transaction (timeout in 45 seconds)
Sep 27 20:45:58 asus-G73Sw NetworkManager[937]: <info>  [1506563158.4614] dhcp4 (wlp3s0): dhclient started with pid 1829
Sep 27 20:45:58 asus-G73Sw dhclient[1829]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 3 (xid=0xbade9764)
Sep 27 20:45:59 asus-G73Sw avahi-daemon[915]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fe80::9d61:e4ba:eb0d:b37c.
Sep 27 20:45:59 asus-G73Sw avahi-daemon[915]: New relevant interface wlp3s0.IPv6 for mDNS.
Sep 27 20:45:59 asus-G73Sw avahi-daemon[915]: Registering new address record for fe80::9d61:e4ba:eb0d:b37c on wlp3s0.*.
Sep 27 20:46:01 asus-G73Sw dhclient[1829]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 4 (xid=0xbade9764)
Sep 27 20:46:04 asus-G73Sw bluetoothd[926]: Endpoint registered: sender=:1.73 path=/MediaEndpoint/A2DPSource
Sep 27 20:46:04 asus-G73Sw bluetoothd[926]: Endpoint registered: sender=:1.73 path=/MediaEndpoint/A2DPSink
Sep 27 20:46:05 asus-G73Sw dhclient[1829]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 5 (xid=0xbade9764)
Sep 27 20:46:10 asus-G73Sw dhclient[1829]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 11 (xid=0xbade9764)
Sep 27 20:46:18 asus-G73Sw bluetoothd[926]: Endpoint unregistered: sender=:1.48 path=/MediaEndpoint/A2DPSource
Sep 27 20:46:18 asus-G73Sw bluetoothd[926]: Endpoint unregistered: sender=:1.48 path=/MediaEndpoint/A2DPSink
Sep 27 20:46:19 asus-G73Sw org.freedesktop.fwupd[909]: (fwupd:2325): Fu-WARNING **: Failed to coldplug: UEFI firmware updating not supported
Sep 27 20:46:21 asus-G73Sw dhclient[1829]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 12 (xid=0xbade9764)
Sep 27 20:46:24 asus-G73Sw NetworkManager[937]: <info>  [1506563184.5877] device (wlp3s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Sep 27 20:46:24 asus-G73Sw NetworkManager[937]: <info>  [1506563184.5886] device (wlp3s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Sep 27 20:46:24 asus-G73Sw NetworkManager[937]: <info>  [1506563184.5888] device (wlp3s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 27 20:46:24 asus-G73Sw NetworkManager[937]: <info>  [1506563184.7861] device (wlp3s0): Activation: successful, device activated.
Sep 27 20:46:24 asus-G73Sw systemd[1]: Starting Network Manager Script Dispatcher Service...
Sep 27 20:46:24 asus-G73Sw systemd[1]: Started Network Manager Script Dispatcher Service.
Sep 27 20:46:24 asus-G73Sw nm-dispatcher: req:1 'up' [wlp3s0]: new request (1 scripts)
Sep 27 20:46:24 asus-G73Sw nm-dispatcher: req:1 'up' [wlp3s0]: start running ordered scripts...
Sep 27 20:46:33 asus-G73Sw dhclient[1829]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 10 (xid=0xbade9764)
Sep 27 20:46:43 asus-G73Sw dhclient[1829]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 14 (xid=0xbade9764)
Sep 27 20:46:44 asus-G73Sw NetworkManager[937]: <warn>  [1506563204.1437] dhcp4 (wlp3s0): request timed out
Sep 27 20:46:44 asus-G73Sw NetworkManager[937]: <info>  [1506563204.1438] dhcp4 (wlp3s0): state changed unknown -> timeout
Sep 27 20:46:44 asus-G73Sw NetworkManager[937]: <info>  [1506563204.1603] dhcp4 (wlp3s0): canceled DHCP transaction, DHCP client pid 1829
Sep 27 20:46:44 asus-G73Sw NetworkManager[937]: <info>  [1506563204.1604] dhcp4 (wlp3s0): state changed timeout -> done
Sep 27 20:47:33 asus-G73Sw systemd[1210]: Stopped target Paths.
```

---

### Post by josephmmorgan on 2017-09-27
Sorry for 2 posts, but on the above one, I forgot to unplug the wire.  So the above one is when a cable is connected.  This one, I shut down, unplugged the wire, then started up, ran the two commands, and then plugged in the wire:

```

josephmmorgan@asus-G73Sw:~$ dmesg | egrep 'ath|firm|wlp|network|wpa'
[   20.276906] ath: phy0: Enable LNA combining
[   20.279475] ath: phy0: ASPM enabled: 0x42
[   20.279476] ath: EEPROM regdomain: 0x60
[   20.279477] ath: EEPROM indicates we should expect a direct regpair map
[   20.279478] ath: Country alpha2 being used: 00
[   20.279478] ath: Regpair used: 0x60
[   20.403185] ath9k 0000:03:00.0 wlp3s0: renamed from wlan0
[   25.467990] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   25.482996] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   26.947568] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[  149.960971] wlp3s0: authenticate with f0:9f:c2:34:85:43
[  149.980009] wlp3s0: send auth to f0:9f:c2:34:85:43 (try 1/3)
[  149.983096] wlp3s0: authenticated
[  149.983954] wlp3s0: associate with f0:9f:c2:34:85:43 (try 1/3)
[  149.990356] wlp3s0: RX AssocResp from f0:9f:c2:34:85:43 (capab=0x431 status=0 aid=1)
[  149.990515] wlp3s0: associated
[  149.990551] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[  194.966595] wlp3s0: deauthenticating from f0:9f:c2:34:85:43 by local choice (Reason: 3=DEAUTH_LEAVING)
[  196.032595] wlp3s0: authenticate with f0:9f:c2:34:85:43
[  196.052079] wlp3s0: send auth to f0:9f:c2:34:85:43 (try 1/3)
[  196.055119] wlp3s0: authenticated
[  196.055982] wlp3s0: associate with f0:9f:c2:34:85:43 (try 1/3)
[  196.060583] wlp3s0: RX AssocResp from f0:9f:c2:34:85:43 (capab=0x431 status=0 aid=1)
[  196.060740] wlp3s0: associated
josephmmorgan@asus-G73Sw:~$ sudo cat /var/log/syslog | grep -e ath -e firmware -e wlp -e wpa -e etwork | tail -n50
[sudo] password for josephmmorgan: 
Sep 27 20:55:02 asus-G73Sw wpa_supplicant[1158]: wlp3s0: Associated with f0:9f:c2:34:85:43
Sep 27 20:55:02 asus-G73Sw NetworkManager[953]: <info>  [1506563702.2941] device (wlp3s0): supplicant interface state: authenticating -> associating
Sep 27 20:55:02 asus-G73Sw kernel: [  196.060583] wlp3s0: RX AssocResp from f0:9f:c2:34:85:43 (capab=0x431 status=0 aid=1)
Sep 27 20:55:02 asus-G73Sw kernel: [  196.060740] wlp3s0: associated
Sep 27 20:55:02 asus-G73Sw NetworkManager[953]: <info>  [1506563702.2995] device (wlp3s0): supplicant interface state: associating -> 4-way handshake
Sep 27 20:55:02 asus-G73Sw wpa_supplicant[1158]: wlp3s0: WPA: Key negotiation completed with f0:9f:c2:34:85:43 [PTK=CCMP GTK=CCMP]
Sep 27 20:55:02 asus-G73Sw wpa_supplicant[1158]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to f0:9f:c2:34:85:43 completed [id=0 id_str=]
Sep 27 20:55:02 asus-G73Sw NetworkManager[953]: <info>  [1506563702.3062] device (wlp3s0): supplicant interface state: 4-way handshake -> completed
Sep 27 20:55:02 asus-G73Sw NetworkManager[953]: <info>  [1506563702.3063] device (wlp3s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'UNIFY-LR'.
Sep 27 20:55:02 asus-G73Sw NetworkManager[953]: <info>  [1506563702.3064] device (wlp3s0): state change: config -> ip-config (reason 'none') [50 70 0]
Sep 27 20:55:02 asus-G73Sw NetworkManager[953]: <info>  [1506563702.3067] dhcp4 (wlp3s0): activation: beginning transaction (timeout in 45 seconds)
Sep 27 20:55:02 asus-G73Sw NetworkManager[953]: <info>  [1506563702.3078] dhcp4 (wlp3s0): dhclient started with pid 2677
Sep 27 20:55:02 asus-G73Sw dhclient[2677]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 3 (xid=0x15624f13)
Sep 27 20:55:03 asus-G73Sw avahi-daemon[980]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fe80::9d61:e4ba:eb0d:b37c.
Sep 27 20:55:03 asus-G73Sw avahi-daemon[980]: New relevant interface wlp3s0.IPv6 for mDNS.
Sep 27 20:55:03 asus-G73Sw avahi-daemon[980]: Registering new address record for fe80::9d61:e4ba:eb0d:b37c on wlp3s0.*.
Sep 27 20:55:05 asus-G73Sw dhclient[2677]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 4 (xid=0x15624f13)
Sep 27 20:55:09 asus-G73Sw dhclient[2677]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 8 (xid=0x15624f13)
Sep 27 20:55:10 asus-G73Sw NetworkManager[953]: <info>  [1506563710.7711] device (wlp3s0): state change: ip-config -> ip-check (reason 'none') [70 80 0]
Sep 27 20:55:10 asus-G73Sw NetworkManager[953]: <info>  [1506563710.7731] device (wlp3s0): state change: ip-check -> secondaries (reason 'none') [80 90 0]
Sep 27 20:55:10 asus-G73Sw NetworkManager[953]: <info>  [1506563710.7735] device (wlp3s0): state change: secondaries -> activated (reason 'none') [90 100 0]
Sep 27 20:55:10 asus-G73Sw NetworkManager[953]: <info>  [1506563710.7736] manager: NetworkManager state is now CONNECTED_LOCAL
Sep 27 20:55:10 asus-G73Sw NetworkManager[953]: <info>  [1506563710.8790] manager: NetworkManager state is now CONNECTED_GLOBAL
Sep 27 20:55:10 asus-G73Sw NetworkManager[953]: <info>  [1506563710.8791] policy: set 'UNIFY-LR' (wlp3s0) as default for IPv6 routing and DNS
Sep 27 20:55:10 asus-G73Sw NetworkManager[953]: <info>  [1506563710.8792] dns-plugin[0x271a4d0]: starting dnsmasq...
Sep 27 20:55:10 asus-G73Sw NetworkManager[953]: <info>  [1506563710.8806] dns-mgr: Writing DNS information to /sbin/resolvconf
Sep 27 20:55:10 asus-G73Sw NetworkManager[953]: <info>  [1506563710.9008] device (wlp3s0): Activation: successful, device activated.
Sep 27 20:55:10 asus-G73Sw systemd[1]: Starting Network Manager Script Dispatcher Service...
Sep 27 20:55:10 asus-G73Sw whoopsie[1344]: [20:55:10] The default IPv6 route is: /org/freedesktop/NetworkManager/ActiveConnection/1
Sep 27 20:55:10 asus-G73Sw whoopsie[1344]: [20:55:10] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/1
Sep 27 20:55:10 asus-G73Sw whoopsie[1344]: [20:55:10] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/1
Sep 27 20:55:10 asus-G73Sw systemd[1]: Started Network Manager Script Dispatcher Service.
Sep 27 20:55:10 asus-G73Sw nm-dispatcher: req:1 'up' [wlp3s0]: new request (1 scripts)
Sep 27 20:55:10 asus-G73Sw nm-dispatcher: req:1 'up' [wlp3s0]: start running ordered scripts...
Sep 27 20:55:10 asus-G73Sw NetworkManager[953]: <info>  [1506563710.9607] dnsmasq[0x271a4d0]: dnsmasq appeared as :1.95
Sep 27 20:55:10 asus-G73Sw dnsmasq[2700]: using nameserver 2600:1700:520:c550::1#53(via wlp3s0)
Sep 27 20:55:12 asus-G73Sw avahi-daemon[980]: Leaving mDNS multicast group on interface wlp3s0.IPv6 with address fe80::9d61:e4ba:eb0d:b37c.
Sep 27 20:55:12 asus-G73Sw avahi-daemon[980]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address 2600:1700:520:c550:37d2:5f1c:eb02:46c0.
Sep 27 20:55:12 asus-G73Sw avahi-daemon[980]: Registering new address record for 2600:1700:520:c550:37d2:5f1c:eb02:46c0 on wlp3s0.*.
Sep 27 20:55:12 asus-G73Sw avahi-daemon[980]: Withdrawing address record for fe80::9d61:e4ba:eb0d:b37c on wlp3s0.
Sep 27 20:55:17 asus-G73Sw dhclient[2677]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 7 (xid=0x15624f13)
Sep 27 20:55:24 asus-G73Sw dhclient[2677]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 12 (xid=0x15624f13)
Sep 27 20:55:36 asus-G73Sw dhclient[2677]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 10 (xid=0x15624f13)
Sep 27 20:55:46 asus-G73Sw dhclient[2677]: DHCPDISCOVER on wlp3s0 to 255.255.255.255 port 67 interval 9 (xid=0x15624f13)
Sep 27 20:55:47 asus-G73Sw NetworkManager[953]: <warn>  [1506563747.1621] dhcp4 (wlp3s0): request timed out
Sep 27 20:55:47 asus-G73Sw NetworkManager[953]: <info>  [1506563747.1623] dhcp4 (wlp3s0): state changed unknown -> timeout
Sep 27 20:55:47 asus-G73Sw NetworkManager[953]: <info>  [1506563747.1789] dhcp4 (wlp3s0): canceled DHCP transaction, DHCP client pid 2677
Sep 27 20:55:47 asus-G73Sw NetworkManager[953]: <info>  [1506563747.1790] dhcp4 (wlp3s0): state changed timeout -> done
Sep 27 20:57:56 asus-G73Sw gnome-session[1950]: Full message: TypeError: NetworkError when attempting to fetch resource.
Sep 27 20:58:19 asus-G73Sw NetworkManager[953]: <warn>  [1506563899.7796] device (wlp3s0): activation-stage: schedule activate_stage5_ip6_config_commit,10 which replaces activate_stage5_ip6_config_commit,10 (id 1715 -> 1717)

```

---

### Post by wildmanne39 on 2017-09-28
Please run this command one line at a time and see if that help:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

The information shows it connected to IPV6 but linux does not work well with IPV6 you need to set it to ignore like in the screenshots I posts early on.

If it does not connect please post a new file from the wireless script.

Thanks

---

### Post by josephmmorgan on 2017-09-28
Here is the output of the above commands (that we did try before but didn't seem to work).  I'll edit this post after I get back on.

```
josephmmorgan@asus-G73Sw:~$ echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
[sudo] password for josephmmorgan: 
options ath9k nohwcrypt=1
josephmmorgan@asus-G73Sw:~$ sudo modprobe -rfv ath9k
rmmod ath9k
rmmod mac80211
rmmod ath9k_common
rmmod ath9k_hw
rmmod ath
rmmod cfg80211
josephmmorgan@asus-G73Sw:~$ sudo modprobe -v ath9k
insmod /lib/modules/4.10.0-35-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.10.0-35-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko 
insmod /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko 
insmod /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1
```

---

### Post by wildmanne39 on 2017-09-28
I went through this whole thread we did not try this set of commands.  I do not think it will work but you are having issues that use to be solved with the above commands and maybe the driver got broken and needs this parameter again.

---

### Post by josephmmorgan on 2017-09-28
[http://paste.ubuntu.com/25634599/](http://paste.ubuntu.com/25634599/)

I must have come across that somewhere else and tried it.  When it didn't work, I reverted.

It is back to endlessly scanning.  Every minute or so I get a popup saying "Disconnected Wireless network".

---

### Post by wildmanne39 on 2017-09-28
Let's revert the changes from the last command:
```
sudo rm /etc/modprobe.d/ath9k.conf
```
Reboot.

---

### Post by josephmmorgan on 2017-09-28
Done.  Rebooted.

[http://paste.ubuntu.com/25634714/](http://paste.ubuntu.com/25634714/)

And it is still endlessly scanning.  I can get the endless scanning to stop by *not* ignoring IPV6 in the wireless settings for the access point. 

*One other note... and this might help.  My daughter came by.  Her new company laptop is a Windows 10 machine (whereas he previous one was Windows 7).  This new Windows 10 machine won't connect to the "UNIFY-LR" or the "unify" (the new network I created to attempt to resolve the all-caps-special-character potential issue).  The Windows 10 will connect to my "ATT4mP7Pyf" just fine.   Android and Apple devices still connect to all just fine, and Windows 7 still connecting just fine.  Just thought that might be relevant.*

---

### Post by wildmanne39 on 2017-09-28
I would connect to the router/modem and bypass the AP's and see it that works.

---

### Post by josephmmorgan on 2017-09-28
Not sure I'm understanding.  Connect directly to the wireless of the router/modem?  If so, that is the "ATT4mP7Pyf" I've been referring to.  That is the one direct to the AT&T router.  No switches or access points in between. Since the wirelss on my Ubuntu's went south, I haven't been able to connect to anything wireless, direct or otherwise.

---

### Post by wildmanne39 on 2017-09-28
I have asked a friend to take a log and help since he is online, hopefully he has the time.

---

### Post by jeremy31 on 2017-09-28
Can you change the encryption on ATT4mP7Pyf so that it is WPA2 only with no TKIP?  I haven't had much luck with my Atheros wifi card when TKIP is present

---

### Post by josephmmorgan on 2017-09-28
Attempted, but no joy, and it isn't a surprise.  Also, it was working fine on two different laptops up until a little more than a week ago without any issues on the previous encryption.  When I setup the "unify" network during the many efforts on this thread (based upon the theory that "UNIFY-LR" was both all caps *and* had a dash in it might have something to do with it), I played with that one a bit.  It is currently set to AES/CCMP only, and no luck there either.

---

### Post by jeremy31 on 2017-09-28
Have you rebooted your routers since the problem started?  I may have missed it as the thread has 52 posts now and some are long.  I have all the updates installed on my laptop with the Atheros Ar9485 wifi and it still works so I can't be sure what the cause of the problem is.  Do you still have the ISO on USB/DVD to see if it still works?

---

### Post by josephmmorgan on 2017-09-28
Well, after a couple of various orders of restarts, I at least have a wireless connection to the ATT4mP7Pyf router on both machines.  Neither machine will now connect to the Ubiquity Unify access point, but that is a matter for Ubiquity to explain.

I can't believe it was this silly.  I've never had to explicitly restart that router for wireless issues in the two years or so I've had it.  

Thanks at least for this much.  I'll reset my Unify connections back to the way they were, except I'll keep the Google DNS settings and play with the IPv6 Ignore a bit longer.

Thanks both of you for your patience and diligence.  Still can't explain why my phones, apple devices, and older windows machines didn't have an issue.

---

### Post by wildmanne39 on 2017-09-29
I am glad they are working. Linux is more sensitive because vender's do not write drivers for linux to use with there devices, volunteers have to backwards engineer them.

---

### Post by praseodym on 2017-09-29
You can look into the router interface how long the IP address is saved there, maybe 1 or 2 years?! Other settings there can also help stabilizing, like WPA2-AES (CCMP), bandwidth of 20 MHz instead of 20/40 and a fixed channel. You can use the program LinSSID to check where the least interferences are

---

### Post by josephmmorgan on 2017-09-29
I understand that, but, would the drivers have changed simply because the Kernel updated?  That is, the Atheros drivers are baked into the Kernel (have been for some time).  Is there a way for me to tell if the drivers were updated for a Kernel (without scanning the source code)?

---

### Post by josephmmorgan on 2017-09-29
> **praseodym said:**
> You can look into the router interface how long the IP address is saved there, maybe 1 or 2 years?! Other settings there can also help stabilizing, like WPA2-AES (CCMP), bandwidth of 20 MHz instead of 20/40 and a fixed channel. You can use the program LinSSID to check where the least interferences are

So, if the IP did change on the router, why would that have affected *only* Ubuntu machines?  I don't have the IP hard-coded.

Another interesting thing is, one of the networks the Ubuntu machines can't connect to is using WPA2-AES (CCMP).

---

