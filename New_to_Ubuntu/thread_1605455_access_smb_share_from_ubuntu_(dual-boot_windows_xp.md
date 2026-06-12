---
title: "access smb share from ubuntu (dual-boot windows xp) in enterprise environnemnt"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Gbillou on 2010-10-25
Hi everybody,

At work we all have to use windows Xp, and I'd rather use ubuntu as my main task on this computer is to launch putty and Cygwin/X to remote connect to other servers, and sometime launch eclipse & dev things locally.

My main problem is that i need to access a samba share (\\SMBSRV\HIDDENSHARE$), which i have access to on windows because i'm logged on the AD. And i don't know how to achieve this on linux.

First of all I don't have a full understanding of domain & else. ie => when i log on my windows computer, i have to choose (what i thought to be) a domain, let's call it AAAA. Then when i'm logged in if i go to system properties, the domain name is xx.yyyy.
I don't really understand what AAAA is, as it seems xx.yyyy is the domain name, then what AAAA is?

Furthermore I managed to get a ticket (krbtgt/XX.YYYY@XX.YYYY) from the kerberos server using xx.yyyy as kdc in krb5.conf via kinit, but when i'm using smbclient -k to list shares on a specific server it gives me an error (i don't have it yet as i'm back on windows, i'll post further details if needed later, i just remember it's not network related, but more something like "no ticket for this service found").

i understand i need a "cifs/????@????" ticket to at least try to connect to the samba share but... i'm not really sure of what i did when i tried to configure krb5.conf (just added a "default_realm", and a section with XX.YYYY as kdc, admin_server and default_domain).

what else.. My first idea was to join this computer to the AD with likewise-open, but i'm for sure not an AD admin, and don't have rights to do so (and don't really want to add an ubuntu box to their AD.. they'll find it a bit weird isn't it?..). Maybe i can use the already existing windows computer account but.. btw the only thing i want is to access this share, as a user point of view i don't see any advantage of beeing part of my enterprise domain..

So here are my questions : what's the best for me to access this share? Can i join this domain using the already existing windows computer account (without an AD admin account)?

Thanks and sorry for my english :-/

---

### Post by luvshines on 2010-10-25
From your Ubuntu machine, can you try accessing the share with smbclient:
```

smbclient //<server>/<share> -UAAAA\\<username>%<password>

```

---

### Post by Gbillou on 2010-10-25
Hey great it worked :) I then tried using the ubuntu gui and it worked too (cool :p).

Questions lefts are :
- What's the name of AAAA? I've seen it's something like "windows 2000 logon prefix"? is there anybody able to explain it (or give me a good link that explains it)?
- Can I join the domain as if i was on windows, because my computer account already exists on the AD, so i "think/hope" it's possible without requiring an ad admin password (as i don't want to be recognized as a "new" computer in the AD)
- What's the best way for me to browse samba shares on this network (without going on windows in order to find share names etc..)?
- I've seen my windows box have dns suffixes in its adapter params, and the dhcp server don't send theses params. I know on linux I have to add the "search" keyword to my resolv.conf for this, and i know i can use NetworkManager for this task (asking it to get ip from dhcp, but let me specify the dns servers and dns suffixes), Btw i don't know if i can get these params using another way? Should the dhcp server send these params to my box? Do you think my windows box have been set up like this or do it gets that from somewhere in the network at each boot?
- And last one => Is there someone able to explain all this "kerberos" stuff.. it would be cool to know what to do to get a cifs ticket manually and use it via smbclient -k :D (I've already read things about kerberos and how it should work, but i'm still not able to use kerberos cli tools on my box to play with tickets :-/, on the other hand i did execute klist.exe on my windows box, and i've seen all the tickets "windows" requested for me.. i want the same on my linux :D (Yes that's just for "fun"))

Hmm it seems that's all, i do have others questions but I keep these for another thread ;)

Thank you btw! :p

---

### Post by luvshines on 2010-10-28
I haven't gone into the details myself :D but I'll try to answer it to the best of my abilities.
Also, share links which are useful if  you have any. I would like to learn :)

> **Gbillou said:**
> Hey great it worked :) I then tried using the ubuntu gui and it worked too (cool :p).

Questions lefts are :
- What's the name of AAAA? I've seen it's something like "windows 2000 logon prefix"? is there anybody able to explain it (or give me a good link that explains it)?

I think that will be your Logon domain. That is domain which you join to, that which is controlled by your Domain Controller. This will also the the Kerberos Realm(default) for your Domain Controller.

> 
- Can I join the domain as if i was on windows, because my computer account already exists on the AD, so i "think/hope" it's possible without requiring an ad admin password (as i don't want to be recognized as a "new" computer in the AD)

I tried to join my domain from my user name and I was able to. Give it a try on your Ubuntu box. Command is 'net ads join' in this link:  [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)
But do you actually need this ? Why go into the complications of domain logon, kerberos stuff when you can access it this way(it will use NTLM here I suppose)

> 
- What's the best way for me to browse samba shares on this network (without going on windows in order to find share names etc..)?You can list the shares with ```

smbclient -L <server-ip> -U<domain\\username>%<passwd>
```And then access them by previous method :)
I think you should also be able to list them by 'connect to server' option in Places and providing domain, username, passwd details there. Just give it a try

> 
- I've seen my windows box have dns suffixes in its adapter params, and the dhcp server don't send theses params. I know on linux I have to add the "search" keyword to my resolv.conf for this, and i know i can use NetworkManager for this task (asking it to get ip from dhcp, but let me specify the dns servers and dns suffixes), Btw i don't know if i can get these params using another way? Should the dhcp server send these params to my box? Do you think my windows box have been set up like this or do it gets that from somewhere in the network at each boot?
For this I can't comment. Did not get the question exactly and also haven't gone into details myself
> 
- And last one => Is there someone able to explain all this "kerberos" stuff.. it would be cool to know what to do to get a cifs ticket manually and use it via smbclient -k :D (I've already read things about kerberos and how it should work, but i'm still not able to use kerberos cli tools on my box to play with tickets :-/, on the other hand i did execute klist.exe on my windows box, and i've seen all the tickets "windows" requested for me.. i want the same on my linux :D (Yes that's just for "fun"))
Found this good link for Kerberos understanding: 
[http://searchwindowsserver.techtarget.com/feature/Logging-on-to-Windows-using-Kerberos-Single-domain-environment](http://searchwindowsserver.techtarget.com/feature/Logging-on-to-Windows-using-Kerberos-Single-domain-environment)[SIZE=2][FONT=Verdana]
By accessing it the way I told you, I think we are actually bypassing all the kerberos authentication stuff from the picture and using NTLM auth only. I did some investigation over this and didn't find any 'kerberos' specific stuff in wireshark by this method
However, by the kerberos way without joining domain, this should suffice:
```

## Prepare the /etc/krb5.conf file
[libdefaults]
 dns_lookup_realm = true
 dns_lookup_kdc = true
[realms]
  <realm>= {
          kdc = <DC-FQDN>
  }

## Request a ticket
kinit username@REALM

## Access the share
smbclient -k //<server-ip>/<share-name>

```Notes:
1. Realm will be AAAA.com, I guess
2. The address for kdc should be reachable[/FONT][/SIZE]

---

### Post by Gbillou on 2010-10-28
I don't have time to investigate more on this yet and try what you told me, btw I'm concidering my main problem as solved :)
I'll keep you posted about my kerberos experiments.

Thx for you help!

---

