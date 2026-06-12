---
title: "connect an IDE to a ftp server with Transfer mode: active"
date: 2008-10-11
forum: Networking &amp; Wireless
---

### Post by ^andrea^ on 2008-10-11
Hello everyone,

I'm a web developer and I'm very desperate!!!

I need to connect one IDE (Quanta [seems to be my favourite] or Eclipse or whatever...) to an ftp server.

It shouldn't be hard, I know... but in fact it is.

I can connect my IDEs to some servers and not to some others...

The unique difference between these two category of servers is the trasfer mode.

I can connect to all of these servers within Filezilla, and it's from there that I see the difference...

If, the trasfer mode, is set to "active" I'm not able to connect within any IDEs...

WHY???

Is there a particolar setting to change?
Within the IDEs there isn't the possibility to choose the trasfer mode...

HELP please... every time I work I use Filezilla to upload files on the server... it's very annoying!!!

Thanks in advance to anyone, even just for a clue... :confused:

PS: I tried also with CURLFTPFS but no luck again with those servers... and anyway, seemed to be too slow for lots of files...

---

### Post by ^andrea^ on 2008-10-24
Now Quanta works but it's terribly slow...

Like 10/15 seconds to upload a 1kb file... :-|

But the size is not that important for the speed, it just stucks.

So, for example, uploading three files (about 5kb each one) takes me something like 40/50 seconds... unbelievable!!!

This depends, as I said before, from the trasfer mode of the server (when it has to be "active" for Filezilla (my ftp client) it works like that.)

For all the other server it works like a charm...

anyone has the same problem?

anyone knows how to solve it?
pleazzz...

bye,
A desperate one... ;-)

---

### Post by ^andrea^ on 2008-10-24
OK, I'm talking to myself... ;-)

Anyway, I solved the problem with Quanta+. Finally!

The active/passive setting is not present into Quanta+ but it's present in the "KDE control Center".

So if you are not in Kubuntu you have to install "kcontrol" and call it from the terminal.

Once it's open: ---> Internet & Network ---> Connection Preferences ---> FTP Options: uncheck "Enable passive mode (PASV)", and it works fantastically!!!

byeee

---

