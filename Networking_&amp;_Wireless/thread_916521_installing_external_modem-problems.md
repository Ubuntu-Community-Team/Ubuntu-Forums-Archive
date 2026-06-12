---
title: "installing external modem-problems"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by acoluthus on 2008-09-11
Hi-
I posted:
[http://ubuntuforums.org/showthread.php?t=906661](http://ubuntuforums.org/showthread.php?t=906661)
re: getting an external hardware modem, new, supposedly linux compatable, up and running.
I am very behind-the-lingo of the times; ie: I didn't recognize that linmodem is probably just a software modem not a hardware one..
anywhoo, I could use some direction, or at least hope to learn where to look to start to learn.
I've bought Linux compatable external stuff: Linksys router for linux and the Trendnet modem; on their in-box CD'R's: .exe & .bin setup wizards to access all the great selling features I bought them for. it's a letdown.
All I need at the moment is to learn how to make this stuff work. ((I came to ubuntu from a dying imac os9 and at work run on a completely stripped and restricted win-98 on a 96Ram processor -yes,that bad, and that far behind the times understanding))

`not sure where to go if the posted instructions don't work, or don't work "all the way"..
 any help appreciated

Sincerely
AC

---

### Post by Shazaam on 2008-09-11
Copy/pasted info from here (take it as you will)...
[http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002](http://www.newegg.com/Product/Product.aspx?Item=N82E16825134002)
```
If you have two Serial Ports it may be a bit of a challenge to get the modem to be detected.
Be sure to put it in your SerialPort0 if possible, this is also the default setting.
To set it up in Ubuntu go to System>>Administration>>Network, click properties on Point to Point Connection.
Once there, click Enable this connection, connection type Serial Modem, set your ISP info, then go to the Modem tab.
Set Modem Port to "/dev/ttyS0", Set Volume to Off (kills the loud dialing noise), in the Options tab check all the check boxes.
Click "OK" and wait for a 'click' noise, this will be it dialing.
Once connected all lights will be red with two RD & SD lights in the middle blinking.
```

---

### Post by trikster_x on 2008-10-14
I know it isn't much, but some people have suggested this- [http://www.linmodems.org](http://www.linmodems.org) .  It may help as it seems to use drivers for specific chipsets rather than manufacturer and model numbers.  As for some of your other problems, You may have gotten a bad install.  I had this happen on the first Linux distro that I used, and have to admit it almost turned me off Linux.  When I did the disk checks to see if it was a bad disk they all came back fine, but when I made a fresh install disk and remembered to burn it at the lowest speed setting the installation worked fine.  You may need to try creating a new .iso disk and completely reinstall Ubuntu.  Since the problems you are having all seem to be related to default programs, this would be the best advice I can give you.  Also, if you search on google you can also find helpful advice there.  Many times people will actually refer you to sources outside of Ubuntu forums.  Here is a couple things I found searching the web.:

If you have two Serial Ports it may be a bit of a challenge to get the modem to be detected. Be sure to put it in your SerialPort0 if possible, this is also the default setting. To set it up in Ubuntu go to System>>Administration>>Network, click properties on Point to Point Connection. Once there, click Enable this connection, connection type Serial Modem, set your ISP info, then go to the Modem tab. Set Modem Port to "/dev/ttyS0", Set Volume to Off (kills the loud dialing noise), in the Options tab check all the check boxes.
Click "OK" and wait for a 'click' noise, this will be it dialing. Once connected all lights will be red with two RD & SD lights in the middle blinking.

The  Linux drivers for the TFM-560x are built into Linux, you can check 
> to see if Agere has Linux drivers for the OCM92 chipset.

[http://howtoubuntu.wordpress.com/2008/03/03/how-to-dial-up-internet-on-ubuntu-with-gnome-ppp/](http://howtoubuntu.wordpress.com/2008/03/03/how-to-dial-up-internet-on-ubuntu-with-gnome-ppp/)

The fact that almost everyone is able to use the same modem as you with nlittle or no problem tells me that either Ubuntu is broke and needs reinstalled, or you modem is busted.  Also, everyone's response to the modem problem is gnome ppp. Just try and reinstall.

---

### Post by acoluthus on 2008-10-15
(sigh)
humbly & sincerely, thank you ... it'd been a while since i'd gotten anywhere and I had a tantrum.  I understand that it's a few serving the many, and I don't take that lightly; I sincerely respect those who have the knowledge that I've not even begun to grasp. In midlife it's quite frustrating to be out of the loop and feel like a disabled person struggling to take a step while others walk by.
I honestly wish that there was a way that along with the "thanks" that I could donate 5 or 10 bucks towards a problem that gets resolved(depending on intensity/etc.) most of my stuff is rather "preschool" level, IMO, compared with other more "sophisticated" threads that I've read.
I bought the book, I read the book, I tried the book - didn't get book results. then search for similar issues in the forums, then when all else isn't found, then posted. = I got frustrated. then i took zathras for a walk. we're better now.

In the mean time, as one reply suggested, I'm downloading (for the 2nd time) the ISO for 8.04; it's what I'm running now already, but I don't mind reloading it. the previous version i followed the instructions to burn it but got some error message. I've burned other data disks before w/o problems.
Other stuff: 
-I have those zip file "boxes" of programs; I dont' know how to run/install;I click, they extract 2to4 copies and repeat opening themselves...
-using shut down software; monitor goes off, pc stays on. Hibernate does ok for a couple of times in a row but then gets non-responsive so I have to hold the power button down and shutdown that way. previous & new Ubuntu versions.
--------------------------------------------------
this is huge: but all my notes from attempts with the GnomePPP and WV Config.  still won't go through. the only other thing I could think of is that I'm using a battery-backup power surge "block" to protect against surges through the phone line- it has happened in our house already so I'd rather not skip using that; that surge fried a previous router in our house; if I'm going direct I don't want to fry my external modem and possibly the xPC /CPU.
ok: here's what I've done; taken notes each step.:(The purple & red show where I removed my name/etc for security)

terminal:information I got while trying to install the modem
[https://help.ubuntu.com/community/NetworkAdmin](https://help.ubuntu.com/community/NetworkAdmin) for the GUI /easy one..
[https://help.ubuntu.com/community/DialupModemHowto/Setserial](https://help.ubuntu.com/community/DialupModemHowto/Setserial) got me to ScanModem
run sudo./scanModem (finally worked) results below:
[COLOR="Purple"]USERNAME[/COLOR]:@[COLOR="Purple"]USERNAME[/COLOR]::~$ gunzip -c scanModem.gz > scanModem 
[COLOR="Purple"]USERNAME[/COLOR]:@[COLOR="Purple"]USERNAME[/COLOR]::~$ chmod +x scanModem 
[COLOR="Purple"]USERNAME[/COLOR]:@[COLOR="Purple"]USERNAME[/COLOR]::~$ sudo ./scanModem 
[sudo] password for dav: 
UPDATE=2008_08_26 
 Continuing as this update is only 1 weeks old, 
 but the current Update is always at: [http://linmodems.technion.ac.il](http://linmodems.technion.ac.il) 
Identifying PCI bus slots with candidate modems. 
Running PCIbus cases 
Analysing card in PCI bus 00:1b.0, writing to scanout.00:1b.0 
 The /proc/asound/ audio+modem diagostics are being copied. 
 Finished copy to Modem/ALSAroot.tgz 
Using scanout.00:1b.0 data, and writing guidance to ModemData.txt 
Writing DOCs/Intel.txt 
Writing DOCs/Conexant.txt 
Writing DOCs/Smartlink.txt 
 Writing residual guidance customized to your System. 
   A subfolder Modem/  has been written,  containing these files with more detailed Information:1stRead.txt  DOCs  ModemData.txt  scanout.00:1b.0  tmp 
    and in the DOCs subfolder: 
 ALSAroot.tgz  Conexant.txt     DriverCompiling.txt  InfoGeneral.txt 
Intel.txt     Rational.txt     Smartlink.txt        SoftModem.txt 
Testing.txt   UNSUBSCRIBE.txt  wvdial.txt           YourSystem.txt 
------------------------------------------------------------------------------------------- 
       Please read 1stRead.txt first for Guidance. 
ok, `found report, then there was another Terminal Line to run to detect External Modems: results:
[COLOR="Purple"]USERNAME[/COLOR]:@[COLOR="Purple"]USERNAME[/COLOR]::~$  sudo wvdialconf  /etc/wvdial.com 
Editing `/etc/wvdial.com'. 

Scanning your serial ports for a modem. 

ttyS0<*1>: ATQ0 V1 E1 -- OK 
ttyS0<*1>: ATQ0 V1 E1 Z -- OK 
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK 
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK 
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK 
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
ttyS0<*1>: Modem Identifier: ATI -- Agere OCM V.92 Ver2.7a (Jun 14 2004) Voice Mercury DP2SH mode-ii SERIAL 
ttyS0<*1>: Speed 4800: AT -- OK 
ttyS0<*1>: Speed 9600: AT -- OK 
ttyS0<*1>: Speed 19200: AT -- OK 
ttyS0<*1>: Speed 38400: AT -- OK 
ttyS0<*1>: Speed 57600: AT -- OK 
ttyS0<*1>: Speed 115200: AT -- OK 
ttyS0<*1>: Max speed is 115200; that should be safe. 
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
Modem Port Scan<*1>: S2   S3   

Found a modem on /dev/ttyS0. 
/etc/wvdial.com<Warn>: Can't open '/etc/wvdial.com' for reading: No such file or directory 
/etc/wvdial.com<Warn>: ...starting with blank configuration. 
Modem configuration written to /etc/wvdial.com. 
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0" 
Took above data to wvmodem
to find answer to “what's my DNS:  I entered & got:
[COLOR="Purple"]USERNAME[/COLOR]:@[COLOR="Purple"]USERNAME[/COLOR]::~$ cat /etc/resolv.conf 
search cable.rcn.com 
nameserver 192.168.0.1 
ok, so I went to the Network Connections: top  of the screen, changed Configuration to what tome was a new selection: Local ZeroConf network: Ipv4LL, and some of the lights on the modem started up..
still wont' connect yet.. -how does one confirm a dial-out? (memory serves me correctly, look for dialer program)
-went to Applications: GnomePPP and ran through that; some results, but incomplete.
/home/[COLOR="Purple"]USERNAME[/COLOR]:/.wvdial.conf<Warn>: Ignoring malformed input line: ";Do NOT edit this file by hand!" 
WvDial<*1>: WvDial: Internet dialer version 1.56 
WvDial<*1>: Initializing modem. 
WvDial<*1>: Sending: ATZ 
WvDial Modem<*1>: ATZ 
WvDial Modem<*1>: OK 
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: OK 
WvDial<*1>: Modem initialized. 
WvDial<*1>: Sending: ATM1L3DT3370840 
WvDial<*1>: Waiting for carrier. 
WvDial Modem<*1>: ATM1L3DT3370840 
WvDial Modem<*1>: NO DIALTONE 
WvDial<Err>: No dial tone. 
WvDial<*1>: Disconnecting at Sun Aug 31 14:48:53 2008 
tried a few variations; ISDN versus Analog, .. etc. .getting “no dial tone”  my phone, from modem does work/get dial tone.. back to wvdial configuration, first: rechecked settings/following steps;
wvdialconf /etc/wvdial.conf 
[sudo] password for [COLOR="Purple"]USERNAME[/COLOR]: 
Sorry, try again. 
[sudo] password for [COLOR="Purple"]USERNAME[/COLOR]: 
Editing `/etc/wvdial.conf'. 
 
Scanning your serial ports for a modem. 

ttyS0<*1>: ATQ0 V1 E1 -- OK 
ttyS0<*1>: ATQ0 V1 E1 Z -- OK 
ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK 
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK 
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK 
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
ttyS0<*1>: Modem Identifier: ATI -- Agere OCM V.92 Ver2.7a (Jun 14 2004) Voice Mercury DP2SH mode-ii SERIAL 
ttyS0<*1>: Speed 4800: AT -- OK 
ttyS0<*1>: Speed 9600: AT -- OK 
ttyS0<*1>: Speed 19200: AT -- OK 
ttyS0<*1>: Speed 38400: AT -- OK 
ttyS0<*1>: Speed 57600: AT -- OK 
ttyS0<*1>: Speed 115200: AT -- OK 
ttyS0<*1>: Max speed is 115200; that should be safe. 
ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK 
Modem Port Scan<*1>: S2   S3   

Found a modem on /dev/ttyS0. 
Modem configuration written to /etc/wvdial.conf. 
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0" 
tried.. odd page, got results, tried to override but didn't enter correctly 1st time
[Dialer Defaults] 
Init1 = ATZ 
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
Modem Type = Analog Modem 
Baud = 115200 
New PPPD = yes 
Modem = /dev/ttyS0 
ISDN = 0 
; Phone = <1234567>  [COLOR="Red"]----I took this off from posting[/COLOR] 
; Password = <my password > [COLOR="Red"]----I took this off posting[/COLOR]
; Username = <mu username>   [COLOR="Red"]----I took this off posting[/COLOR]
followed instructions, got error
Found a modem on /dev/ttyS0. 
Modem configuration written to /etc/wvdial.conf. 
ttyS0<Info>: Speed 115200; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0" 
dav@dav:~$ sudo nano /etc/wvdial.conf 
dav@dav:~$ sudo nano /etc/wvdial.conf 
dav@dav:~$ sudo wvdial 
WvDial<*1>: WvDial: Internet dialer version 1.56 
WvDial<*1>: Initializing modem. 
WvDial<*1>: Sending: ATZ 
WvDial Modem<*1>: ATZ 
WvDial Modem<*1>: OK 
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
WvDial Modem<*1>: OK 
WvDial<*1>: Modem initialized. 
WvDial<Err>: Configuration does not specify a valid phone number. 
WvDial<Err>: Configuration does not specify a valid login name. 
WvDial<Err>: Configuration does not specify a valid password. 
Alternative Way 2 (using pppconfig & pon/poff)
tried. unsuccessfully. left message on help boards
[http://ubuntuforums.org/showthread.php?p=5701670#post5701670](http://ubuntuforums.org/showthread.php?p=5701670#post5701670)
[http://ubuntuforums.org/forumdisplay.php?f=130https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer?action=show&redirect=wvdial](http://ubuntuforums.org/forumdisplay.php?f=130https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer?action=show&redirect=wvdial)
[https://help.ubuntu.com/community/DialupAndFax](https://help.ubuntu.com/community/DialupAndFax)
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#Connecting%20to%20the%20ISP](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#Connecting%20to%20the%20ISP)

---

### Post by trikster_x on 2008-10-15
When you make your new liveCD, make sure you use the make cd image disk or make dvd .iso image disk options or the disks will not turn out right.

---

### Post by acoluthus on 2008-10-15
> **trikster_x said:**
> I know it isn't much, but some people have suggested this- [http://www.linmodems.org](http://www.linmodems.org) .  It may help as it seems to use drivers for specific chipsets rather than manufacturer and model numbers.  As for some of your other problems, You may have gotten a bad install.  I had this happen on the first Linux distro that I used, and have to admit it almost turned me off Linux.  When I did the disk checks to see if it was a bad disk they all came back fine, but when I made a fresh install disk and remembered to burn it at the lowest speed setting the installation worked fine.  You may need to try creating a new .iso disk and completely reinstall Ubuntu.  Since the problems you are having all seem to be related to default programs, this would be the best advice I can give you.  Also, if you search on google you can also find helpful advice there.  Many times people will actually refer you to sources outside of Ubuntu forums.  Here is a couple things I found searching the web.:

If you have two Serial Ports it may be a bit of a challenge to get the modem to be detected. Be sure to put it in your SerialPort0 if possible, this is also the default setting. To set it up in Ubuntu go to System>>Administration>>Network, click properties on Point to Point Connection. Once there, click Enable this connection, connection type Serial Modem, set your ISP info, then go to the Modem tab. Set Modem Port to "/dev/ttyS0", Set Volume to Off (kills the loud dialing noise), in the Options tab check all the check boxes.
Click "OK" and wait for a 'click' noise, this will be it dialing. Once connected all lights will be red with two RD & SD lights in the middle blinking.

The  Linux drivers for the TFM-560x are built into Linux, you can check 
> to see if Agere has Linux drivers for the OCM92 chipset.

[http://howtoubuntu.wordpress.com/2008/03/03/how-to-dial-up-internet-on-ubuntu-with-gnome-ppp/](http://howtoubuntu.wordpress.com/2008/03/03/how-to-dial-up-internet-on-ubuntu-with-gnome-ppp/)

The fact that almost everyone is able to use the same modem as you with nlittle or no problem tells me that either Ubuntu is broke and needs reinstalled, or you modem is busted.  Also, everyone's response to the modem problem is gnome ppp. Just try and reinstall.
Hi-
I tried linmodems, but though i spent hours through those, it appeared that that site was for inboard/software modems.  There was a sentence at one point that seemed to indicate that the chipset-stuff that the site was dedicated to was for internal software items, not for external self-contained modems like the TrendnetTFM560x external linuxfriendly serial-line input one that I purchased. 
There's more detail on what I posted after my tantrum, with fact/my own notes & step-by-step that may mean more to others than myself.
After running what one other advised to "decommission" the wvconf terminal text; the reply I got was "huh?" from the Terminal (not found/didn't/couldn't perform that process) maybe the data I posted may shed light on it..
Perhaps I'll have more time this weekend to delve into it; I'm booked solid through then, but will be attentive to further recommendations.
Sincerely,

AC

---

### Post by Rhubarb on 2008-10-16
I do know a bit about getting dial up modems working in linux (serial external modems).
Unfortunately it's a bit of a catch 22 situation, you need the internet so you can get your internet working.

Firstly, some of the old external modems required brand / model specific initialization commands sent to it in order for it to actually work.
This you'd have to search on the net for your specific modem and see if there's any AT Command Set strings that it requires.

Secondly, it may be a simple problem.  Dial up modems can be configured to "wait for dialtone" before it attempts to actually dial the number.
By default this is usually true, it waits for a dial tone.
It is possible to tell your modem NOT to wait for dial tone.
I'm not sure about wvdial / gnomePPP, but this can certainly be set in KPPP (a nice graphical app for dial up net).

For reference, the **W** character when placed before the number to dial instructs your modem to wait for a dialtone before dialling the number.  So if you find a W, get rid of it.
[http://nemesis.lonestar.org/reference/telecom/modems/at/summary-at.html](http://nemesis.lonestar.org/reference/telecom/modems/at/summary-at.html)

It's times like these when you really could do with a local linux tech to drop in and fix it all up for you :P

Best of luck ;)

---

### Post by _duncan_ on 2008-10-16
> ; Phone = <1234567> ----I took this off from posting
; Password = <my password > ----I took this off posting
; Username = <mu username> ----I took this off posting

FYI, any line that starts with a semicolon ';' is treated as a comment. Try removing the semicolon before running wvdial again.

---

### Post by Riffer on 2008-10-17
I'm assuming that your internet connection is dial-up (it wasn't to clear and I just woke up) which goes over your phone lines.  Lets start at basics, is your modem supported by Linux?  And do you know it works?  And how are you able to get an ISO over the net?

Many times its can be a faulty modem, if you could swap your old modem for another (Linux compatible) modem and try that.

---

### Post by JoshuaRL on 2008-10-19
Or you could try ordering a CD from ShipIt.  That way you would be sure that it wasn't a problem with the download or burn.

---

### Post by acoluthus on 2008-10-26
Re: Riffer:

sorry for so late a reply; essentially my cable internet ISP is "high speed" for about 15minutes then has so many broken connections it's useless, especially since RCN charges a competative rate and none of the "big" cable ISP's in my area have any real support, let alone for linux. SO: to save money, I'm going BACK to dialup; may as well save 2/3 the bill for at least a satisfied level of service.
I bought a Trendex Linux-supported (supposedly "for" linux but their wizard/cd isn't linux based) external modem. others have had no problem setting it up.
I"m continuing the commentary/progress further below for hte additional recommendations that I've followed through w/. Thanks

---

### Post by acoluthus on 2008-10-26
Re: _Duncan_

i just copied and pasted the data as it showed up; the reason I put that comment that you referred to was to take my name/password/etc out of the commentary of my experience in case it was a security "thing". the semicolons were throughout the cut-paste from taking it off the Terminal conversation; it showed up  that way.

---

### Post by acoluthus on 2008-10-26
Dear All, 
 I downloaded & ran the CD-ISO of Heron8.04-1.
1) it asked about partitioning; as I "assumed" that partitioning was for having alt-operating systems (ie: windows/mac) I chose "the whole sha-bang" and overwrote -everything-.  that wiped out all my lovely elective programs that I've been collecting /using for severalmany months.
2)first install attempt: got up to 99percent and froze on "copy installation log" so I got out, and went to re-try.
3) poked around and looked at pre-installation scans "Check Disk" and "Memory Test"; disk ck found no errors; memory ck ran 3times when I figured out it was looping/repeating the same 7 or 8 levels of tests but no errors found anyway.
set my keyboard to Mac keyboard-the only difference from the last install of Heron a few months ago.
4)tried to locate my programs that I liked; there's a problem getting them from the us server; Message Follows:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_8.04+20080805_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_8.04+20080805_all.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_8.04+20080805_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_8.04+20080805_all.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.85eubuntu39.2_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.85eubuntu39.2_all.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-21-generic_2.6.24-21.42_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.24-21-generic_2.6.24-21.42_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.24/linux-ubuntu-modules-2.6.24-21-generic_2.6.24-21.32_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.24/linux-ubuntu-modules-2.6.24-21-generic_2.6.24-21.32_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/gcc-4.2-base_4.2.4-1ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/gcc-4.2-base_4.2.4-1ubuntu3_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libstdc++6_4.2.4-1ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libstdc++6_4.2.4-1ubuntu3_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libgomp1_4.2.4-1ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libgomp1_4.2.4-1ubuntu3_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libffi4_4.2.4-1ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libffi4_4.2.4-1ubuntu3_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/cpp-4.2_4.2.4-1ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/cpp-4.2_4.2.4-1ubuntu3_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/gcc-4.2_4.2.4-1ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/gcc-4.2_4.2.4-1ubuntu3_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libgcc1_4.2.4-1ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.2/libgcc1_4.2.4-1ubuntu3_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.7-10ubuntu4_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008h-0ubuntu0.8.04_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008h-0ubuntu0.8.04_all.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/eject/eject_2.1.5-6ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/eject/eject_2.1.5-6ubuntu1_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/iproute/iproute_20071016-2ubuntu2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/iproute/iproute_20071016-2ubuntu2_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pciutils/pciutils_2.2.4-1.1ubuntu6_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pciutils/pciutils_2.2.4-1.1ubuntu6_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.9p10-1ubuntu3.3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/sudo/sudo_1.6.9p10-1ubuntu3.3_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.2.7-5ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/procps/procps_3.2.7-5ubuntu3_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc35_9.4.2.dfsg.P2-2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc35_9.4.2.dfsg.P2-2_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns35_9.4.2.dfsg.P2-2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns35_9.4.2.dfsg.P2-2_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc30_9.4.2.dfsg.P2-2_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc30_9.4.2.dfsg.P2-2_amd64.deb)
  Could not resolve 'us.archive.ubuntu.com'

so here I am again.. I'll try later to download the updated that the System acknowledges, plus hope to get my preferred OpenSource programs back in. 
**I DID** back up my documents, photos, but didn't catch my bookmarks.-bummer.

Also: one of the items/programs that wouldn't upload was the PPPGnome dialer, so I'm still "pre-modem"/ still haven't dumped my fickle cable internet.

State-of-the-Onion so far; I'll keep posting,
-as the layers unfold in my education online with this...

Thanks, R_E_A_L_L_Y, to all of you'se..

`AC

---

### Post by JoshuaRL on 2008-10-28
The wget errors come from not being connected to the internet.  Before you try updates or getting programs, make sure you have a good live connection.  Then everything should work.

---

### Post by acoluthus on 2008-10-29
well, part of this whole process was to get to be able to use an external, Trendnet 560 linux-friendly modem.. At the moment, the Heron ammenities don't look the same as what I had in the previous version;ie: internet settings/etc. I had a Network status window that I used a lot along with the system status viewer (constant running graph that showed activity)-the Network one showed the incoming/outgoing traffic in Kb/Mb's.. I don't think I've got the same in Heron yet..maybe it's in the updates that arent' downloaded yet. 
Any hints on getting my dialup modem working; even if it takes all night at least I can let it run..
Also: i posted re: getting failure from the Repository; i tried the update manager and the system apps (2 different means to get dowloads). it's almost like I'm not online anymore.
What should my settings look like? lo, etho, etho-avahi? I don't know..
*In one of my earlier postings I listed a system report w/ my system hardware; I can't post it again as I'm at work now and CPU is at home.
Thoughts, suggestions, input?   I'm following your collective leads..
Thank you...(will check back tomorrow a.m.)

---

### Post by acoluthus on 2008-10-30
Followed the -Reload Heron- as recommended; still having problems; `started another thread at [http://ubuntuforums.org/showthread.php?t=959906](http://ubuntuforums.org/showthread.php?t=959906) and am follwing advice there; perhaps the combo of things / issues may illustrate a deeper problem (including my inexperience?)
Your insight would be appreciated. I'm totally non-connective at this point and either hand-write to go back & forth or use a camera chip and try to borrow roommate's XP-running PC to import whatever data is needed to "save" ubuntu..
Please advise..
Thank you--
A.C.

---

### Post by acoluthus on 2008-11-02
see above posting - 
is entering this message "bumping" the issue back to the top/visibilty again?
I'm following the advise given and reloaded Heron - should i reload Heron again and not have the cable internet RJ45 cable connected, and would that help the internet "stuff"/program? choose the external serial modem? that's not working either.
Suggestions welcome-
THank you-

A.C.

---

### Post by acoluthus on 2008-11-08
bump?

---

### Post by acoluthus on 2008-11-14
BUMP: there's good advice started here.,also trying on 
[http://ubuntuforums.org/showthread.php?t=973101](http://ubuntuforums.org/showthread.php?t=973101)
perhaps info merge on the two?
Heaps o' Thanx!
`dav

---

