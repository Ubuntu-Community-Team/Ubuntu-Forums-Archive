---
title: "Unable to open openoffice"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by Karen Forrest on 2009-08-19
I've been using ubuntu 8.10 about a month. Today, when I started work I couldn't open openoffice files because the home folder was full. When I solved that (a backup had been saved in the wrong place) I still couldn't open them because of the .lock file. I then tried to open the database that I was working on last night and got &quot;the connection to the external data source could not be established. SDBC startup error&quot;. The database is on a separate data partion set up when I was using vista. I had a hunt round online and someone suggested installing openoffice-evolution which I tried. However I had opened an email with a .doc file attached at the same time and, of course, it didn't install correctly. (I know...) The .doc file opened though. I closed openoffice and then reinstalled the package with no problem, however since then I can't open any openoffice files in ubuntu. Instead I get a message saying &quot;The application cannot be started. The user interface language cannot be determined&quot;. I've tried a new user profile. I've tried reinstalling openoffice (I'm using 3.1 and have been for more than a week before this). I've tried removing evolution (all with synaptic). I've removed the .lock file when there has been one, since this last error a new one hasn't appeared. I've checked the document is OK - and I can open it in vista. Any suggestions?  If it's any help, when I try to open openoffice from the terminal, I get this:  /home/karen/.openoffice.org/3/user/config/javasettings_Linux_x86.xml:1: parser error : Document is empty ^ /home/karen/.openoffice.org/3/user/config/javasettings_Linux_x86.xml:1: parser error : Start tag expected, '

---

### Post by Wim Sturkenboom on 2009-08-19
Looks like a corrupted file there.

You can try to rename it to something like */home/karen/.openoffice.org/3/user/config/javasettings_Linux_x86.xml.whatever* and next try to start openoffice.

If it does not help, you'll always have the option to rename it back if necessary.

---

### Post by jrothwell97 on 2009-08-19
Welcome to the Ubuntu forums!

It sounds like there's a corrupted configuration file causing this problem: you should be able to fix it by moving the file out of the way.

The folder ".openoffice.org" lives in your home folder, but as it has a full stop at the beginning of its name it's hidden by default. You can show hidden files in the file manager by pressing Ctrl+H.

Navigate to the file at .openoffice.org/3/user/config/ and rename javasettings_Linux_x86.xml to javasettings_Linux_x86.xml.old. You can then try starting OpenOffice.org again.

Good luck!

---

### Post by Karen Forrest on 2009-08-19
Thanks, that has got rid of the error messages in the terminal, but openoffice still doesn't open. I get the same error message from the openoffice programme window and the terminal just waits till I click OK and the whole thing closes. Karen

---

### Post by Karen Forrest on 2009-08-19
What a frustrating afternoon - after the internet went down for 2 hours I was finally able to follow the instructions I found at the Ooo website here [[http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros]](http://wiki.services.openoffice.org/wiki/Documentation/How_Tos/Installing_on_Debian_based_Distros]) and now have openoffice working again. Thanks.
Sorry - don't know how to tag thread solved.
Karen

---

### Post by Scunnered on 2009-08-19
Karen

If you wish to show "solved" go to your initial post and click edit. Once you have done that click edit again.  This will let you edit the subject line.  Save and then close.

You will not see SOLVED when it is displayed on the forum list but opening the post will then display your remark.

Trust this assists

---

