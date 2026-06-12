---
title: "Printing problem from vista to ubuntu &quot;access denied: connection failed"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by masonfoley on 2008-08-24
I have a home LAN with 3 XP boxes, 1 Vista box and one Kubuntu Hardy Heron box.  My HP Laserjet 1100 hangs off the Kubuntu box and we have this printer "shared" onto the network.

The XP boxes have no problem whatsoever printing anything it pleases to the Kubuntu based printer (although bringing up the initial print dialog is a bit slow).

However, the only app I am able to print from Vista is my web browser (Firefox mainly).  Office apps, Adobe Acrobat Reader...none of these will print.

Here is a Screencast of the experience from the Vista side of things.  Note, there doesn't appear to be any errors (Here I am attempting to print for Excel 2007).

[http://screencast.com/t/wCH4CDCgKAd](http://screencast.com/t/wCH4CDCgKAd)

Oddly, whenever I bring up the Printers window in Control Panel, my default printer has an error status (even though I can still print to it from Firefox).

[http://screencast.com/t/N1wiPNnRO](http://screencast.com/t/N1wiPNnRO)

So my questions are, where do I begin to troubleshoot this?  What on the Kubuntu side can I monitor/diagnose that would help bring me closer to the crux of the issue.  Would posting the error_log from the CUPS folder help?

I see this error that appears to correspond with my attempt to print from Excel:
This is all that I see in the error_log when I print from Excel:

```
D [24/Aug/2008:14:48:34 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:48:34 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:48:34 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:48:34 -0400] CUPS-Get-Printers
D [24/Aug/2008:14:48:34 -0400] cupsdProcessIPPRequest: 14 status_code=0 (success                                                                                                                                                            ful-ok)
D [24/Aug/2008:14:48:34 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:48:34 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:48:34 -0400] CUPS-Get-Classes
D [24/Aug/2008:14:48:34 -0400] cupsdProcessIPPRequest: 14 status_code=0 (success                                                                                                                                                            ful-ok)
D [24/Aug/2008:14:48:34 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:15 -0400] cupsdNetIFUpdate: "lo" = localhost...
D [24/Aug/2008:14:49:15 -0400] cupsdNetIFUpdate: "eth0" = 192.168.0.26...
D [24/Aug/2008:14:49:15 -0400] cupsdNetIFUpdate: "lo" = localhost...
D [24/Aug/2008:14:49:15 -0400] cupsdNetIFUpdate: "eth0" = fe80::21d:7dff:fe7f:2801%eth0...
D [24/Aug/2008:14:49:15 -0400] Report: clients=0
D [24/Aug/2008:14:49:15 -0400] Report: jobs=59
D [24/Aug/2008:14:49:15 -0400] Report: jobs-active=0
D [24/Aug/2008:14:49:15 -0400] Report: printers=2
D [24/Aug/2008:14:49:15 -0400] Report: printers-implicit=0
D [24/Aug/2008:14:49:15 -0400] Report: stringpool-string-count=653
D [24/Aug/2008:14:49:15 -0400] Report: stringpool-alloc-bytes=8232
D [24/Aug/2008:14:49:15 -0400] Report: stringpool-total-bytes=12848
D [24/Aug/2008:14:49:26 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:26 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:26 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:26 -0400] Get-Printer-Attributes ipp:///printers/printers
D [24/Aug/2008:14:49:26 -0400] Get-Printer-Attributes client-error-not-found: The printer or class was not found.
D [24/Aug/2008:14:49:26 -0400] cupsdProcessIPPRequest: 14 status_code=406 (client-error-not-found)
D [24/Aug/2008:14:49:26 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:26 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:26 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:26 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:26 -0400] Get-Printer-Attributes ipp:///printers/PDF
D [24/Aug/2008:14:49:26 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:26 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:26 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:26 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:26 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:26 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:26 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:26 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:26 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:26 -0400] cupsdAcceptClient: 18 from localhost (Domain)
D [24/Aug/2008:14:49:26 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:26 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:26 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:26 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:26 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [24/Aug/2008:14:49:26 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:26 -0400] Get-Jobs ipp://localhost/printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:26 -0400] cupsdProcessIPPRequest: 18 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:26 -0400] cupsdReadClient: 18 POST / HTTP/1.1
D [24/Aug/2008:14:49:26 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:26 -0400] Get-Printer-Attributes ipp://localhost/printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:26 -0400] cupsdProcessIPPRequest: 18 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:26 -0400] cupsdCloseClient: 18
D [24/Aug/2008:14:49:26 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:26 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:26 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:26 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:26 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:26 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:26 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:26 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:26 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:26 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:26 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:26 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:26 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:31 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:31 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:31 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:31 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:31 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:31 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:31 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:31 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:31 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:31 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:31 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:31 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:31 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:31 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:31 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:31 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:31 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:31 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:31 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:31 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:31 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:31 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:31 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:31 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/printers
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes client-error-not-found: The printer or class was not found.
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=406 (client-error-not-found)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/PDF
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:32 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:32 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:32 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:32 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:32 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:32 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/printers
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes client-error-not-found: The printer or class was not found.
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=406 (client-error-not-found)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/PDF
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/printers
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes client-error-not-found: The printer or class was not found.
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=406 (client-error-not-found)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/PDF
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/printers
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes client-error-not-found: The printer or class was not found.
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=406 (client-error-not-found)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/PDF
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/printers
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes client-error-not-found: The printer or class was not found.
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=406 (client-error-not-found)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:33 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:33 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:33 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:33 -0400] Get-Printer-Attributes ipp:///printers/PDF
D [24/Aug/2008:14:49:33 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:33 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:34 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:34 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:34 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:34 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:34 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:34 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:34 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:34 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:34 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:34 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:34 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:34 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:34 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:34 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:34 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:34 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:34 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:34 -0400] cupsdCloseClient: 14
D [24/Aug/2008:14:49:34 -0400] cupsdAcceptClient: 14 from localhost (Domain)
D [24/Aug/2008:14:49:34 -0400] cupsdReadClient: 14 POST / HTTP/1.1
D [24/Aug/2008:14:49:34 -0400] cupsdAuthorize: No authentication data provided.
D [24/Aug/2008:14:49:34 -0400] Get-Printer-Attributes ipp:///printers/HP_Laserjet_1100
D [24/Aug/2008:14:49:34 -0400] cupsdProcessIPPRequest: 14 status_code=0 (successful-ok)
D [24/Aug/2008:14:49:34 -0400] cupsdCloseClient: 14

```

Any thoughts?

Cheers

---

### Post by masonfoley on 2008-08-24
Thought I would add to this the text to my /etc/cups/printers.conf file:

```
# Printer configuration file for CUPS v1.3.7
# Written by cupsd on 2008-07-28 19:34
<DefaultPrinter HP_Laserjet_1100>
Info 
Location Upstairs Office
DeviceURI parallel:/dev/lp0
State Idle
StateTime 1217287551
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
<Printer PDF>
Info PDF
DeviceURI cups-pdf:/
State Idle
StateTime 1208889833
Accepting Yes
Shared No
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
```

---

