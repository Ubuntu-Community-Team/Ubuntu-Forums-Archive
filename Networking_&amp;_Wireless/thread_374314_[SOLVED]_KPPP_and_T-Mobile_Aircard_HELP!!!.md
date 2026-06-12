---
title: "[SOLVED] KPPP and T-Mobile Aircard? HELP!!!"
date: 2007-03-02
forum: Networking &amp; Wireless
---

### Post by sanicki on 2007-03-02
I need to write up instructions to get our company's wireless aircards to connect using KPPP.

I used KPPP to get a PC5740 to connect to Verizon. Cake.

Now I'm stuck on a GC89 trying to connect to T-Mobile.

* Used dmesg to find it at /dev/ttyS0.
* Using Init strings ATZ & AT+cdgcont=1,"IP","internet2.voicestream.com" (also tried "wap.voicestream.com")
* When I use "Query Modem" I get junk like )!q, !!), !! !, !! ), !! ), )!}), !!!, )! )
* When I try to connect using phone number *99# in debug window I see }!) and 'Expecting OK'

Anyone help a noob out?

By the way, when I use "Query Modem" on PC5740 I get:
Manufacturer: Audiovox Communications Corp.  Model: PC5740  Revision: P100VE2T04_5.160  1  [Jan 26 2005 16:00:00] [Aug 01 2005 17:32:19]  ESN: 0x4DAAE7C  +GCAP: +CIS707-A, CIS-856, +MS, +ES, +DS, +FCLASS

So is it a driver thang?

---

### Post by sanicki on 2007-03-02
Got it! Okay. Since I couldn't find anything here's my quick and dirty on doing this. Anyone with deeper understanding of this topic please feel free to help clean it up a bit.

Start here...
1. Install KPPP
2. In KPPP under Misc tab have only auto-redials and disconnect on X server shutdown checked.

GC89 connecting to T-Mobile...
1. In Terminal type dmesg, then insert GC89 aircard and type dmesg again. You're looking for a change that contains tty* (mine was ttys0, which I'll use in this example)
2. In KPPP add an Account ('T-Mobile Aircard') and add phone number '*99***1#'. Keep authentication PAP/CHAP.
3. In KPPP add a Modem ('GC89 (TM)')
    a. Under Device tab set 'Modem device' to what you found with dmesg (mine was /dev/ttys0)
    b. Under Device tab you MUST change 'Connection Speed' to 57600
    c. Under Modem tab hit the Modem Commands button and change...
        Initialization string 1: AT+cfun=1
        Initialization string 2: AT+cgdcont=1,"IP","wap.voicestream.com"
4. When you try to Connect type two single quotes for Login ID and two single quotes for Password. (I'm sure there's a way to do this using a login script but I'm just happy to get this far!)

PC5740 connecting to Verizon...
1. In Terminal type dmesg, then insert PC5740 aircard and type dmesg again. You're looking for a change that contains tty* (mine was ttyACM0, which I'll use in this example)
2. In KPPP add an Account ('Verizon Aircard') and add phone number '#777'. Keep authentication PAP/CHAP.
3. In KPPP add a Modem ('PC5740 (VZ)')
    a. Under Device tab set 'Modem device' to what you found with dmesg (mine was /dev/ttyACM0)
4. When you try to Connect type use...
    Login id: <aircard phone #>@vsw3g.com
    Password: vzw

Hope this helps someone. Suggestions to improve welcome!

P.S. If anyone has gotten a Blackberry connected via USB to work as a modem I'd appreciate any insight. I keep getting 'Modem busy'.

---

### Post by sanicki on 2007-03-06
Also, when you start getting those timeouts @ 2 mins 30 seconds do this:
1. Open a Terminal
2. sudo gedit /etc/ppp/options
3. Change lcp-echo-interval to 0

---

### Post by sanicki on 2007-09-12
UPDATE: FYI, Verizon now has a Linux version of VZAccess Manager. I haven't tested it yet because KPPP allows me one interface for using multiple carrier aircards. It's not yet as robust as the Windows version (search for my separate post on trying to use a Moto Q9m tethered modem) and they don't advertise it (I needed a business support login from Verizon to download the deb) but it does exist.

---

### Post by Arch2 on 2007-12-02
Nice 'how-to'. I've been using the following method to get my gc89 working with my Dell L400.
[http://erikstambaugh.com/gprshowto.html](http://erikstambaugh.com/gprshowto.html)
Which is much more complicated.

KPPP was a fairly large install on Ubuntu (I noticed it comes standard on Kubuntu).

My setups were slightly different. 
Initialization string 2: AT+cgdcont=1,"IP","internet3.voicestream.com"
and I deleted the three Volume control strings at the bottom of Modem Commands.
Everything else is the same.

BTW I looked up my settings on my Windows computer under T-mobile Connection manager, Tools> Profiles> expand EDGE/GPRS> highlight T-Mobile(VPN)> Edit button> EDGE/GPRS tab.

I never could get this card to work on the L400 under Windows, but works great on Linux!!!

---

### Post by romanian_prince on 2008-02-28
Very excellent howto on the GC89; thank you; being a noob, this is the furthest I've come thus far! I am however running into an issue. The dialer doesn't seem to connect. It doesn't say why it fails, it just goes back to 'Modem Ready' after CONNECT.

AT+cfun=1
OK
AT+cgdcont=1,"IP","internet3.voicestream.com"
OK
ATM1L1
OK
ATDT*99***1#
CONNECT

I've tried all of the connect lines I could find through searching:
AT+cgdcont=1,"IP","wap.voicestream.com"
AT+cgdcont=1,"IP","internet3.voicestream.com"
AT+cgdcont=1,"IP","internet2.voicestream.com"

Oh, and I'm running Gutsy 7.10 with all updates

Any help would be REALLY appreciated. Thanks!

---

### Post by sanicki on 2008-04-28
(Sorry my response took so long.)

First check that KPPP is working with pppd. Open KPPP and click Configure then the Misc tab. If there's an entry for pppd version then you're fine. There was a bug in Feisty that I reported and I think was fixed for Gutsy but it never hurts to check. If pppd is blank then you need to make /usr/sbin/pppd executable.

For carrier settings [this]("http://www.modmyifone.com/wiki/index.php?title=Carrier_APN_Settings&oldid=3529") is a good resource.

FYI, To prevent timeouts I also had to edit /etc/ppp/options and change lcp-echo-interval to 0.

Hope that helps.

---

