---
title: "Problems with DNS"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by kiwiambo on 2007-02-13
Can open System login and enter dns there, however when I am not using the Internet it disconnects it self.
I then have to go back in and re enter DNS Servers again.
Is there a way around this and save DNS Server Numbers without them disconnecting and having to re enter continually

---

### Post by gradedcheese on 2007-02-14
hmm... I wrote mine to /etc/resolv.conf and I've never had them overwritten.  Can you try that and see if it happens again?

---

### Post by kiwiambo on 2007-02-14
I tried that and I got this message, permission denied, how do I unlock this thing

---

### Post by gradedcheese on 2007-02-14
Sorry.  When you access files in /etc, you need to use sudo.  For example, if you like to edit with gedit:

sudo gedit /etc/resolv.conf

---

### Post by kiwiambo on 2007-02-14
Can you give me step by step instruction to do this please, as I have no clues at present as to how to do all this at present

---

### Post by gradedcheese on 2007-02-14
Sure.  Open a terminal from the Applications menu (Applications->Accessories->Terminal).  Now type "sudo gedit /etc/resolv.conf" and press Enter.  This will open the resolv.conf file in gedit.  Its contents are just the IP addresses of your DNS server(s).  I decided to use opendns, so mine contains:

```

search opendns.com
nameserver 208.67.222.222
nameserver 208.67.220.220

```

Note the syntax: "search [domain_name]", "nameserver [ipaddress]".  Edit the file so that your desired servers are there (or you can make yours like mine to use opendns if you wish).  Save, and then Exit gedit.

---

### Post by kiwiambo on 2007-02-14
done all that stuff and it keeps disconnecting itself still, realyy driving me up the wall now

---

### Post by sdide on 2007-02-14
What is your setup? 
Is it just DNS that doesn't work, or are you actually disconnected?

Try next time when you loose connection, open a terminal and do first:

# ping [www.ubuntu.com](www.ubuntu.com)

if that works, you should be connected and have resolve! 
if it fails try :

# ping  82.211.81.166

if that works, you have connection, but no nameresolver.
if it fails, you are not connected.

if the first fails, and the second works, please post your 
resolv.conf, ie: 

# cat /etc/resolv.conf

and paste out output here.

---

