---
title: "Aventail VPN"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by jackocleebrown on 2007-09-16
Hello,

I've been trying to connect to my company Aventail VPN from ubuntu at home for AGES now. Finally managed to do it! I have not found anyone else having the same problems as me and the breakthrough was actually mainly getting hold of the manual for the VPN so I knew what to try.... which gives you an idea of the level of IT help I got with this from work!!

So, in short, no How-To but please get in touch if you are having similar issues and I'll do my best to help.

Jack.

---

### Post by seanVT on 2007-10-10
> **jackocleebrown said:**
> Hello,

I've been trying to connect to my company Aventail VPN from ubuntu at home for AGES now. Finally managed to do it! I have not found anyone else having the same problems as me and the breakthrough was actually mainly getting hold of the manual for the VPN so I knew what to try.... which gives you an idea of the level of IT help I got with this from work!!

So, in short, no How-To but please get in touch if you are having similar issues and I'll do my best to help.

Jack.

Hi Jack,

Well I would love to know how to do this, so please help. What did you do to connect?

My job has had this for a couple of weeks, and connecting from Windows was a chore!

Now I'm trying to connect from Ubuntu, which is what I really want to do. I have Java installed and it should theoretically be able to connect with Firefox. But it craps out at the last step and connects me, but not with full network access, and a red exclamation point and an ill-defined "error".

I've been looking on the web for a browserless client. [This site]("https://access.llnl.gov/sslvpn_access/") links to something, but it seems to be a script for redhat.

So, do tell - what did you do to connect? Thanks.

--
Sean

---

### Post by jackocleebrown on 2007-10-11
Hi Sean,

I had exactly the same problem you describe. In the end I managed to find the standalone connection applet online which I had to modify slightly to get the install script to run (it sounds like this is the same problem that you are getting). It is pretty simple - you have to replace all the script interpreters with bash instead of sh, this includes all of the scripts in the actual program (which are in a compressed archive). I wonder if this is the same reason the on-demand version doesn't work.

 I kept a copy of the modded install files on my work laptop, unfortunately I've not got this to hand right now - I'll send you the program tomorrow. PM me an email address to send it to. Once installed the program ran as the windows connection client - the only thing to remember is you need to run it as root, it needs the permissions so it can create the VPN connection alongside the other network devices.

Anyhow, will send tomorrow.

Jack.

---

### Post by seanVT on 2007-10-11
> **jackocleebrown said:**
> Hi Sean,

I had exactly the same problem you describe. In the end I managed to find the standalone connection applet online which I had to modify slightly to get the install script to run (it sounds like this is the same problem that you are getting). It is pretty simple - you have to replace all the script interpreters with bash instead of sh, this includes all of the scripts in the actual program (which are in a compressed archive). I wonder if this is the same reason the on-demand version doesn't work.

 I kept a copy of the modded install files on my work laptop, unfortunately I've not got this to hand right now - I'll send you the program tomorrow. PM me an email address to send it to. Once installed the program ran as the windows connection client - the only thing to remember is you need to run it as root, it needs the permissions so it can create the VPN connection alongside the other network devices.

Anyhow, will send tomorrow.

Jack.

This sounds great, PMing now. Many Thankss!!!

---

### Post by Stenitel on 2007-11-29
Hello, I was wondering if one of you could direct me to the "browserless client" (presumably a small java application?) you refer to above.  I have exactly the same problem with an unhelpful error message and not getting the friendly "Full Network Access" flag.

TIA,

Frank

---

### Post by Calmor on 2008-03-06
Jack,

Do you still have the standalone connection script or browserless client for the Aventail VPN?  I'm new to Ubuntu and trying to get on the company network.

I've had the same web connection problems as many, in both Windows and Ubuntu, trying to use any browser other than Internet Explorer 6 (my IT department told us to avoid upgrading to IE7 as it would cause the web client to stop working).  

Thanks!

Jim

---

### Post by rossy65 on 2008-03-31
Jack,
  I too am having difficulty with Aventail in Firefox.  Firefox works fine in Windows with Aventail.   I'm not too surprised I'm having difficulty in linux, but I was hoping that the java applet they use to set up the VPN would work.  
  Can you email me the solution as well, or post a link where I can fetch it?
  I read about the sh to bash change... but in my case the Aventail applet is fetched from my companies web server via a https secure link when I log in... so I think it is more a Java VM issue.
   I'm copying my disk so I can run my old Windows native in VirtualBox... so this may be a non issue shortly.   It just takes a while to copy 60Mb with xcopy... sigh.
 -- Ross

---

### Post by jackocleebrown on 2008-04-11
Hi Ross,

Sure, am happy to help. Please send me a PM with an email address and I'll send you the install program and some instructions on how I got my connection to work.

Jack.

---

### Post by Almumin on 2008-06-20
> **jackocleebrown said:**
> Hi Ross,

Sure, am happy to help. Please send me a PM with an email address and I'll send you the install program and some instructions on how I got my connection to work.

Jack.

Hi Jack,

Another Avential VPN user here. Can you please send me that file? Here is my email [email]sbalmumin@gmail.com[/email]. I am trying to get it working on Ubuntu Hardy.

Almumin

---

