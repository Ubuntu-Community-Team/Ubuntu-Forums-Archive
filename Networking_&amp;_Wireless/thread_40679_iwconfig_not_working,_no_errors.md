---
title: "iwconfig not working, no errors?"
date: 2005-06-09
forum: Networking &amp; Wireless
---

### Post by Prefader on 2005-06-09
First, hello.  Frequent reader, new member.

I'm using Hoary on an HP Pavilion xf328, using ndiswrapper and a realtek wireless "b" card, usually successfully.  I have been able to connect to several APs, all using WEP, until this evening.

The problem is odd.  Any parameters that I set via "iwconfig" seem to go through as always, but no changes are made to the actual config (where, exactly, are these parameters written to? /etc/network/interfaces doesn't seem to reflect the information I see when I type "iwconfig").  Any changes made using the graphic interface are at least retained, but I still can't seem to connect to the AP.

For example, currently, "iwconfig" tells me that the ESSID associated with wlan0 is "off/any".  Typing "sudo iwconfig wlan0 essid <essid>" doesn't result in an error, but it also doesn't seem to change anything, and the essid is still reported as "off/any".  The same goes for all "iwconfig" commands, regardless of whether or not the interface is active.

I'm not *new* to Linux, but I'm also (obviously, I think) not entirely sure how to track down problems such as this one.

Any thoughts?

---

### Post by Prefader on 2005-06-10
I found [this page](http://ndiswrapper.sourceforge.net/phpwiki/index.php/FAQ), which contains some helpful information. Unfortunately, I'm not at the same location I was when I was having trouble.  However, it does suggest that I'm simply doing things out of order (not setting the key properly before attempting to set the ESSID, although I'm fairly certain I did set the key first), and so perhaps that is all that was wrong.

Until I'm able to try connecting at that location again, any other suggestions are welcome.

---

### Post by Prefader on 2005-06-10
<cough>

Helps to make sure that, when trying to set up a new connection, the "this device is configured" radio button is unchecked.  Cleared that, and my problems were solved.

Silly me.  Heh.  Hope this little dialogue can be useful to someone else.

---

### Post by smooveb99 on 2005-06-15
You know what?  I had the same problem and it was driving me nuts.  I'm not too proud to say that your dialogue did actually help.  Dang radio button.

Thanks!

---

