---
title: "Detailed Traffic Accounting Packages need direction."
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by Dalik on 2008-05-28
I have been looking around for traffic accounting packages and I would like some help with this, I am looking to monitor the following.

Network setup.
- Linux Firewall
- Windows Terminal Server
- Linux Server hosting the following - FTP, HTTP, Email.
- Windows or Linux server hosting the data folders for terminal server users files.

So I will need an accounting package(s) that accounts for users connecting to the system (FTP, HTTP, Terminal Server(including file transfers from mapped drives(port 3389 default))) and getting emails sent to internal users mailbox.  Also accounting for users connected to the terminal server sending data to and from a external source such as another FTP server or just browsing the web and sending email out.

Bandwidth accounting based on the following.

1. I want to track how much data is being used for a logged in user which will be an Active Directory account and or IP(possible VPN connected client) and or domain incoming and outgoing over FTP, HTTP, Email, RDP, so based on domainname might be best in many cases.  So the end result is how much bandwidth is being used for sending and receiving based on selected ports/services combined with a who did it(username), what was the ip address the client ip address(possible vpn) as this network could be hosting many domains and many email users and terminal server users from different companies.

I know this is confusing or how I am explaining myself, but I will be hosting many services and I need to account for data used based on who is using it.  So if a user logs in to the terminal server and downloads some files from a website then emails those files to someone else I need to know how much data that person has used.  

2. Web traffic based on domainname.com

3. FTP traffic, sending and receiving data to a domainname.com for example.
If a user connects to their ftp server from home [ftp://ftp.domainname.com](ftp://ftp.domainname.com) data will be accounted by domainname.com or logged in user.  I also want to account for traffic if that same user connects to an external ftp server from the terminal server.

I need to get accounting details up to the minute(on demand), day, week, month etc.  Possible scripting and emailing of reports.  Batch mode so reports can be automatically created and sorted based on users/domains and time ranges.

I know that not one package can do all of this but I am looking for direction and systems that may need to be setup to do all of this.

Example.
1. Firewall will perform basic accounting based on domains so a random person connecting to the email server sent a 5meg email to a user.  The firewall will account for that 5megs against that domainname.com.

A user connects to the terminal server using there own login account.  They transfer some files from his local mapped computer drives 10megs worth of files to the terminal server.  Then this user emails those files to a client.  I need to be able to see that this user has just sent 10megs for file transfer(rdp) and 10megs for email sent.  Also this domainname.com would have a total of 25megs tide to that account due to someone sending an email to this user, this example doesnt include the normal RDP usage just for being connection which will be small anyway.

I think that example shows what I want.

Please help me, I dont need to know exactly how to setup such a system but just direction.

As in...

This program will do this for you.
You will also need this program to do this.
You can use IP_Tables to do this and this.

Then I can do research on those programs, and I would like if possible all programs to be free, and is possible generate reports for easy viewing and possible sending to the client for disputed claims.

Thanks a bunch.

---

