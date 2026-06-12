---
title: "DNS settings will not be saved"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by Aleksandersen on 2006-10-10
Hi,

When I change my DNS settings in Ubuntu they do not get stored. They get revoked after a few hours or after I reboot my computer.

How can I prevent this from happening?

I am changing my DNS servers by entering $ sudo network-admin, selecting the DNS tab and entering costumized DNS servers in the DNS server list. Then I click OK to store the changes.

But as I said this gets revoked when I reboot or just let the computer be idle for a while.

Suggestions on how I can make the changes permanent?

---

### Post by mssever on 2006-10-10
If you're using DHCP and a router, then your router is probably messing with your DNS settings. The best option would be to configure your router to either use the correct DNS settings or to not try to set your DNS. The sledgehammer fix would be to revoke write permissions on /etc/resolv.conf (using sudo chmod 444 /etc/resolv.conf) so that the file can't be changed.

---

### Post by Aleksandersen on 2006-10-10
The sledgehammer fix worked perfectly, thanks. =D>

Correction: It did not work!!!](*,)

---

### Post by Iowan on 2006-10-10
If you'd like to try a smaller hammer, 
[http://www.ubuntuforums.org/showthread.php?t=188551&highlight=dhclient.conf]("http://www.ubuntuforums.org/showthread.php?t=188551&highlight=dhclient.conf")
One method mentioned involves editing /etc/dhcp3/dhclient.conf and removing the **domain-name-servers** entry from the **request** line.

---

### Post by Aleksandersen on 2006-10-10
The method above did not work!](*,)

I rebooted for the second time just now, and my changes where unmade once again. And now my domain name (under the General tab) where removed too!

How should I edit the file to keep these settings?

And why are they being overwritten in the first place? It is stupid to have an interface for editiing it when it just gets undone all the time.

---

### Post by mssever on 2006-10-10
Check to see what /etc/resolv.conf says and if it's getting changed. I suspect it is. If it isn't, then you need to find out somehow what file is getting changed.

If chmod'ing it didn't work, there's another, bigger sledgehammer if you're using the ext3 filesystem (Ubuntu's default):
```
sudo chattr +i /etc/resolv.conf
```This sets the immutable flag on the file which makes it completely unchangable. You can undo this with ```
sudo chattr -i /etc/resolv.conf
```See the chattr man page for more details.

Those changes are being overridden because DHCP needs to be able to set those settings. So ultimately, the issue is with your DHCP server (likely embedded in your router). If those settings weren't overridden by DHCP, then people would be complaining about not being able to access the Internet. But the fact that you need special DNS settings indicates that your situation isn't the most typical.

---

### Post by Aleksandersen on 2006-10-11
My file system is Reiser FS. And the files does indeed get changed.

---

### Post by mssever on 2006-10-11
> **Aleksandersen said:**
> My file system is Reiser FS. And the files does indeed get changed.

And making it read-only doesn't prevent it from changing?

OK...here's another sledgehammer (properly configuring the DHCP server would be ideal, but...): Make a file containing the proper resolv.conf settings, e.g., /etc/resolv.conf.new.
Next, set up a crontab entry to overwrite the file every five minutes:
```
sudo crontab -eu root
#Insert the following line
*/5   *   *   *   *   mv /etc/resolv.conf.new /etc/resolv.conf
```
Save and exit.

---

### Post by handy on 2006-10-11
[Did you try **_*Option 3*_** from **_*post 13*_** of this thread?]("http://www.ubuntuforums.org/showthread.php?t=128254&page=2")

It's the one that satisfies me, & the problem stays solved.

---

### Post by Aleksandersen on 2006-10-11
Yhea, I tried but could not figure it out properly I think.

Anyhow, it seams like the replace every five minutes method works.:KS

---

### Post by Aleksandersen on 2006-10-24
](*,) The problem is back again and my ISP's DNS service is worsse than ever...

Anyone got another solution for fixing these issues?

I have to disable the last fix as I realised it caused problems for other users on the same computer.

What are the function of the "Locations" drop-down menu? As I understand it it saved a set of default settings? Will it help if I created a new location called "Stupid home network" and used that one? Would I have to manually change to "Stupid home network" or could I have that as a default or have a taskbar icon for quick location changes?...

---

### Post by handy on 2006-10-24
Try ***_[this how-to]("http://ubuntuforums.org/showthread.php?t=282034")_***, I've tried to make it easy to follow.

---

### Post by Aleksandersen on 2006-10-24
Thanks! That worked!

...at least for now.

---

### Post by handy on 2006-10-25
Please post here if you still have problems?

Happy to hear it worked :D  It should do the job.

---

### Post by Aleksandersen on 2006-10-25
It is still a little edgy... Right after I have rebooted my computer uses 10.0.0.1 as it's DNS server, and after a few minutes it starts using 208.67.222.222,208.67.220.220 ([OpenDNS.com](http://opendns.com/)) as I wish.

---

### Post by bionnaki on 2006-10-25
do you recommend openDNS?

---

### Post by Aleksandersen on 2006-10-26
I highly recommend OpenDNS!

Note that they sell ads on the "cannot resolve" page. But you will not see this page as often as you would to with any other DNS. Look at the feature page over at OpenDNS's Website.

---

### Post by mssever on 2006-10-26
I've just switched to OpenDNS. I haven't used them long enough to compare them to my ISP's DNS, but I like not being dependant on my ISP--especially since I've had to block their DNS servers from coming across via DHCP since I run my own local DNS server.

---

### Post by Aleksandersen on 2006-10-27
How to: [Use OpenDNS on Ubuntu](http://bonaveo.net/2006/10/use-opendns-on-ubuntu-linux/)

---

### Post by handy on 2006-10-27
Yes thanks for the heads up on OpenDNS, I'm using them now too.

Apart from the obvious benefits; my ISP changes their DNS addresses whenever they feel like it (or so it would seem :(  ) So using OpenDNS should give me a more reliable service, which basically means I don't have to **prepend** new IP's in the **/etc/dhcp3/dhclient.conf** every time they change... :D

---

### Post by Aleksandersen on 2006-10-28
I live in Norway, and the nearest OpenDNS location is in the UK (that might not be online yet, so I may actually be using the US service).

I still have a notable increased speed when using OpenDNS.

---

### Post by handy on 2006-10-28
> **Aleksandersen said:**
> I live in Norway, and the nearest OpenDNS location is in the UK (that might not be online yet, so I may actually be using the US service).

I still have a notable increased speed when using OpenDNS.

I live in Australia, & I can be pretty sure that I'm using the US server's too.

Logging on to my internet banking & web based email was slower, I'll see how that is as  time goes by.  If it remains slower I can live with it! My browsing is as fast or faster apart from those 2 instances so far!

I must say I like the attitude of the OpenDNS people, they come across as open & honest & clever.  Has that nice blend of smarts with heart... :KS

---

