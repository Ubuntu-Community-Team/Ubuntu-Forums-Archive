---
title: "Evince printing problem"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by djmac on 2010-05-31
I am having problems printing pdfs from evince. I can print from OpenOffice, the web, etc without any problems. When I try to print from evince maybe a couple of pages will print (if you are lucky) and then it will just stop, (but the printer status will read "processing").

I don't have any problems printing the same pdf from acroread.

I believe this is a new problem, as I have been printing from evince for years, from the same printer. Is anyone else having this problem or similar, and do you know how to fix it??

Cheers

---

### Post by cjcj on 2012-07-10
I also have this problem - same as described but do not get any of the document actually printing. Am using up to date 12.04 with an Epson Phto Stylus RX 520 printer connected via USB. 

Have you made a bug report?

---

### Post by alfh on 2012-07-11
Confirming this problem on xubuntu 11.10 with HP photosmart c4580.

Printing was working flawlessly from initial install onwards, then for about a week or two (conciding with low ink-levels) printing from evince just fails. The printer will start working, "eat" a little paper and then stop and instruct me to shut it off and on.

I've got this error message: > /usr/lib/cups/filter/gstoraster failed

The usual error, though, is a dialog box with the message > There was a problem sending document xxx.pdf (job no) to the printer and the option to 'OK' or 'Diagnose'

Diagnosing instructed me to publish shared printers, to no avail. Common for every failure is that the printer will 'stop' and need to be enabled again (through system -> printing or through the hplip device manager).

Workaround for now is to print pdf files from other programs.

Tried solutions: remove and reinstall printer, remove and reinstall evince. I kinda don't want to remove & reinstall cups since it's working with other programs.

---

### Post by alfh on 2012-07-12
So it turns out this problem is not only related to evince.

Two days ago I installed Adobe Reader. It was printing and I had a workaround. Until today (ok, still got some kind of workaround since the win 7 laptop is able to print, but, duh).

Now I'm getting the 'HPLIP error 5012' which indicates communication trouble. Unlike the problem described in [http://ubuntuforums.org/showthread.php?t=986058]("http://ubuntuforums.org/showthread.php?t=986058") I can NOT print a test page.

So in line with suggestions in the other thread I set a static ip for my printer, then tried this loop a few times: Open system -> printing. Remove printer. Reboot. Run HP-toolbox and reinstall printer. Bang head in same problem. ](*,)

From terminal tried: ```
hp-check -t
``` (also suggested in the thread mentioned above). This gave 13 errors and / or warnings. last one was > error: User needs to be member of group 'lp' to enable print, scan & fax.
User member of group 'lpadmin'.

Add my user to group 'lp'. Reboot.

New remove / reinstall process. Set default paper format to a4 in HP toolbox. Print test page from HP toolbox succesful. Opening Adobe reader, defaults to Letter. Closing HP toolbox. Opening system -> printing. This dialog defaults to letter. Trying to print from adobe reader, succesful. Change adobe reader print settings to a4 - new print succesful. Print from evince - succesful. Getting hopeful. 8-)

Change system defaults to a4 (system -> printing -> printer properties -> printer options). Open new document in adobe reader. Print succesful. Change default to a4 borderless. Print fails. This setting was working before all those troubles started. Change default to a4 small margins. Print successful.

Summary: do 'hp-check -t' 
check error(s), in my case missing membership in group 'lp'
fix error(s)

My preferred format still doesn't print, but I can live with that. Also, HP toolbox doesn't change settings systemwide, suggesting missing communication somewhere between the toolbox and cups. For now, this too is acceptable.

Good luck to the rest of you!

---

