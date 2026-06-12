---
title: "Html redirect through firewall?"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by rmccabe3701 on 2008-10-13
Hi,

I started hosting my website on my work computer, but it is sitting behind a firewall that doesn't let http traffic through.  Pictorally, what I have is

remote_computer <----> work_firewall <----> work_computer

I also have a globally accessible website on "work_firewall" with URL something like:

```

http://work_firewall/~rmccabe2

```

I would like to open up a browser in "remote_computer" and enter 

```

http://work_firewall/~rmccabe2

```

and have it transparently redirect me to my webpage on "work_computer"

```

http://work_computer/~rmccabe2

```

I'm sure I need to do some combination of html redirection and ssh tunneling, but I am unsure on the details.
 
Any suggestions?

---

### Post by sonicb00m on 2008-10-13
Not sure if this will help but in shorewall you can make it run from a different port using

DNAT  net  net:192.168.0.100:3306  tcp      2255

This allows the mysql port on 3306 to work on port 2255.

This goes in the rules file.

Find the equivalent command for your work firewall

---

### Post by superprash2003 on 2008-10-13
do you have access to the work firewall?

---

### Post by rmccabe3701 on 2008-10-13
I can ssh into the firewall, but don't have root access.

---

### Post by rmccabe3701 on 2008-11-16
bump

---

### Post by kevdog on 2008-11-16
So let me get this straight

From remote computer -> work computer

You would like to ssh into work computer, and then redirect port 80 or simply setup a SOCKS proxy to tunnel your firefox connection through your work computer.

Is this the jist?

---

### Post by dmizer on 2008-11-16
> **rmccabe3701 said:**
> Hi,

I started hosting my website on my work computer, but it is sitting behind a firewall that doesn't let http traffic through.

Hello, it sounds to me as if you are attempting to bypass security for which you do not control.

Please contact the firewall administrator and request the port forwarded to your server.

Thank you.

---

