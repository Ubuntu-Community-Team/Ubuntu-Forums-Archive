---
title: "HOW TO: Connecting HUAWEI E220 through Vodafone Portugal"
date: 2007-01-26
forum: Networking &amp; Wireless
---

### Post by luis.peralta on 2007-01-26
Hi all!
Using the how to made by Daka to establish connection with this device in Vodafone Spain, i got my own device working in Portugal with Vodafone Portugal.


**Main Problem:**
This model 'E220 from Huawei' also known as Vodafone Connect Box in Portugal, is detected as usb-storage device instead of a dial up modem.


**Kernel version used:**
Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006


--------------------------------------------------------------------------------------
**Here's the step by step HOW TO (almost identical to Daka's how to):**


**STEP1 - Inicial setup:**
->_Plug your SIM card in a mobile phone, and remove the PIN authentication._
->First, in terminal give permission of rwx for all groups to the following files:
#  sudo chmod -c a+rwx /etc/wvdial.conf
#  sudo chmod -c a+rwx /etc/ppp/pap-secrets
#  sudo chmod -c a+rwx /etc/ppp/chap-secrets

->With vi in terminal or kate in x (for example), change the content of /etc/wvdial.conf to:
[Dialer hsdpa]
Phone = *99***1#
Username = vodafone
Password = vodafone
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","internet.vodafone.pt";

->With that inicial setup completed, _we can now reboot with the device unplugged_


**STEP2 - Overriding the usb-storage detection problem:**
->Go to System Settings -> Network Settings and deactivate any ethernet or wireless connections.
->Plug the Vodafone 3G into the usb port and, after the detection, click cancel to do nothing with it.
->Enter in terminal and type the following:

#  sudo rmmod usb-storage
Password? (type your password here)
#  modprobe usbserial vendor=0x12d1 product=0x1003
(if that command produces an error, try it with "sudo" at the beggining of the command line)

->remove Vodafone 3G from usb and with ## ls -la /dev/ttyU* ## wait to get the following result:
#  ls -la /dev/ttyU*
ls: /dev/ttyU*: Non existent file or directory

->after the deactivation we made above, plug the device, and wait to get the following, again with the same ls command:
#  ls -la /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2007-01-26 11:59 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2007-01-26 11:59 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2007-01-26 11:59 /dev/ttyUSB2

**NOTE:** until you can't get the USB0, USB1 and USB2 listed, there's no reason to continue this howto. It can be a problem to have them listed and the only solution i've found is repeating this _step_ from the beggining. If someone knows why that happens, or if someone found a better way to have them listed, please post a reply on this thread.


**STEP3 - Connection to Internet via Vodafone Portugal:**
->after USB0 USB1 and USB2 got detected, type the following to connect:
#  wvdial hsdpa

->If it works you'll get the following or something like it:
Connection log:
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1S0=0+IFC=2,2
ATE0V1&D2&C1S0=0+IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP","internet.vodafone.pt";
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Fri Jan 26 11:59:19 2007
--> Pid of pppd: 7170
--> Using interface ppp0
--> local  IP address 87.103.53.253
--> remote IP address 10.64.64.64
--> primary   DNS address 212.18.160.133
--> secondary DNS address 212.18.160.134

->That's it! you got connected :)
->Now keep the terminal open to keep the connection on, and fire up firefox/konkeror/whatever ;)


**Final Note:**
if you accidently close terminal, while you don't reboot you should be able to connect only following STEP3.

Good Luck/Boa Sorte! :)

---

### Post by svenkatesan on 2007-02-15
Hi 
I am from singapore.
I just got this E220 modem and want to surf from Ubuntu.
I read thro your how-to?
I have a doubt in the first line
"Plug your sim card in Mobile Phone and remove the PIN authentication"
Here,the modem has a slot to insert the SIM card but no Phone.
Can you pl expalin on this?
Thanks

---

### Post by luis.peralta on 2007-02-15
that's simple. just remove the sim card from the huawei device and plug it into any cell phone (i supose you can get your hands in one don't you?).
then, at the mobile phone, go to the phone security settings and remove the pin authentication. remove the sim from the phone and put it back in huawei device. that's it.

with the pin auth active, this how-to don't work.

moreover, as you're from singapure your wvdial.conf needs to be changed:
[Dialer hsdpa]
Phone = *99***1#       ->if you're not from vodafone, you'll need to find this number somewhere (try your isp support line, f.e.), if you are, try this one... for spain and portugal it's the same. but as singapure is so far away... the number can be different
Username = vodafone  ->same here
Password = vodafone   -> same here
Stupid Mode = 1
Dial Command = ATDT
Modem = /dev/ttyUSB0
Baud = 460800
Init2 = ATZ
Init3 = ATE0V1&D2&C1S0=0+IFC=2,2
ISDN = 0
Modem Type = Analog Modem
Init5 =AT+CGDCONT=1,"IP","internet.vodafone.pt";  -> finally you'll need to know this server url. even if you're from vodafone, this needs to be changed for your local server. (i found mine in the original settings that came with the vodafone auto installer for windows xp)


the rest of the how-to keeps unchanged.

PS: the above also applies to everyone trying to connect this device in other countries.

---

### Post by svenkatesan on 2007-02-18
Hi Mr Luis
Thanks for the clarification and guidance.
I applied only only for the modem,so no handset.Anyway I can do it from other set.

---

### Post by svenkatesan on 2007-02-22
Hi Mr Luis
Pl see the following text,when I got connected atlast.
The modem light is not consistanly blue,it goes back to green often.What's the error messege
in the highlighted color below.
Pl help me.
Thanks

kumar@ubuntu:~$ wvdial hsdpa
--> WvDial: Internet dialer version 1.55
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
OK
--> Sending: ATZ
ATZ
OK
--> Sending: ATE0V1&D2&C1s0=0+IFC=2,2
ATE0V1&D2&C1s0=0+IFC=2,2
OK
--> Sending: AT+CGDCONT=1,"IP", "INTERNET.VODAFONE.PT";
OK
--> Modem initialized.
--> Sending: ATDT*99***16#
--> Waiting for carrier.
CONNECT
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Thu Feb 22 20:49:21 2007
-->[COLOR="Red"] Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.[/COLOR]
--> Pid of pppd: 10814
--> Using interface ppp0
--> local  IP address 172.22.1.197
--> remote IP address 10.64.64.64
--> primary   DNS address 202.65.247.151
--> secondary DNS address 202.79.127.166

It looks I don't have these directories-pap-secrets and chap-secrets.
Does the modem spedd need to increse to utilize the speed of browsing?
Thanks

---

### Post by luis.peralta on 2007-02-22
hello. as you can see from my how-to at step 1:


**STEP1 - Inicial setup:**
->Plug your SIM card in a mobile phone, and remove the PIN authentication.
->First, in terminal give permission of rwx for all groups to the following files:
# sudo chmod -c a+rwx /etc/wvdial.conf
# sudo chmod -c a+rwx /etc/ppp/pap-secrets
# sudo chmod -c a+rwx /etc/ppp/chap-secrets


you need to remove those permissions. that's why the wvdial.conf isn't being able to update pap-secrets and chap-secrets. (note that those command lines start with sudo and not with #)

i hope that resolved the problem.

---

### Post by svenkatesan on 2007-02-22
Hi Mr Luis
Ya,I followed the same way u said.
Sudo ... pap & chap comments produced error during that time.(It said,can't find that directory)
I went ahead despite the error and got connected.
Anyway thanks for the reply.
Let me look into it.

---

### Post by luis.peralta on 2007-02-27
did you tried without "sudo"? only chmod..?

---

### Post by svenkatesan on 2007-02-27
Again problem.
I was able connect only for 2 days.Past 3 days Whatever I do I get only [COLOR="Red"]ttyUSB0[/COLOR],no USB1,USB2.
when I fire wvdial hsdpa- stopped at Modem can't initialized error.
I did all the steps also end up shown only ttyUSB0,so I can't proceed.
Is this Init5 string is important?How did u get [COLOR="Green"]**init 2 &3.**[/COLOR]First 2 times how am I able to connect without altering your value.
Can you pl explain simpler way to get this strings while I am in Windows?
Somewhere I read there is startup script to coneect this modem automatically during boot-up.
I have the script,but do not know how to put into /etc/init.d(am I Correct?)
Pl help. 
Thanks

---

### Post by badseed on 2007-03-01
Hi Guys,
I have a TMN connection, and (after a few tricks) can't connect (ppp exit code = 16), but I can solve the pin problem:
Init2 AT+CPIN=xxxx
add 1 to the rest of the init lines.


Hope it helps
João Mendes

---

### Post by GothicX on 2007-03-07
I think you should replace "#" by "$".. example: $ sudo

It'll be better for newbies to understand.. :-) Good Tutorial

---

### Post by skywatcher on 2007-03-09
Hi Luis

I'm having trouble connecting my E220. I follow your steps, and I get all ttyUSB0,  ttyUSB1 and ttyUSB2 detected. But it stops at '--> Using interface ppp0'. I don't get the equivalent of the following 4 lines:

--> local IP address 172.22.1.197
--> remote IP address 10.64.64.64
--> primary DNS address 202.65.247.151
--> secondary DNS address 202.79.127.166

My wvdial.conf is correct, because the E620 works on the same machine without any problems. Any idea what could be wrong?

---

### Post by fmagomes on 2007-03-10
I am of Portugal, therefore my English is not great thing, I solved the problem adding the following one:

on setp2 i use also:

modprobe usbserial vendor=0x12d1 product=0x1001

---

### Post by oozie on 2007-06-15
Hi! 

The problems some of you are experiencing is dependent on your kernel version. People using the newest version with kernel 2.6.20 are able to connect once they configure the device with wvdial or pppd. Everybody with older kernel needs to do some udev hacking. I did it for you already acutally, take a look here:

[http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/)

And apropos these four lines you are not getting, are you sure you have "Auto DNS = 1" line at the end of wvdial.conf ? 

Have a lot of phun!

---

### Post by mizwete on 2007-11-04
Hello all, maybe somebody coulp help me.

The Laptop is HP/Compaq nx7300
It runs under gutsy Kubuntu 7.10, kernel 2.6.22-14

 the modem Huawei E220 isn't recognized. NOT EVEN as a disk drive. OK, kernel is newer than 2.6.19, so it shouldn't show up as disk drive anymore.
Anyway !
command **lsusb** doesn't show ANY device connected to an USB port ( but only a Belkin device... and nothing but the Huawei is plugged in a USB port-so wherefrom is this Belkin stuff coming ?).
 
 Even after a command **modprobe usbseriel vendor=0x12d1 product=0x1003**
 no matter how much times the modem is unplugged and plugged again. Nothing shows up !

command **ls -la /dev/ttyU*** doesn't list any "ttyUSB*" device, no wonder the modem isn't recognized !
 
 In such circumstance, I believe that I should incriminate the modem itself, anyway, it HAS functioned properly (under window XP) a few monthes ago.
 
 Any suggestions ?
 I must add that all this doesn't prevent the modem to blink BLUE after it's been plugged 30 or 40 seconds on.

Now, i got a laptop unable to connect to the net, so I CANNOT download anything.
How can I fix it in such circumstances ?
Any help would be gladly appreciated, many thanks in advance

---

### Post by mizwete on 2007-12-02
Fixed now

---

### Post by nullpex on 2007-12-02
Hi, 

I found that Vodafone Spain is sponsoring Linux software for the card:

[http://www.vodafonebetavine.net/web/linux_drivers]("http://www.vodafonebetavine.net/web/linux_drivers")

It's written in Python and has the advantage of allowing usage of sms.

I've tried with Ubuntu 7.04 with bad results (not even able to open the software) so I'm using wvdial again.

I'm just writing to let you guys know. In the future it might improve. Nevertheless I think I'll continue using wvdial because it uses less resources.

Happy browsing for all!

---

### Post by adwiki on 2008-01-29
Hi all! 

1º - For Huawei I noticed that if we plug the modem in windows and then restart and go Ubuntu, the device is USB recognized after we do the 2º step:

"STEP2 - Overriding the usb-storage detection problem:
# sudo rmmod usb-storage
# modprobe usbserial vendor=0x12d1 product=0x1003

->remove Vodafone 3G from usb and with ## ls -la /dev/ttyU* ## wait to get the following result:
# ls -la /dev/ttyU*
ls: /dev/ttyU*: Non existent file or directory
**- > plug and wait for:**
# ls -la /dev/ttyU*
crw-rw---- 1 root dialout 188, 0 2007-01-26 11:59 /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 1 2007-01-26 11:59 /dev/ttyUSB1
crw-rw---- 1 root dialout 188, 2 2007-01-26 11:59 /dev/ttyUSB2

[B]The problem is that when I do this without going into windows, UBUNTU can't recognize the device as usb... So I thougt maybe someone out there knows a way to load the usb module into linux kernel.
(as far as I know the program huawei.tar.bz2 does that[/B]

Another point is the vodafone program that solves this issue 100%... Anyone knows how I can install it in 64 bits distro? (I saw this program only for i386) :( 

Pedro
Portugal..

---

### Post by mik78boa on 2008-04-29
Hi, 
what about Vodafone Internet Box E172 from Huawei? Does it change something? 
Thanks in advance, 

Michele

---

