---
title: "How Do I Know. ."
date: 2010-07-26
forum: New to Ubuntu
---

### Post by TortureQueen on 2010-07-26
Hi, all.  I have a question.  How do I know if my computer is as secure as it can be?  -I realize that the computer *user's* actions are key, and that a computer cannot be totally, 100% secure, but is there things I can do to see if my computer is secure as it can possibly be?  I'm running UNR and I have installed FireStarter Firewall.  I have heard of the ShieldsUp! test, etc, but all that happens is this:  Once I click the link, I receive a warning that the information I send is not encrypted and that others may be able to view the information.  If I click continue, the ShieldsUp notifies me that my system is vulnerable.  If I click cancel, then, well, nothing happens.  Sigh.  Perhaps I am being paranoid.  Many people say that spyware and malware for Linux OS distros do not exist.  I don't believe that--I have heard that there are indeed Linux viruses--but I would like to think that my running Linux leaves me less vulnerable to infections/attacks.  I have also heard that Linux systems cannot succumb to Windows viruses.  Sorry for the paranoid post, all.  But, I would just like to know.  I am particularly worried about spyware.  I'm not sure if I would be able to tell if my computer was infected, if it really did become infected with spyware.  All feedback is appreciated.  Thanks, guys.

---

### Post by collinp on 2010-07-26
The ShieldsUp! test is a load of trash.

The firestarter firewall is a GUI frontend to the iptables Linux firewall kernel module, which is one of the best that currently exists. So you're safe there.

Unless you're tunneling through an encrypted protocol (like ssh), or unless you're using https all the time, you can't be completely sure that someone isn't sniffing the packets you're sending over the internet. The likelihood that someone is, though, is pretty low.

There are Linux viruses, but unless you're running a kernel version from.. say, 2003? (which you're not if you're running Ubuntu), then you can be safe in the knowledge that there are no Linux viruses, as the security holes that they exploited were patched long ago.

---

### Post by pricetech on 2010-07-26
Actually, if Shields Up says your vulnerable, you are, at least in some fashion.

What you want to do it look closer at what ports are open or if your computer is responding to a ping.

Are you connected directly to the Internet (not good) or behind a router (much better) ??  If you're behind a router then what you're seeing is a scan of your router, not your computer.

---

### Post by jerenept on 2010-07-26
open System>Administration>Network Tools.

Now go to the tab that says "Port Scan"

type in 127.0.0.1 in the text entry field. 

Press enter. you will see 3 or 4 open ports. This appears to be normal.

---

### Post by marshmallow1304 on 2010-07-26
What exactly is Shields Up telling you?

---

### Post by TortureQueen on 2010-07-26
> **jerenept said:**
> open System>Administration>Network Tools.

Now go to the tab that says &quot;Port Scan&quot;

type in 127.0.0.1 in the text entry field. 

Press enter. you will see 3 or 4 open ports. This appears to be normal.

 After doing what you suggested, I found that there are two ports open.  I'm a little worried because one says "unknown." (The other says "ipp" under "service".)  Should I be worried about the unknown port?

---

### Post by TortureQueen on 2010-07-26
> **marshmallow1304 said:**
> What exactly is Shields Up telling you?

 After I click "continue," when it tells me that the information I am about to send may be viewable by others, the webpage says, "Without your knowledge, your computer may be offering some or all of your information to [others]," etc.  Do you know what I am talking about?

---

### Post by TortureQueen on 2010-07-26
> **pricetech said:**
> Actually, if Shields Up says your vulnerable, you are, at least in some fashion.

What you want to do it look closer at what ports are open or if your computer is responding to a ping.

Are you connected directly to the Internet (not good) or behind a router (much better) ??  If you're behind a router then what you're seeing is a scan of your router, not your computer.

 When I looked under the "Ping" tab, I didn't see anything listed in the box.  Is there another way to check if my computer is responding to a ping?

---

### Post by TortureQueen on 2010-07-26
> **collinp said:**
> The ShieldsUp! test is a load of trash.

The firestarter firewall is a GUI frontend to the iptables Linux firewall kernel module, which is one of the best that currently exists. So you're safe there.

Unless you're tunneling through an encrypted protocol (like ssh), or unless you're using https all the time, you can't be completely sure that someone isn't sniffing the packets you're sending over the internet. The likelihood that someone is, though, is pretty low.

There are Linux viruses, but unless you're running a kernel version from.. say, 2003? (which you're not if you're running Ubuntu), then you can be safe in the knowledge that there are no Linux viruses, as the security holes that they exploited were patched long ago.

 What I'm worried about the most is my banking and shopping.  Both my bank and the site I use to shop online use https.  I'm unfamiliar with encrypted protocol, so I'm going to do some reading on it.

---

