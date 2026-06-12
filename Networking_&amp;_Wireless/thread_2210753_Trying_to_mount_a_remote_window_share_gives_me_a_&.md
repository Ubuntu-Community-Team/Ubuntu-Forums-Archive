---
title: "Trying to mount a remote window share gives me a &quot;Host is Down&quot; Error"
date: 2014-03-12
forum: Networking &amp; Wireless
---

### Post by ncage on 2014-03-12
I'm not a total newb when it comes to use of linux but on the administration side i probably am. Anyways i've been googling around for 2 hours to try to fix the mount problem i'm running into. I probably know are some of the questions you will ask me so i will try to put as much info as possible:

Client: Lubuntu 13.1 ( pretty much a base install with just a few utilities added)
          --i added CIFS-Utils
 
 Server: Windows Server 2012 R2 (Running a domain)
            Name: MyServer.MyDomain.Com
             Share: MyShare


Yes i can ping the server @ MyServer.MyDomain.com
Yes nslookup reveals its true ip address

Command: sudo mount -t cifs //MyServer.MyDomain.com/MyShare /mnt/share -o username=john,domain=MyDomain
 --note i've tried both MyDomain & MyDomain.com for the domain and both failed with the same error.
 --i've also tried to use the IP address rather than the machine name
 --i've also tried a variety of other forms like the accepted answer here: [http://serverfault.com/questions/414074/mount-cifs-host-is-down](http://serverfault.com/questions/414074/mount-cifs-host-is-down) which didn't work.

Error i receive after entering the password:[B] mount error(112): Host is down
[/B]
I was just curious and entered the incorrect password just to see what would happen and i get the same error. So it appears its not even getting to the point where its trying to validate the credentials.

I can connect to the server with both windows (of course) and a Mac with no issues.


Edit: I tried to install nautilus. I can now see my domain using "Browse Network" though i can't see the individual machines on the domain which makes sense because it never asked me to enter my username/password

---

### Post by ncage on 2014-03-13
No one? :(

---

### Post by steeldriver on 2014-03-13
Have you tried it with the numeric IP in place of the host.domain.com ? that might help narrow it down between a mount problem versus a winbind name resolution problem

---

### Post by bab1 on 2014-03-13
> **steeldriver said:**
> ... that might help narrow it down between a mount problem versus a winbind name resolution problem
This misinformation never seems to go away.  

Winbind maps windows SIDs to Linux UID's.  From the Samba documentation *"The service provided by winbindd is called `winbind' and can be used to resolve user and group information from a Windows NT server."*

WINS is the Windows name server for NETBIOS NAMES.  WINS and Winbind are not related at all.

---

### Post by steeldriver on 2014-03-13
> **bab1 said:**
> This misinformation never seems to go away.  

Winbind maps windows SIDs to Linux UID's.  From the Samba documentation *"The service provided by winbindd is called `winbind' and can be used to resolve user and group information from a Windows NT server."*

WINS is the Windows name server for NETBIOS NAMES.  WINS and Winbind are not related at all.

Apologies for getting the terminology wrong. I was just trying to make a distinction between DNS resolution (which the OP has already checked) and netbios name resolution.

---

