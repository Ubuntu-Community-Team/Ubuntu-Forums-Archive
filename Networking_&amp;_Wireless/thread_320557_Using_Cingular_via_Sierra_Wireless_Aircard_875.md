---
title: "Using Cingular via Sierra Wireless Aircard 875"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by GuerillaVille on 2006-12-17
no ubuntu experience. All talk of scripts and shells are Greek to me.

my box:
Compaq v2000 series notebook
AMD Turion64 chip
WinXP Home (hate it, hate it, hate it)
Sierra Wireless Aircard 875, access by Cingular

Want to make the aircard work with Ubuntu so I can wipe out WinXP and use Linux to access internet. Does anyone know (not surmise, but know) how to set this up? Remember, all the linux speak is Greek to me, so please do not talk over my head in reply. I contacted Cingular support and their response was not helpful. They told me to download a driver file but did not give me the file name, a link, or even the domain to search for it. Told me to configure my dialer with a huge list of scripts, you might as well ask me to jump in an f-16 and take off, never having even seen one before, there's no instructions on how to find the dialer, what menus to look in, etc.

Would be grateful if someone could demystify this process.

GuerillaVille

---

### Post by magicfab on 2007-01-26
Unfortunately lots of manual intervention is required to configure these cards. Your best bet is to formally complain about official support for Linux directly to your provider and to Sierra Wireless. If enough people do that, they will probably provide official .deb packages for Ubuntu and other packages for other distributions or better yet, have them commercially packaged and offered by Canonical or else.

---

### Post by U2ForNow on 2007-04-26
It looks as if some people are getting this to work now. 

Here is the info from Sierra:
[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601]("http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601")

Here is some info from someone who set it up:
[http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/]("http://www.itguyonline.com/blog/2007/03/14/cingular-aircard-875-2/")

Seems that most people I found running this with Linux are using SUSE. I plan to tackle it again as I can not stand having Windows Vista on my laptop for the sole purpose of using the internet. 

Any additional input would be welcome. :)

---

### Post by ChuxMix on 2007-05-03
Tried the steps at itguyonline.com without any luck, but I'm pretty new at Linux...
I'd love to get this working!

---

### Post by jmarshall on 2007-05-06
I just got mine to work.  See the post I made here:

    [http://ubuntuforums.org/showthread.php?p=2606060#post2606060](http://ubuntuforums.org/showthread.php?p=2606060#post2606060)

Good luck,
James

---

### Post by adaptable on 2007-05-07
[Post deleted.]

---

### Post by mimsmall on 2007-10-01
Has anyone tried to get Aircard 875 working using wine or ndswrapper? 

The Sierra site mentions using the latest kernel. 2.6.18 or later, so now I need to know if I should change to Feisty or can I install the latest kernel in 6.04?

---

### Post by Eric Lee Elliott on 2007-10-12
Do full Ubuntu update, it will have needed driver in kernel.  Forget Wine & NDIS.

Two parts remain to do, install scripts & configure kppp.

Here is the info from Sierra:
[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601)
His page is good.  Notice GSM will not call file gsm.  There was one other small typo on his page.  
Chmod did not work at my low level of Linux grok.
I copied scripts to /tmp/ppp/ directory.  Then expanded the scripts in /tmp/ppp/ directory.  Next was sudo kate.  With kate in su mode, the scripts were edited & moved to /etc/ppp/.  Script editing was to enable auth, change baud to  621,200 & insert Cingular APN.  Maybe could have used chmod per Sierra page, but it failed on first fat finger try.

Next configure kppp.  First open your ATT software options & copy UID. PWD, & such.  Save info.  Run Linux.  Sudo kppp.  Follow Sierra instructions. Name of modem is 875.  Select /dev/ttyUSB0, not dev/tty/USB0.  Jack speed to 621,200.  After backing out to first kppp screen, you should be able to drill into "modem query" & get replies from modem.  Put your UID & PWD in again on front screen of kppp.

Push "Connect"

If yours is like mine, service will become more reliable during first week of use without Windiz.  Can't explain it, no clue how it got better.  Now 875 connects quicker, rarely drops connection, rarely gets dead connection & is much faster.  Maybe some of the many recent updates made it better?

One last thing, after it was working, kppp was set to start with 3 keys.  Just right click kppp in control panel, select edit item, select Current Short Cut Key & enter your choice.  My choice, control+shift+' is easy 3 finger salute to start connection.

---

### Post by vvarder on 2007-10-30
A lot of good info here I had a different problem.  I solved it, so I posted my results here in case a google search brings up this thread like it did for me.

For me, I'm using Ubuntu Gutsy Gibbon with an AC875 Cingular card.  The awesome thing about Gutsy is it will detect the card OUT OF THE BOX.  I was excited after that happened :)

I used Sierra's website instructions: [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601) and tried the websites listed here, but I got the same error "Could not determine remote IP address: defaulting to 10.64.64.64", with no connectivity.  I booted into windows, found that the remote PPP address was the same as the local, as well as the default gateway.

I tried to put it in statically, but it was literally changing almost every time.  Then I executed the route commands to remove the default gateway, and add in the ppp and default gatway.  And that worked.  The problem was I had my wireless default route in there, and KPPP couldn't (or wouldn't) overwrite that, despite the fact that I did check the box in the configuration to replace the default gateway.

In any event, after a reboot with the wireless off, the routing table was clean.  KPPP populated it with the 10.64.64.64 address, however, since the table was clean, I'm still able to get out to the internet (because, and I'm guessing here, the network stack sees 10.64.64.64 as local, so it still gets routed correctly, despite that address being bogus to the outside world).  DNS addresses populated just fine.

I'm off to Cingular's site to ask them for "help" just so they get the message that this market does exist.  Again, I just wanted to post this in case anyone else ran into the same problem.

---

### Post by joiningtheherd on 2008-01-11
I'm having a very frustrating issue with this card and the pppd system.  I've never used a ppp connection under linux, and I don't know how it works.  The driver seems to be working as a device node is created for my wireless card.  The device is also apparently obtaining an IP and DNS servers but I could be wrong.  Here's the pertinent bits of 'tail /var/log/messages' for the past three connections.

```
Jan 11 17:59:55 trevor-laptop pppd[8978]: CHAP authentication succeeded
Jan 11 17:59:55 laptop pppd[8978]: CHAP authentication succeeded
Jan 11 18:00:00 laptop pppd[8978]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 11 18:00:00 laptop pppd[8978]: local  IP address 166.128.16.181
Jan 11 18:00:00 laptop pppd[8978]: remote IP address 10.64.64.64
Jan 11 18:00:00 laptop pppd[8978]: primary   DNS address 209.183.48.11
Jan 11 18:00:00 laptop pppd[8978]: secondary DNS address 209.183.48.10
```
```
Jan 11 18:06:11 laptop pppd[9093]: CHAP authentication succeeded
Jan 11 18:06:11 laptop pppd[9093]: CHAP authentication succeeded
Jan 11 18:06:34 laptop pppd[9093]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 11 18:06:34 laptop pppd[9093]: local  IP address 166.128.221.233
Jan 11 18:06:34 laptop pppd[9093]: remote IP address 10.64.64.64
Jan 11 18:06:34 laptop pppd[9093]: primary   DNS address 10.11.12.13
Jan 11 18:06:34 laptop pppd[9093]: secondary DNS address 10.11.12.14
```
```
Jan 11 18:07:44 laptop pppd[9105]: CHAP authentication succeeded
Jan 11 18:07:44 laptop pppd[9105]: CHAP authentication succeeded
Jan 11 18:07:48 laptop pppd[9105]: Could not determine remote IP address: defaulting to 10.64.64.64
Jan 11 18:07:48 laptop pppd[9105]: local  IP address 166.128.43.116
Jan 11 18:07:48 laptop pppd[9105]: remote IP address 10.64.64.64
Jan 11 18:07:48 laptop pppd[9105]: primary   DNS address 209.183.48.11
Jan 11 18:07:48 laptop pppd[9105]: secondary DNS address 209.183.48.10
```
NOTE: The second attempt didn't connect as these are default values used for DNS.

The kernel routing table:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
```
I think it must be some sort of routing error, but not being familiar with how that works (never had issues here before) I'd love some input as to how to fix this.  I've not had an issue with the routes not being overwritten when the ppp connection is established.  The route is always the same ... I'm not sure the proper way to set up a route using `route`  Cheers.

---

### Post by mrbigg75 on 2008-02-21
cal@cal-laptop:~$ pppd call gsm

Starting Sierra Wireless GSM connect script...


Setting the abort string


Initializing modem


Setting APN


Dialing...

Serial connection established.

using channel 4

Using interface ppp0

Connect: ppp0 <--> /dev/ttyUSB0

sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0xdd9b8e22> <pcomp> <accomp>]

rcvd [LCP ConfReq id=0xc <asyncmap 0x0> <auth chap MD5> <magic 0xab44cb4e> <pcomp> <accomp>]

sent [LCP ConfNak id=0xc <auth pap>]

rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0xdd9b8e22> <pcomp> <accomp>]

rcvd [LCP ConfReq id=0xd <asyncmap 0x0> <auth pap> <magic 0xab44cb4e> <pcomp> <accomp>]
sent [LCP ConfAck id=0xd <asyncmap 0x0> <auth pap> <magic 0xab44cb4e> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0xdd9b8e22]
sent [PAP AuthReq id=0x1 user="cal-laptop" password=<hidden>]
rcvd [LCP DiscReq id=0xe magic=0xab44cb4e]
rcvd [LCP EchoRep id=0x0 magic=0xab44cb4e dd 9b 8e 22]
rcvd [PAP AuthAck id=0x1 ""]
PAP authentication succeeded
sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
rcvd [LCP ProtRej id=0xf 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x3 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfNak id=0x3 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x4 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
rcvd [IPCP ConfNak id=0x4 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
sent [IPCP ConfReq id=0x5 <compress VJ 0f 01> <addr 0.0.0.0>]
rcvd [IPCP ConfReq id=0x6]
sent [IPCP ConfNak id=0x6 <addr 0.0.0.0>]
rcvd [IPCP ConfRej id=0x5 <compress VJ 0f 01>]
sent [IPCP ConfReq id=0x6 <addr 0.0.0.0>]
rcvd [IPCP ConfNak id=0x6 <addr 166.129.170.133>]
sent [IPCP ConfReq id=0x7 <addr 166.129.170.133>]
rcvd [IPCP ConfAck id=0x7 <addr 166.129.170.133>]
rcvd [IPCP ConfReq id=0x7]
sent [IPCP ConfAck id=0x7]


Could not determine remote IP address: defaulting to 10.64.64.64

Cannot determine ethernet address for proxy ARP
local  IP address 166.129.170.133
remote IP address 10.64.64.64
primary   DNS address 10.11.12.13
secondary DNS address 10.11.12.14
Script /etc/ppp/ip-up started (pid 6182)
Script /etc/ppp/ip-up finished (pid 6182), status = 0x0



\my only problem is \i cannot get the network to issue a good ip address. many are having this problem.could someone give me a solution n newby language

---

### Post by mrbigg75 on 2008-02-25
success .. <i finally got connected. i do not know how, but it was one of those things.life is good. i did all the updates and my notebook is running fine/..

---

### Post by hannulan on 2008-04-01
I also have problems with the sierra card (MC8775 more precisly).

I dont know where it has been mounted, thought it would be /dev/ttyUSB0, as the sierra faq says (is it the driver that decides that?), but there are no such file. 

How do I find the modem so I can try the connection to the internet?

By the way, when checking what is on the usb-bus (lsusb) the sierra modem does not show up, does it do it for you? 

I have not used it under windows, can it be some configuration problem with the modem? Has anyone used this card in Ubuntu and never in windows?

(I'm not so used to linux and especially not modems, which I have not used before).

---

### Post by mk4umha on 2008-05-08
I'm running 8.04 and i'm running into the same problem "could not determine remote IP address" Did anyone get 8.04 working with the Dell 5520 Wireless Broadband card?

---

### Post by BinaryNomad on 2008-05-15
I found a very simple solution to the default gateway issue if you are using the kppp software for the ppp connection. 

Launch kppp -> select Configure-> Select your account and click Edit. Click the gateway tab and select "static gateway". Leave the Gateway IP address field blank and select Assign the default route to this gateway. LEAVE THE "Gateway IP address" FIELD BLANK.

Thats it. Your done. Happy Surfing.

Hope this helps everyone as I am very new to Linux and appreciate all the help I have recieved.

Here is the link to Sierra Wireless page explaining how to set up kppp if you are not already using it.

[http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601]("http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=601")

--Lance

---

### Post by vvarder on 2008-05-19
Ubuntu 8.04 will detect the card out of the box, as I expect most major distros will now.

However, I also recently installed Fedora 9, and apparently with Network Manager 0.7 (which it comes with, but for some reason isn't listed on the site as stable yet) has the builtin ability to detect that you have a card installed, and gives an option to connect to a GSM network.

It's awesome, it's too bad it didn't make the cut for Ubuntu.  It's literally a right-click then click on "Auto GSM" to connect, way faster than even the windows client, and no configuration needed.  Which is good, because I was getting the same problems listed above with routing using gnome-ppp.

---

