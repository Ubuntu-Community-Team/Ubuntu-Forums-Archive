---
title: "Evolution and Google offline copies of contacts and calendar items"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by kylea on 2009-08-03
I have set up Evolution to link to my Google Contacts and Calendar events. This works fine (at home - not my office as the firewall stops the connections). 

I have selected the option to save an 'off line' copy of both, however this does not seem to work too well as when I am 'off line' (eg at the office) I cannot see any contacts nor calendar items under the Google category headings

---

### Post by kylea on 2009-08-10
No one using this feature?

---

### Post by dave1403 on 2010-03-22
It seems that it still doesnt work...
this is a real bummer. i can't imagine that not enough people have this problem for it not to get fixed :(

---

### Post by kylea on 2010-03-22
I have come across a program called CNTLM - this has helped with my work firewall/proxy issue as I can now get access to the online calendar, but it is still relies upon being online

---

### Post by asciibaron on 2010-08-18
> **kylea said:**
> I have come across a program called CNTLM - this has helped with my work firewall/proxy issue as I can now get access to the online calendar, but it is still relies upon being online

Evolution 2.30 addresses some of the issue.  the Google calendar events will be available offline, but they will not be populated in the panel calendar, just within Evolution.  this is a bummer, i use my netbook instead of a PDA and i really like being able to see at a glance what events are scheduled.

to get Evolution 2.30 add this to your repositories  - 

sudo add-apt-repository ppa:jacob/evo230
sudo apt-get update
sudo apt-get install evolution

this is an unstable release, all disclaimers apply :)

---

