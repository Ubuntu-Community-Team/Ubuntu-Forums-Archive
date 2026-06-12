---
title: "Dell V305 Printer"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-06-17
Hi

I just purchased a Dell V305 Printer when I put the CD in that came with it and click on setup.exe I get this message

> [/media/cdrom0/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/Setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/Setup.exe or
          /media/cdrom0/Setup.exe.zip, and cannot find /media/cdrom0/Setup.exe.ZIP, period.

How do I get the CD to run so that all the feature will be installed?

Thanks

---

### Post by Bölvaður on 2009-06-17
I am not really sure if that will work, nor am I sure the things you will end up getting are actual usable features.

This will probably not work (in the same way you'd expect [which means it doesnt work]) but click this link
[URL="apt:wine"]
sudo apt-get install wine[/URL]

and then try to install this thing again.

I would have thought you'd just plug the printer to the computer and it works as I thought Dell had good compatibility with linux. *oops* I guess I was wrong [http://en.community.dell.com/forums/t/19267417.aspx](http://en.community.dell.com/forums/t/19267417.aspx) perhaps this printer will not work at all unless if Dell will help out ([link to comments on the current nonworking driver]("http://www.openprinting.org/show_printer.cgi?recnum=Dell-V305")) or make the driver. As some people said on this forum (few people here got this printer) that it is strange that Dell doesnt make a linux driver for it when they ship Ubuntu computers and laptops.


sorry :( but try to remember these names [HP]("http://hplipopensource.com/hplip-web/index.html"), [Brother]("http://solutions.brother.com/linux/en_us/") and [Epson ]("http://avasys.jp/hp/menu000000500/hpg000000442.htm")(to a lesser extend than HP and Brother). (stay away from canon, I have had one working but not all printers work)

---

### Post by halitech on 2009-06-17
the cd you have is for windows so it won't run and even if you get it to run in WINE, it won't talk to the printer so its useless to install the software.

[http://openprinting.org/show_printer.cgi?recnum=Dell-V305](http://openprinting.org/show_printer.cgi?recnum=Dell-V305)

Dell V305
Color inkjet printer, this is a Paperweight

Dell doesn't actually make any printers, they buy them from other makers (mainly Lexmark) that have shaky linux support.

I have an Epson Stylus C60 (inkjet) and a Samsung ML2510 (laser) that both work great. HP is generally the best bet but check openprinting.org before you buy.

---

### Post by Anybloodyid on 2009-06-17
Thanks to all.
Will take it back and buy one that does work

---

