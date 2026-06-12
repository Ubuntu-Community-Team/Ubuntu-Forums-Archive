---
title: "Wireless trying for last ONE month....hopeless"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by ritesh on 2007-02-18
Hi All,
Anyone please please help me......with configuring wireless network......
My system is:
Dell Inspiron E1505 laptop
Intel CoreDuo T2250 1.73Ghz
1GB DDR2 533MHz 2 Dimm RAM
256 MB ATI mobility Radeon x1400 HyperMemory
Integrated 10/100 network card and Modem
Dell Wireless 1390 802.11b/g mini card(54MBps)
Dell wireless 355 bluetooth module(2.0 + EDR)

I have installed Ubuntu 6.06 a month ago and from then i am trying to configure my home wireless network.
I have browsed and tried every post on Ubuntu for my configuration and formatted the linux partition 4-5 times....... 
Everything is working fine.......Wifi light is also on.......in the network manager its showing my home wireless network and I also entered my network key (tried both ASCII and Hexadecimal).....but alas no working..................
my ethernet is working fine(active eth0)......in fact in the network manager it shows below wireless network(wlan0 is active)...but it dosen't connect to wireless........
I have installed ndiswrapper and is working fine
when i type command ifconfig it shows all wireless connection(mine also)

I am so frustated now......i dont know what to do................

Please Please .......Any help.........
Thanks.

---

### Post by teaker1s on 2007-02-18
if your using gnome then install
[COLOR="Red"]network-manager-gnome[/COLOR]

simple point and click connect

---

### Post by ritesh on 2007-02-18
Hi 
I have tried to install network manager....but it didn't worked

---

### Post by teaker1s on 2007-02-18
to work you must

on your desktop panel you want to click system administration networking

it's important to make sure that devices show un-configured so network-manager-gnome can control them. Shutdown and remove Ethernet cable, boot and you should now left click network applet next to volume icon select your network and put in Passphrase or network key

---

### Post by ritesh on 2007-02-18
[SIZE="4"]****[/SIZE]

Hi,
I did as you suggested but it still not working,
I installed network manager from the terminal, then removed my ethernet wire and shut down the system, after that I booted again and clicked on System -> Administration -> Networking .....there it showed me 3 options: Wireless Connection the interface wlan0 is active, Ethernet Connection the interface eth0 is active, and the third one Modem connection which was not active...............

When I boot into the ububtu, intially configuring network interfaces toos long time ...........my laptop wifi light is on...............

If you want other information, please mail me....i will post the screenshots of the network.............

thanks a lot.....for helping............

---

### Post by teaker1s on 2007-02-19
> System -> Administration -> Networking .....there it showed me 3 options: Wireless Connection the interface wlan0 is active, Ethernet Connection the interface eth0 is active, and the third one Modem connection which was not active...............

make sure they are un-configured-so no ticks in boxes.(see screenshot)
reboot and post me a screenshot of desktop so I can see desktop panel

---

### Post by Tichondrius on 2007-02-19
I had the same problem and now everything works !

The core issue is that the Dell 1390 wireless card doesn't work with the driver that comes with Ubuntu. So you need to use the utility "ndiswrapper" which uses the windows driver to communicate with the card in linux. 

The link below gives instructions how to set up ndiswrapper:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

This link gives tips about connecting to a wireless network (after you set up the driver with the instructions above):

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Troubleshooting)

---

### Post by teaker1s on 2007-02-19
wiki states your model may or may not work natively depending on version, try what I suggested and if that's no good follow the ndiswrapper route

---

### Post by ritesh on 2007-02-19
Thank you for helping me.......

I am attaching  screenshot for the system-> Administration-> Networking......

A strange thing happened this morning, I took my laptop to the university and tried to connect it to my university wireless and TO MY SURPRISE ....IT GOT CONNECTED......and the internet was working fine.........everything was working fine in internet..................

But that happiness was not too long and when I returned back to my apartment and when I tried to connect to my home wireless internet it was not connecting.....got very frustated..............
then I tried iwconfig ...scanning didn't showed my wireless connection....................although network manager drop down menu showed my network and I entered the network key...but alas no success.............

I thing I want to ask.........my university network didn't require network key but my home network is secured one and has network key (all numbers and no charecters ie, hexadecimal) ......does this creates a problem????
Guide me......

Once again thanks for all the postings............

---

### Post by teaker1s on 2007-02-19
okay so we have success as in wireless works but not on your router. can you disable wireless security just to test if it is the security or connecting to the router causing problems.
Also do you use wpa or wep security/

---

### Post by ritesh on 2007-02-19
Hi,

How do i disable wireless security.....like what commands do i have to type or what i have to do.............

---

### Post by ritesh on 2007-02-19
when i do iwlist.........it shows all the internet connect around my apt including mine..........bit when i type 

ritesh@ritesh:~$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

it shows me this................what to do........

---

### Post by Tichondrius on 2007-02-19
> **ritesh said:**
> Thank you for helping me.......

I am attaching  screenshot for the system-> Administration-> Networking......

A strange thing happened this morning, I took my laptop to the university and tried to connect it to my university wireless and TO MY SURPRISE ....IT GOT CONNECTED......and the internet was working fine.........everything was working fine in internet..................

But that happiness was not too long and when I returned back to my apartment and when I tried to connect to my home wireless internet it was not connecting.....got very frustated..............
then I tried iwconfig ...scanning didn't showed my wireless connection....................although network manager drop down menu showed my network and I entered the network key...but alas no success.............

I thing I want to ask.........my university network didn't require network key but my home network is secured one and has network key (all numbers and no charecters ie, hexadecimal) ......does this creates a problem????
Guide me......

Once again thanks for all the postings............


I guess you didnt read the tips in the second link I posted in my previous email.

The issue is probably with the type of security you have in your wireless network in your apartment. You can have either "restricted" WEP key security or "open" WEP key. I think Ubuntu GUI always use the default which is "restricted". This will not work if your WLAN has "open" WEP.

So to change it to open you have to issue these statements (obviously changing network name and key to your home WLAN name and key):

sudo iwconfig wlan0 key **open **123456789A
sudo iwconfig wlan0 essid "HomeNet"

Then you should be connected.  To check,  type:

iwconfig

And it should say that you are associated with the access point.

To make this permanent, you need to edit /etc/network/interfaces, and add the word "open" just before the encription key in the appropriate line in this file.

---

### Post by ritesh on 2007-02-20
THANKS THANKS THANKS..............THANKS to power INFINITY....................
wireless just started to work........................
thankyou thankyou..................so so much...........

i was just struggling for 2 months.........................exactly 2 months...................with 6 times formatting......................

finally thanks to all of u ......who posted valuable suggestion and links..............
May God Bless You....................

---

### Post by Tichondrius on 2007-02-20
great !

this makes it 3 of 3 for me helping people in one day.....

---

### Post by ritesh on 2007-02-20
Great...........you are a  genius in Linux......
please guide me...actually  i very new to linux and want to really learn it inside out..........

any reference book or website links .....

thanks one again for the help.........
one last question ....where are u from?

thanks..........

---

### Post by Tichondrius on 2007-02-20
For Ubuntu the best site that summarizes how to set things up quickly is ubuntuguide.org

As for linux in general,  regular users should not need to mess around with system administration and configuration of hardware. That's why GUI and automatic setup utilities are useful for most.

btw, I live in north Cal

---

### Post by Tichondrius on 2007-02-20
OK, just in case that you meant you wanted to know linux system administration, and not just how to use it, then I can recommend this book:

[http://www.amazon.com/Linux-System-Administration-Second-Library/dp/0782141382](http://www.amazon.com/Linux-System-Administration-Second-Library/dp/0782141382)

And for online reference to various system administration topics:

[http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/index.htm#Linux](http://www.chinalinuxpub.com/doc/www.siliconvalleyccie.com/index.htm#Linux)

All that is of course way beyond what a normal user will use linux for, which is mostly for web-browsing, email and office type apps. I use linux a little differently than most - I have a 24/7 linux server that I use as a web server, file server (backup all my files on it), and mail server (SMTP+IMAP). I can connect to my linux server using SSH (incl SFTP), Samba, NFS, and HTTP from the other computers on my wireless network (currently I have a windows gaming PC and a laptop). I also use linux for software development, as it's vastly superior to windows in that respect (although Cygwin, a unix shell on windows, is cool).

Hope that helps.

---

### Post by ritesh on 2007-02-27
Hi ....
hope u remember me......wireless dell inspiron......

well i have configured my screen resolution but still fonts looks some kind of wiered..............

I have a 256 MB ATI mobility redeon x1400 graphics card and screen resolution of 1280x800...............

i want to ask wheather i should install 915 resolution for my laptop or not.????and will it work fine with ATI card....

Thanks

---

