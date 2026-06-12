---
title: "Samba netbios naming"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by NTolerance on 2007-10-17
I've found an odd problem with Samba and netbios naming.  The hostname of this Ubuntu Samba server is "htpc".  Naturally I'd like to keep things simple and make the Samba netbios name also "htpc".  If I set "netbios name = htpc" in my smb.conf file, Windows clients can only connect to the Samba share if they use the IP address.  If I change the netbios name to anything other than "htpc", the Windows clients can use the netbios name to browse the share.  Does Samba disallow certain netbios names based on some rules or something?  Here's my smb.conf for reference:

```
[global]
   workgroup = WORKGROUP
   server string =
   netbios name = htpc
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n *password\supdated\ssuccessfully* .

[myth]
        comment = MythTV
        writeable = yes
        valid users = mythtv,nt
        path = /var/lib/mythtv/

[backup]
        comment = backup
        writeable = yes
        valid users = nt,mythtv
        path = /media/hdb5/
```

---

### Post by NTolerance on 2007-11-15
bump

---

### Post by jetsam on 2007-11-16
I'm not a Samba expert by any stretch of the imagination, but I did some testing and was able to get my home server (Gutsy 7.10, Samba 3.026a) to be browsable under XP with the name 'htpc', so it isn't a forbidden name or anything.  The only forbidden name I know of is PIPE.  You shouldn't name your server PIPE.  It's a bug, mentioned in the SWAT documentation.  

A few thoughts:
SWAT just gets rid of the 'netbios name = <whatever>' line when I set my server to my hostname, so Samba defaults to your hostname, and you shouldn't need to specify it.  I don't think there's any problem in spelling it out, though.  

I'm not sure about the 'server string =' line in you smb.conf.  It may be causing problems for the parser for it not to have a value.

It was very unpredictable, when I started changing netbios names and restarting Samba, how and when the changes were visible on the network.  It seemed to completely confuse Ubuntu's nautilus browsing when I restarted Samba, and rebooting the client machine didn't always fix it.  Windows was similarly messy, sometimes allowing browsing, sometimes offering angry beeps and 'workgroup unavailable' messages, then back again a minute later.    It's possible the name change just hadn't populated through the network when you did your test.  I think it can take a half hour or longer for changes to become visible.

---

### Post by NTolerance on 2007-11-16
The reason I have the blank server string value is due to the messy default name that is assigned if I don't have that blank value in my smb.conf file.  It would go something like this:

htpc server (Samba server, Ubuntu htpc 3.026a)

Now that's just ugly.  My guess at this point is that Samba gets angry unless you use its default messy netbios name.  So, given the above alternative I'll stick with htpc_ for now.

---

### Post by jetsam on 2007-11-16
Further messing about showed me there's nothing wrong with no value after 'server string='.  It does neaten things up.  I may set my server up that way.  :)

"Server string" and "netbios name" settings are seperate settings, though.  On my machine, if no netbios name is specified, it defaults to "OLLIE", my server host name.  You still might want to try just deleting the netbios name line altogether.  

I'm wondering if the problem isn't on the Windows side now.  Netbios is complex.  This is from the Samba3 How To:
> When an MS Windows 200x/XP system attempts to resolve a host name to an IP address, it follows a defined path:
1. Checks the hosts file. It is located in %SystemRoot%\System32\Drivers\etc.
2. Does a DNS lookup.
3. Checks the NetBIOS name cache.
4. Queries the WINS server.
5. Does a broadcast name lookup over UDP.
6. Looks up entries in LMHOSTS, located in %SystemRoot%\System32\Drivers\etc. 

Maybe 'htpc' was or is cached somewhere under an old or incorrect ip address, so it resolves to a server that doesn't exist.

---

### Post by nadalizadeh on 2007-11-16
try enabling samba wins server 
and
point the xp box wins server to it.

---

### Post by NTolerance on 2007-11-16
> **jetsam said:**
> Further messing about showed me there's nothing wrong with no value after 'server string='.  It does neaten things up.  I may set my server up that way.  :)

"Server string" and "netbios name" settings are seperate settings, though.  On my machine, if no netbios name is specified, it defaults to "OLLIE", my server host name.  You still might want to try just deleting the netbios name line altogether.  


I've  changed both netbios name and server string to be blank values.  Works as intended now.  Thanks!  :guitar:

---

