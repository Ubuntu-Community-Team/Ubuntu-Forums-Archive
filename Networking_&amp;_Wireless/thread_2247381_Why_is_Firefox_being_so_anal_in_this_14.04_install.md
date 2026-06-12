---
title: "Why is Firefox being so anal in this 14.04 installation?"
date: 2014-10-07
forum: Networking &amp; Wireless
---

### Post by bluplanet on 2014-10-07
I just installed xubuntu 14.04 on two computers. 
 
Neither of them got libasound2 installed.  I installed it on one,  but now I'm having strange problems with this second one. 
 
Firefox will go right to Google.com, to bing.com, and to craigslist.org with no problems. 
And if I search any thing like "libasound2" or "install libasound2", i  get a list of results with both search engines, but none of the search  results are accessible. 
 
When I click on the results, I get:

"waiting for ubuntuforms.org..." 
or  
"waiting for us.wow.com..." 
or  
"waiting for www.howtogeek.org..." 
or  
"waiting for pkgs.org..." 
or  
"waiting for www.dnsrsearch.org..." 
 
I get the same problem if I type ubuntuforums.org in the address bar.

Nothing loads.   
What's going on?

---

### Post by este.el.paz on 2014-10-07
> **bluplanet said:**
> I just installed xubuntu 14.04 on two computers. 
 I get the same problem if I type ubuntuforums.org in the address bar.

Nothing loads.   
What's going on?

@blu:

Difficult to know exactly, but FF has been giving me problems lately in various formats.  Running 32.0.3 in my PPC iMac w/12.04 Xubuntu . . . FF crashed twice while trying to check Yahoo mail, and then trying to get into Gmail.  Other sites seemed to work OK.  Using Ten4Fox, a fork of FF, in 31.1.0 it would crash also in Gmail and other sites . . . upgrading to 31.1.1 and running Safe boot seems to lessen the issue.  In posting to the TFF discussion group I saw that FF has been showing crash issues in new upgrades???  So, there must be a "bug" with recent editions of FF which have not been found or fixed.

I guess for testing purposes you could try to install another browser using synaptic or software update and see if the problem persists.  Other option, wireless or internet connectivity issue?

e.e.p.

---

### Post by bluplanet on 2014-10-07
I can't do any software updates.  That uses connections that the computer (or Firefox) is blacklisting.

I installed the OS connected to the network and told it to download software while installing.  Maybe I should just stick to the Firefox on the install disk which is a few months older.

---

### Post by este.el.paz on 2014-10-07
> **bluplanet said:**
> I can't do any software updates.  That uses connections that the computer (or Firefox) is blacklisting.

I installed the OS connected to the network and told it to download software while installing.  Maybe I should just stick to the Firefox on the install disk which is a few months older.

@Blu:

Might be worth trying the older version of FF and see how it goes; it's not that long ago that FF was working fine.  I don't have the technical chops to ask for the reports that show "blacklisted connections" . . . but that does sound a little odd, no?  What happens if you quit FF and then try the console for "sudo apt-get update" and so forth?  Can you get a connection through the Terminal?  Or if that doesn't work try "ping.google.com" and see what it says--Use "Control C" to stop the infinite loop if you get to ping google?  

Other question, did you check the md5sum number of the iso before the install?  These days it seems more critical that it be correct or otherwise weird stuff happens.  Point being FF shouldn't be "controlling" your access to the internet.

e.e.p.

---

