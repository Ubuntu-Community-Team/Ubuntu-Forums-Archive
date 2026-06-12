---
title: "Accessing windows shares over a wireless network"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by ezramorris on 2008-03-27
Hi,
I'm trying to access some windows shares on a Windows XP machine, and I have done this successfully with both the Windows PC and the Ubuntu laptop connected over a wired connection through a router.

However, when I connect to the same router, but with the laptop connecting as a wireless connection, I cannot access the windows shares.

I don't think this is anything to do with the router, because when I used Vista on the same laptop, I could access Windows shares over both a wired and wireless connection. Also I can ping the Windows machine and VNC to it.

Any help or ideas would be much appreciated.

Thanks.

P.S. Just thought - I was recently accessing a completely different wireless network, and again I could not access the Windows shares.

---

### Post by Eiríkr on 2008-03-27
How are you trying to access the shares?  If via the GUI, you're probably talking about the Nautilus file browser.  There seems to be a bug somewhere in the Samba client code that sometimes prevents the workgroup from displaying properly.  In this case, you need to click in Nautilus's location bar (usually hidden by default but displayable by hitting Ctrl+L or clicking View -> Location Bar) and typing:
```
smb://<windows machine>
```
Replace <windows machine> with the name of the Windows machine.  If that doesn't work, try using the IP address of the Windows machine instead.  

Cheers,

Eiríkr

---

### Post by ezramorris on 2008-03-28
> **Eiríkr said:**
> How are you trying to access the shares?  If via the GUI, you're probably talking about the Nautilus file browser.  There seems to be a bug somewhere in the Samba client code that sometimes prevents the workgroup from displaying properly.  In this case, you need to click in Nautilus's location bar (usually hidden by default but displayable by hitting Ctrl+L or clicking View -> Location Bar) and typing:
```
smb://<windows machine>
```
Replace <windows machine> with the name of the Windows machine.  If that doesn't work, try using the IP address of the Windows machine instead.  

Cheers,

Eiríkr

Hi, thanks for the reply. It looks like the problem is Ubuntu is not resolving the host name. Therefore, i could access it using the ipaddress. I had also tried 
```
smbclient //main/Transfer
```
This did not work, but
```
smbclient //192.168.1.2/Transfer
```
did.
So, it does look like I can access my windows shares - thanks! Now is there any way that the host name can be made resolvable? Coming to think of it, whenever I use VNC or other services, I can only access them using ip addesses but not host names.

Thanks again! :)

---

### Post by milton1 on 2008-03-28
Actually, I believe this is a windows issue. I seem to recall something about XP not broadcasting hostnames under certain conditions.

---

### Post by ezramorris on 2008-03-28
> **milton1 said:**
> Actually, I believe this is a windows issue. I seem to recall something about XP not broadcasting hostnames under certain conditions.

Hmm. Interesting. Never mind, I will set up a static IP then edit 'hosts' in Ubuntu.

---

