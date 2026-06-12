---
title: "Server Email install, round two"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by zoon_unit on 2006-08-02
Okay, this absolute newbie is starting to get it together on email, but I've still got questions.

I have several development packages on my test ubuntu LAMP server that needs to send out emails to subscribers.  I need something lightweight.  I don't need the server to receive email, just send it.  I now know the term "MTA" or mail transport agent.

I now understand that sendmail can have security issues.  I searched the Synaptic package manager and found several MTA's including sendmail, courier, and exim.  None are currently installed on my LAMP package.

THE QUESTION:  Does anyone have suggestions as to what MTA to install?  I liked the fact that courier had a control panel app, but frankly, I know little or nothing about choosing and installing a server based email package.

Any suggestions?

Many thanks to those who have already replied to earlier messages.

---

### Post by tturrisi on 2006-08-02
I use exim on my Debian servers at home to send mail via php scripts & html forms.  I don't receive mail on these servers.  If your are in the US and have broadband connection then you will need to config your MTA to send via your isp SMTP server because most isps filter port 25 and do not allow email relays to combat spam on the isp network & keep bandwidth usage down. It's been a while since I setup those mail servers but I believe exim refers to this type of config as "Smarthost".
see this for some guidelines:
[http://wiki.archlinux.org/index.php/Exim_with_a_remote_SMTP_server](http://wiki.archlinux.org/index.php/Exim_with_a_remote_SMTP_server)

---

### Post by zoon_unit on 2006-08-02
That was just the information I needed!

---

### Post by tturrisi on 2006-08-02
post back success or fail...

---

