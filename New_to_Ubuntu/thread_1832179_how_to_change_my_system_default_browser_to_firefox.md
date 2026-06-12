---
title: "how to change my system default browser to firefox?"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by gchiacch on 2011-08-24
Hello, 
in the preference --> Preferred Application I have Firefox selected with radio button on 'open link with web browser default'
nevertheless when I click on a link, it open the Google-crome.

typing sudo update-alternatives --config x-www-browser in a terminal session, I see:
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                    Priority   Status
------------------------------------------------------------
  0            /usr/bin/google-chrome   200       auto mode
* 1            /usr/bin/firefox         40        manual mode
  2            /usr/bin/google-chrome   200       manual mode

I wonder if the Google-chrome is selected because of auto mode status.
Can someone help me to solve this issue in setting the firefox as system default browser? 
Thank you in advance 
PS: ubuntu 10.10
2.6.35-30-generic-pae #57-Ubuntu SMP Tue Aug 9 19:49:53 UTC 2011 i686 GNU/Linux

---

### Post by gchiacch on 2011-08-24
I wish to add that selecting the general tab from  Advanced Firefox preferences the 'check now' button shows that 'Firefox is already set as your default browser' but as previously said selecting any Web link the Google-crome browser open instead of firefox one. 
I would appreciate the help received. Thanks!

---

