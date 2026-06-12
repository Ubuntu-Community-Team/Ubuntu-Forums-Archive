---
title: "where do the installed programs stored in ubuntu?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by StandUpSpeakUp on 2009-07-10
Hi, i have internet download manager installed on my ubuntu, and i want to integrate it to my firefox.. but i need to find where is firefox.exe is located.. anyone knows?

and can i something, how can i uninstall firefox, because i tried synpastic and add/remove program tools but my firefox still workin.. i want to uninstall my firefox and install a clean firefox 3.5..

thankss...

---

### Post by anystupidname on 2009-07-10
/usr/bin/firefox

sudo aptitude update
sudo aptitude purge firefox firefox-3.0 firefox-3.1 firefox-3.5
sudo aptitude install firefox-3.5

---

### Post by IHeequ5i on 2009-07-10
One other thing - there's no such thing as "firefox.exe" under Linux (at least, not that I'm aware). That's a Windoze naming convention. 

I believe the executable is called "firefox-3.5" and I *think* it will install in /usr/bin. However, I'm somewhat new to this, so I may be wrong.

---

### Post by oldsoundguy on 2009-07-10
If you already have Firefox installed, why not use the a download manager that comes WITH IT?  Look under tools> add-ons.

Why re-invent the wheel?

---

### Post by Xero Xenith on 2009-07-10
IDM is Windows software - the Firefox install on your Ubuntu is Linux software. While IDM will run, the two do not integrate nicely whatsoever.

You can install the Windows version of Firefox, but it won't integrate nicely into Ubuntu, and might not work properly.

A better solution would be to use a Linux download manager, or one integrated into Firefox - I find a combination of DownThemAll! (in Firefox) for normal downloads, and JDownloader for Rapidshare/Megaupload/etc downloads works perfectly. :)

---

### Post by StandUpSpeakUp on 2009-07-10
alriteee.. thanks everyone for the explanation :)..

---

### Post by Paqman on 2009-07-10
On Linux you don't need to know the path to the executable to be able to launch the app. For example, Firefox is at /usr/bin/firefox, but the command to launch it is simply: firefox. Linux is a lot smarter than Windows when it comes to stuff like this.

---

