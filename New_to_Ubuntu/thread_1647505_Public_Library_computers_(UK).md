---
title: "Public Library computers (UK)"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by Weatherlawyer on 2010-12-17
I have no connection at home but have a number of distros on disc. I still can't understand how to get programmes up and running (on 10.10 this time.)
 
The local library is not a fat lot of good as they seem to halt everything eg
 
Security risk blocked for your protection 
Reason:
This Websense category is filtered: Parked Domain. Sites in this category may pose a security threat to network resources or private information, and are blocked by your organization.
URL
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
 
Options:
Click [more information]("http://10.100.0.15:15871/cgi-bin/moreBlockInfo.cgi?ws-encdata=d3MlMkRzZXNzaW9uPTIwOTc0MjUyODcmd3MlMkR1c2VyaXA9MTAlMkUxMDAlMkU5JTJFMTE4JndzJTJEY2F0PTIwMiZ3cyUyRHJlYXNvbj0xMDI1") to learn more about your access policy. 
 
Click **Go Back** or use the browser's Back button to return to the previous page. 
 
Needles to say this is a pain.
 
(In the UK all government and sub government type agencies such as Job Centre and Libraries etc., run on Windows.)
 
I am contemplating moving again so I don't think setting up and ISP is worth the effort.
 
Be that as it may.
 
Do I have to be running the command line or whatever it is called to download and install? Or is there another reason that the GUI doesn't want me to?
 
Kudos to 10.10 btw.
 
I like the tool that is going to let me turn my pictures into a video clip. When I learn how to turn my pictures into a video clip that is.

---

### Post by hwychld on 2010-12-17
I assume you are attempting to boot the library computer from the LiveCD?  If so you won't have much luck installing additional programs (you can install them but the next time you use the CD you will have to install them again - kind of a pain).  Newly installed programs are stored in RAM when running the Live CD, and therefore are not permanently saved.

Likewise, any files you create or modify when in the Live CD will have to be stored to a USB key, otherwise they will be lost once you terminate the Live session.

Perhaps Pupply Linux would be worth a look for you.  It runs completely out of RAM when booted from the Live CD, but is able to save any changes (like newly installed programs or modified files) when you shutdown.  It can store this 'save' file on a USB key or similar (I think you can even save it to a R/W CD/DVD - not sure though, never done it that way).

Puppy is not as polished looking as Ubuntu, and doesn't come with as many fancy applications, but it is very good at what it does.  

Lastly, I am very surprised the library computers can boot a Live CD, that seems like a sys admin nightmare (you could really mess up the installed OS from a Live CD if one were so inclined).

---

### Post by NCLI on 2010-12-17
> **Weatherlawyer said:**
> I have no connection at home but have a number of distros on disc. I still can't understand how to get programmes up and running (on 10.10 this time.)
 
The local library is not a fat lot of good as they seem to halt everything eg
 
Security risk blocked for your protection 
Reason:
This Websense category is filtered: Parked Domain. Sites in this category may pose a security threat to network resources or private information, and are blocked by your organization.
URL
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
 
Options:
Click [more information]("http://10.100.0.15:15871/cgi-bin/moreBlockInfo.cgi?ws-encdata=d3MlMkRzZXNzaW9uPTIwOTc0MjUyODcmd3MlMkR1c2VyaXA9MTAlMkUxMDAlMkU5JTJFMTE4JndzJTJEY2F0PTIwMiZ3cyUyRHJlYXNvbj0xMDI1") to learn more about your access policy. 
 
Click **Go Back** or use the browser's Back button to return to the previous page. 
 
Needles to say this is a pain.
 
(In the UK all government and sub government type agencies such as Job Centre and Libraries etc., run on Windows.)
 
I am contemplating moving again so I don't think setting up and ISP is worth the effort.
 
Be that as it may.
 
Do I have to be running the command line or whatever it is called to download and install? Or is there another reason that the GUI doesn't want me to?
 
Kudos to 10.10 btw.
 
I like the tool that is going to let me turn my pictures into a video clip. When I learn how to turn my pictures into a video clip that is.

All applications should be installed through the Ubuntu Software Center.

---

### Post by matt_symes on 2010-12-17
Hi

@Weatherlawyer. I'm very confused by your post. What exactly are you trying to do?

Connect to Library wireless from a laptop? Use LiveCD or pen drive?

What are you trying to do?

Questions from an Engish Bristolian.

BTW: Where are you based?

Kind regards

---

### Post by hwychld on 2010-12-17
Are you getting the websense messages while booted in the Live CD?  If so you are probably out of luck.  Websense is a filtering proxy and will block any site that has been blacklisted by the Websense admin.  

I thought you were trying to get around the filtering by using a Live CD, figuring the webfiltering was local (on that machine).  But now that I think about it, Websense usually isn't on the local machine.

---

### Post by hwychld on 2010-12-17
> **NCLI said:**
> All applications should be installed through the Ubuntu Software Center.


And why is that?  Command line works just as well using apt-get.  So does compiling from sources if you are so inclined.  For instance, suppose you want the latest version of nmap.  The repository doesn't have it.  That means you don't have the most up to date OS fingerprints.  So it may be best to install from sources in that case.

---

### Post by beew on 2010-12-17
> **hwychld said:**
> And why is that?  Command line works just as well using apt-get.  So does compiling from sources if you are so inclined.  For instance, suppose you want the latest version of nmap.  The repository doesn't have it.  That means you don't have the most up to date OS fingerprints.  So it may be best to install from sources in that case.


Yeah, this is absolute beginer's talk and OP indicates that he doesn't even know what the download thing is called. I don't see your point in bringing up installing from source except to show off your own knowledge, doubt that it would be of any help to OP though.

I have seen several threads where the OP asks a simple question like how to install googleearth and some guy comes along to give a bunch of confusing instructions to install the package from source (and it may not even be correct!) and of course it gets the OP into bigger troubles because  of unclear instructions and broken dependencis etc and when OP gets  into a mess the person who gave the original brilliant advice to install from source have disappeared. The simple instruction should be just activate medibuntu and install from the package manager.

---

### Post by NCLI on 2010-12-17
> **hwychld said:**
> And why is that?  Command line works just as well using apt-get.  So does compiling from sources if you are so inclined.  For instance, suppose you want the latest version of nmap.  The repository doesn't have it.  That means you don't have the most up to date OS fingerprints.  So it may be best to install from sources in that case.

Because this is ABSOLUTE BEGINNERS. The Software Center is the supported package management application, and is very easy to use for beginners.

Stop recommending the CLI and building from source in this subforum.

---

### Post by hwychld on 2010-12-17
OK, fair enough, use the Software Center.  :)  

For the record, I was not recommending installing from sources, I was just wondering why the recommendation  for the Software Center was absolute, and demonstrated a situation where it might not be best.  However, I guess in the context of this forum the Software Center is the correct answer.

I not sure the "installation" is actually the problem the OP is having anyway.

---

### Post by CharlesA on 2010-12-17
> **Weatherlawyer said:**
> 
Security risk blocked for your protection 
Reason:
This Websense category is filtered: Parked Domain. Sites in this category may pose a security threat to network resources or private information, and are blocked by your organization.
URL
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
 

Hi.

That domain is "parked" meaning it is full of ads. They've blocked it to prevent picking up anything nasty. See [here]("http://en.wikipedia.org/wiki/Domain_parking") for some info.

There are other places to find info about Ubuntu:

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

what are you trying to find info about?

---

