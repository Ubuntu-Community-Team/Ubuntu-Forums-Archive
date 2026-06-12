---
title: "Running Windows and Office XP on Ubuntu 10.10 LTSP"
date: 2011-01-31
forum: New to Ubuntu
---

### Post by alexkim on 2011-01-31
Hi Guys,

Okay, this is the story. I want to setup LTSP on an Ubuntu 10.10 (I know how to to do this). However, I want the thin clients to boot to a Windows XP desktop environment upon booting up and run the necessary office suites from there.

I was thinking that I will have to use VMWare Server or Player for this setup.

But somewhere in my mind, how to go about implementing this solution is all muddled up.

There will be between 15 to 20 pure diskless thin clients connecting to the server via their NICs.

I guess what I am saying is that based on the above, how do I go about setting up an applications server dishing out MS Office 2003 / 2007 apps from the Ubuntu LTSP to the thin clients upon boot up.

Also, any ideas on what sort of licencing issues I will be dealing with?

I am pretty comfortable editing Ubuntu system files using Kate.

I have all the hardware to implement this solution. So hardware is not as issue. Can go up to 16GB RAM and SCSI 73GBHD RAID 10 with 2 X Dual core 3.2GHz Xeon CPUs - if I have to. (Just thought to mention this upfront so it does not get disscussed)

I am grateful for how-tos from you guys.

Cheers

Alex

---

### Post by Mark Phelps on 2011-02-01
You did ask about licensing issues, so with MS SW, the licensing is very simple -- one license per machine.

It's not legal to have a single licensed copy of MS Windows or MS Office and "dish them out" to multiple machines.

While that IS done in some enterprise/corporate environments, they can do that because they purchase Site licenses or multiple instance licenses.

What you're doing is trying to avoid the cost of purchasing a license to run Windows and/or Office on each box -- and that is violation of consumer licensing agreements.

---

### Post by alexkim on 2011-02-01
Thanks Mark, wasn't looking to avoid licence issues. Was more interested on how to do this if it is all doable. Thanks all the same. Cheers. Alex

---

### Post by Mark Phelps on 2011-02-01
I know that it IS doable ... some organizations do this to prevent having to install apps on local machines ... but the licensing costs are prohibitive!  I think, from what I read, you must purchase a license for a minimum of 25 "seats" in order to acquire the version that allows this to be done.

So ... 25 copies of MS Office 2010 at $200 (approx) a copy ... that's a LOT of money!

---

### Post by bodhi.zazen on 2011-02-01
I would use Openoffice.

What features do you need that are lacking in Openoffice ?

---

### Post by alexkim on 2011-02-02
Cheers guys. 

What I am looking for is an implementaion of - LTSP on an Ubuntu 10.10 with one or more thin clients booting to a  Windows XP desktop environment and running the necessary  office suites from there.

I.e how to go about  setting up an applications server dishing out MS Office 2003 / 2007 apps  from an Ubuntu LTSP to thin clients upon boot up.

I need help with the how tos. Can this be done?

Cheers

Alex

---

### Post by bizz101 on 2011-02-02
I was thinking the same 1 year ago. In the end I decided it's best to switch from MS to OpenOffice and avoid any licensing issues. I thought it would take months for people to adjust but it only took few days. 

I did it with Ubuntu and with NX server - clients login onto Ubuntu desktop. It's simple to setup and free. Also if I remember I think theres a site where you can build thin client isos online I cant remember its name - search thinclient iso. I build by myself now.

I tried to do it with XP, but was never satisfied with rdesktop. NX + Ubuntu is perfect. Actually I'm writing this from thinclient right now. :)

---

### Post by Mark Phelps on 2011-02-02
> **alexkim said:**
> I need help with the how tos. Can this be done?

Already answered -- reread my post #4.  You have $5000 lying around to try it out?

The only way to avoid the licensing issue (and costs!) is to avoid using MS software in the first place.

The replies you're going to get in this forum, if you keep asking this same question again and again are also going to be the same -- use OpenOffice instead of MS Office.

Folks here are NOT going to assist you in sidestepping the licensing issue with MS Software.  That's illegal and is against the rules in the forum Rules of Conduct.

So, either fork out the money for your MS-based solution, or bite the bullet and switch over to an open-source solution.  There really is no third alternative.

---

### Post by alexkim on 2011-02-02
Cheers. Lets leave the licence issue out of it for now.

What I'd like to know is - Is this doable?

Lets even say for a one user / home user project - you have the product, you have the licence.

You know? One of those things you think about and you go "whaoa that will be cool". 

You fire up the thin client, you connect via LTSP, you get WXP deskstop.

One of those pet projects that take up your weekend.

I was thinking 

1. Load Ubuntu 10.10
2. Sort out LTSP
3. Run VMWare Server
4. Install XP Virtual Appliance,
4. Install Openoffice on the XP VA

Then what?  This is where I get stuck in my though process.

How to?

Cheers

---

### Post by alexkim on 2011-02-02
Sorry.

I mean how do you get the thin client to the XP VA running on the VMWare Server

---

### Post by bodhi.zazen on 2011-02-02
> **Mark Phelps said:**
> The only way to avoid the licensing issue (and costs!) is to avoid using MS software in the first place.

The replies you're going to get in this forum, if you keep asking this same question again and again are also going to be the same -- use OpenOffice instead of MS Office.

Folks here are NOT going to assist you in sidestepping the licensing issue with MS Software.  That's illegal and is against the rules in the forum Rules of Conduct.

This ^^

I will remind you, this is an Ubuntu Forms and you are asking for support on a Microsoft Product.

We will assist with Ubuntu / OpenOffice.

For VMWare support -> Use the VMWare forums.

For Microsoft support -> Use Microsoft.

With that I will close this thread as your question has been asked and answered.

If you need support for Ubuntu or OpenOffice, start a new thread and please stay on topic.

---

