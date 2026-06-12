---
title: "Printer stopped working after Intrepid Updates. Help Please!"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by crjackson on 2008-12-18
Tody I needed to print a map from google maps and ran into a problem.

The map printed fine, then when I needed to print a reverse map nothing happened.  The Dell 5100cn printer (connected by USB) LCD panel would light, the print drum will warm, then it just stops and returns to ready condition.

I tried printing with OOo writer and that didn't work either. I tried printing a test page from the printer-config interface and it works perfectly.

Then I printed from my laptop and noticed the applet appear in the notification area and it worked as normal.

I re-installed the print driver (deb package)no good.  

I'm not sure if some proposed updates broke it, or if I broke in during a recent struggle with OOo (I had to remove it completly and re-install).

Any Suggestions before I'm forced to a clean install?

---

### Post by oldsoundguy on 2008-12-18
first, most will need the make and model of the printer .. but you could try the Windows trick .. re-boot.

---

### Post by ercferret18 on 2008-12-18
did you try restarting it?

---

### Post by crjackson on 2008-12-18
> **oldsoundguy said:**
> first, most will need the make and model of the printer .. but you could try the Windows trick .. re-boot.

It's a Dell 5100cn - The printer isn't the problem though. It will print a test page fine. The problem is that the applications send the data to the printer applet and it's not there to queue up the print.

Yes, it's been rebooted many times.

---

### Post by crjackson on 2008-12-18
> **ercferret18 said:**
> did you try restarting it?

Several times.

---

### Post by plucky on 2008-12-19
Open Firefox or your browser and input into address bar ```
http://localhost:631/admin/
``` and check the log file for errors.Also check the printer job queues on the "jobs" tag to make sure all jobs have completed.


Good Luck

---

### Post by crjackson on 2008-12-19
> **plucky said:**
> Open Firefox or your browser and input into address bar ```
http://localhost:631/admin/
``` and check the log file for errors.Also check the printer job queues on the "jobs" tag to make sure all jobs have completed.


Good Luck

Error log empty, and no imcomplete jobs showing

It's something about the updates that did this. I restored a working backup and after grabbing updates from Ubuntu repos. It broke again...

---

### Post by plucky on 2008-12-19
> **crjackson said:**
> Error log empty, and no imcomplete jobs showing

It's something about the updates that did this. I restored a working backup and after grabbing updates from Ubuntu repos. It broke again...

Bug report time!!!

---

### Post by crjackson on 2008-12-19
> **plucky said:**
> Bug report time!!!

yeah, what package do you think it should be filed against? CUPS?

---

### Post by plucky on 2008-12-19
If you open synaptic package manager and look at the history,there were a number of cups related packages installed on the 17th of December.Could be any one of them,so I am not sure what it could be.

If you have the time,maybe you could try installing the updates one at a time and see which one breaks your printer.

Or just log the bug report and see if they can reproduce the problem upstream.

Good Luck

---

### Post by crjackson on 2008-12-19
Guess it will have to wait a week or so. I'm surprised no one else has run accross the problem.

---

### Post by crjackson on 2008-12-19
Well, I filed a bug report against CUPS.

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/309828](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/309828)

---

### Post by crjackson on 2008-12-19
It would seem I'm the only one in the Ubunverse ;) with this issue. I think I'll do a CLEAN install --> TEST --> Security Updates --> TEST --> Backport Updates --> TEST --> Proposed Updates --> TEST

Perhaps I can narrow it down that way. I just wish someone else could confirm it's not just my machine.

All my other machines are working fine (but haven't been updated in a week). Now I'm concerned that I can't do security updates without breaking more machines.

Feel free to jump in any time and offer any workarounds you may have, or just confirm that it's a bug.

---

### Post by plucky on 2008-12-20
This [thread](http://ubuntuforums.org/showthread.php?t=1016357) seems to have the same problem.He fixed it by downgrading the package.

---

### Post by crjackson on 2008-12-22
I fixed it by doing a clean install and grabing all updates except the proposed. I think it was proposed updates that caused the problem. They are turned off forever...

---

### Post by crjackson on 2009-01-13
Sheesh!!! Here we go again. Todays regular updates (with CUPS) broke my printer again.

I'm starting to think it's best to NEVER get any Ubuntu update and security be damned!:mad:

---

### Post by paulphillips on 2009-01-17
Hi there!  I'm not sure if this is the same error that you've experienced, but certainly seems to be on the surface.

I can't print either after an intrepid-proposed update!  I have a Samsung CLP-300.  I have established that it's not the printer itself.  I can boot up into an old 8.04 install and the print works fine.  And under 8.10, I can grab a testpage.ps file from /usr/share/doc/pnm2ppa/examples/testpage.ps.gz, unzip it, then run the following:

```
$ foo2qpdl-wrapper testpage.ps > xxx.prn
$ lpr xxx.prn
```

And it works fine!

But if I print from any other application, the print icon appears briefly, dissappears as if its all good, but nothing ever happens.

Other forums suggested that I turn debugging on in CUPS, so I did, and the logs say that ghostscript is exiting with an error:

```
Error: /ioerror in --run--
D [17/Jan/2009:21:06:12 +1030] [Job 87] Operand stack:
D [17/Jan/2009:21:06:12 +1030] [Job 87] (/var/spool/cups/tmp/gs_xUQwuW)   --nostringval--   --nostringval--   (%PDF-1.3\n%\0201\0202\0203\0204\n% This file was generated by pdftopdf\n%%PDFTOPDFNumCopies : 1\n%%PDFTOPDFCollate : false\n1 0 obj\n<< /Type /Catalog /Pages 2 0 R >>\nendobj\n2 0 obj\n<< /Type /Pages /Kids [ 3 0 R\n ] /Co...)   false   --nostringval--   (%PDF-1.3\n%\0201\0202\0203\0204\n% This file was generated by pdftopdf\n%%PDFTOPDFNumCopies : 1\n%%PDFTOPDFCollate : false\n1 0 obj\n<< /Type /Catalog /Pages 2 0 R >>\nendobj\n2 0 obj\n<< /Type /Pages /Kids [ 3 0 R\n ] /Co...)
D [17/Jan/2009:21:06:12 +1030] [Job 87] Execution stack:
D [17/Jan/2009:21:06:12 +1030] [Job 87] %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1905   1   3   %oparray_pop   1904   1   3   %oparray_pop   1888   1   3   %oparray_pop   --nostringval--   --nostringval--   %loop_continue   --nostringval--
D [17/Jan/2009:21:06:12 +1030] [Job 87] Dictionary stack:
D [17/Jan/2009:21:06:12 +1030] [Job 87] --dict:1152/1684(ro)(G)--   --dict:0/20(G)--   --dict:70/200(L)--
D [17/Jan/2009:21:06:12 +1030] [Job 87] Current allocation mode is local
D [17/Jan/2009:21:06:12 +1030] [Job 87] Last OS error: 28
D [17/Jan/2009:21:06:12 +1030] [Job 87] GPL Ghostscript 8.63: Unrecoverable error, exit code 1
```

I've attached the log for more info.

The ghostscript package I've installed has the following version:
8.63.dfsg.1-0ubuntu6.1

What's puzzling, is that there was a bug raised on this here:
[https://bugs.launchpad.net/ubuntu/intrepid/+source/ghostscript/+bug/306125]("https://bugs.launchpad.net/ubuntu/intrepid/+source/ghostscript/+bug/306125")
Which resulted in the above package being produced and released in intrepid-proposed.

There's also this bug:
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/309828]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/309828")
...but I don't know yet whether its the same issue.

Anyone had any success with this?

Thanks,
Paul.


**** STOP PRESS ****

I found the source of all my problems - the /var partition was full!!  CUPS uses the /var partition during its generation of the files to print.  When I cleaned up the partition, printing now works fine!!!

---

### Post by crjackson on 2009-03-10
Sorry for not getting back sooner. This issue is still on-going with no improvement. Hopefully the the Juanty release will cure the problem.

---

### Post by ozPATT on 2009-03-10
i think i might also have this problem, it happened a while ago, where I couldn't print anything, even a test page, from ubuntu. then as if by magic, one day it was working again. now however, i can't print anything, and each job says it is completed. is that the same issue? if not, i will start a new thread.. :)

---

### Post by crjackson on 2009-03-10
Possibly. For me it happens in Intrepid Ibex after updates have been installed. Hardy doesn't seem to be having issues. What version of ubuntu are you using?

---

