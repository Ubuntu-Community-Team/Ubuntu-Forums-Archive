---
title: "[SOLVED] VirusScanner,Rkhunter,Chkrootkit"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by unf4b1x on 2008-12-07
I tried installing VirusScanner, Rkhunter, and Chkrootkit, and see what happens next... (these are just my noob observations.)

VirusScanner(ClamTk) scanned for about a day. Althought it did detected about 4 "viruses," I wasn't able to tick one of the options to quarantine the infected files,so I guess I may have to do it again. I didn't see which are the infected files though.

Rkhunter have detected about 5 or more "warnings." I don't know what it meant. There were others like "found","not found" and "ok." I guess, not found and ok would mean there are negative infections. I think the log file would be a big help here just to let you guys understand what I mean.

Chkrootkit did not detect any.

I just hope there's nothing to these so-called detections because now I am having problems connecting to the Internet using the networkmanager or the icon beside the volume icon. My connection is fine though with the windows side and other livecds. Can anybody please give me a piece of your mind?

---

### Post by scorp123 on 2008-12-07
> **unf4b1x said:**
> I tried installing VirusScanner, Rkhunter, and Chkrootkit, and see what happens next...  And why do you think you need that software??

There are no viruses for Linux out there ... all those virus scanners mostly scan for Windows viruses. The other tools only make sense on servers which are exposed to the Internet (e.g. WWW or FTP sites) and which have several users on them: you use them to make sure that none of those users has done or installed anything (e.g. some backdoors into the system) they were not supposed to.

As newbie desktop user you don't have any need for those packages, IMHO.

---

### Post by FreewheelinFrank on 2008-12-07
What exactly did you scam with ClamTK? Home? Root? Windows partition?

What "viruses" were found, in what files and in what location?

I think you'll need tp post the RKHunter log.

---

### Post by unf4b1x on 2008-12-10
> **FreewheelinFrank said:**
> What "viruses" were found, in what files and in what location?

I think you'll need tp post the RKHunter log.

I wasn't able to get the RKHunter log :( and I don't know what "viruses" were found maybe because I didn't know where to look or I was doing it wrong. 

Now, I am trying to read through about iptables and maybe just stick with it once I get to understand the work-arounds in using that.

---

### Post by ronnielsen1 on 2008-12-10
> And why do you think you need that software??
Because of being new and used to having to do tons of protective software and maintenance to keep your computer running. It took me about 5 months to realize I could relax.

---

### Post by unf4b1x on 2008-12-10
> **scorp123 said:**
> And why do you think you need that software??

As newbie desktop user you don't have any need for those packages, IMHO.

I need that software so that I could have peace of mind that my box isn't compromised and if I am, I could readily counteract that attack. But what can a newbie do if all of a sudden you found out that your box is already out of your control? How would you know if you don't install security packages even though you're just a desktop user? Just asking. :)

---

### Post by scorp123 on 2008-12-10
> **unf4b1x said:**
> I need that software so that I could have peace of mind  You installed Linux. Your mind can rest now ):P

> **unf4b1x said:**
>  How would you know if you don't install security packages even though you're just a desktop user?  Look at the facts. It's as simple as that.

[LIST]
[*]The administrator account "root" is locked down per default. Only processes running under his infinite powers could do real damage.
[*]the browser is not integrated into the OS and not a core component! (unlike MSIE on Windows!)
[*]whatever "infects" the browser (and even that would be bit hard to accomplish here!) can't do much damage to the rest of the system
[*]software is installed via repositories which usually use crypto keys to authenticate themselves, and those repo servers are usually guarded by people who know what they do
[*]out of the box there is no server process in the background (unlike in Windows!), there simply is nothing whatsoever that would need the protection of a firewall or that a hacker could connect to or exploit ... No running service = Nothing to connect to = no hacker can get in.
[*]getting into a Linux desktop where 'out of the box' no server processes whatsoever are running is too much of a hassle and therefore you're not even remotely an "interesting" target for any attacker.
[/LIST]

The story would change only if you were running a server, e.g. your own Web site that is exposed directly to the Internet. Yes, then and in that case you should put some extra measures into place. e.g. a firewall that blocks all those connection attempts from Russian and Chinese bot networks, and so on.

But that's something we'd have to discuss in another topic, because that's not something you as a desktop user have to worry about for now.

.
.
.

---

### Post by theozzlives on 2008-12-10
```
sudo apt-get install clamav
```

```
mkdir /tmp/virus
```

```
clamscan -ri --move=/tmp/virus /home/*yourusername*
```


There are viruses for Linux, but a drop in the bucket compared to Windows. You probably won't get one.

---

### Post by scorp123 on 2008-12-10
> **theozzlives said:**
> There are viruses for Linux Only experimental ones, in some people's labs for the most part. Stuff like "clamav" scans mostly for Windows viruses. Hence installing such software only makes sense if you are running e.g. a mail or file server via which Windows machines exchange documents with each other. As far as "protecting Linux" is concerned "clamav" is irrelevant.

---

