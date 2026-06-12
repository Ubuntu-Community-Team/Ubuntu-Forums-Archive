---
title: "E-Mail Problem ?"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by Jancarel on 2009-06-25
Dear Ubuntu Friends,

Since four weeks I have a strange problem with my E-Mail. I am using Thunderbird mail program. I have two computers connected to the Internet. One MAC and one Ubuntu computer. Up till four weeks ago, everything worked fine. Then, overnight, I have a problem sending mails on both computers. Receiving works fine. About one third of my mails go out normally. With two thirds of the mails, I get the failure message "Not Able To Connect To SMTP Server..." I have checked the Server Settings, everything is OK. I contacted my provider but they assured me that there was nothing wrong on their side. "It must be your computer..." I cannot understand how two, completely different computers, have the same problem. Nothing was changed in the setup of both computers. For my provider the case is closed. The problem is not on their side. Any ideas would be appreciated...

Thanks,

Jan

---

### Post by thane1 on 2009-06-25
Hard to tell without more info.  Could it possibly be a problem with a router or a firewall program, if either/both are in use?

---

### Post by halitech on 2009-06-25
open a terminal and see if you can connect via telnet
```
telnet mailserver 25
```
change "mailserver" to whatever your outgoing mail server is

---

### Post by Paddy Landau on 2009-06-25
Can you spot any pattern with the emails sent and the emails rejected?

Visit a friend, using a different computer and Internet connection, set up an account on his computer, and see what happens. Do some of the emails still fail? If so, it's nothing to do with the computer.

I must say that in my experience, that type of message has nothing to do with the computer and everything to do with the SMTP host. It used to happen a lot with my previous web host that had gradually become slow and unreliable. When I switched the host, the problem was solved.

Good luck in finding the problem!

---

### Post by Jancarel on 2009-06-25
> **thane1 said:**
> Hard to tell without more info.  Could it possibly be a problem with a router or a firewall program, if either/both are in use?

I have a combined Firewall/Router. I have tried it without, no change. I have installed a new one, no change...

---

### Post by Jancarel on 2009-06-25
> **Paddy Landau said:**
> Can you spot any pattern with the emails sent and the emails rejected?

Visit a friend, using a different computer and Internet connection, set up an account on his computer, and see what happens. Do some of the emails still fail? If so, it's nothing to do with the computer.

I must say that in my experience, that type of message has nothing to do with the computer and everything to do with the SMTP host. It used to happen a lot with my previous web host that had gradually become slow and unreliable. When I switched the host, the problem was solved.

Good luck in finding the problem!

My friend tells me that, since four weeks, all my mails to him end up in his Junk mailbox. This was not the case before this problem showed up...

---

### Post by Jancarel on 2009-06-25
> **halitech said:**
> open a terminal and see if you can connect via telnet
```
telnet mailserver 25
```
change "mailserver" to whatever your outgoing mail server is

I will try this tonight...

---

### Post by halitech on 2009-06-25
I missed the fact that some are going out properly. It might be a DNS issue where for some reason the mail server IP address cannot be determined, the other option is as Paddy says, an over worked mail server on the ISP side. Can you set up an account with google and use their outgoing mail server?

---

### Post by Repus on 2009-06-25
Random list off the top of my head. Sorry no solutions just possibilities to consider

[LIST]
[*]slow connection? you could be timing out
[*]your isp could have implemented new relay protections 
[*]you could be compromised and your sending a lot more traffic then you realize
[*]you could be fortunate and your new isp provided dhcp IP was previously assigned to a user that had a zombie on their system resulting in all kinds of blacklisting of the ip.
[/LIST]

if the information you provided is all there is we can narrow down to a couple possibilities.
[LIST]
[*]its your ip
[*]its your connection (fw router included)
[*]its your provider
[*]its your providers mail server
[*]its something not listed here at all and you may as will give up computers are evil. Consider taking up the life of a cave hermit. I hear its not all bad
[/LIST]

I would be curious to know what your friend uses that drops your mail into junk.

---

### Post by Jancarel on 2009-06-26
> **halitech said:**
> open a terminal and see if you can connect via telnet
```
telnet mailserver 25
```
change "mailserver" to whatever your outgoing mail server is

Yes Sir, this works fine. What does this proove...

---

### Post by Jancarel on 2009-06-26
> **Repus said:**
> Random list off the top of my head. Sorry no solutions just possibilities to consider

[LIST]
[*]slow connection? you could be timing out
I connect to the Internet via cable...

[*]your isp could have implemented new relay protections 
Maybe, how do I know this...

[*]you could be compromised and your sending a lot more traffic then you realize
How can I see this...

[*]you could be fortunate and your new isp provided dhcp IP was previously assigned to a user that had a zombie on their system resulting in all kinds of blacklisting of the ip.
[/LIST]

if the information you provided is all there is we can narrow down to a couple possibilities.
[LIST]
[*]its your ip
Could be...

[*]its your connection (fw router included)
No, I have tried it without FW/Router, same results...

[*]its your provider
This is what I think...

[*]its your providers mail server
This could be it as well...

[*]its something not listed here at all and you may as will give up computers are evil. Consider taking up the life of a cave hermit. I hear its not all bad
I hope not...
[/LIST]

I would be curious to know what your friend uses that drops your mail into junk.

Don't know, but I will find out...

---

