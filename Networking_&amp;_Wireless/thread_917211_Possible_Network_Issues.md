---
title: "Possible Network Issues?"
date: 2008-09-11
forum: Networking &amp; Wireless
---

### Post by mamweb on 2008-09-11
Hello, 

I have sort of a strange question... here goes:

I recently turned an old PC into a LAMP testing server. I installed Ubuntu 8.04 LTS Server Edition and selected the LAMP option during installation and set all of the network configurations to the same as the old XP  machine it replaced, and the only package I installed was PROFTPD. Everything else is default-- and it works like a dream. 
[B]
Here is the problem:[/B] 

When I notified our IT Department of the change to the operating system and this is the response I received from our IT Manager: 

[INDENT]"I just do not want this machine physically attached to our network since it could cause issues to the rest of the network an d organization."[/INDENT]

I thought this was rather vague so I asked for her to elaborate and her response was: 

[INDENT]"I can't have a testing server in a production environment, especially something that is not monitored by IT since we are responsible for the network." [/INDENT]

I was wondering if anyone has any idea what "issues" she might be talking about? Has anyone ever experienced abnormal network symptoms after setting up a Ubuntu server or could point me in the right direction to research possible "issues" that may occur?

Naturally I had the server running for a full day before I notified IT and there didn't appear to be any "issues". Does anyone know what she is talking about? 

Thanks, 
-M

---

### Post by stoneybroke on 2008-09-11
I think the problem with the IT Dept is she has no idea what Linux is or how it works and is a dedicated Windows IT user tell them you are using a Mac and they will probably say that's ok.

Seriously though I think the "issues" she could be referring to is a hacker being able to penetrate your computer and having free range over the entire network of computers on the network.

The setup you have now is certainly more secure than any windows network will ever be, even Google use apache on their system ISP's and other huge companies also use it. So I think you will have to educate them eh?

---

### Post by mamweb on 2008-09-11
Thanks for your response, I was thinking it is some sort of misunderstanding. 

Do you know of any documentation that I can pass along to help with the education process of our Windows IT department? I can tell you the Mac argument will not work very well as I have already barked up that tree...  

-M

---

### Post by Iowan on 2008-09-11
> **mamweb said:**
> ... especially something that is not monitored by IT since we are responsible for the network." Kinda sounds like "We don't know HOW to monitor it, so you can't have it."  Unfortunately, they're probably right - it is their network to regulate.

---

### Post by mamweb on 2008-09-11
You are correct, IT is in charge of regulating the network. 

But I think that is similar reasoning to an accountant who invents their own tax laws just because they are in charge of doing taxes... no?  

-M

---

### Post by dmizer on 2008-09-11
> **mamweb said:**
> But I think that is similar reasoning to an accountant who invents their own tax laws just because they are in charge of doing taxes... no?

No, it's not like that at all.

This is a tech who is responsible for the security of the network. Any unknown introduced into the network is a very real and potentially devastating security hazard.

---

### Post by bodhi.zazen on 2008-09-11
> **mamweb said:**
> I was wondering if anyone has any idea what "issues" she might be talking about? Has anyone ever experienced abnormal network symptoms after setting up a Ubuntu server or could point me in the right direction to research possible "issues" that may occur?

Well the issues are :

1. It is not your network, it is a private production network.

2. A production environment is no place for testing a new OS. If your box is compromised because you write sloppy php, or other code, the entire network is compromised.

3. Your IT department is responsible for maintaining the production environment.

**[size=2]Your test server belongs at home, not at work, and not on a production environment.**[/size]

Thread closed (the Ubuntu forums do not support activity on any work, school, government, or other private networks where the user does not have proper authorization from his or her IT department).

---

### Post by bab1 on 2008-09-11
I think the IT staff have a valid point.  They are in charge of maintaining a smooth running network.  I, as an administrator would not want any servers in my network not under my control.  If one allows rouge systems they are asking to get called on the carpet and the real potential of loosing their job.

> But I think that is similar reasoning to an accountant who invents their own tax laws just because they are in charge of doing taxes... no?
No new laws -- The boss says kept it running. It is my job to do just that.

Edit: As bodhi.zazen says test at home on your own network.

---

