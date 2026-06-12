---
title: "Setting up a Network Printer in Ubuntu 6.06 LTS"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by johnhop45 on 2007-05-07
i have a Minolta DL2300 and i have been trying to set it up on my network. I have had no luck. The network printer is configured to accept the network and the cable is plugged in. The machine just sits there and does not do anything after i hit test print page. Any recommendations would be helpful

---

### Post by tgalati4 on 2007-05-07
In a browser, tell us what you see when you put in:

localhost:631

Also, check the front panel.  You normally need to program in a network address such as 192.168.1.205.

---

### Post by dbott67 on 2007-05-07
How is the printer configured?  Is it connected directly to the LAN and have an IP address assigned?

If so, when setting up the printer in Ubuntu, you'll want to enter the following parameters:

_**Step 1: Printer Connection Type**_

1. Printer Connection Type: Network Printer, TCP/Socket, HP Jet Direct, Raw Connection.

2. Host: IP address assigned to Minolta Printer

3. Port: 9100 (default)

_**Step 2: Printer Driver**_

4. Manufacturer: Minolta

5. Model: magicolor 2300 DL

6. Driver: foo2zsj (Recommended) (suggested).  Click FORWARD.

_**Step 3: Printer Information**_

7. Enter desired "Printer Information" and click APPLY.

Check here for a similar setup in Suse:
[http://foo2zjs.rkkda.com/suse/dl2300.html](http://foo2zjs.rkkda.com/suse/dl2300.html)

-Dave

---

### Post by dbott67 on 2007-05-07
Just for clarification, tgalati4 is checking whether or not you're using CUPS to share the printer (which is recommended if you have multiple PCs that need to use the printer and you want to "control" access to it, pause jobs, etc.).

Many network printer allow you to print directly to them using TCP (which is the method I outlined above).

If you wish to share the printer among other users with CUPS, then follow these steps:

[http://ubuntuforums.org/showthread.php?p=2599099#post2599099]("http://ubuntuforums.org/showthread.php?t=434022")

-Dave

---

### Post by tgalati4 on 2007-05-07
Most newer network printers have a rudimentary web-based control as well.  You can type 192.168.1.205:9100 and if your printer has a web page, it will show up and you can change some settings that way as well.

I always set up my printers with direct tcp connection and as a CUPS entry.  This way if there is a problem with the printer, I have a backup queue on a machine that will respool the job when the printer comes back on line.

Without this backup queue, the printer will often lose jobs because of power cycling or other network weirdness.

---

