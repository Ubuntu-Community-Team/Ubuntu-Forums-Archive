---
title: "Regarding virus scanner in Ubuntu"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by r3cht3r on 2009-06-05
I just want to ask:

re: Freshclam/ClamTk
1.  Is it advisable to run freshclam daemonized? 
2.  If there are security risk/s, what are these?
3.  How to update its virus signatures? Because I only see a "Check for Updates" and if the status says there's a new version of the application, there's no button that says download updates? Any other info I should know about?

Thanks.

---

### Post by jenkinbr on 2009-06-06
just a question - is there a specific reason why you are using Antivirus in linux?

If you're not hosting a server of some sort, you probably don't need antivirus, as the linux security model nearly rules all threats of viruses out.

---

### Post by uberlube on 2009-06-06
> **jenkinbr said:**
> just a question - is there a specific reason why you are using antivirus in linux?

If you're not hosting a server of some sort, you probably don't need antivirus, as the linux security model nearly rules all threats of viruses out.f

+1

---

### Post by Cows on 2009-06-06
Vouch that. Linux isn't like Windows. It doesn't require virus scanners because Linux is built with security in mind =).

---

### Post by rcayea on 2009-06-06
Isn't it better to just play it safe though and have some sort of virus software on a linux box?

---

### Post by rcayea on 2009-06-06
And to add to that, I use BitDefender Scanner which is free. It updates everyday. I guess I am paranoid.

---

### Post by jenkinbr on 2009-06-06
> **rcayea said:**
> And to add to that, I use BitDefender Scanner which is free. It updates everyday. I guess I am paranoid.
I don't even bother.

It's just more processes running on an already limited machine.

This is why I ran away from windows - because Linux isn't as susceptible to catching a viral infection like windows is.

---

### Post by oldsoundguy on 2009-06-06
virus files are .exe or .com or .sh files etc. that RUN ONLY IN WINDOWS.

As long as you do your updating and installing from the repositories, you do NOT need anti-virus in Linux unless you are running a server with WINDOWS computers on the network .. then only to protect those Windows computers.
There is  NO SUCH THING as installing something in Linux BY ACCIDENT.

As others have said .. Linux is NOT WINDOWS. (and does not strive to be!)

---

### Post by jenkinbr on 2009-06-06
> **oldsoundguy said:**
> virus files are .exe or .com or .sh files etc. that RUN ONLY IN WINDOWS.

As long as you do your updating and installing from the repositories, you do NOT need anti-virus in Linux unless you are running a server with WINDOWS computers on the network .. then only to protect those Windows computers.
There is  NO SUCH THING as installing something in Linux BY ACCIDENT.

As others have said .. Linux is NOT WINDOWS. (and does not strive to be!)
Do keep in mind that the OP may be running a server where virus scanning is needed for the protection of the users of the server who run windows.

However, the OP's posting style indicates otherwise, but I am giving that person the benafit of the doubt on this, because English isn't everyone's first language...

---

### Post by andrew.46 on 2009-06-06
Hi rcayea,

> **rcayea said:**
> Isn't it better to just play it safe though and have some sort of virus software on a linux box?

One of the more definitive discussions on this subject, and lists of resources for further reading, can be found here:

Ubuntu Security
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

All the best,

Andrew

---

### Post by r3cht3r on 2009-06-06
This is regarding Freshclam/ClamTk:

 1.  Is it advisable to run freshclam as a service/daemon? 
I guess simple answer would be yes/no. I just want to know from the people who have used Linux/Ubuntu longer than I am what they have experienced and what they can advice.

2.  If there are security risk/s (running freshclam as a service/daemon), what are these?
If you can direct me to a post/website/forums/thread so that I could read more and understand more.
 
3. How to update its virus signatures? Because I only see a "Check for Updates" and if the status says there's a new version of the application, there's no button that says download updates? Any other info I should know about? (this is regarding Clamtk)

Correct me if I am wrong. IMHO, while many viruses do target Windows for mayhem, Linux has opensource applicatioins equivalent and/or exceeds Windows executables who can do more harm if you don't know how to configure it properly. Right?.

So I guess its good to say "better safe than sorry".

@andrew46 thanks for the link.

---

### Post by cariboo on 2009-06-06
> 3. How to update its virus signatures? Because I only see a "Check for Updates" and if the status says there's a new version of the application, there's no button that says download updates? Any other info I should know about? (this is regarding Clamtk)

Freshclam sets up a cron job that goes out and checks for updates daily. I only set it up to answer some questions, so I don't remember how frequently it checks.

---

