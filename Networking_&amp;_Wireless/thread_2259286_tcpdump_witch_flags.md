---
title: "tcpdump witch flags?"
date: 2015-01-03
forum: Networking &amp; Wireless
---

### Post by guldberg72 on 2015-01-03
i have a ubuntu server there is connected to my Raspberry pi there is in brudge mode so it is router <--> RPI <--> Ubuntu 14.04 server

[TABLE]
[TR]
[TD]                                                        [ ]("https://ask.wireshark.org/vote/38857/up/")      0 
 [ ]("https://ask.wireshark.org/vote/38857/down/")                               [ ]("https://ask.wireshark.org/mark_favorite/38857/")      
                                                      
                     [/TD]
                     [TD]                                                                                       I have installed Tcpdump on my RPI  and placed the RPI between my router and server, i want to capture ip  add. there is connecting and what files they are getting access to and  ofc with a timestamp-
 But i can figure out which flags i have to use ? right know i am running

 tcpdump -I br0 

 and i really need it to be readable by human eyes :D

                             

[/TD]
[/TR]
[/TABLE]

---

### Post by Doug S on 2015-01-03
to timestamp tcpdump output the suggestion is to use -tttt.

tcpdump is not the tool to use to show file names being accessed and such in a pretty and brief format, as it operates at the most primitive packet level. Yes, file names and such are embedded in the stream, if the connection is not encrypted (i.e. http port 80). You could try -A to get the stuff in ascii. I think you will need to experiment to try to get what you want.

On my system I use tcpdump to log all external and most internal traffic on my network, but I save it to files. I use my server logs to look for odd things that I might want to investigate further at the packet level, and then I go back and use wireshark to open the appropriate file and look at the detail. I do not see the advantage of putting another computer in the middle verses doing it on the server itself.

---

### Post by Lars Noodén on 2015-01-03
> **guldberg72 said:**
> i i want to capture ip  add. there is connecting and what files they are getting access to and  ofc with a timestamp-


Which method (SFTP, WebDAV, SMB, etc) are you using to transfer the files?  As Doug S mentions, tcpdump will only show you the unencrypted data.  For anything else, you'll need to look to the daemon's logs to show access to files.  It is even possible that you might have to adjust the configuration for the daemon.

---

### Post by guldberg72 on 2015-01-03
Owncloud is using webdav and i have a https:// connection to that section. ortherwise is it not encrypted.

but can you tell me what i should use instead ?

---

### Post by guldberg72 on 2015-01-03
mabey somthing like ntop but only logs the data between my server and outside world ? and not all local data

---

### Post by Lars Noodén on 2015-01-03
> **guldberg72 said:**
> Owncloud is using webdav and i have a https:// connection to that section. ortherwise is it not encrypted.

but can you tell me what i should use instead ?

All WebDAV activity would be going through the web server.  If you are using Apache2 for WebDAV, then you can look in the Apache2 log files.

---

