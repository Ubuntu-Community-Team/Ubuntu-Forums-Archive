---
title: "Seeking Hardy users with BCM4306 Wireless that fail with b43"
date: 2008-08-09
forum: Networking &amp; Wireless
---

### Post by lwfinger on 2008-08-09
I recently fixed a driver bug that affected my BCM4306/3 PCI card. If you are also having the same problem, please do the following to help me accumulate data regarding these cards:

1. In a terminal, execute the following commands:
```

SPROM=$(find /sys/device -name ssb_sprom)
sudo cat $SPROM > sprom.dat

```

2. Post the contents of sprom.dat in this thread.

3. Run the command 'lspci -n' and post the numbers that correspond to your wireless device.

Thanks,

Larry

---

### Post by NoDecaf on 2008-08-12
not sure if i am having the same problem, but i am having a problem. for a complete description, please refer to this post:

[http://ubuntuforums.org/showpost.php?p=5573075&postcount=18](http://ubuntuforums.org/showpost.php?p=5573075&postcount=18)


```
:~$ SPROM=$(find /sys/device -name ssb_sprom)
find: /sys/device: No such file or directory
```

the second command yields no results (pipes to a 0 byte file)

```
:~$ lspci -nn |grep Broadcom
00:0c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```

---

### Post by lwfinger on 2008-08-12
The "find" command I posted should have found the sprom pseudo-file. It must be in a different place in Ubuntu. As you can probably tell, I'm not an Ubuntu user.

Does this command work?

SPROM=$(find /sys -name ssb_sprom)

One other thing - Please post the first 2 lines of the output of 'lspci -nnv' that pertain to your BCM4306.

Larry

---

### Post by NoDecaf on 2008-08-12
> **lwfinger said:**
> The "find" command I posted should have found the sprom pseudo-file. It must be in a different place in Ubuntu. As you can probably tell, I'm not an Ubuntu user.

Does this command work?

SPROM=$(find /sys -name ssb_sprom)

One other thing - Please post the first 2 lines of the output of 'lspci -nnv' that pertain to your BCM4306.

Larry

sprom in /sys/devices/pci0000:00/0000:00:0c.0/

contents of sprom.dat:
014000000200F91720430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF$
^@


first 2 lines of the output of 'lspci -nnv' that pertain to BCM4306:

00:0c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Unknown device [17f9:0002]

---

### Post by lwfinger on 2008-08-12
To NoDecaf,

Your sprom.dat is incomplete. Please attach the file.

Larry

---

### Post by lwfinger on 2008-08-13
To NoDecaf,

What brand is on your card. I don't find that sub-vendor code (17f9) in any list.

Larry

---

### Post by NoDecaf on 2008-08-13
Larry,

It's a built in bcm4306 in a Gateway7422GX notebook.

I did get the card working. I simply installed WinXP, then rebooted to Linux. Card immediately displayed AP's upon rebooting. Go figure....

---

### Post by lwfinger on 2008-08-14
Were you able to connect as well?

Some BIOS's need to be told not to power off the wireless when shutting down. If they do that step, Linux is unable to power up the card.

Larry

---

### Post by DapperMe17 on 2008-10-06
Larry, I'm sorry to invade your thread. However, I have the BCM4306 & may be able to contribute. 

**lspci -nn |grep Broadcom**
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

I get nothing with the "SPROM" commands


*************************************************************************


Hardy fresh install


I have a working connection with Ndiswrapper, with WPA (using XP 32bit bcmwl5.inf).


My problem...I lose the connection after a reboot. Seems like a problem with the "ssb" module loading, rather than "ndiswrapper".


To get the wlan0 connection up (from "network down") I run these in order....


sudo rmmod b43

sudo rmmod b44

sudo rmmod b43legacy #this step added Apr 27 2008

sudo rmmod ssb

sudo rmmod ndiswrapper

sudo modprobe ndiswrapper

sudo modprobe ssb

sudo modprobe b44 #this step added May 1 2008


echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

sudo /etc/init.d/networking restart


After the above, I now have my internet up!!!


According to lshw -C network...
Seems like a problem with "ssb" loading as my BCM4306 module at start, rather than "ndiswrapper". After running the above commands, the module shows as "ndiswrapper", therefor a simple network restart takes car of business.


So, how can I get Ndiswrapper, not ssb, to stick to my Broadcom interface???

---

### Post by Ayuthia on 2008-10-06
> **DapperMe17 said:**
> Larry, I'm sorry to invade your thread. However, I have the BCM4306 & may be able to contribute. 

**lspci -nn |grep Broadcom**
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

I get nothing with the "SPROM" commands


*************************************************************************


Hardy fresh install


I have a working connection with Ndiswrapper, with WPA (using XP 32bit bcmwl5.inf).


My problem...I lose the connection after a reboot. Seems like a problem with the "ssb" module loading, rather than "ndiswrapper".


To get the wlan0 connection up (from "network down") I run these in order....


sudo rmmod b43

sudo rmmod b44

sudo rmmod b43legacy #this step added Apr 27 2008

sudo rmmod ssb

sudo rmmod ndiswrapper

sudo modprobe ndiswrapper

sudo modprobe ssb

sudo modprobe b44 #this step added May 1 2008


echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

sudo /etc/init.d/networking restart


After the above, I now have my internet up!!!


According to lshw -C network...
Seems like a problem with "ssb" loading as my BCM4306 module at start, rather than "ndiswrapper". After running the above commands, the module shows as "ndiswrapper", therefor a simple network restart takes car of business.


So, how can I get Ndiswrapper, not ssb, to stick to my Broadcom interface???

I put a response to this question in your other thread:
[http://ubuntuforums.org/showthread.php?p=5916745#post5916745](http://ubuntuforums.org/showthread.php?p=5916745#post5916745)

---

### Post by Ayuthia on 2008-10-06
> **DapperMe17 said:**
> Larry, I'm sorry to invade your thread. However, I have the BCM4306 & may be able to contribute. 

**lspci -nn |grep Broadcom**
00:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

I get nothing with the "SPROM" commands


Just to add additional comments, lwfinger's fix refers to the rev 03 instead of the rev 02 of the 4306 card.  As for the SPROM command, since you are using ndiswrapper, did you run the command when you had b43legacy and ssb loaded (and not ndiswrapper)?  Once you remove the ssb module, the information will no longer be there.  Also there was a misprint in the command script.  It should have read:
```
SPROM=$(find /sys/devices -name ssb_sprom)
sudo cat $SPROM > sprom.dat
```It should have had /sys/devices instead of /sys/device.

---

### Post by lwfinger on 2008-10-06
The SPROM readout sequence requires that ssb be loaded. When you unload it, then that sequence will not work. As was pointed out, I am looking for BCM4306/3 cards. Your BCM4306/2 uses b43legacy and does not have the SPROM coding error.

I think you need to blacklist ssb for your system to load ndiswrapper at startup.

Larry

---

### Post by Geoffrey on 2008-10-16
sprom :
1400000FA123C1020430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0000FFFFFFFFFFFFFFFFFFFFFFFFFFFF9000B84BB61BFFFFFFFFFFFFFFFFFFFFFFFFFFFF3130AA14C8FA9FFEFFFFFFFF4C00FFFFFFFFFFFF3E00493A02FF454410FFFFFFFFFF02F9

Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
        Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN [103c:12fa]

cn you send me how to fix my 'sprom'please ? I would like to use my wifi card.

Thanks for your fix

---

### Post by lwfinger on 2008-10-16
Unfortunately, you lost one character in the SPROM contents. The string should be 256 characters long, yours is 255.

Please try again,

Larry

---

### Post by Geoffrey on 2008-10-17
Oh yes sorry,

01400000FA123C1020430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0000FFFFFFFFFFFFFFFFFFFFFFFFFFFF9000B84BB61BFFFFFFFFFFFFFFFFFFFFFFFFFFFF3130AA14C8FA9FFEFFFFFFFF4C00FFFFFFFFFFFF3E00493A02FF454410FFFFFFFFFF02F9

I missed the first character.

---

### Post by Kevbert on 2008-10-17
I have a Broadcom BCM4306 and found that if I install the firmware drivers in the /lib/firmware directory they work. Please take a look at this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13") for details and drivers.  The best post I've found for wireless is [COLOR="Red"][here]("http://ubuntuforums.org/showthread.php?t=766560")[/COLOR]. 
There are many guides, some work sometimes, others don't always work.  If you can nip this problem in the bud Iwfinger that will be great.

---

### Post by lwfinger on 2008-10-17
Your device is known to have the SPROM coding error.

The new contents for your SPROM should be:

01400000FA123C1020430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0000FFFFFFFFFFFFFFFFFFFFFFFFFFFF9000B84BB61BFFFFFFFFFFFFFFFFFFFFFFFFFFFF3130AA14C8FA9FFEFFFFFFFF4C00FFFFFFFFFFFF3E00483A02FF454410FFFFFFFFFF02CD

Copy and paste that string into a file name sprom.new. Then run the following set of commands:

SPROM=$(find /sys -name ssb_sprom)
echo $SPROM
sudo cat sprom.new $SPROM

You only need to do this once. After this step, the BCM4306 should work.

Larry

---

### Post by Geoffrey on 2008-10-17
thanks a lot, it helps much !

Do you know if this fix be inplemented in ubuntu 8.10 ?

---

### Post by lwfinger on 2008-10-18
The fix for the Bluetooth Coexistence for your HP card is included in kernel 2.6.27, which I think is used in 8.10; however, it doesn't matter for you. Once we rewrite the SPROM, the kernel change is immaterial. What it does is rewrite the low-order board flags on the fly - we did it permanently.

Larry

---

### Post by bkline on 2008-10-19
Here's the output from the first command:

```
014000000200F91720430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0000FFFFFFFFFFFFFFFFFFFFFFFFFFFF9000C24B4E26FFFFFFFFFFFFFFFFFFFFFFFFFFFF3130AA14C8FA9FFEFFFFFFFF4C00FFFFFFFFFFFF3E00493A02FF535510FFFFFFFFFF0260
```

and here's the line for the wireless device:

```
00:0b.0 0280: 14e4:4320 (rev 03)
```

Do you have a corrected sprom value?

Thanks!

---

### Post by lwfinger on 2008-10-20
The new value should be

014000000200F91720430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0000FFFFFFFFFFFFFFFFFFFFFFFFFFFF9000C24B4E26FFFFFFFFFFFFFFFFFFFFFFFFFFFF3130AA14C8FA9FFEFFFFFFFF4C00FFFFFFFFFFFF3E00483A02FF535510FFFFFFFFFF0254

If this fixes your device, please let me know. your device is one that we don't know about.

Larry

---

### Post by cowanh00 on 2008-10-22
I'm having issues with my Broadcom wireless PCI card.

The card is:
```
00:07.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
```

This is what my Sprom file contains when I run the commands:

```
&#12592;&#12340;&#12336;&#12336;&#13105;&#12336;&#14131;&#14129;&#12338;&#13108;&#12336;&#12344;&#12848;&#12336;&#12848;&#12336;&#12336;&#12337;&#12336;&#14385;&#12336;&#12336;&#12336;&#12336;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17968;&#12336;&#16945;&#13878;&#13360;&#17204;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#17990;&#13620;&#12337;&#12353;&#12849;&#14135;&#16966;&#17217;&#17734;&#17990;&#17990;&#17990;&#17990;&#17203;&#12336;&#12336;&#12336;&#12336;&#12336;&#12336;&#12336;&#17715;&#12336;&#17456;&#12336;&#17990;&#17990;&#12336;&#12336;&#12336;&#12336;&#12336;&#12336;&#12336;&#12336;&#12592;&#17462;
```

Is is obviously wrong I think! :lolflag:

My card corresponds to (I think):
```
00:07.0 0280: 14e4:4320 (rev 03)
```

---

### Post by lwfinger on 2008-10-22
Your data are not correct - as you probably have seen the data should be a string of hexadecimal digits. For completeness, the commands should be:

SPROM=$(find /sys -name ssb_sprom)
echo $SPROM
sudo cat $SPROM

Larry

---

### Post by cowanh00 on 2008-10-22
> **lwfinger said:**
> Your data are not correct - as you probably have seen the data should be a string of hexadecimal digits. For completeness, the commands should be:

SPROM=$(find /sys -name ssb_sprom)
echo $SPROM
sudo cat $SPROM

Larry

OK, lets try again!

The 2nd command give me this:
```
/sys/devices/pci0000:00/0000:00:07.0/ssb_sprom
```

And the 3rd command gives me this:
```
014000001300371720430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0F001B66044CFFFFFFFFFFFFFFFFFFFFFFFFFFFF4510A01277FBACFEFFFFFFFF3C000000000000003E000D00FFFF0000000000000000016D
```

Looks better now.

---

### Post by lwfinger on 2008-10-22
Cowanh00,

Please copy and paste the following data into a file sprom.new. The entire string should be on a single line without any spaces or other strange formatting:

014000001300371720430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0F001B66044CFFFFFFFFFFFFFFFFFFFFFFFFFFFF4510A01277FBACFEFFFFFFFF3C000000000000003E000C00FFFF00000000000000000159


Once you have the file, run the 3 commands below:

SPROM=$(find /sys -name ssb_sprom)
echo $SPROM
sudo cp sprom.new $SPROM

Larry

---

### Post by cowanh00 on 2008-10-23
> **lwfinger said:**
> Cowanh00,

Please copy and paste the following data into a file sprom.new. The entire string should be on a single line without any spaces or other strange formatting:

014000001300371720430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0F001B66044CFFFFFFFFFFFFFFFFFFFFFFFFFFFF4510A01277FBACFEFFFFFFFF3C000000000000003E000C00FFFF00000000000000000159


Once you have the file, run the 3 commands below:

SPROM=$(find /sys -name ssb_sprom)
echo $SPROM
sudo cp sprom.new $SPROM

Larry

It worksssssss! :guitar: 

I wouldn't say it is perfect as for example when my desktop is under the desk it detects the network but won't connect, as soon as I pull it out from under the desk, the signal stays about the same but it connects.

Thanks again for your help.

---

### Post by AlexZaim on 2008-11-07
Hello! I have been trying all day to fix it.
Before i begin i want to mention that i was trying other drivers from the internet and various tutorials on how to get it run with 'ndiswrapper'.
I believe that b43 is a driver right that comes with the sistem,right?
Well,here is the thing: i think i have blacklisted it.
I also modified some files that had to do with 'modprobe' ...
So that's my history , in case something will go wrong/not work, i gues you'll know where it comes from. A big thanx in advance!!

Here is goes:
```
lspci
```
output: the 2 lines
```
05:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:12f8]
```

```
SPROM=$(find /sys -name ssb_sprom)
```

output:
01400000F8123C1020430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0000FFFFFFFFFFFFFFFFFFFFFFFFFFFF9000F34BECFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF3130AA14C8FA9FFEFFFFFFFF4C00FFFFFFFFFFFF3E00493A02FF535510FFFFFFFFFF0206

---

### Post by Ayuthia on 2008-11-23
> **lwfinger said:**
> I recently fixed a driver bug that affected my BCM4306/3 PCI card.
Has this bug fix been released?  If so, do you recall which kernel it was released?  I am seeing an occasional post for Intrepid users for the 4306 card and wasn't for sure if they should be sent to this post.

---

### Post by notanerd on 2008-11-23
evan@durruti:~$ SPROM=$(find /sys/devices -name ssb_sprom)
evan@durruti:~$ sudo cat $SPROM > sprom.dat
[sudo] password for evan: 
evan@durruti:~$ 

the sprom comes up with nothing for me

lspci -n comes up with this

00:00.0 0600: 1106:3188 (rev 01)
00:01.0 0604: 1106:b188
00:0a.0 0607: 1524:1410
00:0c.0 0280: 14e4:4320 (rev 03)
00:10.0 0c03: 1106:3038 (rev 80)
00:10.1 0c03: 1106:3038 (rev 80)
00:10.2 0c03: 1106:3038 (rev 80)
00:10.3 0c03: 1106:3104 (rev 82)
00:11.0 0601: 1106:3177
00:11.1 0101: 1106:0571 (rev 06)
00:11.5 0401: 1106:3059 (rev 50)
00:11.6 0780: 1106:3068 (rev 80)
00:12.0 0200: 1106:3065 (rev 74)
00:13.0 0c00: 1106:3044 (rev 80)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0300: 1002:4e50

---

### Post by lwfinger on 2008-11-23
To notanerd,

There has been sort of a rolling implementation as we have found these cards, but I believe all were fixed in 2.6.27.

To tell if your card is affected, I need the output of 'lspci -nnv' for the BCM4306. It is the subvendor codes that are important.

Larry

---

### Post by lwfinger on 2008-11-23
To Honor_Jesus,

Your SPROM needs to be updated. The new contents are

01400000F8123C1020430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0000FFFFFFFFFFFFFFFFFFFFFFFFFFFF9000F34BECFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF3130AA14C8FA9FFEFFFFFFFF4C00FFFFFFFFFFFF3E00483A02FF535510FFFFFFFFFF0232

Copy that data to a file name sprom.new. In the file, there should be a single line with no spaces, just the Hex digits. Once you have the file, use the following commands:

SPROM=$(find /sys -name ssb_sprom)
sudo cp sprom.new $SPROM

These two commands should not produce any output.

Sorry to take so long to reply. I missed your posting.

Larry

---

### Post by notanerd on 2008-11-23
00:0c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Broadcom Corporation Unknown device [14e4:0418]
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at d0000000 (32-bit, non-prefetchable) [size=8K]

---

### Post by lwfinger on 2008-11-23
Notanerd,

Your device (Linksys 0x0418) is not one that we know about; however, it could be a problem.

Please run the commands below:

SPROM=$(find /sys -name ssb_sprom)
sudo cat $SPROM

Post the string of hexadecimal characters and I'll see if it fits the pattern.

Larry

---

### Post by notanerd on 2008-11-23
014000001804e41420430080020002000010001800000000ffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffffff90007c4be74dffffffffffffffffffffffffffff44369a1193fba5feffffffff3c000000000000003e000d00ffff0000000000000000013b

---

### Post by lwfinger on 2008-11-23
Notanerd,

I misread your vendor code. Your card is from Broadcom itself. The board flags code in there likely has the problem.

Copy the following data to a file named sprom.new. The data must be in a single line with no spaces in the string:

014000001804E41420430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF90007C4BE74DFFFFFFFFFFFFFFFFFFFFFFFFFFFF44369A1193FBA5FEFFFFFFFF3C000000000000003E000C00FFFF0000000000000000010F

Once you have the file, run the following commands:

SPROM=$(find /sys -name ssb_sprom)
sudo cp sprom.new $SPROM

Those commands should not produce any output. If this does allow your BCM4306 to work, please let me know as this will lead to a new kernel patch.

Larry

---

### Post by notanerd on 2008-11-24
what kind of file should i use? How do i create it? sorry i'm a bit of a computer retard

---

### Post by lwfinger on 2008-11-24
It should be a text file created with any text editor that you like. I use vim, but kate would be easier for you.

Larry

---

### Post by notanerd on 2008-11-24
ok thats done, there was no output after i entered the commands and i rebooted the computer. as far as i can tell i am not wireless

is there a command i should run to check?

---

### Post by lwfinger on 2008-11-24
The next thing to do is to see what the logs have to say. Run the command 'dmesg | grep b43' and post the output.

The next thing to do is run the command '/usr/sbin/iwconfig' and post that output.

The final thing is to run the command 'sudo /usr/sbin/iwlist scan' and post that output.

Larry

---

### Post by notanerd on 2008-11-24
dmesg | grep b43

[   21.720770] b43-phy0: Broadcom 4306 WLAN found
[  248.618973] input: b43-phy0 as /devices/virtual/input/input9
[  249.634174] Registered led device: b43-phy0:tx
[  249.634390] Registered led device: b43-phy0:rx
[  249.634520] Registered led device: b43-phy0:radio

/usr/sbin/iwconfig

 /usr/sbin/iwconfig: No such file or directory

sudo /usr/sbin/iwlist scan

sudo: /usr/sbin/iwlist: command not found

---

### Post by Ayuthia on 2008-11-24
> **notanerd said:**
> dmesg | grep b43

[   21.720770] b43-phy0: Broadcom 4306 WLAN found
[  248.618973] input: b43-phy0 as /devices/virtual/input/input9
[  249.634174] Registered led device: b43-phy0:tx
[  249.634390] Registered led device: b43-phy0:rx
[  249.634520] Registered led device: b43-phy0:radio

/usr/sbin/iwconfig

 /usr/sbin/iwconfig: No such file or directory

sudo /usr/sbin/iwlist scan

sudo: /usr/sbin/iwlist: command not found

Can you try this:
```
iwconfig
sudo iwlist scan
```There really should not be a difference between the two, but I recall that the commands worked earlier for you.

---

### Post by notanerd on 2008-11-24
evan@durruti:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

evan@durruti:~$ sudo iwlist scan
[sudo] password for evan: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

### Post by lwfinger on 2008-11-24
We know that the firmware was loaded.

For Ubuntu, you should use '/sbin/iwconfig' and 'sudo /sbin/iwlist scan'. The commands I gave you were for openSUSE, which is what I use.

Larry

---

### Post by notanerd on 2008-11-25
ok so where to form here then?

---

### Post by lwfinger on 2008-11-25
Run the new versions of the commands. I still need the output of iwconfig and iwlist.

---

### Post by notanerd on 2008-11-25
evan@durruti:~$ sudo /sbin/iwconfig
[sudo] password for evan: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

evan@durruti:~$ sudo /sbin/iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

---

### Post by notanerd on 2008-11-30
Anyone out there?

---

### Post by lwfinger on 2008-11-30
As far as I can tell, you just need to configure the device. I don't have Hardy running, but I installed a new copy of Intrepid. It found my BCM4306/3 and installed the firmware when I went to the restricted code page. From there, I put in the encryption stuff and it just worked.

---

### Post by notanerd on 2008-11-30
Sorry if I am getting annoying but I don't understand what I need to do to configure the device. I have tried to use ndiswrapper and fw cutter and neither of them seemed to work. Is there an actual process for configuring the wireless?
Do you mean entering in the internet connection information?

---

### Post by lwfinger on 2008-12-01
You are a little confused about what ndiswrapper and fwcutter actually do.

You use ndiswrapper to employ a Windows driver when there is no native Linux driver. This may or may not work, but it always carries the risk of inserting a piece of Windows code into the inner most ring of the OS. As these drivers cause the Blue Screens of Death, they may crash Linux.

The program fwcutter is used to extract Broadcom firmware from a driver for some other OS so that b43 or b43legacy can load that firmware into the Broadcom device at startup. You have used it already because your system does not complain that the firmware is missing. You would see such messages from the output of 'dmesg | grep b43'.

Yes, you need to configure the device using whatever tools Ubuntu provides.

Larry

---

### Post by electroweak on 2008-12-05
Hi guys..
I just installed both 8.04.1 and 8.10 to my compaq notebook with BCM4306 (rev3) wifi card. there were no problems during the installation. After I applied available updates I logged in to restricted drivers manager to activate the wifi card. It's fetched and extracted firmware without any errors. then I restarted the computer. Now wifi light is on but I cant see any networks. the output of "iwlist scan" is "no scan results".

I don't know if I am having the same problem with other folks but it's really frustrating. I attached dmesg. messages and syslog, I thought they might be useful to identify the problem.

any help will greatly be appreciated.

---

### Post by lwfinger on 2008-12-05
Everything looks normal. The firmware loaded, etc.

What does 'sudo iwlist wlan0 scan' show? You will likely have to give the full path for iwlist.

I also need to see the output (FOR THE BCM4306 ONLY) of the command 'lspci -nnv'. Again you will likely need the full path.

---

### Post by notanerd on 2008-12-06
sounds like you have the exact same problem as me Electro

---

### Post by electroweak on 2008-12-06
this happened about a week ago when Kubuntu 8.04.1 was installed on the system. one day wifi suddenly disappeared. I tried to find a work around but then I decided to try another distro and I installed opengeu but no luck with that either just like hardy and intrepid.
when I run "sudo iwlist wlan0 scan" output is "No scan results" and "pan0" is visible when I "run sudo iwlist scan" I don't remember seeing that before. I uploaded the lspci -nnv. sorry but I couldn't understand the "full path" can you tell me how can I give the full path.

---

### Post by Ayuthia on 2008-12-06
> **electroweak said:**
> this happened about a week ago when Kubuntu 8.04.1 was installed on the system. one day wifi suddenly disappeared. I tried to find a work around but then I decided to try another distro and I installed opengeu but no luck with that either just like hardy and intrepid.
when I run "sudo iwlist wlan0 scan" output is "No scan results" and "pan0" is visible when I "run sudo iwlist scan" I don't remember seeing that before. I uploaded the lspci -nnv. sorry but I couldn't understand the "full path" can you tell me how can I give the full path.

What lwfinger was saying by full path is to use sudo /sbin/iwlist wlan0 scan and /bin/lspci -nnv.  However, you don't really need the full path since you did get the results when typing it without the full path.

---

### Post by lwfinger on 2008-12-06
The full path of a file is the one that starts at the root of the file system (/), and continues all the way along the chain. For example, when you type the command 'ls', the shell searches through all the directories in your PATH to find an executable file named 'ls'. On my system, the "full path" for that command is "/bin/ls".

Different distros place commands in different directories. On openSUSE, which is what I use, the lspci, iwconfig, and iwlist commands are in directories that are not in the path of the general, unprivileged user, thus I need to specify '/sbin/lspci', '/sbin/iwconfig', and '/usr/sbin/iwlist' to use those commands. On Ubuntu, they are in different places, which is why I said what I did.

---

### Post by electroweak on 2008-12-06
mmm guys I forgot to add lspci -nnv output here. I've just realized sorry for wasting your time :)

00:00.0 Host bridge [0600]: nVidia Corporation nForce3 Host Bridge [10de:00d1] (rev a4)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-amd64
	Kernel modules: amd64-agp

00:01.0 ISA bridge [0601]: nVidia Corporation nForce3 LPC Bridge [10de:00d0] (rev a6)
	Subsystem: nVidia Corporation Device [10de:0c80]
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0

00:01.1 SMBus [0c05]: nVidia Corporation nForce3 SMBus [10de:00d4] (rev a4)
	Subsystem: Hewlett-Packard Company Device [103c:006d]
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 10
	Region 4: I/O ports at 2040 [size=64]
	Region 5: I/O ports at 2000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2

00:02.0 USB Controller [0c03]: nVidia Corporation nForce3 USB 1.1 [10de:00d7] (rev a5) (prog-if 10)
	Subsystem: nVidia Corporation Device [10de:0c80]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at e8000000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.1 USB Controller [0c03]: nVidia Corporation nForce3 USB 1.1 [10de:00d7] (rev a5) (prog-if 10)
	Subsystem: nVidia Corporation Device [10de:0c80]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin B routed to IRQ 20
	Region 0: Memory at e8001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd

00:02.2 USB Controller [0c03]: nVidia Corporation nForce3 USB 2.0 [10de:00d8] (rev a2) (prog-if 20)
	Subsystem: nVidia Corporation Device [10de:0c80]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Interrupt: pin C routed to IRQ 22
	Region 0: Memory at e8004000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:06.0 Multimedia audio controller [0401]: nVidia Corporation nForce3 Audio [10de:00da] (rev a2)
	Subsystem: Hewlett-Packard Company Device [103c:006d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (500ns min, 1250ns max)
	Interrupt: pin A routed to IRQ 21
	Region 0: I/O ports at 1400 [size=256]
	Region 1: I/O ports at 1c00 [size=128]
	Region 2: Memory at e8002000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

00:06.1 Modem [0703]: nVidia Corporation nForce3 Audio [10de:00d9] (rev a2)
	Subsystem: Hewlett-Packard Company Device [103c:006d]
	Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin B routed to IRQ 22
	Region 0: I/O ports at 1800 [size=256]
	Region 1: I/O ports at 1c80 [size=128]
	Region 2: Memory at e8003000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel modules: snd-intel8x0m

00:08.0 IDE interface [0101]: nVidia Corporation nForce3 IDE [10de:00d5] (rev a5) (prog-if 8a [Master SecP PriP])
	Subsystem: Device [f0de:0c80]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0 (750ns min, 250ns max)
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	Region 4: I/O ports at 2080 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd

00:0a.0 PCI bridge [0604]: nVidia Corporation nForce3 PCI Bridge [10de:00dd] (rev a2)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Bus: primary=00, secondary=02, subordinate=0a, sec-latency=128
	I/O behind bridge: 00003000-00007fff
	Memory behind bridge: e8100000-e97fffff
	Prefetchable memory behind bridge: 30000000-37ffffff
	Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr+ DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:0b.0 PCI bridge [0604]: nVidia Corporation nForce3 AGP Bridge [10de:00d2] (rev a4)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 16
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
	Memory behind bridge: ea000000-eaffffff
	Prefetchable memory behind bridge: f8000000-fc0fffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity+ SERR+ NoISA+ VGA+ MAbort- >Reset- FastB2B-
		PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
	Kernel modules: shpchp

00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Capabilities: <access denied>

00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-

00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:00.0 VGA compatible controller [0300]: nVidia Corporation NV17 [GeForce4 420 Go 32M] [10de:0176] (rev a3)
	Subsystem: Hewlett-Packard Company Device [103c:006d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at ea000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Region 2: Memory at fc000000 (32-bit, prefetchable) [size=512K]
	[virtual] Expansion ROM at fc080000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: rivafb, nvidiafb

02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (8000ns min, 16000ns max)
	Interrupt: pin A routed to IRQ 18
	Region 0: I/O ports at 7000 [size=256]
	Region 1: Memory at e8104000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too

02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:12f4]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at e8100000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

02:04.0 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:006d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168, Cache Line Size: 128 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at e8102000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
	Memory window 0: 30000000-33fff000 (prefetchable)
	Memory window 1: e8400000-e87ff000
	I/O window 0: 00003000-000030ff
	I/O window 1: 00003400-000034ff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:04.1 CardBus bridge [0607]: Texas Instruments PCI1620 PC Card Controller [104c:ac54] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:006d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 168, Cache Line Size: 128 bytes
	Interrupt: pin B routed to IRQ 18
	Region 0: Memory at e8103000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
	Memory window 0: 34000000-37fff000 (prefetchable)
	Memory window 1: e8c00000-e8fff000
	I/O window 0: 00003800-000038ff
	I/O window 1: 00003c00-00003cff
	BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

02:04.2 System peripheral [0880]: Texas Instruments PCI1620 Firmware Loading Function [104c:8201] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:006d]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (1750ns min, 1000ns max), Cache Line Size: 64 bytes
	Region 0: I/O ports at 7400 [size=64]
	Capabilities: <access denied>

---

### Post by lwfinger on 2008-12-06
I only needed it for the BCM4306, not everything. In any case, the line "Subsystem: Hewlett-Packard Company Device [103c:12f4]" from your BCM4306 says that you have one of the devices with the faulty SPROM programming. You have 3 options: (1) Switch to Intrepid (8.10), (2) Install the b43-sprom update code, or (3) Post your SPROM contents here so that I can revise them for you to rewrite them.

As I expect you will choose #3, please open a terminal and perform the following commands:

SPROM=$(find /sys -name ssb_sprom)
echo $SPROM
sudo cat $SPROM

Post the output of these commands here. The last one will be a string of hexadecimal characters.

Larry

---

### Post by electroweak on 2008-12-07
I thought rest of the information might be necessary so I posted all.
anyway as you expected I am going to choose the #3. but I have to mention I am using 8.10 right now but still have the same problem.

my terminal output is;

atilla@ubuntu:~$ SPROM=$(find /sys -name ssb_sprom)
atilla@ubuntu:~$ echo $SPROM
/sys/devices/pci0000:00/0000:00:0a.0/0000:02:02.0/ssb_sprom
atilla@ubuntu:~$ sudo cat $SPROM
[sudo] password for atilla: 
01400000F4123C1020430080020002000010001800000000
FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
90009E4B2B7DFFFFFFFFFFFFFFFFFFFFFFFFFFFF60369A11
93FBA5FEFFFFFFFF3C000000000000003E000D00FFFF0000
0000000000000166
atilla@ubuntu:~$

---

### Post by lwfinger on 2008-12-07
Your new SPROM contents should be

01400000F4123C1020430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF90009E4B2B7DFFFFFFFFFFFFFFFFFFFFFFFFFFFF60369A1193FBA5FEFFFFFFFF3C000000000000003E000C00FFFF00000000000000000152

That data should be copy-and-pasted into a file named sprom.new. All the data must be on onne line with no spaces or anything besides the hex digits.

Once the file is prepared, do the following:

SPROM=$(find /sys -name ssb_sprom)
sudo cp sprom.new $SPROM

The above two commands should not produce any output.

Once that is done, unload and reload b43 with

sudo /sbin/modprobe -rv b43
sudo /sbin/modprobe -v b43

and your device should work.

Larry

---

### Post by electroweak on 2008-12-07
No luck :(
I followed all steps but I still can't get any scan results. that's weird I was able to use it about a week ago:confused:
I have created sprom.new file in the /home directory do you think that's ok. I decided to put that there because sprom.dat file appeared in my /home directory after I've run commands that you gave me.

---

### Post by lwfinger on 2008-12-08
I know you recently changed to 8.10. Did anything else happen at that time? I have tried 8.10 with my BCM4306 and it worked right away, so I doubt that it is a generic problem.

What does the output of 'dmesg | grep b43' show?

If you did the 'sudo cp sprom.new $SPROM' step, then it will not need to be done again. It doesn't matter what directory sprom.new is in as long as the command was run in that directory.

Larry

---

### Post by electroweak on 2008-12-08
It was a fresh installation I just installed wine in it. restricted drivers manager says driver is activated.I am going to install 8.10 again but I want to ask if the solution that you told me needs to be applied each time the OS installed or if it is permanent fix.

here is the dmesg output

atilla@ubuntu:~$ dmesg | grep b43
[    7.628179] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   27.972872] b43-phy0: Broadcom 4306 WLAN found
[   45.720513] input: b43-phy0 as /devices/virtual/input/input12
[   45.796397] firmware: requesting b43/ucode5.fw
[   45.915820] firmware: requesting b43/pcm5.fw
[   45.950044] firmware: requesting b43/b0g0initvals5.fw
[   45.990830] firmware: requesting b43/b0g0bsinitvals5.fw
[   46.223459] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   46.377140] Registered led device: b43-phy0::tx
[   46.377721] Registered led device: b43-phy0::rx
[   46.378194] Registered led device: b43-phy0::radio
atilla@ubuntu:~$

---

### Post by lwfinger on 2008-12-08
Reinstallation seems to be a good thing to try.

Once the SPROM is rewritten, the contents stay the same. You will never have to do that again.

Good luck.

---

### Post by fritos75 on 2008-12-08
I have the same problem with my BCM4306, if someone could help me, I'm just getting crazy with this intrepid....:mad:

 ```
lspci
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
```

```
lspci -nnv
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Hewlett-Packard Company Device [103c:12f4]
	Flags: bus master, fast devsel, latency 64, IRQ 17
	Memory at e8104000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
```
```

dmesg | grep b43
[    5.363201] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   24.015053] b43-phy0: Broadcom 4306 WLAN found
[   48.992513] input: b43-phy0 as /devices/virtual/input/input10
[   49.072141] firmware: requesting b43/ucode5.fw
[   49.854767] firmware: requesting b43/pcm5.fw
[   50.048903] firmware: requesting b43/b0g0initvals5.fw
[   50.214707] firmware: requesting b43/b0g0bsinitvals5.fw
[   50.587769] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   50.587860] b43-phy0 ERROR: Initial Values Firmware file-format error.
[   50.587870] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[   50.764249] input: b43-phy0 as /devices/virtual/input/input11
[   52.072104] b43-phy0 ERROR: Microcode not responding
[   52.072125] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[17208.627321] b43-pci-bridge 0000:02:02.0: PCI INT A disabled
[17512.065318] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[17512.255473] b43-phy1: Broadcom 4306 WLAN found
[17516.538730] input: b43-phy1 as /devices/virtual/input/input12
[17516.604060] firmware: requesting b43/ucode5.fw
[17516.857059] firmware: requesting b43/pcm5.fw
[17516.896877] firmware: requesting b43/b0g0initvals5.fw
[17516.937372] firmware: requesting b43/b0g0bsinitvals5.fw
[17517.064065] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[17517.216837] Registered led device: b43-phy1::tx
[17517.217548] Registered led device: b43-phy1::rx
[17517.218027] Registered led device: b43-phy1::radio
[17522.351433] input: b43-phy1 as /devices/virtual/input/input13
[17522.547844] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[17522.704621] Registered led device: b43-phy1::tx
[17522.705165] Registered led device: b43-phy1::rx
[17522.705615] Registered led device: b43-phy1::radio
[17594.826185] input: b43-phy1 as /devices/virtual/input/input14
[17595.017352] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[17595.136663] Registered led device: b43-phy1::tx
[17595.138355] Registered led device: b43-phy1::rx
[17595.139954] Registered led device: b43-phy1::radio
[17646.391134] input: b43-phy1 as /devices/virtual/input/input15
[17646.590705] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[17646.713071] Registered led device: b43-phy1::tx
[17646.713613] Registered led device: b43-phy1::rx
[17646.714059] Registered led device: b43-phy1::radio
[18852.552291] b43-pci-bridge 0000:02:02.0: PCI INT A disabled
[18871.474399] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[18871.572901] b43-phy0: Broadcom 4306 WLAN found
[18875.975151] input: b43-phy0 as /devices/virtual/input/input16
[18876.040069] firmware: requesting b43/ucode5.fw
[18876.046820] firmware: requesting b43/pcm5.fw
[18876.056412] firmware: requesting b43/b0g0initvals5.fw
[18876.082193] firmware: requesting b43/b0g0bsinitvals5.fw
[18876.258622] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[18876.413967] Registered led device: b43-phy0::tx
[18876.415646] Registered led device: b43-phy0::rx
[18876.417540] Registered led device: b43-phy0::radio
[18887.780130] input: b43-phy0 as /devices/virtual/input/input17
[18888.003332] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[18888.124486] Registered led device: b43-phy0::tx
[18888.125033] Registered led device: b43-phy0::rx
[18888.125484] Registered led device: b43-phy0::radio

```

```
SPROM=$(find /sys -name ssb_sprom)
01400000F4123C1020430080020002000010001800000000
FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
9000984BE0E4FFFFFFFFFFFFFFFFFFFFFFFFFFFF60369A11
93FBA5FEFFFFFFFF3C000000000000003E000D00FFFF0000
000000000000015B
```

```
b43-fwcutter -l
b43-fwcutter version 011

Extracting firmware is possible from these binary driver files.
The <ID> column shows the unique identifier string for your firmware.
You must select the firmware with the same ID as printed by the kernel driver on modprobe.
Note that only recent drivers print such a message on modprobe.
Please read http://linuxwireless.org/en/users/Drivers/b43#devicefirmware

<driver>	<filename>		<microcode>	<ID>	<MD5 checksum>

b43legacy	wl_apsta.o		295.14		FW10	e08665c5c5b66beb9c3b2dd54aa80cb3
b43		wl_apsta.o		351.126		FW11	9207bc565c2fc9fa1591f6c7911d3fc0
b43		wl_apsta_mimo.o		351.126		FW11	722e2e0d8cc04b8f118bb5afe6829ff9
b43		wl_apsta_mimo.o		410.2160	FW13	cb8d70972b885b1f8883b943c0261a3c
```

---

### Post by lwfinger on 2008-12-08
You can get as mad as you want, but target your anger in the right direction. The fault is that of HP and Broadcom for producing a device with the SPROM coded incorrectly.

Your revised SPROM contents are

01400000F4123C1020430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF9000984BE0E4FFFFFFFFFFFFFFFFFFFFFFFFFFFF60369A1193FBA5FEFFFFFFFF3C000000000000003E000C00FFFF0000000000000000016F

Copy and paste the above data into a file named sprom.new. The data should be on one line with no spaces, etc. - only the hex characters.

Once the file is prepared, run the following:

SPROM=$(find /sys -name ssb_sprom)
sudo cp sprom.new $SPROM

One thing I do not understand - did you reload the firmware, or was that firmware loading error at 50.78 seconds an isolated event.

Larry

---

### Post by fritos75 on 2008-12-09
Thanks for quik help, but it doesn't seem to work  
You are right i should be angry with HP instead of intrepid. In my case, it has been working with intrepid, but it isn't the case still kernel upgrade to 2.6.27-9-generic. (6 days ago). With hardy and previous ubuntu version, i didn't have any problem, i don't really undersatnd what's wrong ??!!
I have never try ndiswrapper....I hate having Microsoft code in my ubuntu :p

```
dmesg | grep b43
[    5.152594] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   23.865753] b43-phy0: Broadcom 4306 WLAN found
[  104.720328] input: b43-phy0 as /devices/virtual/input/input10
[  104.876059] firmware: requesting b43/ucode5.fw
[  105.058322] firmware: requesting b43/pcm5.fw
[  105.113460] firmware: requesting b43/b0g0initvals5.fw
[  105.163070] firmware: requesting b43/b0g0bsinitvals5.fw
[  105.376071] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  105.540426] Registered led device: b43-phy0::tx
[  105.542234] Registered led device: b43-phy0::rx
[  105.543824] Registered led device: b43-phy0::radio

```

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:
```0

---

### Post by notanerd on 2008-12-09
has anyone actually gotten the BCM4306 Revision 3 card to work in ubuntu? It seems like a dud, it just doesn't want to work.

---

### Post by lwfinger on 2008-12-09
To fritos75,

This morning I booted into Ubuntu (I usually run openSUSE on that machine) and updated to 2.6.27-9-generic. After rebooting, my BCM4306/3 worked immediately with no fussing on my WPA network. Is 2.6.27-7 still available? It was on my system. If it still works, that clears all the other parts of the system that might have been upgraded. I didn't keep track of all the packages that changed - there were 54 of them.

If 2.6.27-7 still works or is not available, I would try reinstalling the kernel package for 2.6.27-9. 

To notanerd,

Yes, mine works just fine in Ubuntu 8.10 and openSUSE 11.0.

Larry

---

### Post by fritos75 on 2008-12-10
Hello,
I have good news !
When I tried with previous kernel, it didn't work...I was feeling really disappointed, and shut off my ?###!!// HP computer.

This morning my wife has booted on Win XP (I have a dual boot). I turn on the wifi, and connect it. Then, when she left , I boot on my Ubuntu, and YES !!!!! It works. So it'really a problem with BIOS.

I don't move my laptop very much, but 9 days ago, I had to bring it with me, I think that's why my broadcom has been with no eletrical power for a long time. Since this moment I was trying to install it on Ubuntu.

But NOW IT WORKS :guitar: 
Anyway thanks to Larry for great help. (and my wife too ;-) and Billou ! ...no I'm joking !)

PS : Is it the advice we have to spread, "install Win xp to make Broadcom Works ??!!" (My laptop is a HP nx9105)

---

### Post by fritos75 on 2008-12-10
I think we have exactly the same problem. You need to install win XP (dual boot), to bring you broadcom card up ! Don't you have a HP nx9105 laptop ? I know it's a little bit strange, but in my case it works !
I know that Live cd XP exist, maybe it could do the work.
Bye

---

### Post by lwfinger on 2008-12-10
Some BIOS codes have a setting that lets Windows turn the power off when suspending. If you boot Linux from that state, then b43 will never be able to turn the power back on.

I tried to find one of the threads that describe this, but could not.

Check your BIOS for such a setting. If you cannot find it, then never suspend Windows, or at least wake it up and then shut down.

Larry

---

### Post by notanerd on 2008-12-11
I have just updgraded to 8.10 and still am not wireless. Any suggestions?

---

### Post by fritos75 on 2008-12-11
My BIOS is secured by HP. I explain : I only have the choice in the boot sequence. Welcome in HP world ):P

To notanerd,

do you have a multi boot ? do you have HP nx9105 laptop ?

---

### Post by electroweak on 2008-12-12
to fritos75
thanks for sharing "booting to XP" tip. Actually I don't have xp installed in my notebook. By the way my notebook is Compaq presario R3000 with Bcm4306 rev(3) wifi card. I used Reatogo-X-PE Boot CD which I have created by following the instructions on its web site years ago. After I've read your post I decided to give it a try before I reinstall 8.10. Kubuntu 8.04.1 installed right now. Anyway I booted to that live cd, it doesn't include my wifi driver so I couldn't get wifi running but after I've rebooted to Kubuntu everything was OK. 
But I have another question about that; there was no xp installed on the system so system didn't hibernated, what was the problem that makes my wifi card unusable. 

To lwfinger
thanks for all your advices and sprom update. my device is back to normal.

Atilla

---

### Post by notanerd on 2008-12-12
I am just running Ubuntu 8.10. My Laptop is an Emachines AMD64

---

### Post by Dr. Tingles on 2009-01-07
lspci -n output:

00:0c.0 0280: 14e4:4320 (rev 03)

sprom.dat could not be attached due to extension, contents follow:

0140000050704F142043008002000200F017001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF90006F96CBF5FFFFFFFFFFFFFFFFFFFFFFFFFFFF4530B01198FB4FFEFFFFFFFF3C00FFFFFFFFFFFF3E000F00FFFF000000000000000001A0

---

### Post by lwfinger on 2009-01-07
The revised data are

0140000050704F142043008002000200F017001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF90006F96CBF5FFFFFFFFFFFFFFFFFFFFFFFFFFFF4530B01198FB4FFEFFFFFFFF3C00FFFFFFFFFFFF3E000E00FFFF00000000000000000194

Copy these data to a file named sprom.new. It should all be on one line with no spaces - just the Hex characters. Once you have the file, run the following commands:

SPROM=$(find /sys -name ssb_sprom)
sudo  cp sprom.net  $SPROM

That will replace the SPROM contents. If this change makes your device start working, please let me know as this particular unit is not in our data base.

Larry

---

### Post by Dr. Tingles on 2009-01-08
[SIZE="2"][/SIZE]Larry,
  I did as you instructed and I'm posting this from a 54Mb/s WPA enabled wifi connection!  Thank you very much.  I tried to follow the instructions from the linuxwireless.org site and received an error that my SPROM was rev.1 and was unable (read=newb) to make it work.  Just for the sake of those following this thread I will list the steps [SIZE="4"][COLOR="Red"]I[/COLOR][/SIZE][COLOR="Black"][/COLOR] [SIZE="2"][/SIZE]took to follow your instructions.

First I entered:
```
find /sys -name ssb_sprom
```
On my m5312 emachines laptop the above command yielded two devices:
/sys/devices/pci0000:00/0000:00:0c.0/ssb_sprom
/sys/devices/pci0000:00/0000:00:0e.0/ssb_sprom

To discover which was the BCM4306 I entered:
```
lspci -nn
```
Which gave me the Name & Number of my PCI devices.

Then, to isolate the proper device I entered your $SPROM command piped through grep with my PCI number as the filter, thus:
```
SPROM=$(find /sys -name ssb_sprom | grep 00:0c.0)
```

To create the file I entered:
```
echo "the hex number you supplied" > sprom.new
```
Where it reads "the hex number you supplied" I entered the hex number you supplied without the quotation marks.  Go figure.

I then checked the file with:
```
cat sprom.new
```

When I was satisfied that it was without spaces or carriage returns or any other anomolies I crossed my fingers, held my breath and entered:
```
sudo cp sprom.net $SPROM
```

I rebooted and was greeted with both my wired b44 and wireless b43 connections upon login!

Like I mentioned above, I was unable to work through the instructions on linuxwireless.org for the ssb-sprom tool.  So, Larry Finger, many many thanks to you.

I'm not very well versed in linux but if I can offer any more info, please feel free to ask.  I'll check back at this thread.

---

### Post by lwfinger on 2009-01-08
What is the name/model on your BCM4306? The SPROM says that the subvendor code is 0x144f and the model is 0x7050. Does that match what you see with an 'lspci -nnv' command? The numbers I need are the pair inside the [] near the end of the second line for the BCM4306.

Thanks,

Larry

---

### Post by notanerd on 2009-01-08
When I enter this command

SPROM=$(find /sys -name ssb_sprom | grep 00:0c.0)

I get the following output

find: `/sys/fs/fuse/connections/8388625': Permission denied
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

what should i use to be able to execute the command?

---

### Post by lwfinger on 2009-01-08
That "error" is harmless. I get it all the time on my system, but you will likely not need the "grep" part. Your commands should be

SPROM=$(find /sys -name ssb_sprom)
echo $SPROM

Only if the echo command yields more than one line will you need a "grep".

If the error message really bothers you, then replace the first line with

SPROM=$(sudo find /sys -name ssb_sprom)

Larry

---

### Post by notanerd on 2009-01-09
damn it, still not working

---

### Post by gusman21 on 2009-01-09
lspci -nnv 
```

02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Dell Device [1028:0003]
	Flags: bus master, fast devsel, latency 32, IRQ 5
	Memory at fafee000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb


```

sprom.dat
```

014000000300281020430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF9000FB96DA6AFFFFFFFFFFFFFFFFFFFFFFFFFFFF44309A1193FBA5FEFFFFFFFF3C000000000000003E000D00FFFF0000000000000000016C
^@

```

-=GuS=-

---

### Post by Dr. Tingles on 2009-01-10
Larry,
  I opened up the mini-pci compartment and didn't see an obvious manufacturer on the card.  There is notation on the board that says Vertex and then below that it says M1.  From the mac address the card decodes as an Askey Computer Corperation card but I don't know the model number.  I doubt this is enough information to nail down what the model of the card is but I will have a look for paperwork and see what I can find out.  If that fails, I'll pull the card and check the backside.  I'll try to get back to you about this over the weekend.
  As an update, I've had no problems since the resetting of the SPROM.  I have excellent signal strength and no dropped connections.  

Thanks again,
  Dr. T

---

### Post by Dr. Tingles on 2009-01-10
Larry,
  From the back of the mini-pci card it is an Askey Comp. Corp. model WLL3010.  

Dr. T

---

### Post by notanerd on 2009-01-10
ok so i have been having a look around and it seems like maybe installing the 32 bit version of ubuntu could result in me getting wireless working. Does anyone think there is any merit to this?

---

### Post by notanerd on 2009-01-11
I have wireless!!! I reinstalled ubuntu with the 32 bit rather than 64 and was able to connect with ndiswrapper. Thank you everyone that has been trying to help me with this

---

### Post by luc0zade on 2009-02-22
My Linksys WMP54G wireless PCI card isn't working and I think it might be because of the BCM4306 rev. 3 Bluetooth coexistance bug.

I did find  [a report on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257020") which seems to say a fix for this has been released, but if so, doesn't seem be working for me yet!  I'm using Hardy kernel 2.6.24-23.48-generic.

From my lspci output:-

00:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Linksys Unknown device [1737:0013]

...and my current SPROM:-

```
014000001300371720430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0F00F16698A6FFFFFFFFFFFFFFFFFFFFFFFFFFFF4510A01277FBACFEFFFFFFFF3C000000000000003E000D00FFFF000000000000000001B9
```

I've read dozens of posts about Broadcom 4306 and the B43 module but I'm still not clear what has to be done to fix this problem, so any help would be appreciated!

Thanks.

---

### Post by kevdog on 2009-02-22
Is this thread still relevant to the newer kernel >=2.6.27

---

### Post by lwfinger on 2009-02-22
luc0zade,

Your device is definitely one that has the problem. I have no idea if the fix has propagated through the Ubuntu kernels as I'm not a user.

You should write the new "code" below into the SPROM:

```
014000001300371720430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0F00F16698A6FFFFFFFFFFFFFFFFFFFFFFFFFFFF4510A01277FBACFEFFFFFFFF3C000000000000003E000C00FFFF0000000000000000018D
```

In case you need instructions, you should copy the above data into a file named sprom.new so that the data are all on one line with no extraneous spaces, etc. After that, run the following commands:

```
SPROM=$(find /sys -name ssb_sprom)
sudo cp sprom.new $SPROM

```
After those commands finish, use modprobe to unload and reload b43 - it should work.

Larry

---

### Post by lwfinger on 2009-02-22
kevdog,

The fix for the devices we know about are in 2.6.27 and later kernels; however, there may be some subvendor codes with the problem that have not been reported. Those will need addition to the b43 quirks list.

Larry

---

### Post by luc0zade on 2009-02-23
Larry, thanks for providing me with a correct SPROM, I've copied it successfully following your instructions.

Unfortunately however the wireless card is still not finding the network.  I realise it might be a problem with my router but I can connect to it okay with a Win XP machine.

Here's some more info on my setup:-

My updated SPROM:-

```
014000001300371720430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0F00F16698A6FFFFFFFFFFFFFFFFFFFFFFFFFFFF4510A01277FBACFEFFFFFFFF3C000000000000003E000C00FFFF0000000000000000018D
```

From LSPCI output:-

```
00:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Linksys Unknown device [1737:0013]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort-
<MAbort- >SERR- <PERR-
	Latency: 64
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at fedfe000 (32-bit, non-prefetchable) [size=8K]
```

From sudo lshw -C network:-

```
   *-network:0
        description: Ethernet interface
        product: 3c905 100BaseTX [Boomerang]
        vendor: 3Com Corporation
        physical id: 11
        bus info: pci@0000:00:11.0
        logical name: eth0
        version: 00
        serial: 00:60:08:78:ca:b3
        size: 10MB/s
        capacity: 100MB/s
        width: 32 bits
        clock: 33MHz
        capabilities: bus_master ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=3c59x multicast=yes port=MII speed=10MB/s
   *-network:1
        description: Network controller
        product: BCM4306 802.11b/g Wireless LAN Controller
        vendor: Broadcom Corporation
        physical id: 12
        bus info: pci@0000:00:12.0
        version: 03
        width: 32 bits
        clock: 33MHz
        capabilities: bus_master
        configuration: driver=b43-pci-bridge latency=64 module=ssb
   *-network
        description: Wireless interface
        physical id: 1
        logical name: wlan0
        serial: 00:0f:66:f1:a6:98
        capabilities: ethernet physical wireless
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

From modprobe b43:-

```
b43                   144548  0
rfkill                  8596  3 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    34308  1 b43

```

From dmesg | grep b43:-

```
[  113.231171] b43-phy0: Broadcom 4306 WLAN found
[  113.258873] b43-phy0 debug: Found PHY: Analog 2, Type 2, Revision 2
[  113.258916] b43-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[  136.175389] input: b43-phy0 as /devices/virtual/input/input4
[  136.471747] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[  138.559657] b43-phy0 debug: Chip initialized
[  138.560871] b43-phy0 debug: 30-bit DMA initialized
[  138.561439] Registered led device: b43-phy0:tx
[  138.561542] Registered led device: b43-phy0:rx
[  138.561646] Registered led device: b43-phy0:radio
[  138.561709] b43-phy0 debug: Wireless interface started
[  138.561731] b43-phy0 debug: Adding Interface type 2
```

One puzzle is why there are references to 'Revision 2' at 113.258873 and 113.258916 in dmesg when all the other data suggests this card has the BCM4306 revision 3 chipset.  I've tried re-installing the firmware a few times and it seems to work okay - the radio LED on the card lights up as normal - however I can't get it to search and locate any networks - not mine or the neighbours!

Any suggestions gratefully received...

---

### Post by lwfinger on 2009-02-23
You did get the SPROM updated. It now has the expected (corrected) results.

You definitely have a Rev 3 BCM4306. If it were Rev 2, it would be loading b43legacy, not b43. In your device, the PHY and radio are Rev 2, which is what you are seeing.

Does your device scan for AP's? What does the command 
```
sudo /sbin/iwlist scan
```
show?

Larry

---

### Post by luc0zade on 2009-02-25
Larry, thanks for the advice, sorry I haven't replied sooner.

As suggested...

sudo iwlist scan

...seems to have got things moving.  I can now see the network although not connect - but I think that's because I need to sort out the encryption settings on the router.

Thanks so much for your help,

Aaron

---

### Post by cucio on 2009-03-13
Larry,

Thanks a bunch for your help, man, much appreciated.

EDIT: never mind, my ROM was fine. Thanks anyway.

---

### Post by lwfinger on 2009-03-13
Glad you got it sorted out. AFAIK, the only HP device with the problem has a subvendor ID of 12F8. Yours is 12FA.

Larry

---

### Post by XoliCB on 2009-03-25
> **lwfinger said:**
> I recently fixed a driver bug that affected my BCM4306/3 PCI card. If you are also having the same problem, please do the following to help me accumulate data regarding these cards:

Thanks,

Hey Dude, hope you can help me!
I've tried EVERYTHING with no luck.

my sprom is: 01200000F40128100C17000002350020F007001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF1A000FA08693FFFFFFFFFFFF0100FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF104B

Thanks in advance!

---

### Post by lwfinger on 2009-03-25
If you posted the contents of your SPROM correctly, something is wrong. My program says that you have an illegal value for the revision.

I'll see if I can recover the data, but you should extract it again and repost. What does the output of 

dmesg | egrep "ssb|b43"

 show?

---

### Post by XoliCB on 2009-03-26
You are right, probably it's from the wired NIC, as now I have 2 entries (think second it's wifi).
I copy everything you asked for plus an lspci:

xoli@emu:~$ SPROM=$(find /sys/ -name ssb_sprom)
xoli@emu:~$ sudo cat $SPROM > sprom.dat
xoli@emu:~$ cat sprom.dat
01200000F40128100C17000002350020F007001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF1A000FA08693FFFFFFFFFFFF0100FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF104B
014000001300371720430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0C006441F6FAFFFFFFFFFFFFFFFFFFFFFFFFFFFF4510A01277FBACFEFFFFFFFF3C000000000000003E000D00FFFF00000000000000000111
xoli@emu:~$ dmesg | egrep "ssb|b43"
[   20.090472] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[   20.090478] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[   20.090483] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[   20.090488] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[   20.090493] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[   20.093817] ssb: Sonics Silicon Backplane found on PCI device 0000:04:09.0
[   20.113627] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   20.113632] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   20.113638] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   20.157624] ssb: Sonics Silicon Backplane found on PCI device 0000:04:07.0
xoli@emu:~$ lspci
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
04:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Thanks again!

---

### Post by lwfinger on 2009-03-26
Your card is definitely one of those that have the problem. The revised contents of the SPROM should be

014000001300371720430080020002000010001800000000FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF0C006441F6FAFFFFFFFFFFFFFFFFFFFFFFFFFFFF4510A01277FBACFEFFFFFFFF3C000000000000003E000C00FFFF00000000000000000125

Copy the above data into a file named sprom.new. It should be on one line with no embedded spaces. Once you have done that, run the following code

SSB_SPROM=$(find /sys/devices -name ssb_sprom | grep 04:09.0)
echo $SSB_SPROM

You should see only a single listing. If so, then do the following

sudo cp sprom.new $SSB_SPROM

That will update the SPROM, and your device should work.

---

### Post by XoliCB on 2009-03-28
Well, it finally worked.

After updating SPROM I tried with ndiswrapper ans b43+ssb without any exit.

Ndiswrapper simply hangs up the computer and b43+ssb keeps giving authentication error.

At last I tried bcm43xx option and it's working by unloading ssb and loading bcm43xx, but still don't know how to make it work on boot-up.

Anyway I got wifi, thanks a lot for your help, get a beer from me!

---

### Post by lwfinger on 2009-03-28
With ndiswrapper, you are running Windows kernel code with no protection. What did you expect? BSOD is the answer.

To use bcm43xx, you didn't need the SPROM change. I'm not an Ubuntu expert so I cannot tell you how to have it load from the start.

Do you have the firmware on the right directory for b43? It needs to be in /lib/firmware/b43/.

---

### Post by XoliCB on 2009-03-30
Yes, the firmware is on the right place, and actually the card is working.

The problem is a timeout in autentication since I updated (and fresh installed) to Hardy, but forget it, I'm happy with this solution.

---

