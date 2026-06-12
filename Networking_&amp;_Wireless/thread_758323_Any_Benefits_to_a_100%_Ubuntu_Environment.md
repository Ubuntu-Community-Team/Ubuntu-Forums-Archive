---
title: "Any Benefits to a 100% Ubuntu Environment"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by SkydiverFL on 2008-04-17
WAS ASKED TO POST THIS HERE - SORRY FOR THE CROSS POST

Good afternoon,

Are there any benefits gained by moving a Windows environment to Unbutu or Linux in general? My biggest concerns are:

- internal user / department security to files & printers
- ease of deployment for updates and new software titles
- protecting laptops & workstations against user abuse

As our user base grows so do our headaches. Windows helps SOMEWHAT with several tasks, such as centralized patch management and GPO-based software deployment / access. Unfortunately, anything outside of the Microsoft world is up to us to maintain (unless we jump through hoops with things like WinINSTALL).

There are three major apps that worry me specifically:

- Microsoft Dynamics / Great Plains (we cannot get away from)
- Exchange 2007
- and, a custom Win32 modem-based program we use

Of these three, we are stuck with Dynamics / Great Plains. We will also need to keep Exchange 2007 around for the next few years. And, that third program is a "must have" for a few of the external devices we tie into.  However, those users can be isolated and are not my biggest concern.

I guess, in summary, I would like a more elegant way of managing the day-to-day operation while reducing our overhead. Most of our challenges are caused by end users.

Do we need to switch platforms? Of course not. At this point I'd just like some opinions on what one environment has over the other, from an administration standpoint, and if it would make sense to [ever] switch. 

Thanks,
Fred

---

### Post by LeoSolaris on 2008-04-17
Well, granted I am not a network administrator, but What I can say is that if you do not give the Users the sudo password, they cannot mess up the system. That by itself would save you a ton of headaches. The custom program you may be able to drum up yourself, and as for the other two holding you to the Windows Server, check to see if there are comparative Linux alternatives. Since Linux is mainly used as a server, chances are there will be some alternatives.

I wish you the best of luck!
Leo

P.S. I found this as a Linux alternative to Microsoft Dynamics [HERE]("http://www.osalt.com/sugarcrm")

And I found this for Exchange 2007 [HERE]("http://www.pcworld.com/article/id,143198-pg,1/article.html")

You're on your own for the custom one though!

---

### Post by SkydiverFL on 2008-04-17
I'm not so concerned about the applications.  I can give them Terminal Service access to Dynamics for now and Zimbra is more than adequate for an Exchange replacement.

My real questions are regarding day-to-day operations.  Users have general user permissions now so security is not a real issue.  I'm more curious about the features within Windows versus Ubuntu and if there are any benefits besides cost.

A nice feature of Windows is the ability to deploy applications using the GPO.  Just make the app available on the network, assign computers, and it's installed during the next reboot.

Things that would be helpful to us specifically are:

1. Complete auditing for all file activity (for example, knowing who deleted a file on the network);

2. The ability to push updates to the OS and applications without having to touch a workstation AND without each workstation having to update itself from a public Ubuntu repository (centralized patch management); and,

3. True roaming profiles... allowing a user's desktop, settings, etc. to follow them from one workstation to another.

These are just examples of the types of things that would be attractive.  I can technically DO all of these in Windows, but it's not very elegant... typical "square peg / round role" kinda stuff.  Also, I am not really concerned about JUST THESE.

I guess my real question is...

What are the benefits, if any, of a total Ubuntu environment (server and workstation) in an office setting?  What features would make life easier for the typical network administrative tasks.

I hope this helps.

Thanx,
Fred

P.S. I'm a .NET developer whom has inherited the networking responsibilities as well.  We don't have ANY issues that we need to overcome.  I'm just trying to reach out to find ways to improve beyond what we are currently doing.  I am passionate about Ubuntu, and Linux in general, but cannot switch our machines solely on personal likes or dislikes.

---

