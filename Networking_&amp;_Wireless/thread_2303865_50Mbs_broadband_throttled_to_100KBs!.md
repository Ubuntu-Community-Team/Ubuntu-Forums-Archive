---
title: "50Mb/s broadband throttled to 100KB/s!?"
date: 2015-11-22
forum: Networking &amp; Wireless
---

### Post by adagio on 2015-11-22
I have a cable broadband connection that should be delivering 50Mb/s.

A few weeks ago downloads for some reason started downloading at no more than 1990's broaddband speeds (100KB/s at most) - enough to watch a Yahoo News video but most certainly not download the latest Ubuntu DVD.

The question essentially is where to next, having been through the following so far:

1) Observing the connection it is odd that every time I ran a broadband speed test at the request of the broadband cable provider, the download speed jumped back up to 50Mb/s, however as witnessed by the ISP also a http download was more or less immediately throttled to approx. 100KB/s.  Multiple parallel downloads did not result in an increase in this bandwidth, i.e., each download slowing down allowing the remaining downloads to start up.  The ISP has sent an engineer around who cannot see any problems with the modem or network otherwise (ergo not suggesting any solutions).

2) Even odder, if I run speedtest-cli in parallel with an http download (e.g., [http://www.thinkbroadband.com/download.html](http://www.thinkbroadband.com/download.html), using curl) the http download accelerates while the speed test is in progress dropping back off again at the point of thinkbroadband reporting the speed test results.

3) Web pages seem to load with a short burst of speed (inc. loading a short video when the play button is pressed), if there is a file downloading at the same time the download will accelerate briefly while the web page is loading then falling back again to the  100KB/s mark.

4) ifconfig reports approaching 20% packet loss on a 5MB download

5) In the past there has been tampering with the broadband cable just outside of the property.

6) Single user mode does not solve the issue.

7) The same results with both a ssh SOCKS5 proxy and openvpn (individually and with ssh tunneled through openvpn).

8) tracepath reports only as expected (with the caveat there do seem to be two or three consistently anonymous nodes in the reported route directly following my own ISP's jumping off point).

9) The reduction in broadband speed is evident from the point that a clean install is first brought onto the Internet.

I'm running at the moment Ubuntu 14.04 LTS (recent install, security updates actually installed from an external drive before bringing a network interface up, reboot, etc.; the install itself not behaving in any way that might suggest any problems other than perhaps the usual web browsing [anonymity based] issue or two).  vnstat has been a useful util. for monitoring network traffic.

Where to start with the above being essentially the question!?

---

### Post by Lars Noodén on 2015-11-22
> **adagio said:**
> 1) Observing the connection it is odd that every time I ran a broadband speed test at the request of the broadband cable provider, the download speed jumped back up to 50Mb/s, however as witnessed by the ISP also a http download was more or less immediately throttled to approx. 100KB/s.  Multiple parallel downloads did not result in an increase in this bandwidth, i.e., each download slowing down allowing the remaining downloads to start up.  The ISP has sent an engineer around who cannot see any problems with the modem or network otherwise (ergo not suggesting any solutions).

2) Even odder, if I run speedtest-cli in parallel with an http download (e.g., [http://www.thinkbroadband.com/download.html](http://www.thinkbroadband.com/download.html), using curl) the http download accelerates while the speed test is in progress dropping back off again at the point of reporting the speed test results.

I would trust the second not the first.  ISPs have been known to prioritize traffic to and from known speed test sites. Your test suggests this may be happening in your case too.  If you can find or make a speed test site that they don't know about you might be able to get more accurate measurements.  Though curl and sftp will probably be enough

---

### Post by adagio on 2015-11-22
The modem 'operation configuration':

Primary Downstream Service Flow / Max Traffic Rate 	57344000 bps
Primary Upstream Service Flow / Max Traffic Rate 	3170000 bps

I'm restricted to HTML speed tests, however some results:

HTML? - [http://www.thinkbroadband.com/speedtest.html](http://www.thinkbroadband.com/speedtest.html) reports 45.9Mb/s download and 3.3Mb/s upload

HTML5 - [http://speedof.me/](http://speedof.me/) reports 14.44Mb/s download and 2.98Mb/s upload

HTML - [http://testmy.net](http://testmy.net) reports 2.9Mb/s download, 1.4 Mb/s upload

http - using a curl file download from [http://download.thinkbroadband.com/20MB.zip](http://download.thinkbroadband.com/20MB.zip) reports averaging 542KB/s

socket - speedtest-cli [https://github.com/sivel/speedtest-cli](https://github.com/sivel/speedtest-cli) reports 35.91 Mbit/s download, 2.93 Mbit/s upload

However the testmy.net result was more interesting, in that the test is based purely on transferring a file, and that while the first approx. 5MB of the 44MB file downloaded in a split second, the speed then suddenly dropping to a crawl more approaching the 2.9Mb/s average, then taking several minutes for the remainder of the file to download (testmy.net I would guess decides on the initial size of the file download based on a quick short test download, hence the file download size set at 44MB following a very fast quick initial test of the connection).

The curl result is even more interesting, taking 37s, there was an initial burst of speed for approx. 1s, peaking at approx. 5MB/s (approaching the full ISP advertised speed), before falling back to approx. 300KB/s for the remainder of the download.  The second (and subsequent) download of the same file however did not show the initial burst with a download time of 55s.

No proxies or encryption otherwise, firefox where browser based.

[Edit] Additional result:

HTML5 - [http://www.bandwidthplace.com/](http://www.bandwidthplace.com/) reports 4.55 Mbps Download, 2.88 Mbps Upload

---

### Post by adagio on 2015-11-22
When I ran thinkbroadband's speed test [http://www.thinkbroadband.com/speedtest.html](http://www.thinkbroadband.com/speedtest.html) (which reported near to the full ISP advertised broadband speed when previously run) alongside the same 20MB curl file download [http://download.thinkbroadband.com/20MB.zip](http://download.thinkbroadband.com/20MB.zip) (i.e., both at the same time) curl reported the file as taking 8s to download at an average speed of 2.49MB/s - just over 4 times faster (approx. half advertised download speed) than downloading the file alone (i.e., without the thinkbroadband browser based speed test running in the background).

---

### Post by tgalati4 on 2015-11-22
Do you have a router between your Cable Modem and your computer?  Is this a wired connection?  Where do you suspect the 20% packet loss coming from?  I had a similar issue a few months ago.  Turned out to be the 1 Gb switch had a failing power supply causing packet drops and slow performance.

---

### Post by adagio on 2015-11-24
The engineer the ISP sent around did mention signal to noise ratio, checked the modem was OK (no indication of any problems, cabling, the network itself, etc.) but did not venture any further as to what might have been causing the packet loss.  He seemed to think this was more likely to be a (I assume, network...) software related issue than anything.

The ISP supplies a modem / router - switchable between the two, I generally keep it in the simplest configuration (modem), if I attach a router usually to a second USB ethernet interface (which does actually drop packets like crazy - probably related to sunspot activity).

---

### Post by tgalati4 on 2015-11-24
How old is the modem?  Most have a webpage that you can log into and download log files.  Look at the modem logs for messages related to dropped packets.

Try changing the wall-wart that powers the modem.  They can fail in subtle ways that cause the modem to act in strange ways.  Find a spare from another piece of network equipment (typically 12VDC, with center-post positive).  Make sure the connector fits easily, don't force it and make sure the voltage, amperage and polarity match the old one.

---

