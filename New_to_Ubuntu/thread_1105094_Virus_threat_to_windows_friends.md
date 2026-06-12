---
title: "Virus threat to windows friends"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by marcus_c on 2009-03-24
Hi everyone,

I've recently switched to Ubuntu and its great. I just had one thought though. Linux is obviously immune to Windows viruses, but could my Ubuntu system be harbouring viruses which could be a problem for my friends and family using Windows?

---

### Post by Mason Whitaker on 2009-03-24
I don't see how it can, unless the viruses were smart enough to save themselves on the new OS and avoid being wiped out when you made the switch to Ubuntu.

---

### Post by acreech on 2009-03-24
> **marcus_c said:**
> Hi everyone,

I've recently switched to Ubuntu and its great. I just had one thought though. Linux is obviously immune to Windows viruses, but could my Ubuntu system be harbouring viruses which could be a problem for my friends and family using Windows?

Your linux system won't be effected by the viruses, but if one was emailed to you and you forwarded it on, then yes that would be passed onto other people. 

They should have an anti-virus program on their system as a general preventative measure and that should stop any viruses that you unknowingly forward on. 

There is a anti-virus program under Applications>Add/Remove

Select "Show: All Open Source Applications" and then search for ClamAV. It should come up there.

---

### Post by Piraja on 2009-03-24
> **acreech said:**
> There is a anti-virus program under Applications>Add/Remove

Select "Show: All Open Source Applications" and then search for ClamAV. It should come up there.

Acreech, let me ask a stupid question, just to make clear: I take it that you mean that the purpose of installing ClamAV is to prevent from spreading viruses unknowingly via e-mail to receivers with Windows and maybe without proper antivirus software? 

I ask this because I think that might be a smart idea, while there is otherwise very little cause to install antivirus software on Linux.

---

### Post by Sir Jasper on 2009-03-24
Hi,

If you copy an email to a friend with Windows an infection could, I believe, be passed on.

ClamTK is already available and I have it installed though I also installed Avast for Debian. Both will search for Windows infections.

AVG and Avira also have good products and there are probably others but since AVG and Avira seemed rather complicated to install I stuck with Avast (brilliant) and ClamTK (OK).

My regards

Addendum:

Avast is fast - except for those on dial-up - because updates are full not incremental

---

### Post by acreech on 2009-03-24
> **Piraja said:**
> Acreech, let me ask a stupid question, just to make clear: I take it that you mean that the purpose of installing ClamAV is to prevent from spreading viruses unknowingly via e-mail to receivers with Windows and maybe without proper antivirus software? 

I ask this because I think that might be a smart idea, while there is otherwise very little cause to install antivirus software on Linux.

I don't run any anti-virus on my machine. I have read several other threads that suggest to those that are worried about viruses to add this app. I would expect that it would alert you to any viruses that you are receiving so that you could dispose of them. 

There are numerous threads on this topic, here is one of them: [http://ubuntuforums.org/showthread.php?t=1103006&highlight=clamAV](http://ubuntuforums.org/showthread.php?t=1103006&highlight=clamAV)

---

### Post by tarps87 on 2009-03-24
I would recommend clamav, it is easy to use an will detect most windows viruses. I am using it on my file server as windows machines connect to it.
Although windows viruses can't effect/infect Linux based os's they can be sent (manually) from them either if you attach it in an email, if it is copied onto removable media or from a share on the machine.

Hope this helps

---

### Post by mcduck on 2009-03-24
> **Piraja said:**
> Acreech, let me ask a stupid question, just to make clear: I take it that you mean that the purpose of installing ClamAV is to prevent from spreading viruses unknowingly via e-mail to receivers with Windows and maybe without proper antivirus software? 

I ask this because I think that might be a smart idea, while there is otherwise very little cause to install antivirus software on Linux.

The real purpose of installing it is if you are running a mail server or gateway, for example for some larger organizations e-mail.

In my opinion, it's rather pointless from home user's point of view, the windows machines will be running antivirus anyway and thus should be able to protect themselves without you doing anything about. If their antivirus isn't able to protect them from infected files without you scanning them on Linux first they are in pretty deep troubles anyway.. ;)

---

### Post by marcus_c on 2009-03-25
Thanks for you replies guys. To be honest I was asking out of interest mostly. I still have my xp system on dual-boot with Ubuntu and to be fair, it only occasionally gets hit with a virus (which AVG soon deals with). 

So I guess theres no need to be overly cautious so I'll continue to run Ubuntu as it is (without ClamAV). 

Thanks again!

---

### Post by stalkingwolf on 2009-03-25
> I don't see how it can, unless the viruses were smart enough to save themselves on the new OS and avoid being wiped out when you made the switch to Ubuntu.


This is not exactly true. Here is an article ,
[http://it.slashdot.org/article.pl?sid=09/03/23/1248214&from=rss]("http://it.slashdot.org/article.pl?sid=09/03/23/1248214&from=rss")

I also read another article yesterday about a new worm that is in the wild
that attacks thru certain types of routers.  They said that 99% of people
have no worry.  If I can find it again I will post a link.

---

