---
title: "How to attach driver to device?"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by scoobyNZ on 2006-11-01
Hello there,

Well, I am continuing to investigate wireless problems and would appreciate some help - if anyone can make head nor tails of my woes.

I have discounted the prism54 driver and have blacklisted this in the blacklist file.

I have downloaded the drivers for 3Com 3CRWE154G72 from the internet, so I know I have the latest drivers. I have then installed the drviers using ndiswrapper and ndiswrapper - l command gives me;

Installed ndis drivers:
3c154g72                driver present 

So I know the drviers are loaded right?

Anyway, if I run a lshw I see the following;
     *-network UNCLAIMED
          description: Network controller
          product: 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter]
          vendor: 3Com Corporation
          physical id: 0
          bus info: pci@02:00.0
          version: 01
          width: 32 bits
          clock: 33MHz
          capabilities: cap_list
          resources: iomemory:42000000-42001fff irq:11

So I know the driver is not attached to the wireless card!!

From the ndiswrapper help page it says to run this command, tail /var/log/messages, to check for error messages. I think i get some error messages as the output is this,

craig@craig-laptop:~$ tail /var/log/messages
Nov  1 22:49:54 localhost gconfd (root-5842): starting (version 2.14.0), pid 5842 user 'root'
Nov  1 22:49:54 localhost gconfd (root-5842): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov  1 22:49:54 localhost gconfd (root-5842): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Nov  1 22:49:54 localhost gconfd (root-5842): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov  1 22:49:54 localhost gconfd (root-5842): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Nov  1 22:49:54 localhost gconfd (root-5842): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov  1 22:50:00 localhost dhcdbd: Unrequested down ?:3
Nov  1 22:50:24 localhost gconfd (root-5842): GConf server is not in use, shutting down.
Nov  1 22:50:24 localhost gconfd (root-5842): Exiting
Nov  1 22:56:56 localhost kernel: [17181099.788000] pccard: card ejected from slot 0
craig@craig-laptop:~$

Can anyone out there shed any light on what is happening? It appears that the driver is being loaded but then not being attached to the wireless card or slot or something - this is one step to far for my limited experience. How do I attach the driver to the card and be on my way laughing. . . . .

Any help would be most appreciated, I am faltering at the edge of giving up and need some support ](*,) 

thanks,
Craig

---

### Post by scoobyNZ on 2006-11-01
Sorry! I note i didnt have the card in the slot when I ran the tail /var/log/messages

the output should read
craig@craig-laptop:~$ tail /var/log/messages
Nov  1 23:13:54 localhost kernel: [17182117.736000] pccard: CardBus card inserted into slot 0
Nov  1 23:13:54 localhost kernel: [17182117.736000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
Nov  1 23:13:54 localhost kernel: [17182117.736000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
Nov  1 23:13:54 localhost kernel: [17182117.736000] ndiswrapper: using irq 11
Nov  1 23:14:10 localhost kernel: [17182133.296000] ndiswrapper (miniport_init:240): couldn't initialize device: C0000001
Nov  1 23:14:10 localhost kernel: [17182133.296000] ndiswrapper (pnp_start_device:479): Windows driver couldn't initialize the device (C0000001)
Nov  1 23:14:10 localhost kernel: [17182133.300000] ndiswrapper (miniport_halt:271): device dade3260 is not initialized - not halting
Nov  1 23:14:10 localhost kernel: [17182133.300000] ndiswrapper: device eth%%d removed
Nov  1 23:14:10 localhost kernel: [17182133.300000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
Nov  1 23:14:10 localhost kernel: [17182133.300000] ndiswrapper: probe of 0000:02:00.0 failed with error -22
craig@craig-laptop:~$

Sorry for any confusion - it has been a long hard couple of nights!

C

---

### Post by wieman01 on 2006-11-02
Deleted... Database error!

---

### Post by wieman01 on 2006-11-02
Mmm... This is a hardware issue, not relating to Ubuntu. Do you have Windows on the machine by chance? Does the wireless device work there?

From what I see here, the card is deactivated. Does it have a hardware switch or anything? Or can you enable it in the BIOS perhaps?

---

### Post by scoobyNZ on 2006-11-02
Hi, thanks for your help!

I do have this wireless card running under windows and I do have windows in a dual boot system. I will eventually ditch windows, once I get the system going on Ubuntu. The card is working under windows under windows drivers, ie I didnt have to install the CD at all.

I dont have a hardware switch on my computer for the card, well not one that I have ever used anyway. I am running an Acer630 travelmate, it is older than switches for wireless i think :D 

How would I go about enabling it in BIOS? I have never seen anything in Bios like that. I will post this and then restart my computer and try and find the BIOS version and have a snoop around there for anything.

Thanks again. . . .
C
ps. how do i track this thread so I do not have to hunt for it each time?

---

### Post by scoobyNZ on 2006-11-02
Hello again,

My system BIOS version is V4R6.1 R01 C0O

I had a look around there and everything to do with ports looked enabled but to be honest it is a bit out of my range of knowledge.

You say you think it is a hardware problem and I do not disagree, the driver is loaded but the light on it wont blink - not even one little blink/glimmer of hope! I just thought that the driver wasnt attaching to the device or the device wasnt activated / initialsed. How do you reckon we do that?

Thanks,
C
ps I found how to track this thread :KS

---

### Post by wieman01 on 2006-11-02
Perhaps this is not a hardware issue after all. The other option I can offer is that you need to get hold of the latest Windows driver (vendor website). Other users seem to have had a similar issue, whereby the version of the driver that is shipped with the device is malfunctioning under Ubuntu (LED not lit). Possibly the latest driver does the job. 

I'll keep an eye on this thread. Please try the latest Windows driver first.

---

### Post by scoobyNZ on 2006-11-03
Funniest thing, when I turned on my computer this morning the wireless was fully operational! All I did was left it alone for a night and went out to the pub:D  But seriously, the only thing I have done differently today was not have my hard wire internet connected to the computer at start-up.

For anyone with the same card I am using the latest driver from the 3com site and am running this through ndiswrapper - there are threads on the forum explaining how to install this.

thanks for your help wieman, the world needs more people like yourself!
C

---

### Post by wieman01 on 2006-11-03
Welcome... I see... This has happened to others before. Should have known that. :-) Anyway, glad it's working now.

---

