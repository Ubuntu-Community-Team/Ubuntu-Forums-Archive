---
title: "Samba slow from Mac OSX to Ubuntu server"
date: 2014-04-25
forum: Networking &amp; Wireless
---

### Post by Greensjp on 2014-04-25
Hi All,

I am having trouble with speed of access between iMacs running Mavericks and an Ubuntu Server using Samba.

The server (12.04) is running on a former Dell PC with 3Gb RAM and a 2.8Ghz Pentium server.

I'm running Samba, and a php / mysql database across a gigabit LAN. The PHP database works fine with no visible lag, although it's only updating the odd line of text so nothing too strenuous.

The problem really manifests itself when using Spotlight on the Mac to locate a certain file. If I select the directory in Finder everything shows up fairly quickly, however if I search for a particular file name or partial name, the results often take minutes to be returned. I have about 500Gb of data across 36624 files stored on the server. I have set up groups / users to match across the iMacs and the server, and set the ownership of the shared folders.

I've read that there are some peculiarities with Mavericks and Samba (according to this - [http://www.tuaw.com/2013/10/27/did-mavericks-kill-your-network-drive-access-heres-a-fix/](http://www.tuaw.com/2013/10/27/did-mavericks-kill-your-network-drive-access-heres-a-fix/)) however I thought I'd look for a second opinion. 

Is this some sort of indexing problem, or is my hardware not up to the task? If the latter, is it processor related, RAM related, or shouldn't I be using an old PC for this task?

I'm relatively new to Ubuntu Server, and it's grating that I am having this problem. 

Many thanks,
Jason

[COLOR=#333333][FONT=UbuntuRegular]Update 15/5/2014[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I've found the answer to this now. It appears that I can install AFP (netatalk) on the Ubuntu Server.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I followed this guide:- [http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/](http://missingreadme.wordpress.com/2010/05/08/how-to-set-up-afp-filesharing-on-ubuntu/)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Everything works fine now :)[/FONT][/COLOR]

---

