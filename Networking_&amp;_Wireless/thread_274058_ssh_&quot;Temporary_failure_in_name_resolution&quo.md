---
title: "ssh &quot;Temporary failure in name resolution&quot;"
date: 2006-10-09
forum: Networking &amp; Wireless
---

### Post by xfred on 2006-10-09
This one has me stumped.  Whenever I try to run ssh to log into my work account from home, I get the error "Temporary failure in name resolution".  Now, I can surf the web no problem, and the /etc/resolv.conf appears to be set correctly (to my providers primary and secondary dns addresses).

When I try to ssh direct to the ip address, bypassing the dns, I get the error:
ssh: connect to host <ip address here> port 22: Network is unreachable

The setup is: ubuntu box <=> static ip lan <=> firewall/router running ipcop <=> adsl connection.

fwiw, I also have several old windows boxes and a redhat (some old version... 5 or 6, can't recall which) box.  The only one I can succesfully ssh out from is the old redhat boxes, and here only if I (a) use the ip address rather than the name and (b) type the ssh command once, wait >= 10 seconds, stop it with ^C, ssh again, and wait 5 seconds... then, and only then, will it connect.

(Sorry if this question is "obvious", but I've being trying to fix it on and off for over a year with no luck).

---

