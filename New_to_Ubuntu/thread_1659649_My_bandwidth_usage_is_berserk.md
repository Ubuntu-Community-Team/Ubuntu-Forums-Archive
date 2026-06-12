---
title: "My bandwidth usage is berserk"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by jermza on 2011-01-04
A few days after I installed Ubuntu, I decided to use Evolution instead of Gmail (via the browser).

I have it set up to IMAP and don't have folder synchronisation on.

I'm saying this because I THINK Evolution might be destroying my bandwidth.  But I hope I'm wrong.

My ISP says that I've used 9 gigs in four days.  I've not done anything unusual or different to my usual activities (which hit 10 gigs in a month).

What could be happening here?  What software - if any - could be eating bandwidth like this?  

I don't have a wireless network either, and the ISP says that all the traffic is coming from my line alone.

I don't know Ubuntu well enough to know what could cause this (other than, say, someone illegally tapping into my physical line at the exchange).

Any advice / troubleshooting?

---

### Post by cariboo on 2011-01-04
That seems to be a lot of usage for just an email client. Open a terimanl and type:

```
netstat -t
```

to see where your system is connecting to, This is what my system looks like with just Firefox and Chromium open.

```
netstat -t
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 chilanko.local:48268    px-in-f125.:xmpp-client ESTABLISHED
tcp        0      0 chilanko.local:54585    24.244.19.222:www       ESTABLISHED
tcp        0      0 chilanko.local:52738    pv-in-f190.1e100.ne:www ESTABLISHED
tcp        0      0 chilanko.local:58273    pv-in-f138.1e100.ne:www ESTABLISHED
tcp        0      0 chilanko.local:33599    24.244.19.159:www       ESTABLISHED
tcp        1      0 chilanko.local:48200    xml.weather.com:www     CLOSE_WAIT 
tcp        1      0 chilanko.local:44364    xml.weather.com:www     CLOSE_WAIT 
```

---

### Post by earthpigg on 2011-01-04
howdy,

lets verify that it is coming from your computer.

take a look [here]("http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-ubuntu-users.html").

run bmon from a terminal. is your connection constantly using bandwidth in the tens of KiB range? does it spike/decreace when certain programs are started and stopped? test the waters by hitting reload on some random webpage and watching it spike for a second.

take a look at iftop.

```
sudo iftop -i eth0
```

what specific hosts is your computer connecting to? if you run this command, it may give you more hints about 'em:

```
whois hostname-or-ip-address-here
```

---

### Post by egalvan on 2011-01-04
{edit}

---

### Post by yoma1977 on 2011-01-04
After some googling i came across this little tool called nethogs.

it lists various programs and their bandwidth usage

from a terminal run

```

sudo apt-get install nethogs
sudo nethogs

```

This way you should be able to find out what's using up your bandwidth (if the traffic even comes from your linux box)

---

### Post by jermza on 2011-01-04
> **yoma1977 said:**
> After some googling i came across this little tool called nethogs.

it lists various programs and their bandwidth usage

from a terminal run

```

sudo apt-get install nethogs
sudo nethogs

```This way you should be able to find out what's using up your bandwidth (if the traffic even comes from your linux box)

I've downloaded it.  Thank you very much.  Will come back here with an update, soon.

---

### Post by jermza on 2011-01-10
It seems that nothing much has changed.  Ubuntu is eating up my bandwidth and I have no idea how or where.

I've tested by quitting Gwibber and Empathy and even made sure that Evolution is using IMAP and synchronising nothing, just about.  

I have been running Nethogs and System Monitor to see the activity, and Evolution pops up a lot.

I've now changed Evolution' settings to check mail every 10 minutes, instead of every minute.  (In Outlook, I checked mail every minute and it didn't eat up my bandwidth like this.)

Is Evolution the cause?  (It seems to be.)

**Edit:**

I notice that "telepathy" pops up a lot too.
And something to the effect of "erts-5.7.4".

---

### Post by JBAlaska on 2011-01-10
I'm guessing you have a wireless router and someone is stealing your bandwidth. Make sure your wireless encryption is enabled and your using wpa2 personal (AES), if your using WEP you might as well be using no encryption as anyone over 10 years old can crack that in about 5 min. (No offense to younger users who can crack WEP lol)

---

### Post by jermza on 2011-01-10
> **JBAlaska said:**
> I'm guessing you have a wireless router and someone is stealing your bandwidth. Make sure your wireless encryption is enabled and your using wpa2 personal (AES), if your using WEP you might as well be using no encryption as anyone over 10 years old can crack that in about 5 min. (No offense to younger users who can crack WEP lol)

Nope.  Wired router.  

Besides, I can see in my System Monitor the activity.  In the last hour, I've received over 100MB and have no idea where it's going or what it is.

This is really ridiculous.  I'm considering going back to Windows if this carries on.  I've used 15 gigs of traffic in 10 days (of doing nothing unusual).

---

### Post by JBAlaska on 2011-01-10
That is strange. Try this:
```
sudo apt-get install wireshark
```

Once the program installs, start it ```
gksu wireshark
``` and click on Capture help, how to capture. Then you can at least see what is being downloaded.

Good luck.

---

### Post by jermza on 2011-01-10
> **JBAlaska said:**
> That is strange. Try this:
```
sudo apt-get install wireshark
```Once the program installs, start it ```
gksu wireshark
``` and click on Capture help, how to capture. Then you can at least see what is being downloaded.

Good luck.

Thanks very much.  I did that, but have no idea what's going on, or what half those options mean. :-(

---

### Post by jermza on 2011-01-10
In Ubuntu, what is known for hogging bandwidth?

Does using Gwibber, for example, hog bandwidth?  

Also, where is all this data - that I'm receiving - going?  My PC has been on for about 2 hours and has received nearly 200mb of data.  (I've been doing very little, other than emailing and working in Gimp.)

[B]Edit
[/B]
See attachment.  This is after around two hours of my PC being turned on (and very little internet usage.)

---

### Post by jermza on 2011-01-10
Let me ask those questions in another way.

How much bandwidth, on average, should a typical Ubuntu installation use, daily?  

(By typical, I am including Gwibber with a few accounts, Empathy with a few accounts, Evolution IMAP, general internet browsing, etc.)

**Edit**

I've quit Evolution and it "seems" that my traffic usage has dramatically dropped.  I'll keep Evolution closed for a few hours to test this...

---

### Post by jermza on 2011-01-10
Having a conversation with myself but it's no problem. :-)

The guys on the Evolution mailing list seemed to have found the problem.  When getting mail via IMAP, I had "check for new messages" checked.

Apparently, IMAP doesn't require the client to check for new messages.  I unchecked it and then checked "use idle mode".

They're of the opinion that this might be a UI bug that needs to be fixed.

For the time being, everything is running at respectable traffic levels...

---

### Post by earthpigg on 2011-01-10
> **jermza said:**
> For the time being, everything is running at respectable traffic levels...

Glad it all worked out.

---

