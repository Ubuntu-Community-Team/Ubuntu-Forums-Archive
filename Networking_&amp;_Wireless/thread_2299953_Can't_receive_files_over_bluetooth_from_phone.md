---
title: "Can't receive files over bluetooth from phone"
date: 2015-10-22
forum: Networking &amp; Wireless
---

### Post by Starbeamrainbowlab on 2015-10-22
Hello,

I've been trying for the last half hour to send a file or two from my phone (Samsung Galaxy Young 2, running Android 4.4.4) to my laptop (Dell Inspiron N5110, running Ubuntu 15.10), but it won't work. It connects, according to the icon in the top left and Blueman Bluetooth manager, but it then disconnects and fails to send the file.

I've tried this: [http://askubuntu.com/q/131570/139735](http://askubuntu.com/q/131570/139735)

And here are a few extracts from my log files:

[FONT=courier new]/var/log/syslog[/FONT]:

[INDENT][/INDENT]
[INDENT=2][FONT=courier new][/FONT][FONT=courier new]Oct 22 19:55:52 Snowflake obexd[2671]: CONNECT(0x0), (null)(0xffffffff)[/FONT]
[FONT=courier new]Oct 22 19:55:52 Snowflake obexd[2671]: CONNECT(0x0), (null)(0x0)[/FONT]
[FONT=courier new]Oct 22 19:55:52 Snowflake obexd[2671]: PUT(0x2), (null)(0xffffffff)[/FONT]
[FONT=courier new]Oct 22 19:55:52 Snowflake obexd[2671]: Agent replied with an error: org.bluez.obex.Error.Rejected, Not Authorized[/FONT]
[FONT=courier new]Oct 22 19:55:52 Snowflake obexd[2671]: PUT(0x2), FORBIDDEN(0x43)[/FONT]
[FONT=courier new]Oct 22 19:55:53 Snowflake obexd[2671]: DISCONNECT(0x1), (null)(0xffffffff)[/FONT]
[FONT=courier new]Oct 22 19:55:53 Snowflake obexd[2671]: DISCONNECT(0x1), SUCCESS(0x20)[/FONT]
[/INDENT]
[FONT=lucida console][/FONT]
[FONT=courier new]systemctl status bluetooth[/FONT]:
[INDENT]
[FONT=courier new]Oct 22 19:40:51 Snowflake bluetoothd[809]: Unable to get io data for Object Push: getpeername: Transport endpoint is not connected (107)[/FONT]
[FONT=courier new]Oct 22 19:42:48 Snowflake bluetoothd[809]: Unable to get io data for Object Push: getpeername: Transport endpoint is not connected (107)[/FONT]
[FONT=courier new]Oct 22 19:44:45 Snowflake bluetoothd[809]: Unable to get io data for Object Push: getpeername: Transport endpoint is not connected (107)[/FONT]
[FONT=courier new]Oct 22 19:50:17 Snowflake bluetoothd[809]: Unable to get io data for Object Push: getpeername: Transport endpoint is not connected (107)[/FONT]
[FONT=courier new]Oct 22 19:50:39 Snowflake bluetoothd[809]:  connected[/FONT]
[FONT=courier new]Oct 22 19:50:39 Snowflake bluetoothd[809]: bnep0 disconnected[/FONT]
[FONT=courier new]Oct 22 19:53:56 Snowflake bluetoothd[809]: Unable to get io data for Object Push: getpeername: Transport endpoint is not connected (107)[/FONT]
[FONT=courier new]Oct 22 19:55:53 Snowflake bluetoothd[809]: Unable to get io data for Object Push: getpeername: Transport endpoint is not connected (107)[/FONT]
[/INDENT]

Does anyone know what I can do to fix this?

uname -a: Linux Snowflake 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 15:35:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by jeremy31 on 2015-10-22
Search Dash for "personal file sharing" and enable "receive files over bluetooth" usually works but the one error makes it look like the pairing was lost

---

### Post by prahladyeri on 2015-10-28
I am facing this exact same issue with 15.10 (Wily Werewolf)! Have you found any resolution yet?

---

### Post by SeijiSensei on 2015-10-28
I find a USB cable is more reliable and less hassle than Bluetooth or wifi for file transfers.

---

### Post by AzurianArcher on 2015-11-03
Also having this exact issue, I'm surprised there is so little information on it, do few people use bluetooth for file transfers? 

All the information I can find is from 2013 or earlier, so far nothing has panned out into a solution

I have to believe this was tested before the switch to bluez 5...

---

### Post by nknwn on 2015-11-04
In Dash, search for 'Personal file sharing'
You can see in the image below that an extra package was required for my system. However when I checked Ubuntu Software Centre and downloaded it - I forget what it was called - Bluetooth worked from my Windows phone - I sent a file from it
[ATTACH=CONFIG]265364[/ATTACH]

I am unable to send files to Windows 8 however on this computer - puzzling

oops, I missed Jeremy's post above, sorry Jeremy.
Ditto for [**[COLOR=#000000]Starbeamrainbowlab[/COLOR]**]("http://ubuntuforums.org/member.php?u=1951206")'s link :) < I couldn't find the blush emoticon

---

### Post by jeremy31 on 2015-11-04
nknwn

I am thinking the package was obex-ftp or something similar

---

### Post by AzurianArcher on 2015-11-08
You guys are right, installing the package obexftp seems to have fixed it

---

