---
title: "&quot;attachment.dat&quot;: how do I open these files?"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by louis.pasteur on 2011-09-01
Hi all,

  I recently received attachments (Evolution) named "attachment.dat" sent from MS-Outlook and cannot open them. I tried tnef but got this message:

$ file attachment.dat 
attachment.dat: RFC 822 mail text
$ tnef attachment.dat 
Seems not to be a TNEF file

Any idea how I can open this file in a human readable way? These files are saved emails, I think.

---

### Post by snip3r8 on 2011-09-01
Do you know the person who sent you this email?
why are they sending you .dat files?

oh and ...

> Best regards,
Anonymous

Are you Anonymous?,are you legion?,Do you forgive?Do you forget?Should I expect you?(not sure exactly what to expect.)

---

### Post by louis.pasteur on 2011-09-02
Sorry about the "anonymous" (forgive my poor English), and about who send me the mail: I think they exported a mail in a MS format but I just cannot open it on Ubuntu.

---

### Post by snip3r8 on 2011-09-02
> **louis.pasteur said:**
> Sorry about the "anonymous" (forgive my poor English), and about who send me the mail: I think they exported a mail in a MS format but I just cannot open it on Ubuntu.

You don't have to be sorry ,I was just making a light joke.
I found this which you might be interested in.

[http://pcsupport.about.com/od/fileextensions/f/dat-file.htm](http://pcsupport.about.com/od/fileextensions/f/dat-file.htm)

Also I have noticed you only have 2 beans,are you new to Linux or just the forums?

---

### Post by louis.pasteur on 2011-09-02
> **snip3r8 said:**
> 
[http://pcsupport.about.com/od/fileextensions/f/dat-file.htm](http://pcsupport.about.com/od/fileextensions/f/dat-file.htm)

Also I have noticed you only have 2 beans,are you new to Linux or just the forums?
  I have been using Ubuntu for about half a year, and this is my first post on the forums. I think I am quite new to Linux.

  Thanks about the link but I want a native Ubuntu way to open the file? I'm sure MS Outlook can open the file and also some other Window applications, but those *.dat s & *.msg s are so hard to open in Ubuntu? I can open some *.dat files after installing something (I forgot what it was after re-installing Ubuntu) but not all of them (some formats are different, probably from a different Outlook version?), and I never had a way to open a *.msg file sent to me from Outlook.

  I googled a bit and found a Perl script doing some file type conversions, but it's not working for me, any suggestions or links of howtos are welcomed. I will try using "wine" if I still can't find a native solution to this file opening problem.

---

### Post by snip3r8 on 2011-09-02
According to this 
[http://ubuntuforums.org/showthread.php?t=1438296](http://ubuntuforums.org/showthread.php?t=1438296)

"A .dat file can contain anything, you need to know what data format is in it."

so i guess you will need to ask the person who sent it to you what it is ,if its a document,movie etc.
Then you need to decide on the application to open it with ,if it is a document then maybe libre office will do ,maybe try making a copy and changing the copys extension to .doc

---

### Post by fooman on 2011-09-02
googling came up with this:

[http://www.faqforge.com/linux/how-to-open-winmail-dat-files-on-ubuntu-or-debian-linux/](http://www.faqforge.com/linux/how-to-open-winmail-dat-files-on-ubuntu-or-debian-linux/)

hope that helps.

---

### Post by stmiller on 2011-09-05
[http://www.winmaildat.com/](http://www.winmaildat.com/)

---

### Post by louis.pasteur on 2011-09-05
Thanks for all the help (I've tried all of them), temporarily using Outlook for opening these files, until I find a better solution.

---

