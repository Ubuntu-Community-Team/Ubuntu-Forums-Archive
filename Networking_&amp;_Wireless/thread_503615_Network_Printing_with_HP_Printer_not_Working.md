---
title: "Network Printing with HP Printer not Working"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by jackn on 2007-07-18
I'm trying to set up network printing from a client laptop to a desktop to which an HP Deskjet 5740 is attached. I emphasize that printing from the desktop (server machine) directly works just fine.

From different posts, I understand that the procedure for setting up network printing to an HP printer is different from the ususal.

In particular, you need to use the jetDirect protocol on the client machine, and not ipp. The jetDirect protocol looks for port 9100, rather than the usual 631.

I set my client laptop as I understand the instructions in the forums, but I don't get any printing done.

The printing window ('open' from the the printing icon) says 'Printing:job-printing', which is just right...

Running lpstat, however:

[CODE]
lpstat -p -d
printer DeskJet-5740 now printing DeskJet-5740-18.  enabled since Wed 18 Jul 2007 09:51:48 AM CEST
        Unable to connect to printer (retrying in 30 seconds): Connection timed out
system default destination: DeskJet-5740
[CODE]

shows that the client can't connect to the printer.
I don't know why that is.

I've enclosed an attachment of my network printer 'connection' configuration (system-administration-printing). 
Basically, I've told it to use jetDirect, gave it 192.168.0.1 as the host address, and it uses port 9100 by default.

Here are the things I wonder about:
[LIST]
[*]Should the host address be different? Should I provide it with an IP address of the printer, and not of the desktop, in other words. If so, how do I find the printer's IP address?
[*]Should I do something on the server side? The default setup (system - administartion - printing) only allows you to set the printers as 'shared printers', but that automatically sets up port 631. Should I open port 9100? If so, how?
[/LIST]

Thanks for your help.

Jackn

---

### Post by linuxwizard on 2007-07-19
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by jackn on 2007-07-19
Very grateful for this quick response, Linuxwizard.

The reference you gave me is indeed the clearest I've found, and I've looked around long and wide...

In order to post the results here, I've followed the reference you gave again.

Results:
[LIST]
[*]When I send a job from the client to the server, I get the usual report (printer icon - open) - "Printing: job-printing", just as I get upon successful printing from the server.
[*]Running lpstat -p -d gives:
```
lpstat -p -d
printer DeskJet-5740 now printing DeskJet-5740-28.  enabled since Thu 19 Jul 2007 09:46:14 AM CEST
        Connecting to 192.168.0.1 on port 631...
system default destination: DeskJet-5740

```
[*]Running lpq gives:
```
jacknn@itamar:~$ lpq
DeskJet-5740 is ready and printing
Rank    Owner   Job     File(s)                         Total Size
active  jacknn  28                                      35840 bytes

```
[/LIST]

In short, it all looks good, except the printer doesn't budge...

One last test I carried out was ping-ing the host and the printer. 

```
ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=5.31 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=5.76 ms
 (snipped)
jacknn@itamar:~$ ping 192.168.0.1:631
ping: unknown host 192.168.0.1:631

```

So the server machine can be talked to, but not the port through which the printer is supposed to be listenting.
Does this mean I need to modify the server's /etc/cups/cups.conf file in order to allow the server to listen at this port?

As I was getting nowhere, I started squatting the forums.
[This post in the forums]("http://ubuntuforums.org/showthread.php?t=288860"), in particular, indicated to me that, with an HP machine, I shoudl not follow the setup recommended in the Ubuntu Wiki.

In particular, I gathered thaI with  HP  machines, on the client side, I should choose the jetDirect HP protocol (instead of the default IPP used by CUPS), and port 9100, instead of 631.
I might have jumped into conclusions there, and I can't find a clear statement on the web, as to whether, indeed, many HP printers require a different protocol for network printing. It might be that this is only true when you have a dedicated print server, I just don't know.

Setting up the client with jetDirect still didn't allow me to print. Again, it would all look good, but there would be no printing.

Where I stand now, I don't know:
[LIST] 
whether indeed my machine calls for the HP jetDirect protocol on the client side (not at all mentioned in the Ubuntu Wiki)
[*]and whether, if I do need this protocol, how to find the printer IP that I need to put in when setting the client up with the jetDirect protocol...
[/LIST]

Can you help, please? Thank you...

Jackn

---

