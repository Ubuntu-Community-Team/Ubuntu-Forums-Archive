---
title: "Update fails"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by Pax Felix on 2009-02-11
When I logged in this afternoon, in the upper right (system tray?) was a bright red arrow.  Cursor hover revealed it was a message about updates ready.  So I clicked on it, and an Update Manager window opened with about 13 updates.  Clicked on the button that said "download," "install," or "apply," whichever it was, and for each one I got an error message to the effect that the connection failed.  Now, browser and email are working fine; it's not my connection to the internet that is the problem.  The exact error message is:

Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

I tried a manual workaround.  Each update was associated with a URL.  I copied and pasted those URL's into Firefox and successfully downloaded 2.  Not the first 2, but still 2.  The last one I attempted resulted in a "Broken Package," with instructions to use the Synaptic Update Manager to repair.  This I did.  Twice.  After each such attempt, Synaptic appeared to have contented itself that the repair was successful.  However, when I attempt anything with the special update button, or plain Update Manager, or the full Synaptic Update Manager, I continue to get the error message:

You have 1 broken package on your system!  Use the "Broken" filter to locate it.

Several of the dialog boxes have also included instructions to enter in a terminal, which I have done, to no effect.  Basically, I'm getting the first error message above when I try to do sudo apt-get update or sudo apt-get install -f.

I've tried everything I can think of, having just downloaded Ubuntu around 48 hours ago.

I would greatly appreciate any help.

Be well,
Pax Felix

P.S., I ran a Whois inquiry on the 127.0.0.1, which yielded a map with a marker squarely in the Atlantic off the coast of East Africa.  No name registered with it.

---

### Post by uberg on 2009-02-11
Are you using Synaptic when you say Package Manager?  Try this from Synaptic: [https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)
See if that works.

Joe

---

### Post by kestrel1 on 2009-02-11
127.0.0.1 is the local loop back address, so it is associated to your machine & not an external server.
Can you run the following in a terminal: ```
sudo apt-get update
```
Let us know what happens.

---

### Post by Coreigh on 2009-02-11
127.0.0.1 refers to your local computer, the one you are using, aka. "localhost".

Regarding the update trouble it may be asking for the CDrom to complete updates. This is not necessary. To change this open the Software Sources from the System >> Administration menu. You will be asked for a password, use your normal login password. Click on the second tab "Third Party Software" and remove the check mark from the CDROM line, if one is there.

Next go to the Update Manager (from the same menu as above) and click the "Check" button. This will refresh the update list and sources. Choose "Install Updates" if any are found.

If you still get errors you may need to try some more advanced options but the easy thing to try is to simply remove the broken packages and re-install them. There are some packages though that this won't work with (major packages like the Xwindows system xorg, or gnome-desktop).

To try remove / replace open the Synaptic package manager (same menu again) find the package in the list and "Mark for Complete Removal". This is done by right clicking on the check mark and selecting from the menu. Synaptic will alert you of dependencies that will be affected or removed also. If you choose to go ahead, then complete the process and REBOOT the computer befor going back and re-installing the packages.

EDIT:
Can someone offer a simple explanation of using dpkg to re-install or reconfigure packages?

---

### Post by Pax Felix on 2009-02-11
Thanks -- went to that webpage, which I had non known of, and followed the instructions under "How to Fix Broken Packages."  I got this error message:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9.0.6+nobinonly-0ubuntu0.8.10.1_i386.deb)
Could not connect to localhost:4001 (127).  -Connect (111 Connection refused)

---

### Post by kestrel1 on 2009-02-11
You may need to select a different ocation to download from. To do this go to:
System -> Administration -> Software Sources
Once this opens go to the where it says: Download From
Click on this & select Other.
Then click on Select Best Server
That should then get the right server for you.

---

### Post by avtolle on 2009-02-11
Take a look at your /etc/hosts file; I've a feeling that there's been a corruption there. Post the contents of the file so we can take a look at its contents.

---

### Post by uberg on 2009-02-11
Try:
sudo dpkg --configure -a
dpkg is the father of apt(-get).  This has worked when the other approach has failed.
Joe

---

### Post by Pax Felix on 2009-02-11
[quote=Coreigh;6718139]To try remove / replace open the Synaptic package manager (same menu again) find the package in the list and "Mark for Complete Removal". This is done by right clicking on the check mark and selecting from the menu. Synaptic will alert you of dependencies that will be affected or removed also. If you choose to go ahead, then complete the process and REBOOT the computer befor going back and re-installing the packages.

Thanks for all the suggestions!  The one quoted from Coreigh's post turned out to be the one that worked in this instance.  It was not entirely clear to me exactly which package was broken, so what I did was mark each of the packages identified for update as "Complete Removal" and then rebooted.  One of those was Firefox, so I had to reinstall it and that's why there was some delay in getting back to post this.

Again, many thanks.

Be well,
Tony

---

