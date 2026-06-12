---
title: "Personal firewall with application filtering (similar to ZoneAlarm)"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by alvevind on 2007-02-04
I am a Windows user trying to convert to Ubuntu, and I'm looking for alternatives to my Windows applications. I am looking for the Ubuntu alternative to the user friendly personal firewall ZoneAlarm (in Windows).

ZoneAlarm is restricitve by default, and asks me each time a new application attempts to access the Internet, if it should be allowed to or not. No application can access the net without my knowledge and approval. This is the most important feature.

Example: I have two different music players installed. I want to allow only one of these to access the net (to fetch CD-info over port 80). The other one should never be allowed to access the web by itself. 

How can I do this in Ubuntu?

If it is impossible - why?

---

### Post by alvevind on 2007-02-04
I found something called "TuxGuardian" that *appears* to do what I want:

[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)

Do any of you have any experience using TuxGuardian? 
Does it work as proposed? 
Does it compile properly in Edgy/Feisty?
Is it available as .deb? (Could not find it in the repositories..)

---

### Post by spd106 on 2007-02-04
I can't find it in a deb package. 

However, all of the dependencies are in the main repos and someone reported success here [http://www.ubuntuforums.org/showthread.php?t=218310](http://www.ubuntuforums.org/showthread.php?t=218310).

---

### Post by dmizer on 2007-02-05
okay ... first of all, for what reason are you needing this level of firewall interaction?

linux as a whole is restrictive by default, and things will only connect to the internet once you've configured them to.  furthermore, even if they ARE configured to connect to the internet, they don't connect unless you tell them to.  there's no reason to use a firewall to do this, it would be redundant and only slow things down.

furthermore, if you're really paranoid, you can simply keep an eye on the logs in /var/log

linux certainly doesn't mean you should forget about security; however, you also should not think about security in the same way as you did with windows.  so, if you want to prevent a program from communicating with the net, there should be no reason why you can't configure it so that it won't, and thereafter be perfectly confident that it indeed is not communicating with the internet.

finally, if you have concerns about particular programs, please feel free to post here and ask about it.  we're all more than happy to help you out.

---

