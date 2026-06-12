---
title: "Network Discovery"
date: 2006-10-07
forum: Networking &amp; Wireless
---

### Post by slacker9876 on 2006-10-07
I am looking for a network service discovery scanner to use at client sites to see what hosts are out there, what ports are open, etc. Under Windows I have used the Langaurd Network Security Scanner, but it is just too bloated now, so I would like to a linux alternative.

What are you folks using?

---

### Post by spd106 on 2006-10-07
One of the most popular tools is nmap, you can find a slightly older version (4.03) in the main repo. It is a command line tool, but you can also use it through the nmapFE gui, though you will have to enable the universe repo. 

If you want a more current version then nmap 4.10 can be found in Dapper backports.

---

### Post by slacker9876 on 2006-10-07
Thank you. I have installed it and tried out both the command line and "fe" it is no LNSS, is there noway to dump my scans to a MySQL db? I have only been able to dump to text. I need db access to the scans to actually use the data. I will admit...I cannot (well, will not) manulipte text.

For one shot use it is very robust, but is there anything better?

---

### Post by spd106 on 2006-10-09
scanrand from [www.doxpara.com](www.doxpara.com) may be able to do this, though I haven't used it, so I can't recommend it.

---

