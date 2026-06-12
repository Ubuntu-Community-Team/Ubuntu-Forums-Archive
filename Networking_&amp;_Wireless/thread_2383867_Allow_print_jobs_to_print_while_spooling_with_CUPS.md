---
title: "Allow print jobs to print while spooling with CUPS"
date: 2018-01-30
forum: Networking &amp; Wireless
---

### Post by swampdog20022 on 2018-01-30
Hello all, I just recently installed Ubuntu Server 16.06 to utilize as a print server for the organization I work for. I have CUPS installed and configured, along with the three networked HP printers that are used. Everything seems to work fine between the Windows clients and Linux print server, however I noticed that with large print jobs, the job must be entirely spooled on the Ubuntu machine in order for the job to finally print. When there was a Windows-based print server, the print jobs would spool and print while still spooling. How to I allow this feature to be the same within Ubuntu, where the jobs sent to the printers begin to print without having the whole job spool on the server first? What setting do I need to enable either in the cups configuration file, or somewhere else, for this to occur? Thank you in advance.

---

### Post by #&amp;thj^% on 2018-01-30
> **swampdog20022 said:**
> Hello all, I just recently installed Ubuntu Server 16.06 to utilize as a print server for the organization I work for. I have CUPS installed and configured, along with the three networked HP printers that are used. Everything seems to work fine between the Windows clients and Linux print server, however I noticed that with large print jobs, the job must be entirely spooled on the Ubuntu machine in order for the job to finally print. When there was a Windows-based print server, the print jobs would spool and print while still spooling. How to I allow this feature to be the same within Ubuntu, where the jobs sent to the printers begin to print without having the whole job spool on the server first? What setting do I need to enable either in the cups configuration file, or somewhere else, for this to occur? Thank you in advance.

Have you yet tried try using the waitjob=false and/or waitprinter=false CUPS options:

```
ipp://host/queue?waitjob=false&waitprinter=false

```
These options are described at [http://www.cups.org/documentation.php/doc-2.0/network.html#IPP](http://www.cups.org/documentation.php/doc-2.0/network.html#IPP), although I'm not sure what the difference between waitjob and waitprinter is.:D

---

### Post by swampdog20022 on 2018-01-31
Ok so where do I put these commands at? The printers are already mapped in Windows, so I am not sure if this goes in the cups config file or what. Thanks.

---

### Post by swampdog20022 on 2018-01-31
So with this syntax: 

ipp://host/queue?waitjob=false&waitprinter=false
How to I add those end parameters in Windows? These appear to be for Linux. In Windows, you need to use the format: [http://hostname:631/printers/printer_name](http://hostname:631/printers/printer_name) to use IPP.

---

### Post by swampdog20022 on 2018-01-31
Ok an update to the issue. I was able to find the information within the /etc/cups/printers.conf file to alter the DeviceURI to attempt to add these settings. So, with that, the printer is an HP LaserJet M806, and it's IP address is 192.168.1.50, and its queue name is HP05. I added the following to the cups configuration file:
```

DeviceURI ipp://192.168.1.50:631/printers/HP05/?waitprinter=false&waitjob=false

```
However, when printing from a Windows client, there is no change, as the documents need to finish spooling first before anything is printed. This is where I am confused as to what to do, as I've done what most I have read on other forums and the cups documentation, to no avail.

---

### Post by #&amp;thj^% on 2018-01-31
> **swampdog20022 said:**
>  These appear to be for Linux. In Windows, you need to use the format: [http://hostname:631/printers/printer_name](http://hostname:631/printers/printer_name) to use IPP.

I only use Linux so no help for windows from me at least.;) How did we get windows involved here?
> Hello all, I just recently installed Ubuntu Server 16.06 to utilize as a print server for the organization I work for. I have CUPS installed and configured,
Sorry I thought you would understand,:( but that was not a command to put in the terminal, instead it was clue for your "/etc/cups/printers.conf" file.
These suggestions are solely for "Ubuntu Server 16.06" to be clear.
Slight delays between print jobs are common when printing multiple documents through CUPS.  This is caused by cupsd waiting for the previous job to complete before processing the next job.  This is done to ensure that print jobs are not lost by sending jobs to the printer before it is ready.  _This behavior can be changed_, **however, it is done at the Administrator's own risk as the steps outlined below remove the built-in safety net of making sure each print job is fully processed.**
You may need to show us the text in: "**/etc/cups/printers.conf**"
Again just to be clear this is an **example to use**:
```
ipp://<ip-address-or-hostname>:<port-number>/<resource>?waitprinter=false
```
Now to try to relieve some frustration, I kind of have a new defintion for CUPS.(Crapy Unix Print Service)(Much Love to the Devs;))

---

### Post by #&amp;thj^% on 2018-01-31
> =swampdog20022;13735851
However, when printing from a Windows client, there is no change, as the documents need to finish spooling first before anything is printed. This is where I am confused as to what to do, as I've done what most I have read on other forums and the cups documentation, to no avail.
And I forgot to mention here that cups needs to be restarted to see the/any effect made.
```
systemctl restart cups.service
```

---

### Post by #&amp;thj^% on 2018-01-31
I just checked our printer uses the following URL on Linux:
```
ipp://ldslnx01/printers/HPLJ4000-PS
```

So the Windows equivalent of that becomes:
```
http://ldslnx01:631/printers/HPLJ4000-PS
```
Add your right syntax.
Hope this Helps you.

---

### Post by swampdog20022 on 2018-02-01
Ok I appreciate your posts, but not really helpful at all. Thanks though. I need to be able to have jobs sent from Windows clients begin to print almost immediately when a job is sent to the Ubuntu server. Again, I have already added the following line to my /etc/cups/printers.conf file:
```

DeviceURI ipp://192.168.1.50:631/printers/HP05/?waitprinter=false&waitjob=false

```
But yet the entire job still needs to spool first before anything prints. Anyone else that uses Windows in an environment like this have any resolution that I might try?

---

