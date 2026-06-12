---
title: "Wireless Range Extender"
date: 2014-12-05
forum: Networking &amp; Wireless
---

### Post by magtrask on 2014-12-05
I am using 14.04 on an HP Pavillion trying to connect via an Amped Wireless SR10000 Range Extender.
The connection information states that it is connected with a strong signal and working, but it is not.
I can connect to the primary wireless modem and it works fine but the signal is very weak.
I do not have the authority to change settings on the extender. It uses WPA security and I have the correct password.
This laptop connects fine when running windows.


Suggestions?
Thank you.

---

### Post by jeremy31 on 2014-12-05
I tested some with my netgear extender and had it connect to my hotspot using TKIP but was able to have the extender use WPA2-AES

---

### Post by magtrask on 2014-12-09
I'm sorry, I don't understand how your response applies to my problem. Please elaborate?

---

### Post by jeremy31 on 2014-12-09
> **magtrask said:**
> I'm sorry, I don't understand how your response applies to my problem. Please elaborate?
Sorry, I missed the part where you can't change settings on the extender, if it uses WPA and TKIP it might not be possible to make a good connection.  But you could get your own extender to connect to the existing one and have it use WPA2-AES

---

### Post by Hadaka on 2014-12-10
Hi, here are the step by step by the manufacture of your extender.
[http://www.ampedwireless.com/docs/usersguide/SR10000_UsersGuide_Rev1.1_English.pdf](http://www.ampedwireless.com/docs/usersguide/SR10000_UsersGuide_Rev1.1_English.pdf)
if you cannot access this extender, then you will nevr get it to work. Read the simple manual
its not difficult and there is even an 888 toll free number for help. The first thing the manual
notes is are you runnung windows ? if so...its different, so if it were set up using windows you
may also have issues...good luck.

---

### Post by magtrask on 2014-12-12
Thank you for the link to the manual but this is not helpful to me as I cannot load [http://setup.ampedwireless.com/](http://setup.ampedwireless.com/)
Also, I no longer have a windows machine, only ubuntu.
Any other suggestions out there?
I may be able to ask the owner to change some router settings. For example it is now WPA2.
Thanks in advance for any help....

---

### Post by jeremy31 on 2014-12-12
You might want to read the sticky post "before posting in networking and wireless" to download and run the wireless script and post the resulting file

---

### Post by magtrask on 2014-12-12
[B]from extender:

[/B]silas@silas-HP:~$  wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2014-12-12 19:15:37--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... failed: Connection timed out.
wget: unable to resolve host address &#8216;dl.dropbox.com&#8217;
silas@silas-HP:~$ 

[B]I suspect the above is not helpful.
from main modem, which I'm not sure is relevant:
[/B]
silas@silas-HP:~$  wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2014-12-12 19:21:03--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 23.23.195.68
Connecting to dl.dropbox.com (dl.dropbox.com)|23.23.195.68|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-12-12 19:21:04--  [http://dl.dropboxusercontent.com/u/57264241/wireless_script](http://dl.dropboxusercontent.com/u/57264241/wireless_script)
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 23.23.255.234, 23.21.176.173, 54.243.70.174, ...
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|23.23.255.234|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dropbox.com
Cookie coming from dl.dropboxusercontent.com attempted to set domain to dropbox.com
Location: [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script) [following]
--2014-12-12 19:21:04--  [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script)
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|23.23.255.234|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13362 (13K) [text/plain]
Last-modified header missing -- time-stamps turned off.
--2014-12-12 19:21:05--  [https://dl.dropboxusercontent.com/u/57264241/wireless_script](https://dl.dropboxusercontent.com/u/57264241/wireless_script)
Reusing existing connection to dl.dropboxusercontent.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 13362 (13K) [text/plain]
Saving to: &#8216;wireless_script&#8217;

100%[======================================>] 13,362      --.-K/s   in 0s      

2014-12-12 19:21:05 (177 MB/s) - &#8216;wireless_script&#8217; saved [13362/13362]

I'm not very versed in this, thank you for the patience. I can't download anything from the extender, although my connection information indicates it can. The connection to the main router, as listed directly above, is not the issue. Please advise.

---

### Post by magtrask on 2014-12-12
How to run the diagnostics on the extender when I am unable to connect? Should I go the extender and plug in a wired connection? What script to run?

---

### Post by magtrask on 2015-01-09
Problem persists, please advise.

---

### Post by mikewhatever on 2015-01-09
Errors like the above ( wget: unable to resolve host address &#8216;dl.dropbox.com&#8217;) are usually DNS related. Can you try <ping -c 5 8.8.4.4> while connected to the extender. Also, post the output of <nm-tool | grep -A5 IPv>.

---

