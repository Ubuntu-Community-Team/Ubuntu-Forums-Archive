---
title: "Network connectivity issues all of a sudden"
date: 2014-10-10
forum: Networking &amp; Wireless
---

### Post by ian49 on 2014-10-10
I had until a couple of days ago been running a pc and laptop both using Ubuntu 14.04 and was able to network them using samba without any issues.

Suddenly, things have stopped working. Firstly, my Windows 7 VMWare installation was no longer able to use a bridged network connection and the only way I was able to access the internet from Win 7 was to switch to NAT.

But then back on the host Ubuntu pc I also suddenly found that I was no longer able to view the contents of the shared folder on my laptop. Attempts to connect gave the following error message:

Could not open location 'smb://laptop/share/'
Failed to mount windows share: no route to host

Similarly the laptop is unable to view the shared folder on the pc. They are all part of the MSHOME workgroup and I have changed none of the settings. The only thing that's changed was that both pc and laptop had a 14.04 upgrade so I'm wondering if that has somehow broken something?

Someone suggested I do an nbtscan and I got the following output from it when running it from the pc:

192.168.1.0    Sendto failed: Permission denied
192.168.1.72     IAN4150          <server>  IAN4150          00:00:00:00:00:00
192.168.1.255    Sendto failed: Permission denied

I really rely on the ability to share files between the pc and the laptop - can anyone suggest what might have gone wrong and how I could fix it?

---

### Post by weatherman2 on 2014-10-10
Can you ping one machine from the other?

Have you tried using IP addresses instead of names?

Any chance you changed something in the router configuration?  There is something called "AP Isolation" that blocks wireless clients connected to the same network from seeing each other.  If that got turned on, you wouldn't be able to do any file sharing.

---

### Post by ian49 on 2014-10-10
> **weatherman2 said:**
> Can you ping one machine from the other?

Have you tried using IP addresses instead of names?

Any chance you changed something in the router configuration?  There is something called "AP Isolation" that blocks wireless clients connected to the same network from seeing each other.  If that got turned on, you wouldn't be able to do any file sharing.

I can't ping in either direction, just get a destination unreachable message.

In addition my WDTV media box which used to be able to access shared folders on both my pc and laptop can no longer see either of them.

I didn't change anything in the router or any other configuration settings on either the pc or the laptop.

---

### Post by weatherman2 on 2014-10-10
Until you can ping one from the other, don't even bother trying to get shared folders working.

Can you ping the gateway?  (Probably 192.168.1.1 .)

What kind of network setup do you have?  A regular home wireless router?  Is it a modem/router combo or a separate router?  How are clients connected: wired or wireless?

Have you tried using IP addresses instead of the names?

---

