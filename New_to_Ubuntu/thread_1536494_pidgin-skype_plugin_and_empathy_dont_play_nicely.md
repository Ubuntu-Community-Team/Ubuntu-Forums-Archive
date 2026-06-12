---
title: "pidgin-skype plugin and empathy dont play nicely"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by g3k0 on 2010-07-22
I found the pidgin-skype plugin in synaptic and installed it.  There is now an account type in empathy named bigbrownchunx-skype-dbus.  I have attempted to use it to connect to my skype account (which I have installed and working) and it just gives me the error : Disconnect-No reason specified.  I have tried it logged into skype and logged out of skype.

Any ideas how to get it working?  I am on Lucid.

Also if I exit skype completely it says disconnected- Network error when I try to connect in empathy

---

### Post by hoho32 on 2010-07-23
well in Ubuntu 10.4 after adding my use name in pidgin skype account while i press on (add) its crash up and the whole pidgin window closed

---

### Post by aggiemarine07 on 2010-08-11
found a solution until the empathy team can fix it. I tried it out and it works flawlessly (didnt even have to restart empathy).

Someone named "ng" filed a bug and a fix for the plugin here:
[https://bugs.launchpad.net/ubuntu/+source/pidgin-skype/+bug/567248](https://bugs.launchpad.net/ubuntu/+source/pidgin-skype/+bug/567248)

First, completely remove pidgin-skype (you cant run both at the same time, besides this fix works for both pidgin and empathy)

 > sudo apt-get remove pidgin-skype 


Second, download the skype4pidginandempathy.deb fix (it should be right beneath the filed bug in a hyperlink; the download is about 421kb)

Third, open it up and install it.

Finally, go into empathy put in your skype username and presto...it displays the contacts in empathy.


Sidenote, Ive read in some places that skype must be open and signed in BEFORE you open and sign in to empathy. I did not have this issue but be aware you may/may not have it.

To fully understand its limitations just read the bug report to see if there are any other updates to it. Hope that helps!

---

### Post by jclauser on 2010-08-12
Thank you. That worked for me. Now I am only able chat using Skype. Is there a way to initiate a Skype video call through empathy?

---

### Post by aggiemarine07 on 2010-08-12
not that i am aware of, again as it says on the bug forum, its a temporary fix until someone at empathy fixes it :-/

---

