---
title: "Intrepid: Wont connect to WPA2 enterprise network"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by loera on 2008-11-04
Hey everyone,

I have a new HP tx2500z laptop that I loaded Ubuntu 8.10, Intrepid, on.

I can connect to WEP networks but the one at my university is WPA2 enterprise. I have friends that have hardy heron on their machines that can connect.

When I put the network settings of PEAP the whole systems freezes and I have to hard reboot. All my searchings for an answer are so far in vain. 

Any help is appreciated so I can stop using vista.

---

### Post by TheSe7enthProphet on 2008-11-04
This problem has been mentioned - several times - over the past few days. No one has really said if any work is being done on it or not.

The new Gnome Network Manager has been screwed with, for whatever reason, and was broken. 

In 8.04, I was able to connect to my university's WPA Enterprise network with no problems. It actually connected faster than Windows or Mac and was a hell of a lot more reliable. Then I updated and it broke. 

I would LOVE to downgrade, but there doesn't seem to be any support for that, and I can't seem to get it to work. It's frustrating as hell. I have to use my school's unencrypted, slow-as-hell internet that doesn't allow SSL connections and has half of the internet blocked. 

But, the silence is reassuring. It's really nice to know that no one will even recognise the problem.

---

### Post by Eezyville on 2008-11-04
I had the same problem when i first installed Hardy. I had to wait till an update was given a few weeks later. I'm now experiencing that problem again. Maybe I should have stuck with Hardy since it worked for me.

---

### Post by jimv on 2008-11-04
I would try using WICD instead.  You can download it at:

[http://wicd.sourceforge.net](http://wicd.sourceforge.net)

---

### Post by Teefs on 2008-11-04
I am experiencing the same problem as well. Both with the default wireless driver as well as the Restricted Broadcomm driver installed.

I hope someone will fix this soon...

---

### Post by linux_newbie_1 on 2008-11-04
I am having the same issue with 8.10 whereas at least 8.0.4 was working fine from LiveCD.

---

### Post by John.Gaythorpe on 2008-11-04
As I posted yesterday. NM appears to be broken.

So WPA2 cannot be configured through it.

Whose idea was it to put out 0.7 of it?

John.

---

### Post by karlr42 on 2008-11-04
I seem to have the same problem, connecting to a WPA enterprise network using PEAP. After a few minutes, my laptop freezes, NUMLOCK, SCROLLLOCK keys flash. Looking at the syslog(dmesg?) I see the last entry is usually regarding ntpdate- a service to update the system time with a remote server? I've tried removing the package, but to no avail.

---

### Post by loera on 2008-11-04
Thank you for all the replies, even though we haven't gotten a solid answer on this post I think it is worth having. 

I will keep looking for an answer, and hopefully soon there will be an update. 

Any idea who I can send this bug to? or how to send a bug like this to ubuntu?

---

### Post by CNLiberal on 2008-11-04
I am also having this issue with WPA2 at work.  We are using WPA2-PSK TKIP and when I put in the key in 8.10 x64, the laptop won't connect.  This is so disheartening!!  I guess I'll just keep an eye on this thread.

---

### Post by jimv on 2008-11-04
Did any of you try WICD yet?  It's a replacement for Network Manager, and it has always worked better for me.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by gali98 on 2008-11-04
Has anyone taken the time to put in a bug in launchpad?
Trust me, devs don't just poll the forums looking for bugs. They go to the source. If you have a problem, you should go to launchpad and tell them about it.
Kory

---

### Post by edrace562 on 2008-11-04
I know of 4 people at my college who have upgraded from 8.04 to 8.10.  Its a WPA2 Enterprise network.  It worked excellent with 8.04, upgraded to 8.10, now we cant connect.  It works fine with a wired connection but the wireless doesnt work.  We tried a lot of work arounds and no results.  Anyone out there know what is being done to solve this quite large flaw?

---

### Post by alexpwalsh on 2008-11-04
I tried the whole Wicd thing... and couldnt get it to work on my WEP network at home, let alone my WPA2 at my University...
I'm going to check out the launchpad and see whats up...

---

### Post by jshprentz on 2008-11-04
Launchpad contains two bugs related to this problem:

**[Bug #276980]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/276980"): ndiswrapper bcm4306 rev 2 won't connect regression**

[INDENT]#276980 provides technical details and a workaround.[/INDENT]

**[Bug #293869]("https://bugs.launchpad.net/ubuntu/+bug/293869"): impossible to connect to WPA and WPA2 wireless networks**

[INDENT]#293869 contains a problem report and a link to this forum thread.[/INDENT]

---

### Post by Teefs on 2008-11-04
Has anyone gotten WPA/WPA2 enterprise to work?

For those of you that are experiencing these what hardware are you using and which drivers? 

Also what symptoms are you experiencing? Does it simply not connect, does it give some error, or does your system completely hang shortly after attempting to connect(like mine)?

Hopefully the more information we can collect on the problem the easier it will be for the devs to troubleshoot. And that hopefully means we get a fix sooner :)

---

### Post by Teefs on 2008-11-05
I have just recently tested with my Netgear WG111V2 wireless usb adapter and have found no issues. It doesn't hang and connects to the network without any issues. 

The system only seems to hang when I try to connect to my schools WIFI with WPA/WPA2 with my internal Broadcom wireless. I have tried using both the default driver and the proprietary driver enabled in the Hardware manager and I get the same effect with both.

Does anyone else who sees these issues have a Broadcom wireless chipset or are you using something different?


PS: I would also like to point out that I have no trouble connecting to regular WPA/WPA2 networks as I use one at home myself. Also both regular and enterprise worked fine under 8.04 once fully updated

---

### Post by loera on 2008-11-05
I just tried WICD. suggested from:
[http://ubuntuforums.org/showthread.php?t=949871](http://ubuntuforums.org/showthread.php?t=949871)
and in this forum too.

It looks nice but I put in WPA2 with GTK (i think) it froze just like NM did.

So far no luck with WICD

---

### Post by Dakani on 2008-11-06
I actually have the reverse situation.
I used to be able to connect to my WPA-TKIP network at home using Hardy, but had so many drop-out and connection issues when trying to connect to my university's network.
Now, after a clean upgrade, the WPA 2 Enterprise network at the university works like a charm, but it axed my home network connection...
So, it was a trade off with one network for the other...

And I tried WICD, it didn't work out though.
Guess different mileage for different people.

---

### Post by laurentp on 2008-11-07
Hi,
I have a tx2524ca with BCM4322 network card and experiencing similar problem. I do connect to WPA network, but sometimes it start disconnecting/reconnecting and suddenly it crash. I can't restart X or my computer and I need to remover power. It happened 1 time at my university that use an open wireless with a VPN for logging. My caps lock key keep flashing when it crash... My logs are available here :[http://ubuntuforums.org/showpost.php?p=6121960&postcount=110](http://ubuntuforums.org/showpost.php?p=6121960&postcount=110) . 

Laurent

---

### Post by mikkoko on 2008-11-07
There is another thread on this topic as well:
[http://ubuntuforums.org/showthread.php?t=963379](http://ubuntuforums.org/showthread.php?t=963379)

I guess the problem has nothing to do with NetworkManager or Wicd, but rather with the kernel or drivers? I can't get WPA to work with either tool on my Thinkpad X61 with an Intel 9565AGN wireless chip. And other people seem to be reporting the same. 

Connecting to an unsecured network works fine. Haven't tried WEP though.


lspci:

03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
Subsystem: Intel Corporation Device 1111
Flags: bus master, fast devsel, latency 0, IRQ 219
Memory at fdf00000 (64-bit, non-prefetchable) [size=8K]
Capabilities: [c8] Power Management version 3
Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
Capabilities: [e0] Express Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting <?>
Capabilities: [140] Device Serial Number 83-4e-36-ff-ff-3b-1f-00
Kernel driver in use: iwlagn
Kernel modules: iwlagn



iwconfig:

wlan0 IEEE 802.11abgn ESSID:"xxxx"
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=15 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

(the ESSID iwconfig shows came from an unsecured public network)

---

### Post by Zeromaru on 2008-11-07
Same problem on my EeePC 1000H. Not sure on the exact chipset, but it's Ralink-based, using the driver included with the Array.org kernel. Worked perfect connecting to my school's WPA Enterprise (PEAP-LEAP, MSCHAPv2) on Hardy (Array.org kernel as well). On Intrepid it also works perfect at home on my WPA2 Airport Extreme network.

My friend's Fedora 9 (Rawhide) laptop also running NetworkManager 0.7.0 connects without difficulty.

---

### Post by sickdabig on 2008-11-07
Hello,

I have the same problems.
 
Using the Kernel 2.6.24-19 and Wicd solved the it for me :). 

As Wicd did not work either with the kernel 2.6.27-7 it must be a kernel issue.

---

### Post by John.Gaythorpe on 2008-11-07
Okay solved it for me. The new version of NetworkManager required the certs in a different format. Had to use openssl to convert the certs to PEM format. 

So I had a PKCS12 personal cert, which I then extracted the CA Root, Personal CERT and the KEY into separate .PEM files. Then it finally connects. Would have been nice if I had knew of this ahead of time.

This information is posted somewhere for Fedora that uses this version.

John

---

### Post by anando on 2008-11-08
Hi John

I have been following this thread with a lot of interest as I haven't been able to join my school's WPA2 Enterprise wireless network. Thanks to your post - I see some hope now. 

Could you please share how you extracted the CA Root, Personal CERT and KEY into separate PEM files ? 

Which file did you point to in the certificates section ? 

I have a usercert.pem file given to me by my CA - could I use this file ?

Thanks,
Anand.

> **John.Gaythorpe said:**
> Okay solved it for me. The new version of NetworkManager required the certs in a different format. Had to use openssl to convert the certs to PEM format. 

So I had a PKCS12 personal cert, which I then extracted the CA Root, Personal CERT and the KEY into separate .PEM files. Then it finally connects. Would have been nice if I had knew of this ahead of time.

This information is posted somewhere for Fedora that uses this version.

John

---

### Post by laurentp on 2008-11-09
> **karlr42 said:**
> I seem to have the same problem, connecting to a WPA enterprise network using PEAP. After a few minutes, my laptop freezes, NUMLOCK, SCROLLLOCK keys flash. Looking at the syslog(dmesg?) I see the last entry is usually regarding ntpdate- a service to update the system time with a remote server? I've tried removing the package, but to no avail.

Did you resolve your problem? I have exactly the same problem here with some message about ntp and a lot of roaming by the network manager (here is my log from the time of connection to the time of crash : [http://pastebin.com/m7f915a7b](http://pastebin.com/m7f915a7b)). Nothing in dmesg... I tried to change the wireless driver but it still freezes. I think it's the networkmanager. When I have some time, I'll try WICD to see if it crashes. 

Laurent

Config : Broadcom Corporation BCM4322 802.11a/b/g/n and a TX2524ca laptop.

---

### Post by anando on 2008-11-10
Following the suggestion towards the very end of this thread, I can confirm that if I choose the [COLOR=Red]/etc/ssl/certs/Thawte_Premium_Server_CA.pem[/COLOR] file where it asks for the certificate file, I *am* able to join the **WPA2 Enterprise** networks using network-manager in 8.10.

Previously in 8.04 it used to be the case that one could use any old .crt file in /etc/ssl/certs - e.g /etc/ssl/certs/ca-certificates.crt would work well. After a lot of trouble, I figured out that since 8.10, *.crt files don't work with network-manager anymore, but .pem files do.

I hope this is useful to other people.

Cheers,
Anand.

---

### Post by anando on 2008-11-10
Following the suggestion towards the very end of this thread, I can confirm that if I choose the [COLOR=Red]/etc/ssl/certs/Thawte_Premium_Server_CA.pem[/COLOR] file where it asks for the certificate file, I *am* able to join the **WPA2 Enterprise** networks using network-manager in 8.10.

Previously in 8.04 it used to be the case that one could use any old .crt file in /etc/ssl/certs - e.g /etc/ssl/certs/ca-certificates.crt would work well. After a lot of trouble, I figured out that since 8.10, *.crt files don't work with network-manager anymore, but .pem files do.

I hope this is useful to other people.

Cheers,
Anand.

---

### Post by ptobin on 2008-11-11
I'm using a DELL Inspiron 1525

Same issue I couldn't use WPA Personal on a hidden network. 

The only work-around I've found is to display my network.

After this change it logged in just like it should. Less secure but I need my WIFI.

---

### Post by CNLiberal on 2008-11-12
I don't know how the heck it happened, but I was able to connect to my work's wireless WPA2-PSK network.  I haven't been able to in several days.  I'm not sure what I did.  I was using the wired network for a couple weeks, and then decided to switch over to wireless for funsies.  It worked.  I'll try again tomorrow.  As an FYI the work wireless network is a hidden network.

Jim

---

### Post by thread_au on 2008-11-13
check out [http://ubuntuforums.org/showthread.php?t=963379&page=5](http://ubuntuforums.org/showthread.php?t=963379&page=5)

Edit: dang, should make sure I read ALLLL the pages of the thread. :)

---

### Post by CNLiberal on 2008-11-14
OK, I was incorrect.  My laptop still doesn't connect to WPA2-PSK TKIP network.  I'm running a Latitude E6500 with an Intel 5300 AGN card.  How do I add to a bug report?

---

### Post by quazi on 2008-11-18
I've got the same problem.  I can connect to my WPA network (at school) sometimes, but it kicks me off frequenty and fails to reconnect.  I'm using an broadcom adapter with the B43 wireless driver.

---

### Post by CNLiberal on 2008-11-18
So there has been no resolution to this?  It's starting to irritate me.  I try and show the awesome benefits of Ubuntu, but can't connect to my work wireless.  Should I open a new bug at Launchpad?  Thanks!

Jim

---

### Post by Cobinja on 2008-11-21
I don't think it's a kernel problem.

I'm having the same NM problem connecting to a WPA Enterprise network with its own certificate chain (.pem).

Manually using the WPA Supplicant and dhclient from a terminal works completely fine for me.

I'm using Intrepid with an Intel PRO/Wireless LAN 2100 3B chip.

---

### Post by kevdog on 2008-11-21
I too am having wpa2 problems, however I suggest for everyone posting in this thread -- to help solve the problem -- you manually try to connect to your wpa2 network using wpa_supplicant and a wpa_supplicant.conf file with the -dd flag as to generate debugging output.  Only will this allow a possible diagnosis of the problem (maybe).

---

### Post by quazi on 2008-11-21
> **quazi said:**
> I've got the same problem.  I can connect to my WPA network (at school) sometimes, but it kicks me off frequenty and fails to reconnect.  I'm using an broadcom adapter with the B43 wireless driver.

The STA driver fixed all my problems, everything works fine right now.

---

### Post by Coombabah on 2008-11-26
> **edrace562 said:**
> I know of 4 people at my college who have upgraded from 8.04 to 8.10.  Its a WPA2 Enterprise network.  It worked excellent with 8.04, upgraded to 8.10, now we cant connect.  It works fine with a wired connection but the wireless doesnt work.  We tried a lot of work arounds and no results.  Anyone out there know what is being done to solve this quite large flaw?

We have WPA Enterprise TKIP at Uni.
Ubuntu 8.04 worked well.
Ubuntu 8.10 connects to other WPA networks but not WPA Enterprise with TKIP.
Tried Dell D630 and ASUS 1000H.

---

### Post by Zeromaru on 2008-11-26
I've discovered that if I kill NetworkManager and wpa_supplicant then restart them, then it's possible to connect.

```
sudo NetworkManager --no-daemon
sudo killall wpa_supplicant 
sudo service wpa-ifupdown start
sudo NetworkManager --no-daemon
```

Then attempt to connect to the network manually, it will fail, but then when it re-asks for information click Cancel. Might have to repeat this 2-3 times, but it'll then connect just fine.

(You can presumably omit the "--no-daemon" part so you don't have to keep Terminal open, but I just leave a dedicated Terminal window in it's own desktop to make sure I don't accidentally close it).

---

### Post by Forlornity on 2008-12-15
Although not written in general terms, I wrote a guide for students of my college to get around this particular problem, running a WPA enterprise network with MSCHAPv2 and TKIP.
Obviously ignore my jabbering on and modify the commands/settings where needed, also ignore the proxy, but the guide (which I use myself, albeit in a bash script) is available at [http://www.ambience-web.co.uk/wifi_instructions.html]("http://www.ambience-web.co.uk/wifi_instructions.html")

Final note, if running in Ubuntu, it helps to either kill the default network manager before running these or just replace it with wicd which happily accepts the command line modifications and will even display signal strength for you once you are connected.

Hope this helps people solve their problems!

---

### Post by Favux on 2008-12-17
I may have a work around for all of you having the WPA2 (WPA2-TKIP) connection problem through networkmanager.  It involves using Gconf editor to correct some erroneous entries networkmanager is making.  At least it's worked for a couple of us already.  It's located here:

   [http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

I really encourage you to take a look.

---

### Post by crazy ivan on 2008-12-23
> **karlr42 said:**
> I seem to have the same problem, connecting to a WPA enterprise network using PEAP. After a few minutes, my laptop freezes, NUMLOCK, SCROLLLOCK keys flash. Looking at the syslog(dmesg?) I see the last entry is usually regarding ntpdate- a service to update the system time with a remote server? I've tried removing the package, but to no avail.

Whereas the change in certificates and the hidden networks seem to be resolved the crash part still remains a mystery. "Full stop" is a major nuisance.. Check out the [Bug-Report]("https://bugs.launchpad.net/ubuntu/+bug/297110") if you're affected by this.

---

### Post by Coombabah on 2009-01-07
> **Favux said:**
> I may have a work around for all of you having the WPA2 (WPA2-TKIP) connection problem through networkmanager.  It involves using Gconf editor to correct some erroneous entries networkmanager is making.  At least it's worked for a couple of us already.  It's located here:

   [http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

I really encourage you to take a look.

Thanks. Finally a fix that works and it's so simple.

For the first time I've had Intrepid connect to WPA enterprise with TKIP using Network Manager.

running gconf-editor from a terminal (as logged in user)
navigating to
system>networking>connections>1>connection to find the right connection. If you have more than one connection it may be 2,3,4 etc.

then
system>networking>connections>1>802-11-wireless-security
then remove the problem entries like ccmp that Network-manager puts in every time you use network-manager editor.

then connect and it works :)

I have an eeePC 1000h with RT2860 so the fix is not just for broadcom

---

### Post by Paulo79 on 2009-01-07
Has anybody had any luck trying this fix with Intel 3945 wireless?

---

### Post by cak3 on 2009-01-27
I was able to connect just fine to my university's WPA2-Enterprise network, using the correct CA cert with WICD (an alternative network manager, see using the built in PEAP with TKIP profile. (this is on a tx2500z w/ Intrepid). I also deleted the "ccmp" line in the gconf editor, as suggested above. WICD does not add it in, so doing that in combination with replacing the default netman with wicd works as a permanent and easy solution.

---

### Post by LCollins on 2009-02-09
I have a similar problem (in intrepid) in that my laptop can connect to a WPA & WPA2 Personal network, but not WPA & WPA2 Enterprise network (at University). However, I know the problem is not with the Certificate, as this university network does not require one and a friend of mine has intrepid as well, selects the setting so as to not provide a Certificate and connects without flaws.

---

### Post by Paulo79 on 2009-02-25
Using Ubuntu 8.10 here (Intrepid Ibex).

When I first boot my computer, I'm always able to connect to my university's WPA Enterprise network. The problem is that after a few minutes the connection is dropped and I cannot reconnect, unless I reboot.

Just found a workaround: instead of rebooting, I can run the command
```

sudo /etc/init.d/NetworkManager restart

```

Then I'm able to reconnect. This might be useful to some people out there.

Best,

Paulo

BTW: NetworkManager in Ubuntu 8.10 is really problematic...

---

### Post by SaiHayashi on 2009-03-09
> **Favux said:**
> I may have a work around for all of you having the WPA2 (WPA2-TKIP) connection problem through networkmanager.  It involves using Gconf editor to correct some erroneous entries networkmanager is making.  At least it's worked for a couple of us already.  It's located here:

   [http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

I really encourage you to take a look.

after upgrading to kernel 2.6.27-13-generic and following the guide provided to remove the ccmp craps i finally manage to connect to WPA2 enterprise via network-manager. mine still connects after reboot.:popcorn:

---

### Post by Cattfish on 2009-04-10
Hi, I had this problem with Intrepid and I solved it for Purdue's network using this link [http://groups.google.com/group/PurdueLUG/browse_thread/thread/29eedbe6a8af84ef](http://groups.google.com/group/PurdueLUG/browse_thread/thread/29eedbe6a8af84ef)

---

### Post by NoobBiscUiT on 2009-04-23
What version of Ubuntu were you using?

---

### Post by JK3mp on 2009-04-23
> **NoobBiscUiT said:**
> What version of Ubuntu were you using?

This is a quite older thread. Or at least the main issue's are quite older. And as many of them mentioned they are having problems with ubuntu intrepid. WHich btw is also an issue i've noticed. My comp connects to unsecured network at my school but not the WPA2 enterprise network. Im hoping this fixes when i upgrade to 9.04 at some point.

---

### Post by Alv20 on 2010-06-09
Hello, I have Ubuntu 8 and a IBM T41, i cant connect to my wireless network with WPA-PSK TKIP. The card is a intel 2100, under XP run well with WPA, but under ubuntu 7 and 8 not connect. I try with gnome and kde.

Anybody know a fix for it??? Or in Ubuntu 10 run ok??


Thanks,

---

### Post by datacrusher on 2011-03-25
I got a fresh install of ubuntu 10.10, using a RaLink RT3090 wireless adapter, i cant connect to my work wpa2-enterprise network. wired and wpa-psk works fine.

on syslog i got the frequent error (among some others):

wlan0 supplicant connection state associated -> disconnected
deauthenticating from local choice reason=3
wpa_supplicant CTRL-EVENT-DISCONNECTED event remove keys


the connection get stablished, but when i try to transfer data it hangs and after a short while i got dropped, and a bunch of errors appears. By this time I got 640 connected terminals, windows, iphones, macos...

---

### Post by jfeeney on 2011-06-27
Make sure you're using the most recent network manager and that you've pointed to the proper certificates file for WPA2 enterprise.

I just had the exact same issue trying to connect to my university's secure network that uses WPA2 Enterprise.

The certificates file can be found at:  /etc/ssl/certs/ca-certificates.crt

**all other certs are in the same folder in case your network uses a different one.

Once I pointed here, I connected no problem. I'm also quite impressed,  ubuntu connects quicker and is more reliable with my university network  than Windows 7.

Cheers,
Justin

---

