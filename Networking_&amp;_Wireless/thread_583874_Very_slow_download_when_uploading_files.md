---
title: "Very slow download when uploading files"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by DrumScum on 2007-10-20
Hi,

When I'm uploading files (ftp, bittorrent ... ) browsing the internet is very slow. Even a simple page like google.com takes ages to show up. Directly downloading files though (http, ftp, bittorrent ... ) works at normal speed. Any ideas? Could it be that the uploads jam the upload bandwidth so that sending ack packets goes way to slow? If so, is there a way to "cap" the general upload speed to some kB/s below the theoretical maximum?

I have a broadband cable connection (wired) and onboard AMD (ATI) lan. Gutsy here, but Feisty did the same.

---

### Post by benchMarc on 2007-10-28
I was asking myself the same question. I guess it can be done, but how?

---

### Post by aldeby on 2007-11-01
This is an issue of your internet provider, it is not an Ubuntu problem.

The reason behind this misbehavior is that you certainly use an ADSL line which is by design *asynchronous*. That means that you have a wide download bandwith and a very narrow upload bandwith. You should know that TCP/IP protocol (the one we all use to surf/download from the internet) requires that for every data packet that gets in, one ACK packet needs to get out in order to tell the remote server the previous packet correctly arrived at his destination. If the remote server does not receive any ACK packet it does not send you any further data packet.

Now, since you saturate with an upload (i.e. high P2P uploads) all your upload bandwith your provider provides you, your network interface has to queue the ACK packets, thus the remote server slows down the data packets thinking there is a traffic jam on your internet connection. And that is what actually happens!

You should definitely complain with your internet provider for this! Or maybe just buy an internet access where DL/UL speed are not so different. I.e. a 4Gbit/0,2Gbit connection will never reach its full download speed if you use up all your upload bandwith.

---

### Post by NotRoot:-) on 2007-11-01
[http://news.google.com/news?hl=en&ned=&ie=UTF-8&q=throttling&btnG=Search](http://news.google.com/news?hl=en&ned=&ie=UTF-8&q=throttling&btnG=Search)

The above URL gives multiple news stories about Comcast and other ISP's throttling their network traffic.

Also most ISP's a much higher download ratio than upload ratio.  If you max out the upload ratio, the downloads will be very slow or
blocked.

---

### Post by Ultimadlamer on 2007-11-01
It should be noted that setting a system-wide cap would be a  bad idea, because due to what aldeby said, it would run slower.

I think the appropriate solution would be to find the throttling options in the programs you use for Bittorrent and FTP.  I happen to not be using those protocols much inside linux at the moment, but on XP my bittorrent client (utorrent) has a function for throttling the upload speed.  I would look for a similar option within whatever program you're using.

---

