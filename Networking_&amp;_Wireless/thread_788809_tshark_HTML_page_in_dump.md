---
title: "tshark HTML page in dump"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by adityaj on 2008-05-10
Hi

I am trying to look for keywords in a html response (the html page ie)
via tshark. Now i have found that data-text-lines holds the HTML data
and I am trying to dump the data in this field:

tshark -r datadump -V -T text -Tfields -e data-text-lines

Where datadump is a libpcap dump of the n/w data.

Now all that gets printed out is the mime type text/html etc.. not the
whole page. How can i get it to dump the whole html page in ascii??

Thanks and Regards

Aditya

PS: I know i can use the matches clause to look for patterns (via
PCRE) but i am interested in the complete html page too

---

