---
title: "Impossible to stop outgoing NTP port 123 connections"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by mistypotato on 2009-05-01
Hi,

I have been trying to stop outgoing time update requests from my server for over a month now with no success.  I have looked in list of running programs and can't find any that do this.

Firestarter shows several hundred blocked attempts every day ( I blocked port 123) but I want to stop the process that is doing it.

I have used  synaptic to uninstall everything related to time and date synchronizing to no avail.

Can anyone point me in the right direction?

Thanks!

---

### Post by wizard10000 on 2009-05-01
> **mistypotato said:**
> Hi,

I have been trying to stop outgoing time update requests from my server for over a month now with no success.  I have looked in list of running programs and can't find any that do this.

Firestarter shows several hundred blocked attempts every day ( I blocked port 123) but I want to stop the process that is doing it.

I have used  synaptic to uninstall everything related to time and date synchronizing to no avail.

Can anyone point me in the right direction?

Thanks!

Stop or uninstall the NTP daemon?

sudo apt-get remove ntpdate

---

### Post by mistypotato on 2009-05-01
It says "NOT INSTALLED, SO NOT REMOVED" when I tried that?

See what I mean ???

---

### Post by wizard10000 on 2009-05-01
> **mistypotato said:**
> It says "NOT INSTALLED, SO NOT REMOVED" when I tried that?

See what I mean ???

Yup.

The only application-based firewall I know of for Linux is TuxGuardian but development on it has stalled - maybe it'd be a good idea to give it a try and find out exactly what application is looking for a time hack.

Sorry, I don't have anything better.

---

### Post by arapa on 2009-05-01
The ```
lsof -i
``` command will show you a list of programs currently using a port.

You can also lsof -i :*port* for example, ```
lsof -i :123
```

Does this help?

---

### Post by mistypotato on 2009-05-01
Thanks.

That command returns no response.

Meaning when I type it in, it seems to accept the command, but just goes back to the command line for the next command.

When I do lsof -i

It returns a few lines (none of them with port 123) about java listening on ports 52994, 53495, 51565, 6800 and 8600. (I know what 6800 & 8600 are)

It still attempts to connect to various servers around the globe EXACTLY every 10 seconds.

---

### Post by wizard10000 on 2009-05-01
> **mistypotato said:**
> Thanks.

That command returns no response.

Meaning when I type it in, it seems to accept the command, but just goes back to the command line for the next command.

That's because the port has to be in use when the command is executed.

---

### Post by wizard10000 on 2009-05-01
Mine says this -

```
COMMAND     PID  USER   FD   TYPE DEVICE SIZE NODE NAME
firefox   13902 wizard   22u  IPv4 691924       TCP wizard-desktop.local:57028->feijoa.canonical.com:www (ESTABLISHED)
firefox   13902 wizard   38u  IPv4 691864       TCP wizard-desktop.local:55409->iy-in-f102.google.com:www (ESTABLISHED)
gvfsd-smb 26095 wizard   13u  IPv4 523236       TCP wizard-desktop.local:50620->192.168.1.102:netbios-ssn (ESTABLISHED)

```

If I run it under sudo I get:

```
COMMAND     PID  USER   FD   TYPE DEVICE SIZE NODE NAME
avahi-dae  2787 avahi   14u  IPv4   7387       UDP *:mdns 
avahi-dae  2787 avahi   15u  IPv4   7388       UDP *:41295 
saned      2832 saned    4u  IPv4   7495       TCP *:sane-port (LISTEN)
saned      2834 saned    4u  IPv4   7495       TCP *:sane-port (LISTEN)
dhclient   3114  root    5u  IPv4   8125       UDP *:bootpc 
firefox   13902 wizard   38u  IPv4 691864       TCP wizard-desktop.local:55409->iy-in-f102.google.com:www (ESTABLISHED)
mpd       20734   mpd    4u  IPv4 321445       TCP localhost:6600 (LISTEN)
gvfsd-smb 26095 wizard   13u  IPv4 523236       TCP wizard-desktop.local:50620->192.168.1.102:netbios-ssn (ESTABLISHED)
cupsd     26778  root    2u  IPv6 663018       TCP localhost:ipp (LISTEN)
cupsd     26778  root    3u  IPv4 663019       TCP localhost:ipp (LISTEN)

```

---

### Post by mistypotato on 2009-05-01
Thanks for your help wizard.

This one has been an ongoing issue for me for several months now.  Some other people tried to help then and there were some posts but none of them helped me resolve the issue.

Maybe it's a cron job that runs because it happens every 10 seconds exactly.

Time and Date settings are set to MANUAL, not automatic.

How could I check that?

Thanks

---

### Post by mistypotato on 2009-05-01
I installed gnome-schedule to check for cronjobs and none were found.

Now I'm REALLY at a loss.

Can noone help with this?

---

### Post by arapa on 2009-05-01
What about using the watch command in conjunction with the lsof -i like this?

sudo watch -n .5 lsof -i :123

the watch command's '-n 1' is the interval it checks in seconds. The default is 2 seconds. You can also use smaller increments of a second ie "watch -n .1". 


Let it run until it catches the bugger. Then hit CTRL + C to stop it.

---

### Post by mistypotato on 2009-05-01
Hey,

I LIKE that :KS

I have it running now.

So far nothing has popped up but I'm going to give it a while.

Whatever "IT" is runs every 10 seconds so I would think it would get a hit before long?

Thanks!   Hope it tells me something.

---

### Post by brian_p on 2009-05-01
> **mistypotato said:**
> Hi,

I have been trying to stop outgoing time update requests from my server for over a month now with no success.  I have looked in list of running programs and can't find any that do this.

Firestarter shows several hundred blocked attempts every day ( I blocked port 123) but I want to stop the process that is doing it.



These outgoing requests are all on port 123 and at 10s intervals? May we see a log of this?

---

### Post by wizard10000 on 2009-05-01
> **mistypotato said:**
> Thanks for your help wizard.

This one has been an ongoing issue for me for several months now.  Some other people tried to help then and there were some posts but none of them helped me resolve the issue.

Maybe it's a cron job that runs because it happens every 10 seconds exactly.

Time and Date settings are set to MANUAL, not automatic.

How could I check that?

Thanks

I do have another suggestion.  If this is happening every ten seconds it should be fairly easy to catch.

First, open port 123 back up.  I think if you're dropping connections at the firewall maybe you won't see an open port.

Then do this -

```

sudo -i

(that gives you a persistent root prompt)

for f in $(seq 1 10); do lsof -i :123 >> /home/username/Desktop/lsof.txt; done

```

This will run ten loops of lsof, appending to a text file on your desktop.  We've targeted port 123 so you can just let it run for awhile.  If you need more loops just change the number 10 to something else  ;)

With the port open and lsof recording activity you should be able to find the process that's causing all the traffic.

Good luck -

---

### Post by mistypotato on 2009-05-01
ok, upon closer examination, whatever "IT" is is only running at 33 minutes past the hour every hour and it runs for 1 minute.   Then it stops until 33 past the next hour.

I'll have to wait until then I suppose.

---

### Post by unutbu on 2009-05-01
Building on arapa's suggestion, the command
```

watch -n 0.5 'lsof -i :123 >> ~/Desktop/lsof_123'
```

will log activity on port 123 to the file ~/Desktop/lsof_123, so you don't have to watch it yourself.

---

### Post by wizard10000 on 2009-05-01
> **unutbu said:**
> Building on arapa's suggestion, the command
```

watch -n 0.5 'lsof -i :123 > ~/Desktop/lsof_123'
```

will log activity on port 123 to the file ~/Desktop/lsof_123, so you don't have to watch it yourself.

That's a much more elegant solution than my silly little for-next loop  ;)

---

### Post by brunogirin on 2009-05-01
Note that you have two potential packages for NTP: ntpdate will just adjust the date when requested or in a cron, while ntpd will run as a daemon. So you could try this:

```
sudo /etc/init.d/ntp stop
```

And to remove it completely:

```
sudo apt-get remove ntp
```

---

### Post by mistypotato on 2009-05-01
Well,

Here is what was captured?  Not sure how to decypher that?

[?1049h[1;24r[m(B[4l[?7h[H[2JEvery 0.1s: lsof -i:123[1;57HFri May  1 14:21:59 2009[24;80H[1;72H2:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H3:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H4:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H5:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H6:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H7:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H8:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H9:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;71H30:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H1:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H2:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H3:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H4:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H5:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H6:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H50[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;72H7:00[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H10[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H20[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H30[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H[1;75H6[24;80H[1;75H7[24;80H[1;75H8[24;80H[1;75H9[24;80H[1;74H40[24;80H[1;75H1[24;80H[1;75H2[24;80H[1;75H3[24;80H[1;75H4[24;80H[1;75H5[24;80H

---

### Post by mistypotato on 2009-05-01
> **brunogirin said:**
> Note that you have two potential packages for NTP: ntpdate will just adjust the date when requested or in a cron, while ntpd will run as a daemon. So you could try this:

```
sudo /etc/init.d/ntp stop
```

And to remove it completely:

```
sudo apt-get remove ntp
```

[COLOR="Red"]**When I try this the response is....**[/COLOR]

***[COLOR="Blue"]Package ntp is not installed, so not removed[/COLOR]***

---

### Post by unutbu on 2009-05-01
The single quotes around ```
'lsof -i :123 >> ~/Desktop/lsof_123'

``` should have made the output look cleaner than what you posted. The output you are seeing is just the timestamp moving. 
Did you have single quotes in the command you used? If not, try it again with quotes.

---

### Post by mistypotato on 2009-05-01
Still in Limbo over this one :confused:

seems it should not be this difficult?

---

### Post by mistypotato on 2009-05-01
> **unutbu said:**
> The single quotes around ```
'lsof -i :123 >> ~/Desktop/lsof_123'

``` should have made the output look cleaner than what you posted. The output you are seeing is just the timestamp moving. 
Did you have single quotes in the command you used? If not, try it again with quotes.

ok, sorry, I omitted the single quotes.  I'll try again.

I have to wait until 3:30 when it cycles again.

---

### Post by brian_p on 2009-05-01
> **mistypotato said:**
> 

I have to wait until 3:30 when it cycles again.

While we are waiting may we see any sort of log? From firestarter, perhaps.

---

### Post by mistypotato on 2009-05-01
This time the file came back empty.

I changed the permissions to the file to my user and so I'll try again at 5:30



Where would I find the firestarter logs?

---

### Post by brian_p on 2009-05-01
> **mistypotato said:**
> 

Where would I find the firestarter logs?

The 'Events' page, I believe. But, in essence, what are you looking at which tells you something is connecting out on port 123 at 33 minutes past the hour every hour and running for 1 minute?

---

### Post by The Cog on 2009-05-01
How about you run these two commands, and leave it running. It should print the process name when it connects:
```
sudo -i
while true  ; do netstat -nalutp | grep ':123 ' ; sleep 1 ; done
```

---

### Post by starz677 on 2012-04-03
> **The Cog said:**
> How about you run these two commands, and leave it running. It should print the process name when it connects:
```
sudo -i
while true  ; do netstat -nalutp | grep ':123 ' ; sleep 1 ; done
```

This may be an old thread...but I have the exact same problem and I am using this thread to locate a resolution.
(Please don't close it if not absolutely necessary?)

I just tried "**[COLOR=Red]The Cog's[/COLOR]**" suggestion but there was no output at all.
I also tried the previous suggestions but the output was unhelpful and the same as the OP's listed in an earlier post.

I still have not found a way to determine what process is creating these outgoing calls on port 123.  Some to The Russian Federation and many to hostile sites around the globe.  My assessment at this point is that a file has been altered such as a web page or a vbulletin forum script.   That or there is something in a database that creates a process to create these calls.   There is no NTP service running.   None of the calls get past the firewall because I have that port blocked, but I sure wish I could once and for all resolve this.

It also appears a cron job has been created because it occurs like clockwork at a specific time every hour.
I looked through the cron jobs but didn't see anything.   A hidden cron job maybe?

Does anyone else have any suggestions?

thx

---

### Post by lisati on 2012-04-03
@starz677: a lot can change in 2 years. Please start a new thread.


Thread closed.

---

