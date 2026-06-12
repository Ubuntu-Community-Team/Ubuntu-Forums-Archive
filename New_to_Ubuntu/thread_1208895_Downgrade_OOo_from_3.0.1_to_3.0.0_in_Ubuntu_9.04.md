---
title: "Downgrade OOo from 3.0.1 to 3.0.0 in Ubuntu 9.04"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by dkbk on 2009-07-09
Hi all

This seemed like the most appropriate place to post.

We're going to be doing an Ubuntu rollout where I work to replace some XP machines.

However, OOo 3.0.1 (and 3.1) has bugs in writer tables that are not present in 3.0.0 and that are a showstopper for us.

As such, I'd like to downgrade to 3.0.0 but, obviously, 3.0.0 is not in the package manager (and can't be found on the OOo website either).

From reading around the net, I was under the impression that the 9.04 beta shipped with the 3.0.0 version.  Is there any way I could get the sources list from the beta to try and get that version going ?

Or is there any other way to acquire the old version and downgrade the OOo version ?

Thanks.

PS : This subforum seemed like the most suitable place to post this in, please feel free to move this as required.

---

### Post by Sef on 2009-07-09
Moved to Absolute Beginners.

---

### Post by phillw on 2009-07-09
[SIZE=2][FONT=Arial]Hi ..

I've had a hunt round, and unless you want to compile from source, I can't find it either !!

May I suggest you post a request on

[http://user.services.openoffice.org/en/forum/](http://user.services.openoffice.org/en/forum/)

I am sure one of the people on there will assist you.

Sorry I can't be of more help :-\


Phill.
[/FONT][/SIZE]

---

### Post by RedRat on 2009-07-09
While I don't want to rain on the 9.04 parade, since you are doing this in the workplace, I would suggest that you might want to go with 8.04 LTS. This version has been designated for long term support and has been worked on for quite sometime. Most of the bugs have been found and corrected. 9.04 and the upcoming 9.10 are quite new and are the forerunners of what the next long term support edition of Ubuntu (maybe 10.04 or 10.10, perhaps even 11.04 or 11.10). 

They seem to be getting many of the glitches out of 9.04, I have seen enough both here and in the newsgroups that indicate that it is not quite ready for prime time in an office setting. Sometimes it is better to be a bit conservative and sit back and wait while all those who want to push the envelope crash and burn. Businesses usually do not like to do that.

---

### Post by yeats on 2009-07-09
I'll add a vote for the Hardy Heron and mention that installing OOo3 in Hardy via a .deb downloaded from the website is quite straightforward.

---

### Post by dkbk on 2009-07-17
Thanks for everybody's reply.

I was consumed with setting up our zimbra mailserver so I had left this issue slide to the wayside somewhat.  I'm happy to say its now working flawlessly on that end with Centos.

As for my OOo issue, I found sites today which mentioned the filename of the distribution : OOo_3.0.0_LinuxIntel_install_en-US_deb.tar.gz

From there on I could do a google search for the exact name and ended up finding an old russian mirror who still had the files.  I got the files since the md5 matched with the official OOo website.

I also found out the downloaded version of OOo is going to crash if ubuntu's OOo has been run on the account.  So I just created a new account and deleted the old one and that solved it.

As for the advice about using the LTS, I actually considered it long and hard and had the version available been 8.10 instead of 9.04, I probably would have went with it but since the end support period is 6 months apart and there has been many "improvements" added since the LTS, that was my decision. And apart from the version of OOo, everything else went fairly smoothly.

There are however 3 issues I still have :

1) We use rdekstop to RDP into our order system.  The version that comes with 9.04 seems to have a bug in it with the cf keyboard layout : the numpad and delete/home/etc keys do not work.  If I leave it at default or US, it does the default US key + my ubuntu key (cf) with the same keystroke - mostly accents issues.  That's obviously a bit of an issue but still workable since most text is in english hence has no accents.  Is that a new issue in the 9.04 version of rdesktop ?

2) We use relayfax fax server on our windows box and we get tiff faxes e-mailed to each user through OCR decoding.  evince works great for viewing these but some faxes from certain specific customer print with the top part cut off and toying with the print settings in evince seems to have no effect.  Is that a known issue again ?

3) I want to share this computer's printer as easily as possible with our server (win 2003).  What's the simplest way to do so ?  Can CUPS alone do that or do I need Samba ?  At this point, with only cups printer sharing, the windows box can't see the ubuntu one so I don't know how to proceed and every tutorial I've seen seems fairly convoluted.  I'd like the simplest, easiest way to do this if possible.

Rolling back to LTS isn't out of the question to solve #1 and #2 if its needed but everything else seems to be going really well so I'm happy with the current install.

Thanks.

---

### Post by T.J. on 2009-07-17
This is just my opinion, not a fact.  With the respect to everyone's love of Ubuntu, if you are making a business deployment, you would be better off using either CentOS or Debian. 


Ubuntu is based on Debian "unstable" and goes through a rapid "use and replace" cycle (every six months) so there are bound to be some really bad bugs that never get fixed before the next version is released and the entire cycle begins all over again. (In my opinion, six months is just too short a time to keep the quality up for an *entire* release. A yearly release or even a rolling release would be far better.) 

If you need to use Ubuntu I'd very, very seriously take everyone's suggestion of 8.04 LTS.

Good luck!

---

### Post by dkbk on 2009-07-17
Thanks for the feedback.

I arguably played a lot more with CentOS than Ubuntu for setting up my zimbra server.  CentOS is without a doubt a very solid product.  However, what drew me to Ubuntu was the apparent "install and use" approach.  These were my first steps in the Linux world so my choosing of both products, one for a server and the other for computer illiterate user's workstations, had a lot to do with their reputation.

Ubuntu, right after install, is much more useable than a windows install for example.  While that's still the case with CentOS, I felt the end product was closer to our final environment with the smb clients installed and set up and all the other included software.  And it also has the reputation of being more user friendly.  

As for my personal day to day experience, I can't say I see much of a difference in usage actually.  The only big difference is the install process and I actually like CentOS's approach a bit more than Ubuntu's since I don't get to choose anything with Ubuntu while its the opposite with CentOS.  I am definately not a normal user however so there may be things I understand naturally in one or the other that normal users would struggle with.

As for stability, I've rolled out Ubuntu to one of my user in production to see the results and the system is rock stable.  The only issues I've had are those above which are with side-programs I would be using with either Ubuntu or CentOS.

If going to CentOS is going to make it easier to get those working than that's whats going to happen but the OS itself is very stable so I figure these are application issues much more moreso than OS stability issues.  Am I misreading the situation and its actually Ubuntu's subcomponents that tie into these applications that are giving me headaches ?

I have a week before I start rolling out others systems whithin the company.  By then I'll have made a choice.  I'm leaning towards this version of ubuntu because of the out of the box useability and solving the issues above would make this a sure thing.  However, if people with experience with these software tell me they either work better in CentOS or the LTS, then I'm certainly willing to change course.

---

### Post by Murz on 2009-11-02
Openoffice 3.1.1 have the bug with tables too, so let's vote for this bug:
[http://www.openoffice.org/issues/show_bug.cgi?id=101472](http://www.openoffice.org/issues/show_bug.cgi?id=101472)

---

