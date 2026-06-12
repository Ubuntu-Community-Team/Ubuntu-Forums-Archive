---
title: "Can't access shares from a virtualbox server - &quot;Failed to retrieve share list&quot;"
date: 2022-02-22
forum: Networking &amp; Wireless
---

### Post by username2758 on 2022-02-22
I don't know a lot about networking, and am trying to set up a Samba server with Ubuntu 20.04.3 using Virtualbox for learning and testing purposes.

In order to do this I had to fiddle with Virtualbox settings and create a "Host-only Network" (see attached screenshot), but I am not able to access the samba server. 

The following error message appears when I try to access the shares from this VM server: "Failed to retrieve share list from server: Invalid argument".

What could be wrong?

---

### Post by TheFu on 2022-02-22
Use "bridged" networking.  The virtualbox manual has as good an explanation as anywhere else.  I think it is in Chapter 6.

---

### Post by SeijiSensei on 2022-02-22
That sounds it could be a Samba error. Regardless, to debug the connection launch a terminal on the client and run
```
smbclient -L server_name
```
If you haven't set up name resolution you can add "-I ip.of.your.server".  Run "[man smbclient]("https://www.samba.org/samba/docs/current/man-html/smbclient.1.html")" to see the full array of options available.

If you don't have smbclient installed, use "sudo apt update; sudo apt install smbclient" first.

You can also add the "-d number" option to choose a debug level. They range from zero to ten and correspond to the "log level" parameter in smb.conf.

---

### Post by username2758 on 2022-02-22
> **TheFu said:**
> Use "bridged" networking.  The virtualbox manual has as good an explanation as anywhere else.  I think it is in Chapter 6.

Hooooray! It worked! Thank you! :D

So I didn't actually needed to mess with "Host Network Manager" and create a "Host-only Network". I wonder what that does anyway.

---

### Post by SeijiSensei on 2022-02-22
I believe it creates a network among separate virtual machines running on a single host. 

That's what I thought you were trying to do, using two virtual machines, one running as the Samba server and the other as a client. Bridged networking wouldn't have solved that, but since it did solve your problem, I assume Samba was running on the VM, and you wanted to access it from another machine on your local network.

---

### Post by username2758 on 2022-02-23
> **SeijiSensei said:**
> I believe it creates a network among separate virtual machines running on a single host. 

That's what I thought you were trying to do, using two virtual machines, one running as the Samba server and the other as a client. Bridged networking wouldn't have solved that, but since it did solve your problem, I assume Samba was running on the VM, and you wanted to access it from another machine on your local network.

Yes! I'm definitely not very good with networking let alone running a Samba server on a virtual machine, so it's difficult even describing the question here.

Hopefully I will be able to learn more about Samba and networking now.

Thanks for the help! :D

---

### Post by username2758 on 2022-02-26
Hey guys, just one more thing.

The bridged networking worked fine over Ethernet, but it isn't working over WiFi.

Do you know if there's a way to make bridged networking work over WiFi connection in Virtualbox as well?

---

