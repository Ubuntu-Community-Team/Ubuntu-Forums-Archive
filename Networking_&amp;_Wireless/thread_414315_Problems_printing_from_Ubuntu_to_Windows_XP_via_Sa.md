---
title: "Problems printing from Ubuntu to Windows XP via Samba"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by tsvim on 2007-04-19
Ok, this has been bugging me for quite some time. I'd appreciate some help.

I set up my Ubuntu box to connect to my windows station over my local network and to print using the attached HP Officejet 5510.
I managed getting it to send the print job to windows, where I can see the job appearing in my printers window. The printer starts grinding, the usual noises, and then ... silence.
Nothing happens the printer is stuck, deleting the print job from windows doesn't work unless I stop the print spooler etc.

I know it seems like a windows problem but I suspect something is wrong with the printer's driver. Note: from Win to win it prints perfectly fine, same goes for local. From Ubuntu's POV the job was sent successfully, it's just that once it's in the windows system, it's dead.

I'm completely clueless.
Either something in Windows or in Ubuntu must probably change to be able to print correctly. Please help.

---

### Post by tripolitan on 2007-04-20
assuming HP Officejet 5510 is supported, do sudo gedit, type a word and see if it prints it, I'm guessing permisions.

---

### Post by TheReaperD on 2007-04-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gs-esp/+bug/109205](https://bugs.launchpad.net/ubuntu/+source/gs-esp/+bug/109205) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've ran into what sounds like the same issue. I'm also using a HP OfficeJet 5510. I've submitted a bug report. Please take a look at the bug page for updates.

---

### Post by TheReaperD on 2007-04-24
Well, I got a humbling reply about my bug report (soon to be closed).  You have to turn off bidirectional support on the Windows box that the printer is attached to.  I did that and it printed just fine.

Instructions (on Windows XP)
1)  Start ->  Printers and Faxes
2)  Right-click on the printer in question
3)  Select "Properties"
4)  Click on "Ports" tab
5)  Remove check mark from "Enable bidirectional support"
6)  Click "Apply"

That should take care of the problem.

---

### Post by tsvim on 2007-04-25
This solution solved my problem as well.
Any idea what bidirectional support does?

In any case, I'm happy. I finally can print from my laptop using linux. One more reason less to log in on windows.

---

### Post by TheReaperD on 2007-04-25
According to [PC Magazine]("http://www.pcmag.com/encyclopedia_term/0,2542,t=bidirectional+printer&i=38594,00.asp"):

[I]
"Definition of: bidirectional printer

A printer that prints alternate lines from right to left." 
[/I]

---

### Post by epee on 2007-04-26
> **tsvim said:**
> Any idea what bidirectional support does?In this case it allows the printer to communicate back to the host. My Epson printer has it and when networked it causes problems. When printing Windows->Windows the remote host gets an error, but printing proceeds.

I'll be trying this 'fix' at home - see what gives.

---

### Post by sams2100 on 2007-05-06
The bi-directional thing fixed it for me as well.  I had an OfficeJet 4215.  I thought I remember the driver saying something about supporting bi directional, but it may only support that when the printer is connected locally.  Which local printing does work with bi-directional, just wont work over samba share.

---

### Post by kmoffat on 2007-05-13
Two million thank you's for the tip about turning off 
bi-directional support, which I have been trying to solve for days! 


ken

---

### Post by epee on 2007-05-14
Yup - that was how I got my printing working too.

---

### Post by Tryll on 2007-07-11
Thank you!  That fixed everything  :grin:

---

