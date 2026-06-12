---
title: "Setup that completely replace Microsoft"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by isme_tze on 2009-07-13
Hi everyone,

This post is not really an Ubuntu related questions. The answer(s) should be able to apply to other Linux distributions easily. However, I will use Ubuntu as the main distribution because I like Ubuntu. 

This is my first post to ubuntuforums. Let me tell you about my-self first. My first Linux experience was in many many years ago. Do you know Coral Linux? I still have a box (CD and Manual) under the basement somewhere. I have try Red Hat, Coral, SUSE, Mandrake (or Mandriva), PuppyLinux, Knoppix, Fedora, Ubuntu, Kubuntu, and etc. throughout those years, and my favourite is still Ubuntu. I consider my-self still a newbie :(. Linux to me was a play around OS. My previous experience about Linux is usually begin with smooth installation &#8594; play around &#8594; encounter problem but don't know how to fix it &#8594; frustration &#8594; and end up re-format the hard disk. 

Even though my experience/skill with Linux wasn't good enough, but I do managed to setup Joomla on LAMP server (hosting Joomla and host 2 other testing web sites on the same server), DNS & DHCP Services on Ubuntu Server Version 6.06 (that is why I like Ubuntu). Ubuntu 9.04 does change my perspective recently as I can run it smoothly on my PC.

I am an administrator for an organisation that have 5 offices. We have 150+ computers/laptop/notebook, and additional of 2~3 servers for each site. We run mostly Microsoft product such as Windows 2003 Server, SMS 2003, SQL 2003, Project Server 2007, Office 2003, Exchange 2003, Windows XP and Vista, Blackberry Server, Backup Exec 11D and other windows based applications. Some of our user remote desktop to the server just to run the access database that was written 10~15 years ago. All sites are VPN connected (router based). Every PC is installed with Ultra-VNC. 

OK. if I would like to implementing Ubuntu into the organisation and slowly face out Microsoft products (I know this is big thing), can Linux replace Microsoft products completely? What about the following area?

1.Active directory? Any recommendation?
2.Single login? Like windows environment where you can login to any computer within the domain. How can I do this in Linux?
3.Roaming profile?
4.File and print sharing? And security setting as well.
5.Daily operation applications? Such as Microsoft office, access database application, and etc.?
6.Email and Microsoft outlook (especially the global address issue as I still cant get my to work)? 
7.Centralised systems management software like SMS 2003? 
8.Project management software that equivalent to Microsoft Project server?
9.Remote desktop to server?
10.VNC connection that allow me to troubleshoot remotely?
11.Administrative ability? How easy to administrate Linux environment? Windows based is mostly in GUI interface. I have not administrate large Linux environment before therefore I need to know.
12.And the important thing is whether what I am thinking an achievable target? 

I know this is hard. Should I apply the same concept/methodology in administrate Microsoft to Linux environment? Or does Linux have it own way of doing things? How hard is it to learn the new way (please take into consideration that I am a MCSE, DCSE, Network+, and some self-teaching ability)?

I will appreciate your help (and I do believe a lot of systems admin personnel who like to Linux would like to know as well). 

Regards
Tze

Ps. Sorry for bad English (English is my 4th language) :p

---

### Post by Ocxic on 2009-07-13
From my experience and what I've read and seen what you want to do should be possible with an all linux environment.

Administration is easy with ssh, and remote desktop/vnc. I would checkout [www.howtoforge.com]("http://www.howtoforge.com") they have a lot of tutorials on how to do most of the stuff that your trying to accomplish.

The only place i see you running into problems is with windows based apps like office/exchange, and the specific features that they offer.  you might want to look into a virtual environment that users could access from 
a central server to run a windows virtual machine remotely form a server for those specific features/applications.

From what i under stand Linux systems don't use domains like windows machines. As an alternative you could setup a remote server that users could login to and have there office computer act like a terminal, or you setup a script that would sync there home directory at login/logout, the latter most likely being the easiest. There are also many mail servers that you could use with Ubuntu, (ex: postfix) all available from the repos and some tutorials are on howtoforge.

I would also take a look into webmin a remote administration web based app that could help administer the various servers and computers you'll be administering.

The best part of all this is that once you setup one machine you should be able to ghost/copy the hard drive of one to all your other machines, making the initial setup much easier. There may be some final adjustments and tweaks needed for each machine. but it should go fairly smoothly for the most part.

P.S.  Your English is pretty good, I wouldn't worry.

---

### Post by lavezarez on 2009-07-13
I, too, would like to start to switch my 100+ desktop users to Ubuntu from Microsoft Windows.  Doing some practice at home, converting my home internet gateway to Ubuntu (from XP) has, however, given me some reality check on the challenges I would be facing.

Aside from the technical challenges you mentioned, I believe we also have to hurdle the "human" issue of getting things done. 
1. Managing change: getting a broad acceptance from our end-users to using Ubuntu desktops instead of what they've been used to for years - windows
2. Getting my IT staff to accept and learn new things in Linux

Perhaps if Ubuntu could get the best of what XP / Win 7 does with ease of installation, and user-friendliness in software design... that would be the day.  [B]

But I am optimistic.  Linux is getting closer :)
[/B]

---

### Post by IHeequ5i on 2009-07-13
People are wary of anything they don't understand. I'd start by getting your IT staff comfortable with Linux - set up a PC that they can "play" with. Come up with a Windows / Linux equivalents chart and post it next to that computer.

Once your staff gets grounded, then start rolling Linux out to your end-users. I'd recommend picking two or three of your most savvy users and starting with them. Use them as test subjects to iron out bugs. Then slowly add everyone else. It's definitely a long-term project.

---

### Post by lavezarez on 2009-07-13
thanks Doomspark, that sounds like a good plan :) the one thing i'm not really worried about is the support - with so many people willing to help other linux newbies like me.

isme_tze, for what its worth - the company I'm working for uses Microsoft Dynamics Great Plains as a mission-critical ERP app.  about half of the user base connect via RDP with our Microsoft terminal services for that app, along with MS-Excel and Crystal Reports.

using Ubuntu's Terminal Server Client, I was able to connect to the server and run those apps just as they do it with their Win XP machines.

---

### Post by R_U_Q_R_U on 2009-07-13
> **lavezarez said:**
> I, too, would like to start to switch my 100+ desktop users to Ubuntu from Microsoft Windows.  Doing some practice at home, converting my home internet gateway to Ubuntu (from XP) has, however, given me some reality check on the challenges I would be facing.[B]..
[/B]

Just curious:

1. Is the reason you want to do this political, economic or for effectiveness/efficiency?

2. Have you done any estimates on training costs involved in switching 100+ users to a new environment?

2a. Have you done any estimates on the total cost to migrate from one environment to Ubuntu including down time, lost productivity and so forth? 

3. Have you developed a marketing pitch to these 100+ users as to what benefits they will receive from making a switch from an environment in which they are effective and efficient to one that is new and has an unknown learning curve? 

Are you the technical person or the boss? If you are not the boss how will you sell this in monetary terms?

I love using Ubuntu but I am not sure this is anything like a trivial switch or something management will buy.

Remember the old saying: "No one ever got fired for buying Microsoft" :p

---

### Post by t0p on 2009-07-13
> **lavezarez said:**
> 
Perhaps if Ubuntu could get the best of what XP / Win 7 does with ease of installation, and user-friendliness in software design... that would be the day

The user interface of some Linux apps isn't so hot.  But how is Windows software installation easier than in Ubuntu?  Open Synaptic, search for program, select to install program, click Apply... where's the difficulty in that?  It's *different* from the Windows installation model, but different doesn't necessarily mean *harder*.  If you ask me, I reckon the repository system is much easier to use than the Windows system.  No searching the internet for suitable software, just open Synaptic and you're off.  Wonderful.

The prejudice you're exhibiting here is the same prejudice you're going to have to deal with in your colleagues before you have any chance of migrating your work systems to Ubuntu.  Like you, your colleagues will equate "different" with "harder".  Your IT staff in particular will find it hard to accept that all their prior experience with Microsoft systems is no longer relevant, that they have to start from scratch.  It's a hard one, but if you can overcome it you are halfway there.

Just keep repeating: ***Linux is not* harder *than Windows.  It's just* different...**

---

### Post by kwacka on 2009-07-13
Whilst you're still at the planning/development stage how about installing some of the open source 'equivalents' - e.g. OpenOffice, on Windows computers?

---

### Post by Mark Phelps on 2009-07-13
> **isme_tze said:**
>  ... can Linux replace Microsoft products completely? 
Yeah, I KNOW that some will flame me bigtime for saying this, but really, the answer is NO -- not "completely".  While it IS true that virtually everything you do in an MS Windows app can be done using Linux apps, but that breaks down when you get into the details. So, basically, the more you depend on details of MS apps, the less likely a migration to Linux is going to be successful.

Also, and really more important, is why you're switching your users in the first place. Some "learning" is going to be necessary; some minor details of functionality are likely to be lost or different.  While you may (and are likely to) think of learning how to do your same job very differently to be fun and exciting, it's highly unlikely that your users are going to feel the same way.

If this was just switching from MS Office to Open Office, that would be one degree of transition, but when you throw MS Exchange (and all the embedded Outlook functionality) and Active Directory and Domains into the works, you're also taking great risks that you end up in a new environment where some of the IT stuff simply no longer works anymore.  But that's your problem.

What concerns me more is that if they are happy using their current apps (I know, BIG presumption), why are you forcing them all to learn new ways to do their jobs simply because you want to experiment with Linux?  

If you REALLY want this switch to work, a better approach would be to recruit one or two folks from your users who could server as champions for the change.  Once you get them up and working, THEY can show everyone else how much better it is, and then, the switch over for the rest of them, it will be much less painful.

---

### Post by HermanAB on 2009-07-13
You need to set up a couple of test machines in your lab.

The first hurdle to pass is getting Active Directory authentication to work properly.  You can use Samba Winbind.  It works.

The next hurdle is remote administration.  You can either mount the user home and usr directories over NFS on a central server, or you can use Parallel SSH (my favourite).

The third hurdle is to figure out how to roll out new machines easily.  You can either duplicate disks, or you can use Redhat Kickstart (it works with Ubuntu too).

Only after solving the above, should you move on to the applications.  Here, I would look at the organization and identify a group of users that use a very simple set of applications.  You may find them in shipping/receiving of a typical organization.  You can then add more applications to the this base and work your way up the corporate ladder.

Eventually, you will find a small group of users that simply cannot be served with Linux only.  You can either leave them on Windows, or you can provide a Windows terminal server that they can use from their Linux desktops.

---

### Post by isme_tze on 2009-07-13
Wow! Thanks guys for all the responses. I didn't expect such a great responses in less than 24 hours. You all nerd are so helpful.

OK. the reasons that I am posting this question is:-
1.Our current computer is average of 4-5 years old. XP is the OS that run &#8220;OK&#8221; on this machines. I need to plan ahead, I need to sort-of come up a plan for the future. Should I still stick with Microsoft product (I have tried windows 7 and I like it, I don't like Vista) which I will need to buy/upgrade all the hardware? Or can I use Linux and keep the current hardware setting? Purchasing 100+ new PC will cost &#8220;A LOT&#8221; to the company. I know some one will say &#8220;don't purchase those PC in one lot. Spread out the purchasing phase in the time frame of 2~3 years&#8221;, but the end of the day, it is will cost &#8220;that much&#8221; to the company.
2.Our finance controler (My BOSS :twisted:) did hint me (am I too sensitive? I believe I should get my-self prepare \\:D/) that &#8220;it will be good to reduce some expenditure&#8221;. I knew that Microsoft recommend &#8220;License installed on each computer should expire ALONG WITH that computer&#8221;. Therefore, I will need to pay 100+ licenses if I really need to purchase 100+ new PC. 

For me as an IT guy and as an end-user, I am not going to worry about end-user at the moment. I know user is the most problematic issue in any IT changes (should I said changes in the organisation), however, I will not need to worry about user at the moment until I get the technical right. Like what you guys have suggested, I will setup a testing environment and chose 2~3 user for testing it if I decided to implement Linux. But at the moment, lets not worry about it. Allow me to get the RIGHT answer whether should I phase-out Microsoft product completely and slowly.

Like what I said before, I want to find out more about whether I can switch to Linux completely. If the answer is yes, what is the big picture look like especially in the Active directory setup. There is a lot of help on Linux on the net for different subjects. What I really need is the more complete picture on how everything work together.

Thanks guys for all your help in advance.

Tze

Lavezarez &#8230; if most of your user just required to RDP to server and run the application, ThinStation is a good choice. It can even run on a 486. I have a few stations setup for our accountant. It work perfectly as long as that user don't want/need to use audio (such as youtube, or some training flash have sound incorporated).

Doomspark &#8230; Windows / Linux equivalents chart is a good idea.

R_U_Q_R_U &#8230; Thanks for point out such a important question in regards to the &#8220;reason of change&#8221;. Those question will definitely help me in the future.

t0p &#8230; seem like you know what you are talking. Can you please me with my first post? I have no problem in using Linux as a desktop. I need help in the BIG PICTURE of the entire setup in the organisation. Any help would be much appreciated.

kwacka &#8230; I am doing it now. However I do have some issues in OpenOffice such as the SpreadSheet cant have dotted line, Evolution have problem in synchronise the global address list with Microsoft Exchange, and etc.

Mark Phelps &#8230; Thanks for point out your view. I believe you have just expressed how hard it will be to do a complete switching between two environment.

---

### Post by R_U_Q_R_U on 2009-07-14
> **isme_tze said:**
> Wow! Thanks guys for all the responses. I didn't expect such a great responses in less than 24 hours. You all nerd are so helpful.


Good luck with your migration. PLEASE post back on how it goes so others can learn from your experience.

---

### Post by isme_tze on 2009-07-14
any more help? anyone? ](*,)

---

### Post by Mark Phelps on 2009-07-15
One more suggestion ... which I didn't make before because I didn't catch that you were already trying Windows 7.

As an experiment, I loaded Windows 7 onto a 4-year-old Tablet PC, a box that did NOT come with Vista and was a complete nightmare to upgrade -- since the vendor supplied NO Vista drivers for that make and model.

And, surprise, surprise!  I was able to load ALL the XP-era drivers in compatibility mode and get ALL of them to work -- without any problems whatsoever!!  This "old" tablet PC now actually works a LOT better under Seven than it ever did under Vista.

I was expecting nearly nothing to work (given the age of all the hardware on the box).  So, my message is, that you might not have to upgrade as much hardware as you think.  Presuming you have a test box running Seven, try installing XP drivers in compatibility mode and see how well they work.  You might be pleasantly surprised.  If they do work, that gives you a short-term migration path to Seven while you still work on a longer-term solution of migrating folks away from MS Windows.

Good luck to you either way.

---

### Post by namdung on 2009-08-17
> **isme_tze said:**
> Hi everyone,

This post is not really an Ubuntu related questions. The answer(s) should be able to apply to other Linux distributions easily. However, I will use Ubuntu as the main distribution because I like Ubuntu. 

This is my first post to ubuntuforums. Let me tell you about my-self first. My first Linux experience was in many many years ago. Do you know Coral Linux? I still have a box (CD and Manual) under the basement somewhere. I have try Red Hat, Coral, SUSE, Mandrake (or Mandriva), PuppyLinux, Knoppix, Fedora, Ubuntu, Kubuntu, and etc. throughout those years, and my favourite is still Ubuntu. I consider my-self still a newbie :(. Linux to me was a play around OS. My previous experience about Linux is usually begin with smooth installation &#8594; play around &#8594; encounter problem but don't know how to fix it &#8594; frustration &#8594; and end up re-format the hard disk. 

Even though my experience/skill with Linux wasn't good enough, but I do managed to setup Joomla on LAMP server (hosting Joomla and host 2 other testing web sites on the same server), DNS & DHCP Services on Ubuntu Server Version 6.06 (that is why I like Ubuntu). Ubuntu 9.04 does change my perspective recently as I can run it smoothly on my PC.

I am an administrator for an organisation that have 5 offices. We have 150+ computers/laptop/notebook, and additional of 2~3 servers for each site. We run mostly Microsoft product such as Windows 2003 Server, SMS 2003, SQL 2003, Project Server 2007, Office 2003, Exchange 2003, Windows XP and Vista, Blackberry Server, Backup Exec 11D and other windows based applications. Some of our user remote desktop to the server just to run the access database that was written 10~15 years ago. All sites are VPN connected (router based). Every PC is installed with Ultra-VNC. 

OK. if I would like to implementing Ubuntu into the organisation and slowly face out Microsoft products (I know this is big thing), can Linux replace Microsoft products completely? What about the following area?

1.Active directory? Any recommendation?
2.Single login? Like windows environment where you can login to any computer within the domain. How can I do this in Linux?
3.Roaming profile?
4.File and print sharing? And security setting as well.
5.Daily operation applications? Such as Microsoft office, access database application, and etc.?
6.Email and Microsoft outlook (especially the global address issue as I still cant get my to work)? 
7.Centralised systems management software like SMS 2003? 
8.Project management software that equivalent to Microsoft Project server?
9.Remote desktop to server?
10.VNC connection that allow me to troubleshoot remotely?
11.Administrative ability? How easy to administrate Linux environment? Windows based is mostly in GUI interface. I have not administrate large Linux environment before therefore I need to know.
12.And the important thing is whether what I am thinking an achievable target? 

I know this is hard. Should I apply the same concept/methodology in administrate Microsoft to Linux environment? Or does Linux have it own way of doing things? How hard is it to learn the new way (please take into consideration that I am a MCSE, DCSE, Network+, and some self-teaching ability)?

I will appreciate your help (and I do believe a lot of systems admin personnel who like to Linux would like to know as well). 

Regards
Tze

Ps. Sorry for bad English (English is my 4th language) :p


Pls consider the following:

1 & 2 : LDAP - OpenLDAP [http://www.openldap.org/](http://www.openldap.org/)
3 : NFS, LTSP, Cloud Computing - depending on your requirements
4 : Samba, CUPS built in with Ubuntu. For security at Network level try FOSS UTM like Untangle, Endian, Pfsense etc. No antivirus required for individual workstations.
5 : OpenOffice.
6 : Evolution. 
7 : apt-mirror for centralised Update System. Canonical also provides commercial Landscape for Ubuntu centralised management.
8 : Many FOSS Project Management Software available.
9 : VNC
10 : Many VNCs version available. However, you might want to try SSH, ClusterSSH.
11 : Most Linux administration is now GUI. But knowing the terminal is an added advantage which is not at all difficult.
12 : It is definitely an achievable target. 

Keep posting any specific issues here. Good luck.

---

### Post by mrbiggbrain on 2009-08-17
> **lavezarez said:**
> I, too, would like to start to switch my 100+ desktop users to Ubuntu from Microsoft Windows.  Doing some practice at home, converting my home internet gateway to Ubuntu (from XP) has, however, given me some reality check on the challenges I would be facing.

Aside from the technical challenges you mentioned, I believe we also have to hurdle the "human" issue of getting things done. 
1. Managing change: getting a broad acceptance from our end-users to using Ubuntu desktops instead of what they've been used to for years - windows
2. Getting my IT staff to accept and learn new things in Linux

Perhaps if Ubuntu could get the best of what XP / Win 7 does with ease of installation, and user-friendliness in software design... that would be the day.  [B]

But I am optimistic.  Linux is getting closer :)
[/B]

Honestly, i believe for every day use, linux is much easier then windows, and its not just me, my parents, friends, grandparents, all have had one of my live cd's in there drives, or used my laptop running ubuntu.

For a non computer literate person installing windows xp, then drivers, then finding and installing office, an im program, and all the other things they need is a huge task, and as a computer tech i see the results of that task a lot. with ubuntu it all just comes, out of the box, working.

Installing a program on windows involves going around the web looking for it, or going to a store and asking 10,000 questions just to get some software, then manually installing it. with ubuntu its all a simple "sudo apt-get install" away.

I could list hundreds of things that linux does better, faster, or with fewer clicks then windows, ranging from the simple, to the complex.

---

### Post by lavezarez on 2010-04-17
> 1. Is the reason you want to do this political, economic or for effectiveness/efficiency? 
a) Economic - license costs for Windows OS, and extra licenses for antivirus, other security software that would not be needed in Linux
b) Effectiveness - yes, tighter security and control over what applications are in the desktop

> 2. Have you done any estimates on training costs involved in switching 100+ users to a new environment?

Yes, I have.  Outsourced training for Linux Debian systems administration is a must.  Ubuntu desktop training, we can do in-house, conducted by the IT staff.  

> 2a. Have you done any estimates on the total cost to migrate from one environment to Ubuntu including down time, lost productivity and so forth? 
Downtime should be minimal, with migrations done during offpeak hours.  I would have to still compute on the total manhours per desktop needed, and charge this to an overtime rate to get the cots. Lost productivity is a bit harder to measure... 

> 3. Have you developed a marketing pitch to these 100+ users as to what benefits they will receive from making a switch from an environment in which they are effective and efficient to one that is new and has an unknown learning curve? 
The marketing pitch I'm using is not really to the 100+, but to the influencers and some key power users.  Small steps but I'm getting there.  I wrote this post a year ago, and now that the Lucid LTS is coming out, I feel this is the Ubuntu Year for us.
One strategy is to change the apps first, before the OS, e.g. From Excel to OO Calc.

> Are you the technical person or the boss? If you are not the boss how will you sell this in monetary terms?
Technical, here.  It's all about relationships and credibility. It's easy to sell the idea also if you show them that you are actually using it.  I've installed Ubuntu 9.10 and have used it full-time for 2 months now at work, making the Windows ERP run in my Ubuntu box, printing, substituting Ms Office with go-OO (and getting 1 million rows, at that).

---

### Post by skyeric on 2010-04-17
> **isme_tze said:**
> 
Ps. Sorry for bad English (English is my 4th language) :p


blown away

---

### Post by quadproc on 2010-04-17
> **isme_tze said:**
> any more help? anyone? ](*,)
Just one thought that may be useful in selling the transition to your management: Microsoft systems have a lot of hidden costs while Ubuntu has smaller hidden costs.  These hidden costs include things such as virus recovery, antivirus software, installation (and removal and reinstallation) of antivirus software, being forced to change the way that your users do things when a new Windows version is installed, and so forth.

The registry is effectively a collection of thousands of global variables.  Why subject yourself to the problems associated with that if you don't have to?

quadproc

---

