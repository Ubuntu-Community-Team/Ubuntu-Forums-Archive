---
title: "Slower and slower wifi with feisty"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by Sendervictorius on 2007-04-26
Although wifi under feisty is working, the performance is bad. Under dapper  I get around 1000kbps up and down on my cable connection. Under feisty I'm lucky to get 250kbps. And what's worse, the performance seems to drop off the longer I'm connected. Repository downloads start ok, but get slower and slower. Web pages download ok, but often dont complete, with the last graphics never loading.

When I look at network monitor,  notice there is always an 800bps recieve rate even though there is no internet trafic at the time. Under dapper recieve drops to zero with no traffic.

The first 100kB to 200kB or so of download seem to go ok, but then it stops, never to complete. Other internet traffic like web page downloads still work.

I have a clean feisty install, and can dual-boot feisty and dapper. NIC is Atheros AR5212. connection is DHCP, and WEP.

Does anyone know how i can diagnose the problem, or have suggestions about what might be happening?

---

### Post by stu_edgar on 2007-04-26
I have had similar problem.
It is intermittent.
I think this thread  might be linked to this bug on launch pad

[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940")

Hope that helps

---

### Post by Sendervictorius on 2007-04-27
Thanks. 

I took a look at your System Monitor Screenshot - looks exactly like mine. Spikes of activity with gaps of silence between.  

I couldn't follow the thread very well. Did you resolve the issue by chnaging the /etc/nsswitch.conf "hosts: files" line?

---

### Post by Sendervictorius on 2007-04-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The suggestion in the launchpad bug thread seems to have worked well enough for me get usable download performance. Its not a perfect workaround though. There is a long delay before downloads start, but once they start things seem to rocket along at a reasonable speed.

To fix, I edited  /etc/nsswitch.conf

and changed
```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```
to
```
hosts: files mdns4_minimal [NOTFOUND=return] dns
```

I had no idea what I was doing however, so if anyone can tell me,  I might understand what's going on.

---

### Post by Sendervictorius on 2007-04-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This hosts entry in /etc/nsswitch.conf works even better. It fixes the long delay at the beginning of a download.

```
hosts: files dns
```

So, it does look like my problem was bug 94940, and this workaround does fix it.

---

### Post by jmagsho on 2007-05-03
Sender, thanks for the info on this.  It seems to have helped my abysmal wireless performance since the Feisty upgrade.

---

### Post by lukew on 2007-06-01
Thanks for the heads up; having the same problem here.

This fix makes downloads more manageable. i.e less drag time for web though peaks at no more than 50KB/s and stays around 30KB/s; less for web browsing. Swap to wired and back up to 280KB/s.

This is very anoying still but atleast it is manageable. Most web pages were timing out.

Thanks again for post.

Luke

---

### Post by lnm477 on 2007-06-01
I am having the same problem.  I would like to try to use this fix, however I seem to be having a problem editing the /etc/nsswitch.config file.  When using the sudo gedit /etc/nsswitch.config, I come up with a blank screen as if the file doesn't exist.  I've looked in the file system=>etc and can see the nsswitch.config file, but cannot edit it.  It is a read only file.  I'm thinking I may have to login to the root user, but being very new to linux, I have no idea how to do that because at the login screen it won't allow me to login as root.  If you could assist me with this giving instructions for morons, I would greatly appreciate it.

---

### Post by lukew on 2007-06-01
> **lnm477 said:**
> I am having the same problem.  I would like to try to use this fix, however I seem to be having a problem editing the /etc/nsswitch.config file.  When using the sudo gedit /etc/nsswitch.config, I come up with a blank screen as if the file doesn't exist.  I've looked in the file system=>etc and can see the nsswitch.config file, but cannot edit it.  It is a read only file.  I'm thinking I may have to login to the root user, but being very new to linux, I have no idea how to do that because at the login screen it won't allow me to login as root.  If you could assist me with this giving instructions for morons, I would greatly appreciate it.

conf not config. Always tab to auto complete in the buffer; maked life so much easier.

---

### Post by insert_name_here on 2007-06-01
Would this be the same as my increasingly worse signal strength while in feisty?

When in windoze or edgy or dapper, I can see about 10 access points from my dorm room.  With Feisty I can only see 4 or 5, and can only connect to one or two, and my signal strength is so bad I am disconnected every few minutes.  The longer my session has been running, the worse the connection is.  

Any ideas?

---

### Post by lnm477 on 2007-06-01
Thank you Luke for the quick reply.  I can't tell you how many times, I looked at that and saw config not conf.  Thanks for the autocomplete tip. That worked like a charm.  This other tip about editing /etc/nsswitch.conf file didn't help my problem of slower than dialup wirless connection.  Any other ideas?

Thanks for your help

---

### Post by lukew on 2007-06-01
> **lnm477 said:**
> Thank you Luke for the quick reply.  I can't tell you how many times, I looked at that and saw config not conf.  Thanks for the autocomplete tip. That worked like a charm.  This other tip about editing /etc/nsswitch.conf file didn't help my problem of slower than dialup wirless connection.  Any other ideas?

Thanks for your help

Its ok. The original post did not work for me 100%; just made things better. I am going to have a play and any findings i will get back to you. 

Luke

---

### Post by lnm477 on 2007-06-01
I realized that my problem is with my router settings.  On a whim, I connected to an unsecured network, and bang!  I got a lightning speed internet connection.  I switched back to my own network and couldn't connect to the internet nor any of my network (windows) conputers.  I disabled the wep encryption and was able to get a slow internet connection.  I enabled the wep encryption and got no internet connection again.  Any ideas?

---

### Post by lnm477 on 2007-06-02
Here's an update on my situation.

1- Re-formatted hard drive
2-Re-installed Feisty
3-Fiddled with bcm43xx-fwcutter Got network up and running.  Not blazing speed, but at speed test got 2984 d/l 784 u/l.  Logged into unsecured network did speed test  6984 d/l forgot u/l.
4- did automatic updates.
5- Logged in to unsecured network did speed test d/ dropped to 2984/ d/l  200 u/l.  Logged into my own secured network and couldn't even get to the web page that had the speed test.

My advice?  don't do automatic updates.

---

### Post by lukew on 2007-06-02
I found a post about removing all entried in /etc/network/interfaces except the loopback. Create /etc/default/wpasupplicant with enabled=0. Touch the file and restart.

It stated that network manager through system admin will show wpa; it did not but nm-applet did. I can not connect and though things are not 100% Things are 98% good. just a little drag on some web pages. It must be noted that i undid the change from previous (nsswitch add) so this might be worth a change.

Unfortunatly i can not find the original post to my actions....

Luke

---

### Post by Sendervictorius on 2007-06-09
Update to my original posts when I started this thread.

I eventually tracked down my problem with slow wifi performance after following a lot of dead ends, and trying all manner of suggestions from the forums. These dead ends included disabling IPv6 and removing avahi and editing nsswitch.conf hosts line to remove mdns4_minimal and mdns. These dead ends helped a bit, but they didn't fix the problem totally.

So, I resorted to installing Ethereal, and went looking at what was happening on my network. I was getting a load of fragmented Ethernet packets over wlan0, probably because the signal strength was poor. 

Then I searched the forums, and found out that the madwifi driver (for my D_link card Atheros AR5212 chip set ) shipped with feisty has problems (a bug)  with signal strength.

I found this thread [http://ubuntuforums.org/showthread.php?p=2688436#post2688436](http://ubuntuforums.org/showthread.php?p=2688436#post2688436) that was useful.  [I tried using ndisgk got a lockup, so resorted to ndiswrapper on command line]. 

After a bit of faffing around I got my network going, and now it works great. Performance couldn't be better.

So, I learned two things:
1. the madwifi driver for feisty is borked
2. don't blindly try things in the hope that it might work - track down the problem by looking for evidence.

Hope this will be useful for someone.

---

