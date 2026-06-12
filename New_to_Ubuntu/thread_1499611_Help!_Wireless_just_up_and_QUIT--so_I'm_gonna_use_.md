---
title: "Help! Wireless just up and QUIT--so I'm gonna use CAT5! :D"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by bytescribe on 2010-06-02
Okay, I've had Karmic for a few weeks now. I've been successfully running wireless with a Linksys router/adapter(dongle) until this past Monday. Everything was working fine Sunday night, then Monday morning, zip, zero, nada!

I rebooted and rebooted trying to bring up the 'linksys' router connection in the dropdown list since that's worked before. But not this time.

I remember installing some security updates recently, including an update to the kernel, but that was Sunday, and I have no clue whether that would have anything to do with what's just happened to my wireless connection.

Now, one option I have for sure is to pay out the money for DSL cable, which I am more than willing to do, should that be necessary, because I am tired of dealing with issues like these.

The other option (since I also can't seem to find the disks for my router--that I've not had to use since my adapter has managed to 'see' the signal so far, ergo not yet needing a passkey), is to buy an entirely new router just to get new disks, a new passkey (ergo needing to get new wireless drivers, since I assume not even the same router model has the same driver requirements?)...

So, I am feeling real frustrated since I (and my boyfriend) just signed up for Skype services that we have really enjoyed--AND I'm without a printer now, since I'd need the internet connection to download the hplip-gui. ARGH!

I guess, in the biggest scheme of things, this isn't a big deal, but my livelihood includes the internet, to some extent. Not to mention the convenience of Skype! ;)

Can anyone shed some light on my situation?

---

### Post by Martin Marshalek on 2010-06-02
Okay, I might be able to help you out here. Go into terminal and type: ```
lspci
``` Then run the command. Copy and paste the output here and I'll see what I can do based off of that. I had a similar problem but found a solution but would like to make sure yours is the same.

---

### Post by bytescribe on 2010-06-02
Hi Martin! I ran the command you suggested and this is what I got:

[B]00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:02.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)

[/B]

Any thoughts? I'm totally wishing I had a laptop right now just for internet purposes. :/

Thanks a Bunch!
Kat ^.^

---

### Post by sandyd on 2010-06-02
> **bytescribe said:**
> Hi Martin! I ran the command you suggested and this is what I got:

[B]00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:02.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)

[/B]

Any thoughts? I'm totally wishing I had a laptop right now just for internet purposes. :/

Thanks a Bunch!
Kat ^.^
its not in there - unless its the 56k modem.

can you do
```

lsusb
```?

---

### Post by bytescribe on 2010-06-13
Hmmm...you'd think that's what someone else would have recommended before...:P

Okay...I haven't run it yet because I'm fed up enough with wireless/Linux issues that I went and found m'self a super-nice bargain on 100 ft of CAT5 ethernet cable that I can plug into the router downstairs and run it (with my boyfriend's help) all the way across the basement ceiling up to my room. This is what I originally wanted but my non-computer-geek dad (with a bent towards going to Staples and paying their outrageous prices just because a salesperson sells him a "bill of goods") told me he didn't want to pay out. But I now have a source (verified/accredited by the BBB!) for such supplies that would make Staples CEOs have an immediate need for the Heimlich maneuver.

Sooo, completely new question...just for clarification's sake:

I am going to assume that I need to have my ethernet cable plugged in to my computer so that the connection called "eth0" is recognized automatically...correct? I know...dumb question, but I don't want to have my computer not recognize the cable because I did something out of order. :P

Thanks again,
Kat ^.^

---

### Post by coolbrook on 2010-06-13
> I need to have my ethernet cable plugged in to my computer so that the connection called "eth0" is recognized automatically.That's correct.

---

### Post by bytescribe on 2010-06-22
I thought so...thank you for that confirmation! :D 

Time for a fresh reinstall of Ubuntu...

But first--time to put on the coffee and have me some lunch!

Laterz,
Kat ^.^

---

### Post by Iowan on 2010-06-22
Connect the cable and give it a try **before** you re-install... if it doesn't work, you haven't invested much time.

---

### Post by bytescribe on 2010-07-01
Well, I mostly wanted to reinstall because I felt like starting completely fresh, and I had to wait to install the cable anyway since my boyfriend's work schedule isn't like mine. But it's neither here nor there, now. The cable connection works like a dream! I am accessing most sites with far less trouble than I did with wireless. And no more worrying whether an update's gonna stall out because of a dropped signal.

---

