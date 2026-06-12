---
title: "why is it so hard to link to internet?"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by jbeckxxx on 2009-02-26
I downloaded xubuntu and ubuntu installed on separate hd drive for simplicity.fine.the directions point 1 direction but theres no direction to be found...Ijust want to hook to internet.EASILY.Maybe Ive got wrong version(8.10)It sounds simple in directions if lay-out was actually there.But its not.The best conclusion is I hv wrong version for 56k modem.





















I have 8.10 installed Iwant hook to internet. HELP.PLEASE.i hv 56k modem,is my version wrong?

---

### Post by NoBugs! on 2009-02-26
It sounds like the problem is the modem. What type is it? It is supported? in the console, type:
```
lshw -C network
```
This should show what network devices you have.

---

### Post by kyphi on 2009-02-26
There is nothing wrong with your version of Ubuntu.

It would help if you gave some details about your 56K modem.

---

### Post by halitech on 2009-02-26
internal or external modem? Do you still have windows installed and does it work there?

more details will help us get things running. Along with the lshw command, also post the output of
```
lspci
```

---

### Post by LowSky on 2009-02-26
this document should help you the most
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

