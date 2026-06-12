---
title: "How do you define a telnet terminal ID for use with WYSE 60 emulation?"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by quad-u on 2007-11-11
Allright, here goes.

I work in tech support for a retail company and I'm trying to make myself use linux (Gutsy) on a spare box we've got in our department because I've figured out how Windows works and I'm ready to move on.

On our Windows machines, we use ProComm Plus with WYSE 60 emulation to connect to our POS/Inventory system.  We do have to specify a terminal ID/callback in ProComm's address book in order to connect.

I've installed wy60 on our linux box and it appears to work, but when I type "wy60 -c telnet xxx.xxx.xxx.xxx" into the terminal, I get the following message:


[FONT="System"]

&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; Information &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474;    This Station (unknown) Has Not Been Defined In System Control   &#9474;
&#9474; &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472; &#9474;
&#9474;                             <OK>                              &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;


Station Startup ...
[/FONT]

I know for a fact that this would work if I could just specify a Station ID.

Thanks in advance.

---

### Post by quad-u on 2007-11-18
Well, I've figured out that telnet is useless on that front.

Putty seems to do a great job, and it allows you to define a terminal ID via "Terminal-type string", but I can't find a way to make it play nicely with wy60.

Any ideas out there?

---

### Post by Blutack on 2007-11-18
From
[http://ubuntuforums.org/archive/index.php/t-90810.html](http://ubuntuforums.org/archive/index.php/t-90810.html)

2. There is a FOSS solution that also works for the wyse 60 emulation.
$ sudo apt-get install ckermit
$ sudo apt-get install wy60
and then something like this:
$ wy60
$ kermit configFile

where configFile looks like this:
set modem type none
set line /dev/ttyS0
set speed 38400
set flow none
set carrier-watch off
connect
or you can do it all on one line ( this is also how you can set up a launcher with your company logo as an icon )
$ wy60 -c kermit configFile
Getting this working may depend on the font you use ( I use Andale Mono from the msttcorefonts package). Some mono fonts cause the lines around boxes and some text to get garbled when the screen repaints. This is also related to the wyse60 entry in your termcap file. I assume you are logging into a unix server.

Hope this helps

---

### Post by quad-u on 2007-11-18
> **Blutack said:**
> From
[http://ubuntuforums.org/archive/index.php/t-90810.html](http://ubuntuforums.org/archive/index.php/t-90810.html)

2. There is a FOSS solution that also works for the wyse 60 emulation.
$ sudo apt-get install ckermit
$ sudo apt-get install wy60
and then something like this:
$ wy60
$ kermit configFile

where configFile looks like this:
set modem type none
set line /dev/ttyS0
set speed 38400
set flow none
set carrier-watch off
connect
or you can do it all on one line ( this is also how you can set up a launcher with your company logo as an icon )
$ wy60 -c kermit configFile
Getting this working may depend on the font you use ( I use Andale Mono from the msttcorefonts package). Some mono fonts cause the lines around boxes and some text to get garbled when the screen repaints. This is also related to the wyse60 entry in your termcap file. I assume you are logging into a unix server.

Hope this helps

Yeah, thanks for the referral, but I've seen this post before and it pertains to a serial connection.   I'm actually connecting via our company's LAN to an HP UNIX server.  Telnet appears to be the only way in (as it's responding nicely to port 23), but my issue lies with telnet being incapable of defining a Terminal ID / Terminal-type string.

---

