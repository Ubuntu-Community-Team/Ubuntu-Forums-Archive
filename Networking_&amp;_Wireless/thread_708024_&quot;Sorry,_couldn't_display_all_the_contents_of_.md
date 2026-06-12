---
title: "&quot;Sorry, couldn't display all the contents of &quot;Windows Network: windows&quot;"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by KidBomba on 2008-02-25
Hello, I have set up SAMBA as described in the ubuntu samba guide. 
I can see the shared folder I have in Linux from Windows and I am able to dump files into the linux shared folder, but vice-versa, when I try to check the shared folder I have in Windows from Linux, I get this error when going "places"->"Network"

[IMG]http://www.geocities.com/mauricio.rm/Screenshot-nautilus.png[/IMG]

How come it works one way, but not the other?

I have Windows Firewall Off, Zone Alarm Off, and still, nothing. I am able to ping the Windows Machine and it pings fine.

In windows, I can see (linux):
[IMG]http://www.geocities.com/mauricio.rm/lionux.JPG[/IMG]

(self):
[IMG]http://www.geocities.com/mauricio.rm/windoz.JPG[/IMG]

Any tips as to what might be happening or how I can correct this issue :)
I appreciate any advice :)
:popcorn:

PS: the name of the windows machine is just Windows, so the UNC being \\Windows\
As for linux, I use \\Workgroup (I know, its stupid, but its just for testing and Windows can see it though).

---

### Post by Iowan on 2008-02-27
Try  Places>Connect to Server - sometimes that works better for me.

---

### Post by ekendra on 2008-03-01
got the exact same problem. must be something we can do about this. anyone got any specific ideas?

I posted a lot of related data here:

[http://ubuntuforums.org/showthread.php?p=4432152#post4432152](http://ubuntuforums.org/showthread.php?p=4432152#post4432152)

Let's stick together on this one KidBomba. If I come up with any solution (unlikely) then I'll post it here. Please do the same.

:guitar:

---

### Post by ekendra on 2008-03-01
forgot to subscribe

---

### Post by ekendra on 2008-03-01
?

---

### Post by kilrae on 2008-03-01
I had this problem.  I fixed it by adding the computers on my network to my hosts file (right-click on the network icon in the system tray, choose manual, go to the hosts tab).  This will only work if the computers all have static IP addresses.

For some reason, smb/Gnome/Ubuntu/something is using DNS to look up hostnames (which I think does not work with a Windows network).

[Edit: see final answer further down.]

---

### Post by kilrae on 2008-03-01
Are you using OpenDNS?  [http://ubuntuforums.org/showthread.php?p=4175328](http://ubuntuforums.org/showthread.php?p=4175328)

Linux tries to resolve hostnames by DNS before it resorts to broadcast.  OpenDNS returns a result even if the name doesn't resolve.  You have to add your network to the exceptions in OpenDNS.

---

### Post by kilrae on 2008-03-01
Ok, final answer.  If you're using OpenDNS, anyway.

Log in to OpenDNS and go to your dashboard (I assume you've already set up a network for yourself).
Go to Typo Exceptions.
Enter your workgroup/domain name (eg: my windows workgroup is 'Home', so I entered 'home')

While you're waiting for that to take effect:

Click on the network tray icon.
Go to the General tab
Enter your workgroup/domain name under Domain
Install the Name Service Cache Daemon (`sudo apt-get install nscd`)
Restart it (`sudo /etc/init.d/nscd restart`)
This will flush the cache of bad entries your computer may have now

Things should hopefully be working.

If you're not using OpenDns, your problem might be fixed in a similar fashion (if you use another DNS service) or you might want to switch if it is your ISP's DNS messing things up.  Try running `smbclient -L another-computer's-hostname`.  If you get an error saying it can't connect to some weird IP not on your network, then it is probably a DNS problem.

---

### Post by ekendra on 2008-03-01
Thanks for the help. I read the response to this post over here:

[http://ohioloco.ubuntuforums.org/showthread.php?t=711590](http://ohioloco.ubuntuforums.org/showthread.php?t=711590)

and that seemed to solve the issue.

---

