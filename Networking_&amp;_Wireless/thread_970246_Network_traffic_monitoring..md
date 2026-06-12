---
title: "Network traffic monitoring."
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by AJB2K3 on 2008-11-04
I'm interested in what traffic is in my network and all messages/request but how do I see all these messages/request in real-time/viewing them as they happen?

---

### Post by leonj@infogro.co.za on 2008-11-04
Hi,

Try as root :

```
apt-get install iptraf
```

Then type in command line

```
iptraf
```

Hope this is what you were looking for... ):P

---

### Post by AJB2K3 on 2008-11-05
For the first part, yes it is thanks.

now for the next bit.
Can I get the ip address automatically run through whois and printed to a file?

---

### Post by y@w on 2008-11-05
You could pump it into a log file and use awk to parse out the IPs and do a whois on each of them if you really wanted to..

---

### Post by jonobr on 2008-11-05
Hello


Should also take a look at wireshark this makes looking at network traffic very easy and brings you down to the hex code if you want to go down that far.

On Wireshark you can use the command line version, and filter traffic based on what you want to see, source, destination IP, port number protocol etc.

For constructing filters, wireshark.org has some tips, and the gui itself allows you to construct simple filter rules

---

### Post by AJB2K3 on 2008-11-05
I have an Idea for a network protection tool but first I need to learn about network traffic.

---

### Post by The Cog on 2008-11-05
Then you will be wanting wireshark and a shed-load of books. Definitely wireshark.

---

