---
title: "Squid as a manual proxy"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by mowbray on 2008-11-04
Hi

I have installed squid on my ubuntu 7.10 using apt-get and configured it to allow my internal network address range.

If I point the browser on the ubuntu box to itself as the proxy, I can browse the web and the proxy works OK. However, if I point any other client at the proxy then I can see a connection is made (by running netstat), however a page is never returned to the browser.

I am kind of suspecting that a proxy loop is taking place, but I dont know enough about squid or Linux to solve it.

Can anyone help? Have out missed out some crucial step?

I dont really want to make it a transparent proxy at the moment - I may come back to it later.

Thanks in advance.

Setup:

ADSL Wireless Router/Switch

Ubuntu 7.04 with squid installed - single nic

client on windows machine with proxy manually configured

I asked for some help in the general forum but have not got an answer, I didnt realise this forum was here - sorry for cross posting.

Here is the other thread showing what I have already done: [http://ubuntuforums.org/showthread.php?t=967729](http://ubuntuforums.org/showthread.php?t=967729)

TIA

---

### Post by iamsumesh on 2008-11-04
Hi,

Are you running behind any firewall?.

Paste your squid.conf and be more specific

---

### Post by mowbray on 2008-11-05
there is no firewall involved on the ubuntu box.

I have a adsl/router/switch/firewall connected to my broadband.

The ubuntu box is plugged into this switch as is the client I am trying to use it as a web proxy for.

There is no firewall running on client.

I can telnet to port 3128 on the ubuntu box from the client machine and issue a 'get' command for [www.google.co.uk](www.google.co.uk) - this works OK.

I can see that the web browser on the client connects to the ubuntu box by running a netstat. But nothing is ever returned to the web browser . If I stop the squid daemon, then the browser says it cant connect to the proxy so it is defitnely pointing to the right place.

I dont think there is much point posting the squid.conf as it only has the network and visible_hostname specified - I didnt change anything else.

---

### Post by mowbray on 2008-11-07
I have copied back the original squid.conf and re-edited to make sure.

Only changes are visible_hostname localhost and the network access for my internal network which was the same as the example in the squid.conf

still not working.

Anyone got any ideas.

I have tried this from the firefox browser on the ubuntu box and it works with no problem, but when I configure IE or Firefox on a Windows client machine the page never gets returned

If I telnet from the Windows client to port 3128 I get connected and can issue a http get!

---

### Post by mowbray on 2008-11-15
Anyone got any ideas about this one - I would really like my squid proxy to work.

---

