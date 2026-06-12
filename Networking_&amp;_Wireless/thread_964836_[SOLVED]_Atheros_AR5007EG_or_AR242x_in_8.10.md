---
title: "[SOLVED] Atheros AR5007EG or AR242x in 8.10"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by Malet on 2008-10-31
Here's the solutions (although both give inconsistent connections):
[LIST=1]
[*]You can try the **linux-backports-modules-intrepid** method outlined here [http://ubuntuforums.org/showpost.php?p=6089169&postcount=3](http://ubuntuforums.org/showpost.php?p=6089169&postcount=3) which people have said is a better connection, but you'll need to reload the driver every time you log in.
**OR**
[*]Compile latest ath5k driver:
[LIST][*]Download the package at [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)
[*]Use file-roller (or similar) to extract the source.
[*]Move to the directory you extracted in terminal.
[*]paste this into terminal:
```
make
sudo make install
sudo make unload
sudo make load
```
[/LIST]
[/LIST]
If you have problems and need **to uninstall** you can do:
```
sudo make unload
sudo make uninstall
```
in the source directory.

---

### Post by Malet on 2008-10-31
See above post

---

### Post by tednugent68 on 2008-10-31
hey i have an acer laptop with a atheros wireless card and i can't seem to get mine to work either. did you do this in terminal?

---

### Post by Malet on 2008-10-31
Putting that in terminal should work - Apparently ath5k was included in 8.10 but just disabled by default so there's probably a much easier way of doing this.

---

### Post by tednugent68 on 2008-10-31
when i get to your cd compat-wireless-2.6 it says No such file or directory then when i do the sudu make install i get make: *** No rule to make target `install'.  Stop.

---

### Post by Malet on 2008-10-31
Ok I think I've fixed it now - although the folder name will probably change.
it should have been ```
cd compat-wireless-2008-10-31
```

---

### Post by H-N7 on 2008-10-31
I have the same card but haven't upgraded yet (still downloading :D ).
Thanks for posting your solution. The problem is mentioned in the Release Notes [Here](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default).
So, installing *linux-backports-modules-intrepid-generic* should solve it. If not, your solution will become handy ;) .

---

### Post by -X- on 2008-10-31
Thanks! It looks messy but it works. Installing the backports didn't work for me but this did.

---

### Post by KermitJr on 2008-10-31
If you goto the wireless.kernel.org website, it says they have blocked direct downloads from things such as wget if you don't get a dated file. So use a browser and goto:

[http://wireless.kernel.org/download](http://wireless.kernel.org/download) 

and download it via web browser.

But for the record, I stuck in the CD, enabled it (You have to enable it in software sources or repositories or it won't work), reloaded, installed linux-backports-modules-intrepid-generic and rebooted and it automagically worked.

So if you had trouble with the backports method, make sure you're enabling and reloading or it won't work.

Cheers,
KermitJr

---

### Post by FunteX on 2008-10-31
> **Malet said:**
> I've now got it working!!! :) for anyone with similar problems here's what I did:

```

wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2008-10-31
make
sudo make install
sudo make unload
sudo make load

```

Then reboot and it should be working in network-manager :D

I can confirm that this approach works very well for getting wireless connection to work on the Fujitsu Siemens Esprimo Mobile v5535

Good work :)

---

### Post by GoldNugget on 2008-10-31
This fix also worked for me, running an Asus eee pc. This machine has been running Intrepid since Alpha 4. The wireless started working flawlessly in Alpha 5 and just quit with a recent kernel update. 
I tried installing the backport modules, as suggested in another post, but it did not work for me. Installing the compat-wireless module as suggested above (one line at a time in a terminal) finally worked for me.
Thanks!

---

### Post by JoshEngleman on 2008-10-31
I did everything mentioned here and I now can view my wireless network. However, when I am connected, the speed is horrible. It feels like I'm using a 56k modem. Is anyone else having the same issue after doing this?

---

### Post by MrGreen on 2008-11-01
After upgrading to Ibex wireless worked out of the box.... then updated system wifi was gone ;-( 

Using above it now works again :-) .....

Hopefully a bug will be made and others will not get caught out

Thanks for sharing

MrG

---

### Post by salwator on 2008-11-01
WOW, it works great.

THANKS!! :)

---

### Post by aweller on 2008-11-01
Great, with a manual download (as opposed wget), this seems to have worked for me too (Compaq Presario C793VU).

However, wireless seems a little jerky when compared to wired...

Is there a chance that what's needed ("compat...") is going to be included in the repos at some point?

---

### Post by alex-debian on 2008-11-01
On my Thinkpad T60 this solution is not working. Any ideas, how I can install correct driver?

---

### Post by &#1587;&#1604;&#1605;&#1575;&#1606; &#1575;&#1604;&#1587;&#1576;&#1610;&#1593;&#1610; on 2008-11-01
I can confirm that this approach works very well for getting wireless connection to work on the Fujitsu Siemens Esprimo Mobile v5535

Good work 


---------------------------------------------

ME TOO SAME LABTOP AND WORKING

BUT ITS SUCKS VERY SLOW AND SOME TIME SAYING "CHECK YOUT CONNECTION" 

I MEAN EVERY 4 MINUTE


SO WHAT IS WRONG HOW CAN I FIX IT ?? MAKE IT WORK PROPPLEY .

---

### Post by yamagami on 2008-11-01
This did not work for me either on Thinkpad T61p. 
I got the driver to load but could not connect to a wpa network. I tried to compile wpa_supplicant from source (latest version) but i couldn't get it to config against ath5 as it only had Madwifi option, and puthing ath5 source dir in the .config file did not work. 
What did work, eventually, is going back to madwifi/wpa_supplicant. 
I had the same problem in hardy where EVERY time i updated my kernel i had to recompile both madwifi and wpa_supplicant from source. I had a shell script to do it so it became a habit, but needless to say - this is wrong. wifi should be the first think to work...
Anyway -  get madwifi source from svn (see madwifi.org site). Then download latest source for wpa_supplicant. 
config wpa_supplicant by creating a .config file:
from wpa_supplicant dir:
cp defconfig .config
edit the .config file, search for MADWIFI and uncomment the 2 madwifi lines. you will need to point wpa_supplicant to the madwifi source dir. 

now compile madwifi (make; sudo make install) then 
compile wpa_supplicant (make; sudo make install). 

last:
sudo modprobe -r ath_pci
sudo modprobe ath_pci

i then rebooed and here i am - online and posting this post ;o)

Harel

---

### Post by Datoyminaytah on 2008-11-01
Thanks! This worked great! As soon as I rebooted and logged in, a notification box popped up saying wireless networks were available. It even auto-detected WPA/WPA2 security!

---

### Post by rvanscherpe on 2008-11-01
I just wanted to say that I have an Acer Aspire One and installed Intrepid.  The wireless did not work out of the box.  I performed the instructions that were provided on this thread and it worked!  The only thing that is missing is the wireless LED does not seem to work.  Minor issue. The main issue has been resolved.  I'm online wirelessly!  Thanks a bunch!

Ron.

---

### Post by ElementalDragon on 2008-11-01
Well... i'm assuming this is talking about 802.11n wireless networks, which i think is kinda funny.  Ran the desktop version of the disc so i could just boot and run Ubuntu from the CD to test it out on my somewhat aging laptop with a D-Link DWA-652 Xtreme-N card.  Went into the network manager and set up a wireless network.  put in the SSID of my wireless network, and saved the settings, and it the wireless worked.  Granted, the Link light sat there and blinked slowly as if it were looking for a connection, and the activity light didn't blink at all... but there isn't any other form of wireless connection on the laptop, and there isn't any network cable attached directly to it, and i was able to search google for stuff and go to other websites.

---

### Post by jTips on 2008-11-01
The process outlined in this thread is confirmed working on Compaq C768TU! :)

Thanks.

---

### Post by Spartacus84 on 2008-11-02
I have a Compaq Presario f756nr, and this did not quite work for me. I got no error messages while installing the driver, but when I try to connect to my WPA2 encrypted network, it tries to connect for a few seconds, and then asks for the password again, never actually connecting. Anybody know what's wrong?

---

### Post by eks on 2008-11-02
Another approach, without installing the modules manually, is to check that ath5k is NOT blacklisted anywhere on any /etc/modprobe.d/ file.

If you install the backports-modules package and wifi still does not work it's probably because you have ath5k blacklisted somewhere. 

I have outlined the steps to do this with more detail here: [http://ubuntuforums.org/showpost.php?p=6089169&postcount=3](http://ubuntuforums.org/showpost.php?p=6089169&postcount=3)

---

### Post by rblevitt on 2008-11-02
Looks like things are moving in the right direction.  Now if they can get the Atheros 5K to work straight out of the box, I wouldn't have half the headaches I've outlined in the next message.

*R. Levitt*

---

### Post by rblevitt on 2008-11-02
> **Malet said:**
> I've now got it working!!! :) for anyone with similar problems here's what I did:

```

wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2008-10-31
make
sudo make install
sudo make unload
sudo make load

```

Then reboot and it should be working in network-manager :D

When I typed in the last two instructions--"sudo make unload", then "sudo make load"--I got a message about needing to be root. I also got a message about only needing to enter "make unload" and then "make load". However, the procedure did work on my machine--a Compaq C751NR--for the most part. The only fly in the ointment is that I have to go into System/Administration/Hardware Drivers and first inactivate and then reactivate the Atheros 5K driver in order to get wifi up and running. Any ideas about how to fix this bug?

*R. Levitt*

---

### Post by Mnemonic Device on 2008-11-02
> **Malet said:**
> I've now got it working!!! :) for anyone with similar problems here's what I did:

```

wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-2008-10-31
make
sudo make install
sudo make unload
sudo make load

```

Then reboot and it should be working in network-manager :D

Thanks much! This works on my eee PC 900, BUT I'm noticing a lot of slowdown, and intermittent dropouts. 

For example, I'm downloading Open Office 3 right now and I've watched the time remaining jump from 17 minutes remaining to 3 days and back to 8 minutes. Then I see "time remaining unknown." 

I'm pretty sure it's not an Open Office server issue since I saw the same behavior when the automatic updates were running. 

Everything else I've got on the same router is happy and chuging along normally. 

Any thoughts?

---

### Post by Datoyminaytah on 2008-11-02
The only problem I'm having now is that it seems to be much slower and less reliable than when I run Vista that came pre-installed on the laptop. Are there any settings that could help this? I went to an internet speed test website in both wired and wireless mode, and in wireless mode the speed test showed bursts of data followed by long periods of nothing. I'll have to try it in Vista and write down the numbers, but I think it was at least twice as fast as what's working now in Ubuntu.

---

### Post by banana jama on 2008-11-02
it's not working for me this is what i get when i enter the command. > akeem@akeem-laptop:~$ wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2)
--2008-11-02 17:13:17--  [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2)
Resolving wireless.kernel.org... 83.246.72.84
Connecting to wireless.kernel.org|83.246.72.84|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1522534 (1.5M) [application/octet-stream]
Saving to: `compat-wireless-2008-10-31.tar.bz2'

100%[======================================>] 1,522,534    576K/s   in 2.6s    

2008-11-02 17:13:21 (576 KB/s) - `compat-wireless-2008-10-31.tar.bz2' saved [1522534/1522534]

akeem@akeem-laptop:~$ tar jxvf compat-wireless-2.6.tar.bz2
tar: compat-wireless-2.6.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
akeem@akeem-laptop:~$ cd compat-wireless-2008-10-31
bash: cd: compat-wireless-2008-10-31: No such file or directory
akeem@akeem-laptop:~$ make
make: *** No targets specified and no makefile found.  Stop.
akeem@akeem-laptop:~$ sudo make install
[sudo] password for akeem: 
make: *** No rule to make target `install'.  Stop.
akeem@akeem-laptop:~$ 



---

### Post by warped6 on 2008-11-02
Excellent! I can now use the native driver and not the Winblows one. Thanks eks!

---

### Post by Mnemonic Device on 2008-11-02
> **Datoyminaytah said:**
> The only problem I'm having now is that it seems to be much slower and less reliable than when I run Vista that came pre-installed on the laptop. Are there any settings that could help this? I went to an internet speed test website in both wired and wireless mode, and in wireless mode the speed test showed bursts of data followed by long periods of nothing. I'll have to try it in Vista and write down the numbers, but I think it was at least twice as fast as what's working now in Ubuntu.

Yep, same wireless results here. It's like someone is turning the internet faucet on and off at random. Every other machine on my network is fine, so I know it's something to do with this machine.

---

### Post by Malet on 2008-11-02
> **banana jama said:**
> it's not working for me this is what i get when i enter the command.

I've updated my post - it should work now

---

### Post by lakour on 2008-11-02
when I type wget and the url you provided it will not allow to conect....maybe thats only temporarily but in the mean time I used another way

**1)**Choose which kernel
You can compat-wireless for kernels >= **2.6.27 **here:

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

You can download compat-wireless for kernels <= **2.6.26** here:

[http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-old.tar.bz2)

when you choose one of those then
**2)**

wget space and the link


Extract the content of the package:

[SIZE="4"]tar jxvf compat-wireless-(here goes the date of the package I used 2008-10-31).tar.bz2[/SIZE]
example: tar jxvf compat-wireless-2008-10-31.tar.bz2 



**3)**Build the latest Linux wireless subsystem:

cd compat-wireless-(the date again like in the example above)
make

Install:

They use the updates/ directory so your distribution's drivers are left intact.

sudo make install

Then type this in order to replace the old drivers with the new ones
sudo make unload

sudo make load


*This way you don't need to uninstall madwifi and can comeback to your previous drivers without much hassle...here is a [link]("http://wireless.kernel.org/en/users/Download")for more info..I think there is even a link for a driver released today 2 nov..but I will stick with these one for now.

This worked for my Toshiba a215-s4807 with atheros AR5007EG while its making the install It might say about some errors but don't seam to affect the final installation reboot and thats it

---

### Post by refractal on 2008-11-02
Confirmed to work for Compaq C751NR, the speed of the connection is terrible, however. 

Had to do a complete power down for networks to show up.

---

### Post by Mnemonic Device on 2008-11-03
> **Malet said:**
> I've now got it working!!! :) for anyone with similar problems here's what I did:

```

wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2008-10-31.tar.bz2
tar jxvf compat-wireless-2008-10-31.tar.bz2
cd compat-wireless-2008-10-31
make
sudo make install
sudo make unload
sudo make load

```

Then reboot and it should be working in network-manager :D


Being the Linux noob that I am, and interested in learning -- how would I go about undoing this now that I've done it?

---

### Post by Malet on 2008-11-03
> **Mnemonic Device said:**
> Being the Linux noob that I am, and interested in learning -- how would I go about undoing this now that I've done it?

I think it's just:
```
sudo make uninstall
```

---

### Post by audiobreather on 2008-11-04
Just wanna say THANK YOU VERY MUCH to Malet! This fix worked on my Atheros AR242x on Acer Aspire 5220! Good job! Ubuntu rocks!

---

### Post by BoyBlunder on 2008-11-04
I have tried all of the steps above and still have no wireless connectivity (the card is detected though).

Does anyone else have any idea as to what else to do? Can I uninstall linux-backports-modules-intrepid-generic and reinstall it without messing anything up?

---

### Post by lavikl on 2008-11-04
I confirm this works on LG R405 laptop. 
I used the 2008.11.4 tar file.
As previously reported, data transfer is a bit flaky.

thanks for the solution !

---

### Post by toddedw on 2008-11-04
Installing linux-backports-modules-intrepid-generic by itself doesn't actually enable it. In order to enable it you have to go to System -> Administration -> Hardware Drivers

Make sure that:

1.) Support for Atheros 802.11 wireless LAN cards is Disabled.
2.) Support for 5xxx series of Atheros 802.11 wireless LAN cards is Enabled.

This method works and it works well with less signal loss than the other method however, it stops working after each reboot. After I reboot the Driver Manager claims that 5xxx series module (ath5k) is enabled, but in order to get wireless connectivity I have to go into the Driver Manager, disabled it, and then enable it. Then I have wireless. 

Can anyone tell me how to make my system load the ath5k module at boot time?

---

### Post by eks on 2008-11-04
> **toddedw said:**
> Can anyone tell me how to make my system load the ath5k module at boot time?

Try checking it's not being blacklisted on any file on /etc/modprobe.d/ directory. See here for more information on that:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

If you installed the driver manually they probably blacklist ath5k (the one on the backports-modules), to not cause any conflict. You might have to take that blacklisting manually. It's just commenting one line anyway, mine was on /etc/modprobe.d/madwifi

Malet, you could also update your first post with this other solution, so it's more complete.

---

### Post by amd is the best on 2008-11-05
This procedure worked perfect on my HP DV6000 (DV6768SE) to get a wireless connection, although mine as well is having the intermittent connection issues.

Any updates on this issue?

Nick

---

### Post by efledderman on 2008-11-05
> **FunteX said:**
> I can confirm that this approach works very well for getting wireless connection to work on the Fujitsu Siemens Esprimo Mobile v5535

Good work :)

This worked great for my Atheros card, however my wireless connectiong seems to get slower over time.  After about 15-20 minutes I'm at about dial-up speeds, sometimes even much slower.  This machine is dual booted with with Windows, and the internet is blazing when booted into Windows, so it's definently not the network...

I'm thinking something with drivers, but I'm very new too Ubuntu, and even Linux for that matter.

Any ideas?

---

### Post by aweller on 2008-11-05
Although this method worked, I was really unhappy with the speed of my connection.  It kept dropping out, etc, when it was working fine before in 8.04.  I can confirm that I get better speeds with this method:

[http://ubuntuforums.org/showthread.php?t=967520]("http://ubuntuforums.org/showthread.php?t=967520")

---

### Post by toddedw on 2008-11-05
> **eks said:**
> Try checking it's not being blacklisted on an file on /etc/modprobe.d/ directory. See here for more information on that:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

If you installed the driver manually they probably blacklist ath5k (the one on the backports-modules), to not cause any conflict. You might have to take that blacklisting manually. It's just commenting one line anyway, mine was on /etc/modprobe.d/madwifi

Inside of /etc/modprobe.d/madwifi:
[INDENT]## ath5k (mac80211)
blacklist ath5k
[/INDENT]
I commented that blacklist ath5k line and everything works at boot. Thanks so much.

Edit:
I made a thread with the information I used to fix my 5007. You can find it [here]("http://ubuntuforums.org/showthread.php?t=969306").

---

### Post by tim183 on 2008-11-06
I have an HP dv6700 with atheros ar5007eg.

The compat wireless method worked for me in intrepid, BUT only to the stage where I can see the wireless network, but I can't connect to my home network which is an open network.

I also had a similar experience with the old ndiswrapper method on hardy and also with madwifi on hardy. it makes me think there is something wrong with my network configuration or something?

can someone please try and help me with this?

---

### Post by eks on 2008-11-06
> **tim183 said:**
> can someone please try and help me with this?

You can do a "dmesg | grep ath" and posts the results. Just FYI, [dmesg]("http://en.wikipedia.org/wiki/Dmesg") is kind of a boot up log, so you can review what went wrong (or right) during boot up procedure. | grep ath tells to just show messages containing ath, which is probably where your problem is.

---

### Post by Krone1 on 2008-11-06
I realized my 8.10 upgrade was using the old ath_pci driver.  I followed the link supplied by eks, installed linux-backports-modules-intrepid package, the 5xxxx series atheros driver loaded.  Now the wireless works great.  Thanks eks!

---

### Post by derksacklowski on 2008-11-06
Hello,

first of all i'd like to thank you a lot for your good work.

Now my problems:

1. I have to load the driver manually at every start of Ubuntu.

```
sudo make load
```

2. My Wlan connection is incredibly slow! If I try to ping my router i get a strange message:

```
ping: sendmsg: No buffer space available
```

I would be very thankful if you guys are able to help me.

Greets from Germany

---

### Post by daxomatic on 2008-11-06
Hi All, 
I got my wifi working on an Acer Inspire 5520 with a 
 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
on kernel Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008
and the only thing i did was 
1 - follow [http://ubuntuforums.org/showpost.php?p=6052699&postcount=4](http://ubuntuforums.org/showpost.php?p=6052699&postcount=4) ( install linux-backports-modules-intrepid )
2 - blacklist ath_hal and ath_pci 
3 - reboot
4 - profit 

Regards
Daxomatic

---

### Post by mrpelas on 2008-11-07
double post

---

### Post by Greg F on 2008-11-08
> **KermitJr said:**
> But for the record, I stuck in the CD, enabled it (You have to enable it in software sources or repositories or it won't work), reloaded, installed linux-backports-modules-intrepid-generic and rebooted and it automagically worked.

Cheers,
KermitJr
This is all I did, and it fixed the problem on a MSI notebook with the Atheros wireless chipset.

---

### Post by tim183 on 2008-11-09
I have an HP dv6700 with atheros ar5007eg.

The compat wireless method worked for me in intrepid, BUT only to the stage where I can see the wireless network, but I can't connect to my home network which is an open network.

I also had a similar experience with the old ndiswrapper method on hardy and also with madwifi on hardy. it makes me think there is something wrong with my network configuration or something?

can someone please try and help me with this?


> **eks said:**
> You can do a "dmesg | grep ath" and posts the results. Just FYI, [dmesg]("http://en.wikipedia.org/wiki/Dmesg") is kind of a boot up log, so you can review what went wrong (or right) during boot up procedure. | grep ath tells to just show messages containing ath, which is probably where your problem is.


ok, so here is the output:

tim@tim:~$ dmesg | grep ath
[   28.083165] ath5k_pci 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 16 (level, low) -> IRQ 16
[   28.083174] ath5k_pci 0000:03:00.0: setting latency timer to 64
[   28.083210] ath5k_pci 0000:03:00.0: registered as 'phy0'
[   28.220275] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

I took the laptop to work to see if it was jsut my home connection, but the same thing happened on the open network at work.

also other computers, both ubuntu and windows have no problem connecting to the home access point. any suggestions would be appreciated!

---

### Post by tim183 on 2008-11-10
bump

---

### Post by Ghostlove on 2008-11-10
Is it possible this might work for those of us having trouble using Ethernet rather than wireless?

---

### Post by eks on 2008-11-10
> **tim183 said:**
> tim@tim:~$ dmesg | grep ath
[   28.083165] ath5k_pci 0000:03:00.0: PCI INT A -> Link[LK1E] -> GSI 16 (level, low) -> IRQ 16
[   28.083174] ath5k_pci 0000:03:00.0: setting latency timer to 64
[   28.083210] ath5k_pci 0000:03:00.0: registered as 'phy0'
[   28.220275] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)

I took the laptop to work to see if it was jsut my home connection, but the same thing happened on the open network at work.

Very weird, if dmesg just shows ath5k, it should be working. :?

I really don't know what might be happening. Have you taken a look at what's happening on /etc/modprobe.d/? It's the folder where it loads or blacklists modules. Take a look at the [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") also. I'm sorry, I'm really not that an advanced user to help you with just that information. :(

---

### Post by eks on 2008-11-10
> **Ghostlove said:**
> Is it possible this might work for those of us having trouble using Ethernet rather than wireless?

The ath5k module no, it's a "driver" for Atheros wifi cards. BUT! The backports modules might, it's where the Ubuntu developer places new, "supposedly stable", modules in-between Ubuntu distributions, so it might have a module that might be newer and resolve the case. Take a look at the first part of this wiki:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Either way, is just a package on Synaptic, if it doesn't work you can hopefully just uninstall it. On Intrepid the package is called *linux-backports-modules-intrepid* (just search for "backports" and you will find it).

---

### Post by tradiuz on 2008-11-10
What worked for me was doing everything in the madwifi ticket:

[http://madwifi-project.org/ticket/1192](http://madwifi-project.org/ticket/1192)

And note, you'll have to do this every time you update the kernel i think.

---

### Post by tim183 on 2008-11-11
> **eks said:**
> Very weird, if dmesg just shows ath5k, it should be working. :?

I really don't know what might be happening. Have you taken a look at what's happening on /etc/modprobe.d/? It's the folder where it loads or blacklists modules. Take a look at the [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros") also. I'm sorry, I'm really not that an advanced user to help you with just that information. :(

Does anyone else have any ideas, I followed eks's tips and the wiki as well but am still at the same stage, I can see available networks, wwhen I attempt to cobnnect the networkmanager icon swirls around as though it is attempting to connect then a notification popup appears saying that my network connection has been disconnected.

I'm getting very frustrated at being sooo close!

---

### Post by eks on 2008-11-11
> **tim183 said:**
> Does anyone else have any ideas, I followed eks's tips and the wiki as well but am still at the same stage, I can see available networks, wwhen I attempt to cobnnect the networkmanager icon swirls around as though it is attempting to connect then a notification popup appears saying that my network connection has been disconnected.

I'm getting very frustrated at being sooo close!

If you can see the wireless networks listed, then the module/driver should be working and it's a matter of configuring the connection.

I had the same problem, because before the upgrade, with the installed driver, the WPA Supplicant the manager was using was "madwifi", changing it to "wext" solved the problem.

I use [wicd]("http://wicd.sourceforge.net/"), so I don't know where to find this option on the network manager (try some googling if you don't find it). Or try to install wicd.

---

### Post by tim183 on 2008-11-12
> **eks said:**
> If you can see the wireless networks listed, then the module/driver should be working and it's a matter of configuring the connection.

I had the same problem, because before the upgrade, with the installed driver, the WPA Supplicant the manager was using was "madwifi", changing it to "wext" solved the problem.

I use [wicd]("http://wicd.sourceforge.net/"), so I don't know where to find this option on the network manager (try some googling if you don't find it). Or try to install wicd.

I installed wicd and ensured it was using the wext setting as described. It can also see the network just fine but when I try to connect it just stalls at "obtaining ip address"

---

### Post by dipaish on 2008-11-12
Hi the most easiest way to make atheros work is as follows: 



Step 1: Open the terminal mode and type or copy the following command
deep@deep-laptop:~$ sudo apt-get install linux-backports-modules-intrepid-generic 

Step 2: disable any other wireless driver if enabled by going to system----administration--hardware drivers ---(in my case i need to disable support for atheros 802.11 wireless lan cards)

Step 3: Restart your computer
 deep@deep-laptop:~$ sudo reboot

The above commands enables the Atheros ath5k wireless driver which is not enabled by default.This is all about making wireless work on Ubuntu with atheros drivers.

---

### Post by Me! on 2008-11-12
> **Malet said:**
> Here's the solutions (although both give inconsistent connections):
[LIST=1]
[*]You can try the **linux-backports-modules-intrepid** method outlined here [http://ubuntuforums.org/showpost.php?p=6089169&postcount=3](http://ubuntuforums.org/showpost.php?p=6089169&postcount=3) which people have said is a better connection, but you'll need to reload the driver every time you log in.
**OR**
[*]Compile latest ath5k driver:
[LIST][*]Download the package at [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)
[*]Use file-roller (or similar) to extract the source.
[*]Move to the directory you extracted in terminal.
[*]paste this into terminal:
```
make
sudo make install
sudo make unload
sudo make load
```
[/LIST]
[/LIST]
If you have problems and need **to uninstall** you can do:
```
sudo make unload
sudo make uninstall
```
in the source directory.

I'm Sorry, it did not working with me !

Asus r5rl , with Atheros AR242x

Wireless Led is off just starting Xorg
can not scan or connect to any wireless network

Old Ver. running on 2.6.26 or less



I am thinking to downgread to 8.04 until finding a solution for this problem, But I will try more today !

Thanks

---

### Post by tim183 on 2008-11-13
I bought an intel pro/wireless card off ebay in order to try and solve this issue because it's driving me crazy, I have been trying to work around this issue for 4 months now following every forum/howto/blog post.

the intel card wouldnt work though. I was old about a 'white list' for hp notebooks.

does anyone have any other advice to get this annoying ar5007eg card to connect to the networks I can see?

---

### Post by Me! on 2008-11-13
it works now !

the problem is the conflict between the restrict drivers & ath5k (compat-wireless-2008-11-13)

you can download it by
```
wget -c http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
```
do this if you want to cancel restrict driver:
```
sudo update-rc.d -f linux-restricted-modules-common remove
sudo apt-get update
sudo apt-get install build-essential
cd [pathTo]compat-wireless-2008-11-13/
sudo make unload
sudo make load
```

See installing steps : [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex)
:popcorn:
Thanks all

---

### Post by TpyKv on 2008-11-23
Number 2 worked for me, thank you so much!! :guitar:

(Sony Vaio with Atheros AR5007)

---

### Post by off4vra on 2008-12-09
Works fine with “linux-backports-modules-intrepid” 
Asus F5RL! And the led is on!
Just need to do this:
1.open and edit the file /etc/rc.local
2.before the final exit 0, insert this line:
echo 1 > /sys/devices/platform/asus-laptop/wlan

---

### Post by ufos2010 on 2008-12-26
> **aweller said:**
> Although this method worked, I was really unhappy with the speed of my connection.  It kept dropping out, etc, when it was working fine before in 8.04.  I can confirm that I get better speeds with this method:

[http://ubuntuforums.org/showthread.php?t=967520]("http://ubuntuforums.org/showthread.php?t=967520")is 

Yep! This helped me out great!:)

---

### Post by nrayever on 2008-12-27
> **Malet said:**
> Here's the solutions (although both give inconsistent connections):
[LIST=1]
[*]You can try the **linux-backports-modules-intrepid** method outlined here [http://ubuntuforums.org/showpost.php?p=6089169&postcount=3](http://ubuntuforums.org/showpost.php?p=6089169&postcount=3) which people have said is a better connection, but you'll need to reload the driver every time you log in.
**OR**
[*]Compile latest ath5k driver:
[LIST][*]Download the package at [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)
[*]Use file-roller (or similar) to extract the source.
[*]Move to the directory you extracted in terminal.
[*]paste this into terminal:
```
make
sudo make install
sudo make unload
sudo make load
```
[/LIST]
[/LIST]
If you have problems and need **to uninstall** you can do:
```
sudo make unload
sudo make uninstall
```
in the source directory.

Thanks a lot Malet! Method # 2 worked great for Intrepid Ibex! Hope that this issue gets solved soon in main branch. :lolflag::lolflag:

Regards Nrayever

---

### Post by jdruin on 2008-12-28
> **rblevitt said:**
> When I typed in the last two instructions--"sudo make unload", then "sudo make load"--I got a message about needing to be root. I also got a message about only needing to enter "make unload" and then "make load". However, the procedure did work on my machine--a Compaq C751NR--for the most part. The only fly in the ointment is that I have to go into System/Administration/Hardware Drivers and first inactivate and then reactivate the Atheros 5K driver in order to get wifi up and running. Any ideas about how to fix this bug?

*R. Levitt*
Looks like on [http://linuxwireless.org/en/users/Download#Buildingandinstalling]("http://linuxwireless.org/en/users/Download#Buildingandinstalling") they mention that 

sudo make load

will run unload for you, so you could skip the unload step.

> Note that this will run make unload first, just in case you forgot. This unloads your old wireless subsystem drivers and loads the new shiny ones. For example if ipw3945 and its proprietary daemon are found it'll be stopped and the module unloaded and then iwl3945 will be loaded. If you are simply upgrading a mac80211 driver this will unload the old one and the old mac80211 drivers and load the new ones. 

---

### Post by karomann on 2009-01-02
Hi,
the backported modules approach didn't work for me. The compat wireless approach almost worked - i can't get wpa to work for me - the iwlist wlan0 scan does not show any wpa networks, it shows only the wep and unrestricted access networks:/. 

I thought that compiling a more recent version of compat wireless might help, but after trying it i can't insert ath5k into kernel:
```

sudo modprobe ath5k

```
gives:
```

WARNING: Error inserting lbm_cw_cfg80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-cfg80211.ko): Invalid module format
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.27-11-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath5k (/lib/modules/2.6.27-11-generic/updates/ath5k.ko):Unknown symbol in module, or unknown parameter (see dmesg)

```
dmesg grep lbm_cw-cfg80211.ko gives:
```

lbm_cw_cfg80211: exports duplicate symbol cfg80211_wext_giwmode (owned by cfg80211)

```

any help greatly appreciated :-)

---

