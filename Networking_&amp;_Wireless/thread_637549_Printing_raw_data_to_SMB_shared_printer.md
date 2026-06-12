---
title: "Printing raw data to SMB shared printer"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by protonephridium on 2007-12-11
Hi there. I'm new to the forums and hope that someone might be able to help. I've been trying out Ubuntu for a while and begin to really like it.

My problem is I'm trying to send a file containing raw printer commands from an Ubuntu Gutsy machine to a printer shared by an XP box. The printer itself was found and drivers were installed without a problem when I added the printer. So I can send files (e.g. the test page) to the printer driver and it will print. What I need to do is send raw printer commands to the printer.

Is there a command line tool for this? (LP only prints the commands themselves). For reference, on windows the command would be [FONT="Courier New"]**print /d:\\winxp\zebra test.prn** (where "winxp" designates the name of the remote machine in the workgroup and "zebra" the share name of the printer, "test.prn" is the file)[/FONT]

My ultimate goal is to generate printer data from a PHP script (data is supplied by user input from a web frontend) and send that string directly to the printer shared on a machine running Windows XP. The printer in question is a barcode printer and the data written to it is in ZPL (Zebra Printing Language), which looks something like this: 

```
^XA^FDtest print^FS^XZ
```

So my plan is to write that string to a file and have a cron job check every second or so if a new file was written and if yes, to send it to the remote printer ([FONT="Courier New"]**smb://NET/WINXP/Zebra**[/FONT]).

Any help/pointers welcome ;)

---

### Post by protonephridium on 2007-12-11
-little bump-

---

### Post by protonephridium on 2007-12-13
anyone?

---

### Post by protonephridium on 2007-12-14
Argh, almost 50 views and noone with a little hint?

---

### Post by protonephridium on 2007-12-15
last bump..

---

