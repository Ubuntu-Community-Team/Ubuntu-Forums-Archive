---
title: "portable ubuntu os"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by vinceCOOK on 2009-05-17
Hello Forum people,

I am using a version of Ubuntu called Portable Ubuntu. It works from within microsoft
windows.

It is very easy to use and install p/u and it did not require any reboot of the machine. I am able to use both windows and ubuntu at the same time.

I am happy with the performance of p/u but i wonder if anybody can remind me of something? 

what is the generic command line instruction that will go away and find all the latest
updates for my ubuntu and get all the right repositories live for me....and completely refresh and update my system?

i know this generic command can take a while to complete itself...but it leaves your ubuntu system totally up to date.

[http://portableubuntu.demonccc.cloudius.com.ar/](http://portableubuntu.demonccc.cloudius.com.ar/)

thankyou

Vince

---

### Post by The Cog on 2009-05-17
> sudo aptitude update
sudo aptitude safe-upgrade
But I'm not sure that's wise. If your sources.lst is pointing at the Ubuntu repositories and Portable Ubuntu uses a modified kernel then you could end up breaking it all. Of course I would hope they have pointed to their own maintained repositories, but I don't know - I've never looked at it.

---

### Post by vinceCOOK on 2009-05-17
Hello

As far as i understand it....Portable Ubuntu is almost the same as ubuntu. It operation viewed from a USERS perspective is the same as ubuntu. 

It is certainly the same with regard to the mass proportion of common features of ubuntu...such as terminal operation and command line commands.

Things are suppossed to work in an identical fashion to ubuntu....i dont think pu would allow any command line options that destroyed its own Kernel....or at least you would hope that it was programmed that way..

I am not sure what repositiries PU has listed for itself...it seams to show the same lits
as ubuntu would show...

thanks

Vince.

---

### Post by The Cog on 2009-05-17
OK. Well, I'm talking from a position of total ignorance.

---

### Post by Didius Falco on 2009-05-17
I saw this thread earlier, and went and had a quick look at the web site for it. I didn't spend a long time there, but long enough to note that it does use a different kernel.

I'd advise you to go to the website and enquire in the forum there - it's an offshoot that isn't affiliated with Canonical, and you'd do better to get advice from the creator.

Regards,

Didius

---

