---
title: "windows shares"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by Mersenne on 2008-08-16
Hi!

I have ubuntu hardy (the 8.04 edition) with GNOME and all.

Its just that I can't access my Windows shares (I never could). My Windows shares are actually run via Samba on an ubuntu server and are accessible via XP computers.

I'm on the same workgroup as the other computers and stuff...its just that the windows shares part comes up blank...

[IMG]http://mersenne.zapto.org/www/readfile.php?salt=69977a497df884bcb9d46e664e1130eb&file=mersenne/windows.png[/IMG]

([http://mersenne.zapto.org/www/readfile.php?salt=69977a497df884bcb9d46e664e1130eb&file=mersenne/windows.png](http://mersenne.zapto.org/www/readfile.php?salt=69977a497df884bcb9d46e664e1130eb&file=mersenne/windows.png))

is there any way I can get this working? Thanks.

---

### Post by Iowan on 2008-08-16
> **superprash2003 said:**
> to access windows shares from ubuntu go to terminal and type nautilus smb://x.x.x.x whre x.x.x.x is the ip of the windows machine..  This is the quick/dirty answer.  I'm still looking for the clean, "servername" version. In some cases, installing Winbind and modifying nsswitch.conf solve the problem.

---

### Post by Malfet on 2008-08-18
> **Mersenne said:**
> Hi!
is there any way I can get this working? Thanks.

Did you try to type smb://serveradress/sharename, instead of smb://serveradress? If it works then you have a known gvfs bug (see [https://bugs.launchpad.net/ubuntu/%2Bsource/samba/%2Bbug/235560]("https://bugs.launchpad.net/ubuntu/%2Bsource/samba/%2Bbug/235560")). So far I know there is no fix available for that issue.

&#1052;.

---

### Post by dmizer on 2008-08-18
The best fix I know of for this problem is to do it manually.  You get much better speed and overall network performance this way too.  If you're interested in doing this manually, please see the second link in my sig.

Alternatively, it would help if you posted the /etc/samba/smb.conf file from the ubuntu samba server.

---

### Post by saxophin on 2008-08-20
I've just discovered today that I can access shares on my XP box using Places/Network but if I want to access the shares on my Vista box none show up and I have to enter "smb://ip address/share" in nautilus's address line.  So in my case this looks like a Vista problem.  I'll bet it's different for other people though :)

---

### Post by Iowan on 2008-08-21
In the aforementioned How-To is a link to [this]("http://ubuntuforums.org/showthread.php?t=190542") thread on Firestarter and name resolution.  Could it be that installing **winbind** and **smbfs** on Ubuntu and editing /etc/nsswitch.conf to include **wins** at the tail end of the hosts: line is the magic combination I read about?

---

### Post by dmizer on 2008-08-21
> **Iowan said:**
> In the aforementioned How-To is a link to [this]("http://ubuntuforums.org/showthread.php?t=190542") thread on Firestarter and name resolution.  Could it be that installing **winbind** and **smbfs** on Ubuntu and editing /etc/nsswitch.conf to include **wins** at the tail end of the hosts: line is the magic combination I read about?

Be careful with this.  The order DOES make a difference.  You need to make sure that wins is before dns in this line.  This is a show stopper for some people. Still, I think the Firestarter issue is an entirely different problem.

---

### Post by Iowan on 2008-08-21
> **dmizer said:**
>  Still, I think the Firestarter issue is an entirely different problem.Probably so... but I keep hoping for a "mount by hostname" solution.

---

### Post by dmizer on 2008-08-21
Configuring /etc/nsswitch.conf as you've described, and installing winbind will give you "mount by hostname".

---

### Post by simplr on 2008-08-23
I found that the Windows shares, except for Windows 3.11, worked correctly in the Places->Network after adding the IP address of one of the Windows computers in System->Administration->Network->DNS->SearchDomains.

Any idea how I can get the 3.11 shares to work?

---

### Post by dmizer on 2008-08-23
> **simplr said:**
> I found that the Windows shares, except for Windows 3.11, worked correctly in the Places->Network after adding the IP address of one of the Windows computers in System->Administration->Network->DNS->SearchDomains.

Any idea how I can get the 3.11 shares to work?

Interesting solution.

As for Windows 3.11, don't expect much.  Hardy uses CIFS exclusively, and Windows 3.11 won't work with CIFS.  So you'll have to compile in SMBFS support for Hardy just to get your foot in the door.  No idea what kind of hoops you'll have to jump through after that.

---

### Post by redmk2 on 2008-08-23
> As for Windows 3.11, don't expect much. Hardy uses CIFS exclusively, and Windows 3.11 won't work with CIFS.
@ Dmizer,

I'm confused here.  From what I have read, CIFS will work with Windows 3.11 will.  See [***this***]("http://www.protocolbase.net/protocols/protocol_CIFS.php").

Does Hardy use CIFS in a different way?  I see by the postings to this forum that Hardy has problems with samba in general.  Why is that?  I have a Gutsy samba server and it works perfectly.  I'm just about to setup  the same basic setup at a friends house and he has a Widows for Workgroups (3.11) on one of his computers.  Should I go back to Gutsy?

---

### Post by simplr on 2008-08-30
Solved!  All my Windows/Samba shares are now showing in the Places->Network, including Windows 3.11.

The main thing was that I needed the Windows 3.11 IP address to be specified in addition to the other Windows domain in the DNS settings. But I struggled to understand the behavior because I was fighting against the DHCP client. If I deleted the 'Search domain' that was allocated by default, it would delete my changes and replace it with the default.  Thinking that I would get the better of the system, I edited /etc/resolv.conf directly - but this was also quickly replaced with the original.

I tried to first add the IP address of the Windows 3.11 computer into the /etc/hosts file (System->Network->Hosts) and then add the name (not the IP address) into the DNS->Search Domains without deleting the 'sticky' one. This seemed to work but a minute later the DNS settings were back to default. However I could still see my Windows 3.11 shares! I added a Windows 98 host to the /etc/hosts file and then all worked, but only until the next reboot.

Only after I realized that the DHCP server, which is a host on my LAN acting as a router and gateway to the Internet, was forcing the DNS settings did I add the IP addresses of the key Windows computers into the DHCP server settings.  Now all is good.

```
sudo vim /etc/dhcpd.conf
...
option domain-name-servers ...,...**, 192.168.0.49, 192.168.0.250**;
...
```

If you do not have access to the DHCP server configuration, then you could, I guess, use a static IP address instead. Maybe then the manual DNS settings will stick!

---

