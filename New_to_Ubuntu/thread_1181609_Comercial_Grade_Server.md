---
title: "Comercial Grade Server"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by RichardCL on 2009-06-08
Dear Forum,

I'm just looking at the hosting bill for my small company and thinking we can buy a PC quite easily for that kind of money. I switched the company to Ubuntu for desktop applications a year ago and, after a reasonable learning curve, we've been pretty much OK (except that the Open office rendering is lousy for presentations).

I've found guides for most of the applications we outsource but would like some advice on how easy it would be to set up a server. Is there anything special that I need to think about?

I've got a free account with DynDNS and can access my PC from the internet.

Must have:
 - LAMP server with PHP5 for our website (we use Joomla CMS)
 - Ability for external users to ftp files to our server (also with secure authentication/ftp via ssh)
 - Mail server with IMAP compatible with Evolution desktops accessing from internal LAN
 - Addressbook server to allow mail users to use company address book (LDAP I think)
 - Access to the sever for configuration is possible from Ubuntu desktop over the LAN
 - Software RAID 1
 - Ability to backup to external USB drive

Nice to have
 - Ability to access the mail server from external (Internet)
 - Ability to use internal TV card to collect business TV programs from Cable TV (CNBC)

Regards


Richard

---

### Post by LowSky on 2009-06-08
> **RichardCL said:**
> 
Must have:
 - LAMP server with PHP5 for our website (we use Joomla CMS)
 - Ability for external users to ftp files to our server (also with secure authentication/ftp via ssh)
 - Mail server with IMAP compatible with Evolution desktops accessing from internal LAN
 - Addressbook server to allow mail users to use company address book (LDAP I think)
 - Access to the sever for configuration is possible from Ubuntu desktop over the LAN
 - Software RAID 1
 - Ability to backup to external USB drive


- LAMP +PHP5 = yes
- FTP? Sure why not, but localized network folders is better and easier and possible
- Mail seriver with IMAP and EVO, yes
- Address book, yes
access to server from desktop, yes
- Software RAID? possible yes, but hardware RAID is better
- Backup over USB, yes

> **RichardCL said:**
> 
Nice to have
 - Ability to access the mail server from external (Internet)
 - Ability to use internal TV card to collect business TV programs from Cable TV (CNBC)


- Mail form away, yes, using VPN client is the best option
- TV to record, yes, think MythTV back-end, the more channels the more tuners required.


It is all possible, but for such a taking you will need someone to develope and maintain this system. Its way too much work for one guy. Many companies specialize in Linux servers.

---

### Post by Cheesemill on 2009-06-08
You may be able to afford a server, but depending on how many users you want to serve your external website to you may be looking at a lot of money for a business-class internet connection with a high upload capacity.

It is not really good practice to have a machine on your internal LAN that serves external web pages, if someone hacks into your web server you are pretty much screwed.

Also regular off line and off-site backups **are a must!!!**


> - Ability to access the mail server from external (Internet)
I use Roundcube webmail for this, it's far better than squirrelmail IMHO (personal use only).

Cheesemill

---

### Post by LewRockwell on 2009-06-08
> **Cheesemill said:**
> You may be able to afford a server, but depending on how many users you want to serve your external website to you may be looking at a lot of money for a business-class internet connection with a high upload capacity.

It is not really good practice to have a machine on your internal LAN that serves external web pages, if someone hacks into your web server you are pretty much screwed.

Also regular off line and off-site backups **are a must!!!**



I use Roundcube webmail for this, it's far better than squirrelmail IMHO

Cheesemill

seconded

---

### Post by bodhi.zazen on 2009-06-08
I will cast a dissenting vote ;)

Off site hosting is not *that* expensive, what is it you are hosting ?

Inexpensive solutions range from VPS to 1u rack servers with colocalization (shared hosting).

I don not think running a web server on your LAN is a huge security risk, just be sure to firewall it (ie run it in a DMZ, isolated from the rest of your LAN). This hardware configuration is extremely common.

The risks are in a mis-configured server.

---

### Post by reeseslover531 on 2009-06-08
Also something you need to consider is your time for having to manage the server. That time can add up, especially if you have to learn everything you are doing.  If you are looking for help though, I **highly** recommend [http://www.howtoforge.com](http://www.howtoforge.com). They have many articles including ones that teach how to install everything to get a server running on Ubuntu Server or many other distros.  If you need some help I am sure that the forums and IRC will gladly help you though.

Good Luck!

---

### Post by albinootje on 2009-06-08
> **RichardCL said:**
>  I'm just looking at the hosting bill for my small company and thinking we can buy a PC quite easily for that kind of money.

If I were you I would let -another- company do the webhosting (Depending on your monthly data traffic and your needs you can have your own domainname and hosting via a very good webhosting company for 30 euros .. a year), and then do the email yourself if you feel confident enough to do that.

And I can tell you from experience that migrating mailservers can take quite some time and energy, don't underestimate that.

---

### Post by RichardCL on 2009-06-13
> **bodhi.zazen said:**
> 
Off site hosting is not *that* expensive, what is it you are hosting ?

Just 5 mail accounts over 3 users for the mail.
3 Joomla sites with very low traffic and usage.

> **bodhi.zazen said:**
> The risks are in a mis-configured server.
This is what I'm worried about as a beginner. I don't want to just follow a tutorial without understanding steps and risks. I guess I'll have to do a load more reading.

The whole thing has to be "set and forget" or allow me to do changes when I want. I'm not bothered about new features and so on. Imagine an LTS release with only basic functionality on the premise that if it works today and I don't change anything...

My desktop never gets updated it just works. I'll only install an update if it really fixes a problem that I have or if I have lots of time on my hands and the weather outside is bad.

---

### Post by albinootje on 2009-06-13
> **RichardCL said:**
>  The whole thing has to be "set and forget" or allow me to do changes when I want. I'm not bothered about new features and so on. Imagine an LTS release with only basic functionality on the premise that if it works today and I don't change anything...

My desktop never gets updated it just works. I'll only install an update if it really fixes a problem that I have or if I have lots of time on my hands and the weather outside is bad.

:( Please do some extensive reading on "security" for Linux, and try to understand why security updates are offered, and what the impact on your desktop or server can be if you simply don't upgrade.

---

### Post by bodhi.zazen on 2009-06-13
google search VPS and look at something like fivebean

[http://fivebean.com/](http://fivebean.com/)

Mail servers do not take much RAM, but honestly there is a reason for services such as gmail.

The biggest "problem" with a mail server are spam and bad attachments.

You should be fine with apache.

My guess is you probably need 512-1024 Mb RAM (start with 512 and upgrade if needed).

---

### Post by reeseslover531 on 2009-06-15
also [http://www.slicehost.com](http://www.slicehost.com) is very good as well.

---

