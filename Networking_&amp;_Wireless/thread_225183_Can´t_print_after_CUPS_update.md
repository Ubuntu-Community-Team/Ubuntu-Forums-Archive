---
title: "Can´t print after CUPS update"
date: 2006-07-29
forum: Networking &amp; Wireless
---

### Post by arthur on 2006-07-29
As soon as I installed Dapper, everything was working with my office network HP LaserJet printer.

Until a CUPS update was applied through aptitude ... :confused: 
Since then, no more printing (nothing changed by me)

Am I overlooking the obvious, or is it a bug somewhere in the update??

---

### Post by veki on 2006-07-29
What is output of your /var/log/cups/error_log

regards,

veki

---

### Post by arthur on 2006-07-31
Sorry, busy on other things!
The file you mention is EMPTY!!

Make sense? #-o

---

### Post by funkydan2 on 2006-08-04
No it doesn't make sense... except **the same thing has happened to me**!

I have been searching and searching for an solution to the problem but there is nothing!

Basically to restate the problem, I have an ubuntu box which used to be able to print to my HP Laserjet printer which is connected to a Windows XP box.  I used to be able to print, but after a recent update - no more printing.  And what's more is that there is *nothing* in cups' error_log file.

I'm at my wits' end - has anyone got a solution to this problem?

---

### Post by arthur on 2006-08-04
That is odd
Very likely to be related to CUPS itself, unless you use a Pavilion ZT3000, that is :)

---

### Post by felippe miranda on 2006-08-04
Same happened with my canon bjc 4300 - no more printing in dapper after CUPS update ! Is it a bug ?

---

### Post by felippe miranda on 2006-08-04
Problem solved - Changed model to canon 4200 in printer setup (canon 4200 uses same bjc600 driver )

---

### Post by funkydan2 on 2006-08-06
Well it's a "bug", because things don't work as they should.

I've reported it as a bug on [launchpad](https://launchpad.net/distros/ubuntu/+bug/55243).  Please add more information there if you can.

---

### Post by arthur on 2006-08-06
Cheers, Funky
Let's see if this is spotted ;)


BTW, I had a look [here](http://www.ubuntuforums.org/showthread.php?t=158973), but no luck

---

### Post by edopizza on 2006-08-06
Same problem for my box. I have an HP 2550L connected to my print server included in the router. But the problem started already before the last cups update. The printer use to go in pause mode after I sent a job to it, I always had to reset the printer online via system -> administration -> printing. That wasn't a big deal. But after the last update, the job just stays in the printing cue with the state "job printing" but anything happends. Even if I reboot the system and the printer, the job wont wanish till I delete them.  
It shouldn't be a problem on the printer server: if the usb cable is disconnected, it will report "printer not ready" and will find the printer again as soon I plug it in. On windowz it prints just fine. 

What kind of data from my system could give a clue to solve the problem? 

Here is my /var/log/cups/error_log 

```

E [06/Aug/2006:17:44:05 +0200] PID 7083 (/usr/lib/cups/backend/http) stopped with status 1!
E [06/Aug/2006:17:57:16 +0200] Resume-Printer: Unauthorized
E [06/Aug/2006:17:57:17 +0200] [Job 268] Print file was not accepted (server-error-device-error)!
E [06/Aug/2006:17:57:17 +0200] PID 8413 (/usr/lib/cups/backend/http) stopped with status 1!
E [06/Aug/2006:17:58:14 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:14 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:17 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:19 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:19 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:20 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:20 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:20 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:23 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:24 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:24 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:26 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:26 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:26 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:29 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:32 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:32 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:32 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:34 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:34 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:35 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:38 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:38 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:38 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:39 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:39 +0200] cupsdAuthorize: Local authentication certificate not found!
E [06/Aug/2006:17:58:41 +0200] cupsdAuthorize: Local authentication certificate not found!

and so on, so on...

```

---

### Post by felippe miranda on 2006-08-06
I've posted some information on launchpad. Thank you for your attention .

---

### Post by spork on 2006-08-06
I've got a similar problem:  I've got a HP 3740 on a printer.file server running ubuntu 5.10 and it worked fine until a few days ago.  Now whenever I send sometine to it, it prints "$$" (ascii) then spits out the page.  If I plug the printer directly into my laptop (ubuntu 6.06) it's behaves as it should.  The only thing that has changed recently is that I've applied the various automatic updates as suggested by update-manager to the laptop.  Nothing has changed on the server...

---

### Post by funkydan2 on 2006-08-07
@edopizza - Your problem is quite different to ours since you are getting an error message.  During my research I found lots of threads devoted to that problem.  Use the error message to search either this message board or the internet, and you may find a solution to your problem.

Also, I've had a look at the "Event Viewer" on the Windows server (it's in the Administrative Tools section of the control panel).

It appears that the windows machine is recieving the print-job, but that it throws error 259.  I'll try and work out what that means - but from my breif reading it's something like "no data".

> 
The document Remote Downlevel Document owned by Guest failed to print on printer HPLaserJet. Data type: NT EMF 1.008. Size of the spool file in bytes: 485583. Number of bytes printed: 32. Total number of pages in the document: 0. Number of pages printed: 0. Client machine: \\192.168.1.4. Win32 error code returned by the print processor: 259 (0x103). 

For more information, see Help and Support Center at [http://go.microsoft.com/fwlink/events.asp](http://go.microsoft.com/fwlink/events.asp).


---

### Post by felippe miranda on 2006-08-07
again, my printer is not working after a update on cupsys - updated to cupsys 1.2.2-0ubuntu0.6.06 - printer canon bjc 4300 prints only a few lines then stops the output - same occurs using canon bjc 4200 driver

---

### Post by _logic on 2006-08-08
> **spork said:**
> I've got a similar problem:  I've got a HP 3740 on a printer.file server running ubuntu 5.10 and it worked fine until a few days ago.  Now whenever I send sometine to it, it prints "$$" (ascii) then spits out the page.  If I plug the printer directly into my laptop (ubuntu 6.06) it's behaves as it should.  The only thing that has changed recently is that I've applied the various automatic updates as suggested by update-manager to the laptop.  Nothing has changed on the server...

i had this problem twice already, the [first]("http://ubuntuforums.org/showthread.php?t=208187") was solved by replacing cupsd.conf with cupsd.conf from [here]("https://help.ubuntu.com/community/NetworkPrintingWithUbuntu") and it was working perfectly until latest update which was similar with you had. But instead of "$$" it printed "00", then spits out the paper. So, in the print server, I restored the original cupsd.conf, enabled sharing by adding "Listen 631" in ports.conf (or issue the "sudo /usr/share/cups/enable_sharing 1" command) and restarting cupsys. Afterwhich I added "ServerName server_ip" in the client.conf of my desktop (the one Im typing in now and print to the server later ;)) and restarted cupsys. And happy days are here again .... Problem is: I have a deskjet printer installed locally and it was gone after i restarted cupsys. Help guys?

---

### Post by jeremybar on 2006-08-11
Hi,

In deed, the latest Ubuntu 6.06 Cupsys update packages impacted printing, only from Ubuntu 6.06 clients to Ubuntu 6.06 servers.
I also get a page with '$$' at the top left when the bug occures.

Apparently, it isn't related to the server, only the clients are having issues because the old SuSE 9.2 client system didn't have any problems with printing even though the server had the latest Ubuntu 6.06 updated packages.

Any how, the /etc/cups/client.conf file change with ServerName <IP> seems to fix things.

-- 
Jeremy Bar

---

### Post by arthur on 2006-08-11
Any news?

---

### Post by arthur on 2006-08-16
Success, anyone?

---

### Post by gborzi on 2006-08-16
Hello Arthur, I think you can find a solution here: [http://www.ubuntuforums.org/showthread.php?t=230914&page=2](http://www.ubuntuforums.org/showthread.php?t=230914&page=2)
hope it helps.

---

### Post by shookone on 2006-12-26
I have an HP DeskJet F300 Series printer which uses the dj3650 driver. My printer model is DesjJet F380. 

Initially i was able to print perfectly. Then a couple of updates occured and my printer starts to feed paper then stalls. Newly install HPLIP and CUPS give me an Error on my Printer. 

I too get this in my logs:

cupsdAuthorize: Local authentication certificate not found!


Does anyone know what version of cups was working before that blasted update?

---

