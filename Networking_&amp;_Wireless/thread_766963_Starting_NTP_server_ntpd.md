---
title: "Starting NTP server ntpd"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by HuckleSmothered on 2008-04-25
Just upgraded from Gutsy to Hardy.

When I boot up, no network. So I do a **/etc/init.d/networking restart** and it goes through the whole deal but at the end, it hangs at: 

Stopping NTP server ntpd 
... done
Starting NTP server ntpd 
... done

Eventually I'm able to get my wireless to work, after a **sudo ifdown eth0** the eth1 (my wireless) will start working. Sometimes it takes some playing around with of ifdown eth1 then ifup eth1, etc. Even when doing ifup's I get the NTP server message and it just hangs there. I have to ctrl-c to get a command prompt again.

I've also tried setting the time manually, as opposed to using an NTP server, no change though, still happens.

Anyone know what is causing this?

It did not happen with Gutsy.

---

### Post by sports fan Matt on 2008-04-28
I have the exact same issue...

---

### Post by Swiftfeet8 on 2008-04-28
First do you have devices or computers on your network that need a local NTP server?  You probably don't need an NTP server running on your PC.  This is not the same as getting your time from an NTP server.  Essentially your computer is setup to give out time to other devices/computers.  It would be pretty safe to say that unless you know you need it, you could get rid of ntpd.

As far as the wireless working when you do an ifdown on your LAN connection, it might be because you don't have one of the connections setup as roaming and the other set as manual.  Not completely sure, but check the setting in Network Settings and try setting everything to roaming.  Let me know if this helps.

---

### Post by djconnel on 2008-04-28
I have the same issue.  How do I shut off attempts at establishing ntp services?  I certainly never requested it, nor did this problem occur prior to upgrading to 8.04.

Do I simply delete these  lines in /etc/services?
ntp		123/tcp
ntp		123/udp				# Network Time Protocol

thanks,
Dan

---

### Post by Swiftfeet8 on 2008-04-28
The ntp service that you are referring to is what keeps your computers clock sync'd with a computer/clock across the internet.  If you want to turn off synchronization you can go into "System > Administration > Time and Date".  You can then change the time to "Manual".

Are you having the same problems with getting your internet to work as the original poster?

---

### Post by djconnel on 2008-04-28
My particular problem is when I take my Lenovo T60 out of suspend, there is a long delay during which ntp services are stopped, then started again.  I receive the same message:
"stopping ntp server ntpd"
"starting ntp server ntpd"

I have no interest in serving time, but would prefer that once per day, or at reboot if I'm on the net, the system access an on-line time server and reset my clock.  So this is why I haven't set the clock to "manual".

---

### Post by tweedledee on 2008-04-28
I'm not entirely sure what the change was, but apparently the "ntp" package in Hardy now runs a local ntp server, whereas in Gutsy it did not.  The correct package to just sync time to a server is ntpdate.  Anyone upgrading from Gutsy to Hardy has the ntp package, and so it gets upgraded, with the result that you are now running a server.  You can uninstall ntp and keep ntpdate for syncing purposes.

The issue is slightly more complex than that, I stopped working out the details once I found removing ntp and keeping ntpdate worked.  I'm actually not sure why Gutsy installed ntp, as it wasn't necessary then, either.

---

### Post by Swiftfeet8 on 2008-04-28
Wow, I wasn't aware that Heron installed an ntp server.  Just follow what tweedledee said above and it should fix your problem.  I know that Ubuntu has had issues with coming out of suspend/hibernation.  I am not sure if the issues were fixed in Heron or not.

---

### Post by kevdog on 2008-04-28
So the best way to run ntpdate is to run it through the root or system wide cron file (say once a day or once an hour)?  This is the solution so many are after right now.

---

### Post by tweedledee on 2008-04-29
> **kevdog said:**
> So the best way to run ntpdate is to run it through the root or system wide cron file (say once a day or once an hour)?  This is the solution so many are after right now.

The issue is looking more complex.  Apparently ntpd has always been responsible for ntp time syncing in Ubuntu, it's just that the version that ships with Hardy also runs a local server.  Ntpdate must be run manually (or manually placed in cron.hourly or .daily), and must specificy a server on the command line when invoked.  Although the system clock still appears to be configured for ntp when you only have ntpdate installed, I don't believe it is actually doing so automatically.

I don't have time now, but within a day I'll search launchpad and if there isn't an active, accurate bug report I will initiate one; simply keeping my clocked synced should not require this much effort OR a local server, especially since it worked fine in previous versions.

---

### Post by HuckleSmothered on 2008-04-29
Ok, I unchecked the box under **System | Administration | Services** for **Clock Synchronization Service (ntp)** and did a **/etc/init.d/networking restart**.
The NTP messages still came up.
Then I ran **sudo apt-get remove ntp**
Restarted networking again, this time it worked!

However, based on your replies to my initial problem, I ran **ntpdate** because I DO want to have my clock automatically synch'd.
ntpdate gave me an error: *no servers can be used, exiting*
After breezing through the manual pages for it, I saw it uses a **/etc/ntp.keys** file similar to ntpd's configuration file.
I had none.
Hence the possible reason for failure of running **ntpdate**?
BUT, looking into my Services again, the NTP service has been re-checked.
... I had just set my clock from manual to update from NTP server ...
Does this mean I am now synching with NTP servers but not running an NTP daemon now (since I removed NTP)?
Or is it just going to TRY to synch but never do it since **ntpdate** is not working and **ntp** is not installed?

---

### Post by tweedledee on 2008-04-29
Got it figured out.  The very short version is that you can safely remove ntp and ntpdate will still occasionally synchronize time with no further effort on your part, but that will not be true in future Ubuntu releases.

The key is the file /etc/network/if-up.d/ntpdate.

This file is run whenever you reset networking (strictly speaking, whenever a network interface comes up - which means if you have multiple ones, it runs for each upon /etc/init.d/networking restart).  Within it are the following relevant lines: ```

invoke-rc.d --quiet ntp stop || true

/usr/sbin/ntpdate-debian -s $OPTS 2>/dev/null

invoke-rc.d --quiet ntp start || true
```

What this means:
1) ntpdate is executed each time your network interfaces restart (i.e., at a minimum upon each boot).  I have confirmed that the command actually works and will sync your time.

2) The first and last lines are what cause ntpd to restart.  You can safely comment those out to prevent ntpd from doing so.  ntpd must be synchronizing at other times as well, and apparently needs to restart to recognize new servers (e.g., if you were switching networks and wanted to synchronize to a new server on the new local network, which applies to presumably very few people).  I assume nptd is also synchronizing at other times, but I don't know how often.

However, this will likely not be true in future releases of Ubuntu, as discussed in passing here: [https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/83604](https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/83604).  Basically, ntpdate is officially deprecated and will be removed in future versions, leaving only ntpd (in the ntp package).  ntpd is more accurate, but obviously also runs a full server, which seems absurd.  There used to be an /etc/network/if-up.d/ntp file in addition to the ntpdate file there; my guess is that future releases will revert back to the ntp file in favor of ntpdate, but have a similar server restart.  As I find it highly objectionable that the server automatically runs just to synchronize time (because it DOES open ports on your computer for others to connect to it), I'm still going to file a new bug report on this to address that problem.

---

### Post by bradhamilton on 2008-07-10
> **tweedledee said:**
> Got it figured out.  The very short version is that you can safely remove ntp and ntpdate will still occasionally synchronize time with no further effort on your part, but that will not be true in future Ubuntu releases.

The key is the file /etc/network/if-up.d/ntpdate.

This file is run whenever you reset networking (strictly speaking, whenever a network interface comes up - which means if you have multiple ones, it runs for each upon /etc/init.d/networking restart).  Within it are the following relevant lines: ```

invoke-rc.d --quiet ntp stop || true

/usr/sbin/ntpdate-debian -s $OPTS 2>/dev/null

invoke-rc.d --quiet ntp start || true
```

What this means:
1) ntpdate is executed each time your network interfaces restart (i.e., at a minimum upon each boot).  I have confirmed that the command actually works and will sync your time.

2) The first and last lines are what cause ntpd to restart.  You can safely comment those out to prevent ntpd from doing so.  ntpd must be synchronizing at other times as well, and apparently needs to restart to recognize new servers (e.g., if you were switching networks and wanted to synchronize to a new server on the new local network, which applies to presumably very few people).  I assume nptd is also synchronizing at other times, but I don't know how often.

However, this will likely not be true in future releases of Ubuntu, as discussed in passing here: [https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/83604](https://bugs.launchpad.net/ubuntu/+source/ntp/+bug/83604).  Basically, ntpdate is officially deprecated and will be removed in future versions, leaving only ntpd (in the ntp package).  ntpd is more accurate, but obviously also runs a full server, which seems absurd.  There used to be an /etc/network/if-up.d/ntp file in addition to the ntpdate file there; my guess is that future releases will revert back to the ntp file in favor of ntpdate, but have a similar server restart.  As I find it highly objectionable that the server automatically runs just to synchronize time (because it DOES open ports on your computer for others to connect to it), I'm still going to file a new bug report on this to address that problem.

Running 7.10 on a laptop at home, behind a firewall...

OK - first of all, apologies if I'm opening a can of worms here...

I want to avoid using ntpdate at all; I have a computer system, and I don't need to be running commands manually!        :-)

What I want to do, very simply, is to keep ntpd running at all times (yes, I know, it's insecure, and will destroy world peace, etc., but this is what I want to do).

I removed ntpdate and ntp, and re-installed ntp only.  I checked the syslog, and I notice that ntpd actually runs at boot time, syncs to the servers that I have configured in /etc/ntp.conf, and then (somehow) stops running.  I want it to stay up after boot, and continue to make the minute adjustments that it is supposed to make to keep my system's clock in sync with the servers, all without my having to issue commands (my fingers have more important things to do, like bother you folks with questions...:-).

How do I accomplish this goal *without* resorting to cron entries to periodically restart ntpd?  And why does ntpd exhibit this behavior?  I run ntpd on my home VMS system, and it starts up and stays running after boot time, all without manual intervention on my part.  I also seem to recall running other flavors of "Linux" (Slackware, RedHat, etc.) and don't recall ntpd exhibiting this behavior.

TIA

---

### Post by bradhamilton on 2008-07-10
Apologies for the bad form of following up on my own post, but...

I first asked this question here, because all of my searching through the forums here led me to lots of posts where folks wanted to know how to mimic ntpdate using ntpd.

Since my question is exactly the opposite, I decided to Google "ntpd -q", and found to my surprise that virtually everyone wants to mimic ntpdate using ntpd.

I'm now diligently searching through all my files to see if I can find a script that actually runs "ntpd -q" at boot time, but I'm afraid I won't have much luck.        :-(

---

### Post by BassKozz on 2009-10-15
Not sure if my issue is related or not, but I am using the server edition of Ubuntu Jaunty 9.04 (64bit) in a VM.  And My networking is also getting hung up on "Starting NTP server ntpd".
I am confused as to why and what the correct solution is to resolve this problem while still keeping clocks in sync?

---

