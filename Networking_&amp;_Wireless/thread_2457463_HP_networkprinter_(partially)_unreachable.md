---
title: "HP networkprinter (partially) unreachable"
date: 2021-02-02
forum: Networking &amp; Wireless
---

### Post by Lólindir on 2021-02-02
Hi all!

I encountered the following strange behavior on the Ubuntu laptop from a friend. She updated from 18.04 to 20.04 last week and wanted to reinstall her HP OfficeJet Pro 8720 network printer, which was working correctly before.

Since she didn't like the auto discovered printers popping-up all the time, I've tried to disable the auto-discovery. I might have messed up something here. What I did was:
[LIST=1]
[*]systemctl stop cups-browsed
[*]systemctl disable cups-browsed
[/LIST]
Since that didn't work I've enabled an started the service again. I've also tried to put BrowseProtocols to None in /etc/cups/cups-browsed.conf, which also didn't seem to work. I've reverted these settings.

Since she's using HPLIP (repository version), we wanted to reinstall the printer here. Unfortunately the printer was not found anymore. Nevertheless, the printer seemed to be auto-discovered again in the Ubuntu printer screen.
I've tried to ping the printer, which was not possible. Also trying to open the embedded web server of the printer was not working (address unreachable). However if she tries to open the embedded web server from her smartphone in Chrome (same WiFi network), this works. Why it is not reachable from her laptop (Firefox and Chromium) is not clear to me. I have the same printer at home as well, and I can ping it and browse to it from mu Ubuntu 20.04 desktop.
FYI: other IP's like the default gateway are pingable and reachable via the web-browser, only the IP address of the printer is not reachable.

I've tried to remove HPLIP and CUPS afterwards (apt purge), and reinstall it, that however didn't solve anything, as I was afraid. Next I've removed HPLIP and downloaded the latest version from the HP website. I've installed it, but also here the same problem: no printer found with HPLIP. I've removed the downloaded version again and reinstalled the version from the repository, however now I cannot startup the HP toolbox at all anymore (it crashes: I think the version from the HP website did break something).

I can add the printer manually via CUPS in the web browser. It is displayed there and I can install it. However when trying to print something, it says that communication with the printer is not possible.

I'm out of ideas at the moment, what can be wrong. Can someone help?

Many thanks in advance!

---

