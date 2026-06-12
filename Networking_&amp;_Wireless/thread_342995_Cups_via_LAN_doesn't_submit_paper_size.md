---
title: "Cups via LAN doesn't submit paper size"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by mthie on 2007-01-20
Hello,

I have two servers on Dapper Drake 6.06.1 AMD64:
- a CUPS server with 6 printers without any GUI
- an XDMCP/LTSP-Server with Kubuntu

The problem:
The XDMCP server uses the printers, that are shared by the CUPS server. That works good but the XDMCP server doesn't get the correct paper format. We use DIN ISO A4 but I always get Letter format. If I change it in OpenOffice.org it prints in A4 but after restart OpenOffice.org I have Letter as standard format.

If I connect with my Ubuntu 6.10 with Gnome I also get no correct format but if i change it in gnome-cups-manager it saves the correct settings even for OpenOffice.org.

On Kubuntu I change the settings to A4 (or another printer to A3), go into OpenOffice.org but it has U.S. Letter as format.

Is there any chance to say the complete system and any software using CUPS to use the correct paper format per printer?

We have printers by Kyocery and HP and some others, so it can't be a problem of one manufacturer.

Thank you

Martin

---

