---
title: "how to set up iptables script"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by renaissance on 2006-07-21
how i can up load and set up iptables rules in script file ?

---

### Post by wieman01 on 2006-07-21
If you want to do it manually, here we go: 

[http://doc.gwos.org/index.php/IptablesFirewall]("http://doc.gwos.org/index.php/IptablesFirewall")

Personally I prefer to configure IP Tables via Firestarter, a nice little tool including GUI that has been my best friend for a while now:

[http://www.fs-security.com/download.php]("http://www.fs-security.com/download.php")

Firestarter is the easiest way to go.

---

### Post by GuyW on 2006-07-22
Hi

does Firestarter just alter the iptables ?

The reason I ask is that I have set up a redirection in iptables to divert port 80 to port 8080 (to use Tomcat as a web server). So I am wondering if there will be some undesirable interaction going on. 

Particularly as I am setting the redirection by simply restoring iptables from the existing settings in /etc/network/interfaces like this:

pre-up iptables-restore < /etc/iptables.up.rules

Is there a better way of doing this ?

Guy

---

### Post by wieman01 on 2006-07-23
> **GuyW said:**
> Hi

does Firestarter just alter the iptables ?

Firestarter is making use of IP Tables, however, the rules are altered dynamically... You won't find the rules in the normal text files for IP Tables.

I have no experience with port diverting in connection with Firestarter. Sorry...

---

