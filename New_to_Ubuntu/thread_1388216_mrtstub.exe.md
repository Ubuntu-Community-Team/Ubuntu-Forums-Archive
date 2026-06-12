---
title: "mrtstub.exe"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-01-22
There is a very odd folder on an external NTFS drive.

The folder is named "e3556a29348d0c587c45145d", and it has three files in it:
mrtstub.exe
mrt.exe._p
$shtdwn$.req

I've done a spot of googling and mrtstub.exe would seem to be somehow related to the Microsoft Malicious Software Removal Tool. But there's a suggestion by some that it might just be masquerading as that.

The thing that confuses me most is why on earth the Vista update process, which I presume must have installed it, chose to place the folder on an external drive????? That makes me suspicious that it's not kosher.

Is there anyone here who has encountered a similar issue?

Does anyone know how I can tell whether I should delete the folder? And what might happen if I do?

---

### Post by HereInOz on 2010-01-22
That is a temporary installation folder, and as such, can turn up in the root directory of any NTFS drive on the system.

Worry not - if you can't trust Microsoft, who can you trust ;)

---

### Post by gnometorule on 2010-01-22
Looks like malware:

[http://www.pcreview.co.uk/forums/thread-2237807.php](http://www.pcreview.co.uk/forums/thread-2237807.php)

Seems unlikely that Vista update installed it. It might be hard to get rid of  by simple deleting the folder/files - you might already have an infected system. In your shoes, I'd run all freely available, good software against it and see what happens, in about this order:

Avira
Avast
AVG

Article speaks of defense against some AV, so you need to see what happens. It can't hurt to run Rootkitrevealer too, although spotting false positives can be hard. Maybe check sites more specifically for such problems (e.g., Bleepingcomputers). Well, I'm actually assuming you see those on the Windows partition in a dual boot, as you mention vista. 

In any case, take it seriously. I caught a rootkit/keylogger last year that compromised my on-line banking account. I got the money back, but watch out. 

Good luck. :(

---

### Post by gnometorule on 2010-01-22
...or not:

"For example, when you run the **[[COLOR=blue]MS Malicious Software Removal Tool[/COLOR]]("http://www.microsoft.com/security/malwareremove/default.mspx")** (MSRT), a temporary folder named with random alpha/numeric characters (i.e. 79f142e5e9e574d23954) will be created on your C:\ drive that contains mrt.exe, mrtstub.exe and a file named $shtdwn$.req. Most of the time after performing a scan and you click finish/cancel the folder will automatically be removed right away or after the next restart. If not, the folder can be deleted manually without an adverse effect on the computer."

(from: [http://www.bleepingcomputer.com/forums/index.php?showtopic=232668&hl=mrtstub.exe](http://www.bleepingcomputer.com/forums/index.php?showtopic=232668&hl=mrtstub.exe))

Other link I added is much older; this is June 2009. So looks like I get the brown bag, get into a corner; and you're good. But have a look at both articles. I like BC; maybe check in with them too.

---

### Post by Roger Allott on 2010-01-22
Thanks for the info, chaps.

As a precaution, I've deleted the "e3556a29348d0c587c45145d" folder that was on my external drive, and the "MRT.exe" file from my C:\Windows\System32\ directory. I did that from Ubuntu, so hopefully there's no replacing reaction by an infected registry.

The thread from Google Groups at [http://groups.google.com/group/microsoft.public.security.virus/browse_thread/thread/a8bc331495e37fa3/e87b349e4c8d4bf2?lnk=st&q=mrt.exe+cpu&rnum=1&hl=en#e87b349e4c8d4bf2]("http://groups.google.com/group/microsoft.public.security.virus/browse_thread/thread/a8bc331495e37fa3/e87b349e4c8d4bf2?lnk=st&q=mrt.exe+cpu&rnum=1&hl=en#e87b349e4c8d4bf2") is a bit odd, as it is discussing exactly the issue I've identified, but the posts are from over 4 years ago! And the last post there is by a chap from Microsoft thanking people for bringing it to MS's attention and saying it has now been resolved.

I've got to the stage where I was only using Vista for picture editing and online poker, so I'm going to leave it a while before I boot it up again.

---

### Post by Roger Allott on 2010-01-22
I've just had a thought.

Clamav is installed on my Ubuntu system, but I've never run it and I'd guess it's virus library is not completely up-to-date.

So my questions are:
would it make sense to run clamav on my NTFS drives from Ubuntu?
how do I ensure that clamav's virus library is up-to-date?
how do I run clamav?

---

### Post by presence1960 on 2010-01-22
[http://www.free-av.com/en/products/12/avira_antivir_rescue_system.html](http://www.free-av.com/en/products/12/avira_antivir_rescue_system.html)

Download avira antivir rescue system and burn it as a bootable CD. Boot from the CD and then update the definitions & scan your NTFS devices. Since windows is not running the sophisticated nastys can't hide like they can when windows is running.

I would do that if you are really worried. But that folder sounds legit.

---

### Post by Sir Jasper on 2010-01-22
Avast 5 free version (with active protection) for Windows has become available this week. The old 4.8 version has invariably been ranked amongst the top 5 malware protection products with a detection rate of some 98%+.

The Debian version of Avast (on demand scanning) is available for use in ´buntu
though the usually twice daily definition updates are full (not incremental as with Clam) so broadband is almost essential. Its external test detection rate is usually some 12% higher than Clam and it scans many times faster than Clam.

---

### Post by gnometorule on 2010-01-23
For all I know, ClamAV is just a virus scanner. Avira, Avast etc. cover all type of malware. I'd be much less worried about a virus than about rootkit or rootkit style invasions, such as keyloggers. If ClamAV is really just an AV proper, it wouldn't find those. Rootkits in particular are pretty hard to spot as a rootkit, already present, might anyway hide from AV full-service systems if those install after it (there are proof of concept rootkits that aren't even located on your harddrive, but deeper in your system). 

So if you want to scan, and are worried, I'd actually run both Avira and Avast, plus one run of Rootkitrevealer. As presence1960 mentions above, best way is from external bootable disk, if you don't mind the additional hazzle. If not, just from your harddrive. Best of luck.

---

### Post by theozzlives on 2010-01-23
I always delete those hexadecimal folders, never had a problem.

---

