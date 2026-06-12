---
title: "Unable to connect to Amazon EC2 from home using Samba"
date: 2014-05-22
forum: Networking &amp; Wireless
---

### Post by Matthew_Canty on 2014-05-22
Hello all,

**Please note I have now forwarded this question [on to Ask Ubuntu]("http://askubuntu.com/questions/471189/unable-to-connect-to-amazon-ec2-from-home-using-samba") due to lack of response.**

I am trying to connect my laptop running Ubuntu 14.04 to a Samba share on EC2 instance running Ubuntu 13.10.

Things I have tried:


[LIST]
[*]Set inbound rules on EC2 to "All Traffic" for my home and work IP addresses.
[*]Connecting to Samba share from work PC running Windows 7 - works fine.
[*]Connecting to Samba share from work wifi on my laptop - works fine.
[*]SSH into EC2 instance from laptop at home - works fine, eliminating security group issues.
[*]Connecting to Samba share from home wifi on my laptop - [COLOR=#ff0000]DOES NOT WORK![/COLOR]
[/LIST]

Desired Action:
Type smb://<PUBLIC-DNS>/myshare into the search bit - don't know what it's called yet, when you press the 'windows' key on Ubuntu...

Result at home:
Error thrown  "Unhandled error message: Failed to mount Windows share. Connection timed out".

Result at work:
"myshare" directory opens.

Hope someone can help.

Thanks,
Matt

---

### Post by dannyboy79 on 2014-05-24
are you first connecting to a vpn? i wasn't aware samba worked over WAN.

---

