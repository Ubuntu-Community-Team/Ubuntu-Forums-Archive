---
title: "How can I check if I've been hacked?"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Orographic on 2009-06-30
Hi all,

My website has apparently been hacked with this in the index file, at the end of it:



<adsttnmq1><font style="position: absolute;overflow: hidden;height: 0;width: 0">testsfksdlkshd2445</font></body></html><sdioyslkjs2>

It should just have </body></html> there.

I've restored the backup index file but want to make sure now that My Jaunty install hasn't been hacked. What is the best way to do that?

I'm using a single computer, connected to the net via a wired, firewalled router. Nothing unsual installed except fireftp in firefox.

Thanks all.

---

### Post by Celauran on 2009-06-30
They would need a way in. What services are you running? Open ports? Start checking logs, IMO.

---

### Post by bvanaerde on 2009-06-30
When [searching google]("http://www.google.com/search?q=testsfksdlkshd2445"), you can see that a lot of websites have this attached underneath their html code.

What website system are you using?
Check your files (using FTP). My guess they have been changed recently. If that is the case, someone found your FTP login. I suggest you change your password.

---

### Post by Orographic on 2009-06-30
I'm pretty new to Ubuntu. I am not running any services that I know of. what are examples of services? I have changed my FTP PW tonight. It only came up in my index file and no other. Its a very basic site.

See here:


[http://www.blackheathweather.com/](http://www.blackheathweather.com/)

How do I check logs?

---

### Post by Celauran on 2009-06-30
Logs are in /var/log. Which one(s) to check would depend on what's running. The above poster was probably right, though, it looks like someone exploited a CMS vulnerability. If you're using Joomla, Wordpress, or anything of the sort, that's probably a good place to start looking.

---

### Post by bvanaerde on 2009-06-30
Were you using a standard FTP password?
When deploying a webserver (e.g. XAMPP), you are given some standard logins for FTP, mySQL, ... It's always best to change this right away.

Also, is this hosting you are paying for, or is this website located at your PC at home (meaning you setup the server yourself).
Because it looks to me you're using paid hosting, or you're at least not hosting your website at home. If so, big chance that the hoster is having a problem, and it doesn't have anything to do with your own PC.

---

### Post by Orographic on 2009-06-30
My password was pretty unusual but i guess it could have been guessed but is changed again now. Not using word press, joomla or anything.

Thanks for the help, its a non profit website and i'm also worried my Jaunty is hacked but its probably not. I hope!

It could be a problem at my hosts end in australia. They use Cpanel 11.

Yeah, I'm using paid hosting in Australia. I only re-imaged my Jaunty via Clonezilla a week ago (experimenting with intel graphics fix) so its pretty fresh and I do have other images to restore if needed.

Thanks so much for this help!

Is there a good program I can install to check if my Jaunty has been hacked?

---

### Post by bvanaerde on 2009-06-30
[Web defacements]("http://zone-h.org/archive/special=1") happen every day, so it's good practice to use a hard to guess password. If they managed to add code to your pages, they can easily remove your whole website too. So make sure you backup your website on a regular basis, even if your provider does too.

---

### Post by Orographic on 2009-06-30
Thanks. Yeah, I backup everyday but don't want to backup anything tonight if its corrupted.

What can i install via synaptic to check for keyloggers or other things?

---

### Post by bvanaerde on 2009-07-01
> **Orographic said:**
> What can i install via synaptic to check for keyloggers or other things?
Maybe a combination of firewall + virusscanner? I never cared to install one, so I can't really help you with that. But I'm sure there's plenty of information here at the forums.
[This thread]("http://ubuntuforums.org/showthread.php?t=1195606&highlight=firewall") seemed to be quite informative about firewalls. At least it's a good read :)

---

### Post by ddminusd on 2009-07-06
This seems to be part of an automated attack.

They basically scanned the Internet looking for vulnerable hosts and added that as a mark of a site that they can hack again.

My suggestion is:

-Fix whatever method they used to hack you.
-start monitoring your system closely.

To fix the holes, first:

-Update all your services (ftp, apache, wordpress, etc). This is the most important part.
-Change all your passwords and remove all unused accounts.
-Run tools like OSSEC to look for rootkits, attacks in the logs.

To monitor your system:

-Use tools like OSSEC and modsecurity to protect your web server
-Use something like [http://sucuri.net ]("http://sucuri.net")(network integrity monitor) to remotely check your pages/domain for changes/malware/blacklist/defacement/etc.

--dd

---

