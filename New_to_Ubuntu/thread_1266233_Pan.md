---
title: "Pan"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by shadowlands on 2009-09-14
How does it work? I went to the edit tab and I have my news group info put in to it but is there anything else I will need.  I really would like to get this working and I have very little clue as to what I am doing.  Sorry if I am being a pest but I really need some help.  

I mean, point me in the right direction and I will read the stuff but what should I be reading?


  I tried to import NZB files but could not locate the files I down loaded on to my computer and I am still not sure if I need par2 and how do I get he par2 to work?

---

### Post by ayenack on 2009-09-14
This should help you out.

[https://help.ubuntu.com/community/Pan](https://help.ubuntu.com/community/Pan)

There are links at the bottom of the page for more info/help on pan.

---

### Post by shadowlands on 2009-09-14
You are top shelf!!  Thanks> **ayenack said:**
> This should help you out.

[https://help.ubuntu.com/community/Pan](https://help.ubuntu.com/community/Pan)

---

### Post by shadowlands on 2009-09-14
> **shadowlands said:**
> You are top shelf!!  Thanks

I have it installed.  It does not answer my questions and the Pan guide is still being created any other tips or suggestions?

---

### Post by ayenack on 2009-09-14
You could try Klibido. It may be a better choice.

**sudo apt-get install klibido**

Screenshots.

[http://klibido.sourceforge.net/#_screenshots](http://klibido.sourceforge.net/#_screenshots)

Also here's a newsgroup list.

[http://www.binsearch.info/groups.php](http://www.binsearch.info/groups.php)

Also Liferea is a good news group reader. Not sure it'll cover what you want to do though.

To install Liferea.

**sudo apt-get install liferea**

---

### Post by shadowlands on 2009-09-14
Thanks for taking the time to replay.:KS:KS:KS

sudo apt-get install lifera can not be found.  This is the message i got when I tried to install it.

---

### Post by ayenack on 2009-09-14
It should be 

**sudo apt-get install liferea**

My mistake.

---

### Post by oldos2er on 2009-09-14
> **ayenack said:**
> 
Also Liferea is a good news group reader. Not sure it'll cover what you want to do though.

To install Liferea.

**sudo apt-get install liferea**

 Liferea is an RSS feed reader, not a Usenet client like Pan.

---

### Post by shadowlands on 2009-09-14
It is Monday need we say more > **ayenack said:**
> It should be 

**sudo apt-get install liferea**

My mistake.

Why was I told packages were installed that would know longer be needed, but the apt-get autoremove did not remove them. I got the following message:

 E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by ayenack on 2009-09-14
Did you use sudo?

---

### Post by shadowlands on 2009-09-14
> **ayenack said:**
> Did you use sudo?yes I did

---

### Post by ayenack on 2009-09-14
Try this.

**sudo apt-get install -f**

Then try to update again and see if it works.

---

### Post by shadowlands on 2009-09-14
k
> **ayenack said:**
> Try this.

**sudo apt-get install -f**

Then try to update again and see if it works.

---

### Post by shadowlands on 2009-09-14
no luck

---

### Post by ayenack on 2009-09-14
How about this.

**sudo apt-get update -f**

EDIT: come to think of it this is not an option I don't think.

---

### Post by ayenack on 2009-09-14
You haven't got synaptic open or downloading any updates have you?

---

### Post by shadowlands on 2009-09-14
nothing is open and i am not running updates.

---

### Post by Bradtek on 2009-09-14
Back to your original question re pan.

It would be helpful if you gave a more detailed description 
of what you are doing / trying to do.

Have you entered the details of your news server ?
(it should ask you if you have not)

Have you downloaded the list of available news groups ?
(it usually does this automatically after a new news server is added)
if not ... Groups menu / Refresh Groups List

What do you want to do with pan ?
Browse news groups ? (eg alt.binaries.pictures.garden) 
Pan is good for this.

Download using .nzb files  you found on an nzb indexing site ?
You are better off with klibido or sabnzb ?

You say you can not locate .nzb files ?
do you know where you downloaded them to  ?
are you sure they are not inside a .rar or .zip etc ?

---

### Post by shadowlands on 2009-09-15
Thank you for your questions your wording of terms will help me explane more.

I have entered my server.  


I had a list of available news groups but I can not figure out how to recall them.  They loaded up when I loaded the server up. Or did I do something wrong.

I down loaded items and I can not located where they down loaded to.  I looked in the down load folder and I found nothing.

Thanks for the info concerning "
Download using .nzb files  you found on an nzb indexing site ?
You are better off with klibido or sabnzb" and informing me they would be best.  The thing I am messing some thining.  I can not get the systems to work.  

Can you provide me with an idiot check list? I can not figure out how to get the items I want to down load or I have them on the computer desk top but I can not figure out how to get them to a location were they can be open by the software.


I have a program to open zip files but in case it is not a good program could you recommend some or provide me with a good link and I will read up on them and chose from the list.  

Thanks for responding.:KS:KS:KS


> **Bradtek said:**
> Back to your original question re pan.

It would be helpful if you gave a more detailed description 
of what you are doing / trying to do.

Have you entered the details of your news server ?
(it should ask you if you have not)

Have you downloaded the list of available news groups ?
(it usually does this automatically after a new news server is added)
if not ... Groups menu / Refresh Groups List

What do you want to do with pan ?
Browse news groups ? (eg alt.binaries.pictures.garden) 
Pan is good for this.

Download using .nzb files  you found on an nzb indexing site ?
You are better off with klibido or sabnzb ?

You say you can not locate .nzb files ?
do you know where you downloaded them to  ?
are you sure they are not inside a .rar or .zip etc ?

---

### Post by ayenack on 2009-09-15
Can you show the contents of this file.

/etc/pam.d/common-auth

You can copy and paste it into reply.

---

### Post by mangurt on 2009-09-15
People are asking what you are trying to do with PAN.  If it's to download .nzb files, use hellanzb or SABnzbd (both are in synaptic if you are running Jaunty).

I never had that much luck with PAN, and I switched over to thunderbird to read/write in newsgroups.  You can give that a try also....

---

### Post by shadowlands on 2009-09-15
I got pan to work the thing know how do I unpack the information I might have downloaded?

I will give the others a try also.

---

### Post by mangurt on 2009-09-15
get unrar and par from synaptic

then unrar the files...use par to fix the files

Hellanzb and SABnzbd does this automatically....just takes a bit to set up....SABnzbd is a lot easier to setup....just need to run in firefox....

---

### Post by shadowlands on 2009-09-16
got pan to work. the item is a zip file.  Which zip program is best for opening files?

---

### Post by shadowlands on 2009-09-18
Dancing like Dora the Explora " We did it ! We Dit IT!" Pan is working! Pan is working." NOw on to the next part of the battle.

---

### Post by shadowlands on 2009-09-18
THanks everybody for there help:KS:KS:KS:KS:KS:KS

---

### Post by unutbu on 2009-09-18
[Dancing like Dora the Explora]("http://www.youtube.com/watch?v=Vwraz9-PYfY")

---

### Post by shadowlands on 2009-09-18
lol > **unutbu said:**
> [Dancing like Dora the Explora]("http://www.youtube.com/watch?v=Vwraz9-PYfY")

---

### Post by shadowlands on 2009-09-19
This solved my problem:KS:KS:KS

Thanks> **mangurt said:**
> get unrar and par from synaptic

then unrar the files...use par to fix the files

Hellanzb and SABnzbd does this automatically....just takes a bit to set up....SABnzbd is a lot easier to setup....just need to run in firefox....

---

