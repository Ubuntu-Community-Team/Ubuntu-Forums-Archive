---
title: "ftp connection refused"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by benzipperer on 2008-11-17
I cannot download files from a remote, public FTP server using firefox or wget:

$ wget [ftp://www.bls.census.gov/pub/cps/basic/200701/jan07dd.txt](ftp://www.bls.census.gov/pub/cps/basic/200701/jan07dd.txt)
--17:39:17--  [ftp://www.bls.census.gov/pub/cps/basic/200701/jan07dd.txt](ftp://www.bls.census.gov/pub/cps/basic/200701/jan07dd.txt)
           => `jan07dd.txt'
Resolving [www.bls.census.gov](www.bls.census.gov)... 148.129.75.7
Connecting to [www.bls.census.gov|148.129.75.7|:21](www.bls.census.gov|148.129.75.7|:21)... failed: Connection refused.

On a Windows machine, I can use Internet Explorer to open a link like this. I am not able to do this using my machine running Feisty. Using my Feisty machine I am able to connect to non-anonymous FTP sites using gFTP.

My goals are to be able to

(1) use firefox so that when I click on a link like the one above, it opens successfully in firefox; and

(2) download files like the one above using a simple wget command.

Both (1) and (2) worked a few months ago on my machine. Now they don't work. What should I do to troubleshoot this problem?

Thanks for your help,
Ben
Linux hume 2.6.22-15-generic #1 SMP Tue Oct 21 23:47:12 GMT 2008 i686

---

### Post by cariboo on 2008-11-17
I checked all the links, and they all work except for the last link, where I get:

> Port Restricted For Security Reasons

see screenshot.

I'm located in British Columbia, so they are restricted by ip address.

Jim

---

### Post by benzipperer on 2008-11-18
cariboo907 - thanks for responding. My problem is that I cannot access the first link, or any of ftp links at [http://www.bls.census.gov/cps_ftp.html](http://www.bls.census.gov/cps_ftp.html) using firefox or wget. I am able to access them using a Windows machine using the same IP address/connection. 

What should I be looking for on my Feisty system to help me access those links by firefox or wget?

---

### Post by jonobr on 2008-11-18
Hello

Not much help for your here other then to say
I tested the links using swiftweasel 3.03
Firefox 3.04 and wget, all worked.

Im in the US/PST.

Im on Hardy, but I dont think that relates.

---

### Post by benzipperer on 2008-11-18
jonobr, thanks a lot for your reply -- since I can access the links on a Windows machine and since you can too using Ubuntu, that confirms the problem is isolated to my Feisty system in particular. 

I assume I have made some setting or have some process running that prevents me from accessing the ftp links below. If anyone has ideas on where to look on my system, I would appreciate any suggestions. For example, the wget command below tries to connect to the remote server via port 21, but then fails; is there some way to locate what is preventing this kind of connection from my machine?

For anyone else who is interested, please let me know if I'm not providing enough information.

---

### Post by jonobr on 2008-11-19
AFAIK, the commands ports are on port 21 but the data port is 20.
So for example, if you were to ftp on the command line
ftp <ipaddress>
it will ask for user name and then password.

Which you enter,
That done, on command line, you may change to binary mode (bin) and then enable hash markings (hash)

All of this is done on port 21.

Port 20 actually transports the data traffic.
Just mentioning incase you allowed port 21 and blocked port 20 on your firewall/router.

---

