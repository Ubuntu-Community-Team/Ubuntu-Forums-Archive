---
title: "auto dectected network printer works but manual doesn't"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by jmclauren on 2007-01-19
I am trying to print from Ubuntu to a printer conntected to a Mac running OS X 10.4 and I'm having some strange problems.  I've added a network printer with the correct ipp path and driver.  When I print a test page, the status of the printer changes to "Printing" and the job appears in my local queue.  After a while the job dissapears and the status changes back to "Ready", but no job ever appears in the queue on the Mac.  When I check the cups log on the Mac I see that the job has made it that far.  Here is the exerpt from the log.

```
I [19/Jan/2007:03:58:58 -0600] Adding start banner page "none" to job 353.
I [19/Jan/2007:03:58:58 -0600] Adding end banner page "none" to job 353.
I [19/Jan/2007:03:58:58 -0600] Job 353 queued on 'Stylus_CX7800' by 'jeremiah'.
```

But that's as far as it gets.  Printing from other Macs and Linux boxes on the network works fine.  Here's what a normal print job from any other machine looks like in the log.

```
I [19/Jan/2007:04:17:32 -0600] Adding end banner page "none" to job 355.
I [19/Jan/2007:04:17:32 -0600] Job 355 queued on 'Stylus_CX7800' by 'jeremiah'.
I [19/Jan/2007:04:17:32 -0600] Started filter /usr/libexec/cups/filter/pstopdffilter (PID 11408) for job 355.
I [19/Jan/2007:04:17:32 -0600] Started filter /System/Library/Printers/Libraries/PrintJobMgr/Contents/MacOS/PrintJobMgr (PID 11409) for job 355.

```

Now here's where it gets interesting.  When I enable browsing on the Ubuntu machine, a new printer shows up in the list.  And, when I print using this auto dectected version, the entire process above completes and someting actually comes out of the printer!  But, the colors are wrong.  So, I need to be able to specify a driver, which means that I need the printer that I added manually to work.  I don't know what the difference is between the two.  The ipp path is exactly the same, but one works and the other doesn't.  Any ideas?  I know my printer is supported by Ubuntu because I found it in the list of printers when I added the first one manually.

There are some other weird things going on that may be clues.  I can't delete an auto detected printer.  I disabled browsing right-clicked on the printer and hit delete, but the printer remained even after a reboot.  When I first saw the auto dected printer, I checked it's properties and it had an option to select a driver.  An Epson CL something was selected.  Mine is an Epson Stylus CX7800 so I selected that driver and closed the window.  The status of the printer changed to "Paused" and another auto detected printer appeared.  I hit resume and it changed back to "Ready", but it still wouldn't print.  When I checked the properties on it again, the path had changed to "/dev/null".  I tried the new printer that just came up and it had no option to select a driver.  Go figure.  I don't know what the heck is going on.  It's pretty weird.  I've had some experiance with cups setting up printers, and I've never seen anyting like this.  Does anyone know whats going on and why the auto dected version works, but the one I added manually doesn't?  Any help would be greatly appreciated.  Thanks.

---

### Post by jmclauren on 2007-01-19
Sorry, I should have set the log level to debug for those excerpts.  Here is the verbose log excerpt from an attempt using the printer I created manually.

```
D [19/Jan/2007:06:09:55 -0600] AcceptClient: 10 from 192.168.1.6:631.
D [19/Jan/2007:06:09:55 -0600] ReadClient: 10 POST /printers/Stylus_CX7800 HTTP/1.1
D [19/Jan/2007:06:09:55 -0600] ProcessIPPRequest: 10 status_code=1
D [19/Jan/2007:06:09:55 -0600] ReadClient: 10 POST /printers/Stylus_CX7800 HTTP/1.1
D [19/Jan/2007:06:09:56 -0600] print_job: request file type is application/vnd.cups-raw.
D [19/Jan/2007:06:09:56 -0600] check_quotas: requesting-user-name = 'jeremiah'
D [19/Jan/2007:06:09:56 -0600] print_job: requesting-user-name = 'jeremiah'
D [19/Jan/2007:06:09:56 -0600] Adding default job-sheets values "none,none"...
I [19/Jan/2007:06:09:56 -0600] Adding start banner page "none" to job 360.
I [19/Jan/2007:06:09:56 -0600] Adding end banner page "none" to job 360.
I [19/Jan/2007:06:09:56 -0600] Job 360 queued on 'Stylus_CX7800' by 'jeremiah'.
D [19/Jan/2007:06:09:56 -0600] Job 360 hold_until = 0
D [19/Jan/2007:06:09:56 -0600] StartJob(360, 0x1800a00)
D [19/Jan/2007:06:09:56 -0600] StartJob() id = 360, file = 0/1
D [19/Jan/2007:06:09:56 -0600] dnssdRegisterPrinter(Stylus_CX7800) update
D [19/Jan/2007:06:09:56 -0600] job-sheets=none,none
D [19/Jan/2007:06:09:56 -0600] banner_page = 0
D [19/Jan/2007:06:09:56 -0600] StartJob: argv = "Stylus_CX7800","360","jeremiah","Test Page","1","","/private/var/spool/cups/d00360-001"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[0]="PATH=/usr/libexec/cups/filter:/bin:/usr/bin"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[2]="USER=root"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[3]="CHARSET=utf-8"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[4]="LANG=en_US"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[5]="PPD=/private/etc/cups/ppd/Stylus_CX7800.ppd"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[6]="CUPS_SERVERROOT=/private/etc/cups"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[7]="RIP_MAX_CACHE=8m"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[8]="TMPDIR=/private/var/spool/cups/tmp"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[9]="CONTENT_TYPE=application/vnd.cups-raw"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[10]="DEVICE_URI=file:///dev/null"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[11]="PRINTER=Stylus_CX7800"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[12]="CUPS_DATADIR=/usr/share/cups"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[13]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[14]="CUPS_SERVER=localhost"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[15]="IPP_PORT=631"
D [19/Jan/2007:06:09:56 -0600] StartJob: envp[16]="<CFProcessPath>"
D [19/Jan/2007:06:09:56 -0600] StartJob: statusfds = [ 12 13 ]
D [19/Jan/2007:06:09:56 -0600] StartJob: filterfds[1] = [ 14 -1 ]
D [19/Jan/2007:06:09:56 -0600] ProcessIPPRequest: 10 status_code=0
D [19/Jan/2007:06:09:56 -0600] UpdateJob: job 360, file 0 is complete.
D [19/Jan/2007:06:09:56 -0600] CancelJob: id = 360
D [19/Jan/2007:06:09:56 -0600] StopJob: id = 360, force = 0
D [19/Jan/2007:06:09:56 -0600] dnssdRegisterPrinter(Stylus_CX7800) update
D [19/Jan/2007:06:09:56 -0600] StopJob: printer state is 3
D [19/Jan/2007:06:09:56 -0600] ReadClient: 10 POST /printers/Stylus_CX7800 HTTP/1.1
D [19/Jan/2007:06:09:56 -0600] ProcessIPPRequest: 10 status_code=1
D [19/Jan/2007:06:09:56 -0600] ReadClient: 10 POST /printers/Stylus_CX7800 HTTP/1.1
D [19/Jan/2007:06:09:56 -0600] ProcessIPPRequest: 10 status_code=1
D [19/Jan/2007:06:09:56 -0600] CloseClient: 10

```

And here is what happens when I print from the auto detected printer.

```
D [19/Jan/2007:17:34:18 -0600] AcceptClient: 10 from 192.168.1.6:631.
D [19/Jan/2007:17:34:18 -0600] ReadClient: 10 POST /printers/Stylus_CX7800 HTTP/1.1
D [19/Jan/2007:17:34:18 -0600] ProcessIPPRequest: 10 status_code=1
D [19/Jan/2007:17:34:18 -0600] ReadClient: 10 POST /printers/Stylus_CX7800 HTTP/1.1
D [19/Jan/2007:17:34:19 -0600] print_job: request file type is application/postscript.
D [19/Jan/2007:17:34:19 -0600] check_quotas: requesting-user-name = 'jeremiah'
D [19/Jan/2007:17:34:19 -0600] print_job: requesting-user-name = 'jeremiah'
D [19/Jan/2007:17:34:19 -0600] Adding default job-sheets values "none,none"...
I [19/Jan/2007:17:34:19 -0600] Adding start banner page "none" to job 361.
I [19/Jan/2007:17:34:19 -0600] Adding end banner page "none" to job 361.
I [19/Jan/2007:17:34:19 -0600] Job 361 queued on 'Stylus_CX7800' by 'jeremiah'.
D [19/Jan/2007:17:34:19 -0600] Job 361 hold_until = 0
D [19/Jan/2007:17:34:19 -0600] StartJob(361, 0x1800a00)
D [19/Jan/2007:17:34:19 -0600] StartJob() id = 361, file = 0/1
D [19/Jan/2007:17:34:19 -0600] dnssdRegisterPrinter(Stylus_CX7800) update
D [19/Jan/2007:17:34:19 -0600] job-sheets=none,none
D [19/Jan/2007:17:34:19 -0600] banner_page = 0
D [19/Jan/2007:17:34:19 -0600] StartJob: argv = "Stylus_CX7800","361","jeremiah","Test Page","1","","/private/var/spool/cups/d00361-001"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[0]="PATH=/usr/libexec/cups/filter:/bin:/usr/bin"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[1]="SOFTWARE=CUPS/1.1"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[2]="USER=root"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[3]="CHARSET=utf-8"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[4]="LANG=en_US"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[5]="PPD=/private/etc/cups/ppd/Stylus_CX7800.ppd"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[6]="CUPS_SERVERROOT=/private/etc/cups"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[7]="RIP_MAX_CACHE=8m"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[8]="TMPDIR=/private/var/spool/cups/tmp"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[9]="CONTENT_TYPE=application/postscript"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[10]="DEVICE_URI=file:///dev/null"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[11]="PRINTER=Stylus_CX7800"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[12]="CUPS_DATADIR=/usr/share/cups"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[13]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[14]="CUPS_SERVER=localhost"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[15]="IPP_PORT=631"
D [19/Jan/2007:17:34:19 -0600] StartJob: envp[16]="<CFProcessPath>"
D [19/Jan/2007:17:34:19 -0600] StartJob: statusfds = [ 12 13 ]
D [19/Jan/2007:17:34:19 -0600] StartJob: filterfds[1] = [ 14 -1 ]
D [19/Jan/2007:17:34:19 -0600] StartJob: CFProcessPath=/usr/libexec/cups/filter/pstopdffilter
D [19/Jan/2007:17:34:19 -0600] StartJob: filter = "/usr/libexec/cups/filter/pstopdffilter"
D [19/Jan/2007:17:34:19 -0600] StartJob: filterfds[0] = [ 15 16 ]
D [19/Jan/2007:17:34:19 -0600] start_process("/usr/libexec/cups/filter/pstopdffilter", 0xbffe9fc0, 0xbffeaae0, 14, 16, 13)
I [19/Jan/2007:17:34:19 -0600] Started filter /usr/libexec/cups/filter/pstopdffilter (PID 11961) for job 361.
D [19/Jan/2007:17:34:19 -0600] StartJob: CFProcessPath=/System/Library/Printers/Libraries/PrintJobMgr/Contents/MacOS/PrintJobMgr
D [19/Jan/2007:17:34:19 -0600] StartJob: filter = "/System/Library/Printers/Libraries/PrintJobMgr/Contents/MacOS/PrintJobMgr"
D [19/Jan/2007:17:34:19 -0600] StartJob: filterfds[1] = [ -1 14 ]
D [19/Jan/2007:17:34:19 -0600] start_process("/System/Library/Printers/Libraries/PrintJobMgr/Contents/MacOS/PrintJobMgr", 0xbffe9fc0, 0xbffeaae0, 15, 14, 13)
I [19/Jan/2007:17:34:19 -0600] Started filter /System/Library/Printers/Libraries/PrintJobMgr/Contents/MacOS/PrintJobMgr (PID 11962) for job 361.
D [19/Jan/2007:17:34:19 -0600] ProcessIPPRequest: 10 status_code=0
D [19/Jan/2007:17:34:19 -0600] ReadClient: 10 POST /printers/Stylus_CX7800 HTTP/1.1
D [19/Jan/2007:17:34:19 -0600] ProcessIPPRequest: 10 status_code=1
D [19/Jan/2007:17:34:19 -0600] ReadClient: 10 POST /printers/Stylus_CX7800 HTTP/1.1
D [19/Jan/2007:17:34:19 -0600] ProcessIPPRequest: 10 status_code=1
D [19/Jan/2007:17:34:19 -0600] [Job 361] PrintJobMgr - copying PDF to temp file "/private/var/spool/cups/tmp/45b1557ba9fa1"
D [19/Jan/2007:17:34:28 -0600] PID 11961 exited with no errors.
D [19/Jan/2007:17:34:28 -0600] [Job 361] JobManager converting file: /private/var/spool/cups/tmp/45b1557ba9fa1 (6 args)
D [19/Jan/2007:17:34:28 -0600] AcceptClient: 13 from localhost:0.
D [19/Jan/2007:17:34:28 -0600] ReadClient: 13 POST / HTTP/1.1
D [19/Jan/2007:17:34:28 -0600] ProcessIPPRequest: 13 status_code=1
D [19/Jan/2007:17:34:28 -0600] ReadClient: 13 POST / HTTP/1.1
D [19/Jan/2007:17:34:28 -0600] ProcessIPPRequest: 13 status_code=1
D [19/Jan/2007:17:34:28 -0600] CloseClient: 13
D [19/Jan/2007:17:34:28 -0600] AcceptClient: 13 from localhost:0.
D [19/Jan/2007:17:34:28 -0600] ReadClient: 13 POST / HTTP/1.1
D [19/Jan/2007:17:34:28 -0600] ProcessIPPRequest: 13 status_code=1
D [19/Jan/2007:17:34:29 -0600] ReadClient: 10 POST /printers/Stylus_CX7800 HTTP/1.1
D [19/Jan/2007:17:34:29 -0600] ProcessIPPRequest: 10 status_code=1
D [19/Jan/2007:17:34:29 -0600] ReadClient: 10 POST /printers/Stylus_CX7800 HTTP/1.1
D [19/Jan/2007:17:34:29 -0600] ProcessIPPRequest: 10 status_code=1
D [19/Jan/2007:17:34:29 -0600] ReadClient: 13 POST / HTTP/1.1
D [19/Jan/2007:17:34:29 -0600] ProcessIPPRequest: 13 status_code=1
D [19/Jan/2007:17:34:29 -0600] ReadClient: 13 POST / HTTP/1.1
D [19/Jan/2007:17:34:29 -0600] ProcessIPPRequest: 13 status_code=1
D [19/Jan/2007:17:34:30 -0600] [Job 361] `/private/var/spool/cups/tmp/45b1557ba9fa1' has 1 pages.
D [19/Jan/2007:17:34:30 -0600] [Job 361] PDFtoTiogaRaster: xResolution = 738, yResolution = 738
D [19/Jan/2007:17:34:30 -0600] [Job 361] PDFtoTiogaRaster: SheetWidth = 612, SheetHeight = 792
D [19/Jan/2007:17:34:30 -0600] [Job 361] ImageableArea.origin.x = -0, ImageableArea.origin.y = 0, ImageableArea.width = 612, ImageableArea.height = 792
D [19/Jan/2007:17:34:30 -0600] [Job 361] frameWidth = 6273, frameHeight = 8118
D [19/Jan/2007:17:34:30 -0600] [Job 361] PDFtoTiogaRaster USING DISPLAY LIST IMPLEMENTATION
I [19/Jan/2007:17:34:30 -0600] [Job 361] kPMEventJobProgress:1 1 1 1 1 1 0
D [19/Jan/2007:17:34:30 -0600] [Job 361] sendJobProgressEvent: currentPage: 1 currentCopy: 1 currentSheet 1 percent: 0 isEndOfSheet:no
I [19/Jan/2007:17:34:30 -0600] [Job 361] kPMEventJobProgress:1 1 1 1 1 1 0
W [19/Jan/2007:17:34:31 -0600] [Job 361] recoverable: ink is out.

```

This would have completed had the ink not been out.  But, you can see the first one never got this far.  I'm not sure what all this means.  I've been trying to decipher it, but so far I haven't even been able to find out what the status codes mean.  Does anyone get any clues from this?

The log level in cupsd.conf was set to debug.  When I tried the debug2 level, there was so much output that the log file was truncated.  This log is from the server on the Mac, by the way.

---

### Post by jmclauren on 2007-01-25
Well, thanks for all the help so far.  :-k  Meanwhile I've figured out the diffrenece between the auto detected instance of the printer and the one I added manually.  Since the manually created instance is using a specific driver, it appears from the log I posted above that the request file type is "application/vnd.cups-raw".  On the other hand, the request file type for the auto detected instance is "application/postscript".  So I guess the problem is with the server and it's ability to handle the raw file type.  I checked /ect/cups/mime.convs and mime.types and it appears that everything needed to handle the "application/vnc.cups-raw" file type is in place and the appropriate lines are uncommented.  Is there anything else I need to do?  I realize that this probably doesn't have much to do specifically with Ubuntu anymore, but if there's any cups experts hanging out in these forums your help would be greatly appreciated.  Thanks.

---

### Post by jmclauren on 2007-01-26
I figured it out!  :D  What I needed to do was create a raw queqe on the server for Ubuntu to print to.  Yea, I know what you're thinking.  Dugh!  :roll:  But one would think that the regular queque should be able to handle raw data if it is specified as such.  Apparently not I guess.  Anyway, I just thought I'd post my solution in case anyone else stumbles upon this thread wondering how to print to a server using a client-side driver.  Cheers.

---

### Post by peter3 on 2007-02-25
Hi, JM
I'm having the same problem you are, I think.  I've already destroyed the OS X and
had to Archive/Reload it once.  A printer was wedged.  Wouldn't go in our out.  But
my wife's Mac is Panther, so it's harder to do anything with the web interface.  

Can you tell me how to create the "raw queue"?  I think that may allow me to print
from my Ubuntu/Debian side of the room over to her OS X side.  She can print just
fine from her side to my laser printers.

Thanks.
Peter

---

### Post by jmclauren on 2007-02-27
Peter,

Glad to help!  Here's how I created a raw queue on Tiger.  The process should be the same on Panther, I hope.

1. Open a web browser on the Mac and go to [http://localhost:631/](http://localhost:631/).  This should get you the cups web interface.
2. Click on the "Manage Printers" link.
3. Click the "Add Printer" button at the bottom of the page.
4. Enter the username and password for the OS X administrator account, not root.
5. Supply a name, location, and description.  It doesn't matter what you put in here.  Then click the "Continue" button.
6. From the device list, select the printer that you want to print to from your Linux computer.  It should be a specific printer, not one of the general protocols.  Then click "Continue".
7. Select the "Raw" option from the list of printer manufacturers.  It should be at the top.  Then click continue.
8. Select the raw queue option from the model list.  It should be the only one.  Then continue.
9. You should see a message saying that the printer was added.  Thats it!

The new printer should already be shared in the system preferences, but you might want to check and make sure.  Then all you have to do is add it on the Linux side and select the appropriate Linux driver for that printer.  I've found that this works better in Linux than just printing to the Mac's default queue becuase it gives you more control, assuming that Linux has a good driver for your printer.

Let me know if this works for you, or if you have any more questions.  Good luck!

[Jeremiah]

---

