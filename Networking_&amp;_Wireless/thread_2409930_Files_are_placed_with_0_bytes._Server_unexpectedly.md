---
title: "Files are placed with 0 bytes. Server unexpectedly closes SFTP network connection."
date: 2019-01-08
forum: Networking &amp; Wireless
---

### Post by intrados on 2019-01-08
I have a mystery I'm hoping that someone on this forum can help me solve. 

I just purchased a new computer and it's great. The only problem is that I can't get FTP to my remote Ubuntu server working correctly with any program (WinSCP, FileZilla, etc.). 
[LEFT][COLOR=#222222][FONT=Verdana]On my older computer using the exact same login information it works fine.[/FONT][/COLOR][/LEFT]

On the new machine: SFTP to remote server works both with password and RSA key and passphrase. PuTTY works to provide shell access with no problem.
I'm able to navigate through folders in the WinSCP commander view, delete files, and make modifications to file properties. 

The **problem** is that I can't place local files onto the server with drag and drop or by any other means. 

Specific errors during upload attempt:
1. Server unexpectedly closed network connection.
2. Copying files to remote side failed.

I can try to reconnect, but it just loops continuously. It places a file with the same name and extension on the server but with 0 bytes (that I then have to log in to delete).

At first I thought it was my Windows 10 stopping the connection. I've tried to allow through firewall with dedicated rules. Even turned firewall off entirely. No luck.

[LEFT][COLOR=#222222][FONT=Verdana]the user logging in through WinSCP is the owner of all folders and files on the server. I've also tried logging in as root with same result. [/FONT][/COLOR][/LEFT]

I've run out things to try and am looking for help. 

Posting here because now I'm wondering if the problem is actually with my Ubuntu 16.04 server etc/hosts or something else. Perhaps the log file from WinSCP below provides a clue?
I set up the server a long time ago and perhaps there is something in the original settings that doesn't agree with my new machine.

Thanks!                

WinSCP l[LEFT][COLOR=#222222][FONT=Verdana]og file shows:
[/FONT][/COLOR][/LEFT]
. 2019-01-07 21:06:59.155 Copying "C:\[…]\file" to remote directory started.
. 2019-01-07 21:06:59.157 Binary transfer mode selected.
. 2019-01-07 21:06:59.157 Opening remote file.
> 2019-01-07 21:06:59.157 Type: SSH_FXP_OPEN, Size: 96, Number: 33539
< 2019-01-07 21:06:59.190 Type: SSH_FXP_HANDLE, Size: 13, Number: 33539
> 2019-01-07 21:06:59.190 Type: SSH_FXP_WRITE, Size: 1607, Number: 34054
> 2019-01-07 21:06:59.191 Type: SSH_FXP_CLOSE, Size: 13, Number: 34308
> 2019-01-07 21:06:59.191 Type: SSH_FXP_SETSTAT, Size: 92, Number: 33801
. 2019-01-07 21:06:59.234 Server unexpectedly closed network connection
. 2019-01-07 21:06:59.234 Connection was lost, asking what to do.
. 2019-01-07 21:06:59.234 Asking user:
. 2019-01-07 21:06:59.234 Server unexpectedly closed network connection. ()
* 2019-01-07 21:07:01.220 (ESshFatal) Server unexpectedly closed network connection.
* 2019-01-07 21:07:01.220 Copying files to remote side failed.

---

### Post by intrados on 2019-01-08
When I originally set up LAMP and SSH in Ubuntu the etc/hosts file gained two new lines. See below. I'm wondering if this could be the issue. 
I've redacted some information in case it's a risk to place the unedited version here. [LEFT][COLOR=#222222][FONT=Verdana]I wonder if I should delete l[/FONT][/COLOR][/LEFT]ines 3 and 4. Since I set the server up and established this hosts file, the IP address DNS has changed (swapped servers). In fact name.website.org does not work as FTP hostname, only website.org or the new IP work. [LEFT][COLOR=#222222][FONT=Verdana]I'm afraid to modify etc/hosts though because I'm a novice and I don't want to break everything. The etc/deny and allow files are completely hashed out so they are not to blame. And the problem must be more subtle since I can log in and navigate folders without a problem. What other server system files might be suspect?[/FONT][/COLOR][/LEFT]

127.0.0.1 localhost
127.0.0.1 ubuntu
XXX.255.XXX.102 name.website.org name
2500:4d02::XXXX:91ff:XXXX:450a [LEFT][COLOR=#222222][FONT=Verdana]name.website.org name[/FONT][/COLOR][/LEFT]


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

---

