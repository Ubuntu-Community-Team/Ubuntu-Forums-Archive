---
title: "GUFW Firewall - linking local computers"
date: 2020-01-20
forum: Networking &amp; Wireless
---

### Post by ChrisOfBristol on 2020-01-20
I have a Ubuntu (Budgie 19.10) desktop and a Windows 7 laptop both connected to my modem/router by wireless. The modem is connected to the Internet, so I have the default Windows firewall on the laptop and UFW on the desktop running a firewall and I have the recommended simple home setup which has these:

Basic Permissions[INDENT]Profile:      Home
Status:      On
Incoming:  Deny
Outgoing:  Allow

[/INDENT]
That's fine for the Internet, but the laptop couldn't see the desktop unless the desktop firewall was off, so I added these:

Advanced Rules[INDENT]Name:             Laptop
    Insert:             0
    Policy:             Allow
    Direction:        Both
    Interfaces:      All Interfaces
    Log:                Do not Log
    Protocol:         Both
    From: 192.186.0.15   Port 24        # I want to link from the modem port that the laptop attaches to, through port 24 of the desktop
    To:          192.186.0.15    Port 24        # I want to link     the modem port that the laptop attaches to, through port 24 of the desktop    
[/INDENT]
 
The laptop still can't see the desktop unless the desktop firewall is off. 

Is the problem because I have assumed that the Advanced Rules allow exceptions to the Basic Permissions? Because if the Basic Permissions override the Advanced Rules I suppose it wouldn't work.
Alternatively I may have misunderstood how the IP address and port numbers work.

---

### Post by TheFu on 2020-01-20
Yes, you don't understand how port numbers work.  Modem numbers, switch port numbers, and network port numbers aren't connected in any way. They are each completely different things.

I don't think "port 24" does what you want.  I cannot think of any popular protocol that uses 24/tcp or 24/udp for communications.

If you can spell out exactly which protocols you'd like to have the machines communicate using, we can help to relax the firewall rules on each to allow those specific protocols.
However, it is common in a home network to allow all LAN clients full access to each other, so you would use something like  192.186.0.0/24 in the rule on both clients to allow the entire subnet access.

There is a firewall how-to guide for ufw.  That is probably all you really need to understand.

BTW, there are 64K ports, with about 15 commonly used transports - udp, tcp, icmp are the most common, but others are used. So randomly picking port 24 really isn't so useful.   A few, default, example ports:
http is 80/tcp
https is 443/tcp
ssh is 22/tcp

Those defaults can be changed, but only on the server-side, not the client.  If you run a web server, you most likely want to be on port 80 and 443 to prevent issues from potential customers/readers.  ssh is different, since only trusted people should be using it, moving that service/daemon to a non-standard port is considered a best-practice for security.

One more thing about ports - any port if 1024 or less requires root to start it.  Often, webapps will listen on ports like 8080/tcp so they don't have to run as root, which is a good idea for system security.  Running on higher ports is common inside businesses.

Really, if you want to understand basic internet networking google "how the internet works GRC" and listen/read the 3 episodes of that podcast where they explain it.  I think episodes 25, 26, 27 are the ones you want, but might be off.

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)
And if you are running a server, not a desktop, [https://help.ubuntu.com/lts/serverguide/firewall.html](https://help.ubuntu.com/lts/serverguide/firewall.html)

---

### Post by ChrisOfBristol on 2020-01-20
Incorrect post blanked.

---

### Post by ChrisOfBristol on 2020-01-21
> **TheFu said:**
> Yes, you don't understand how port numbers work[...]However, it is common in a home network to allow all LAN clients full access to each other, so you would use something like 192.186.0.0/24 in the rule on both clients to allow the entire subnet access.
I should have stated that I just want the Linux desktop to share a folder so that it can be seen from the laptop so I can copy (sets of) files from one to the other easily. I have nemo-share installed and was able to do the sharing easily enough.

I haven't really understood the networking properly, but have picked up on your statement above and not using the port numbers and tried again with the settings in the attached images (corrected). It works!!! After dozens of attempts I was mixing the numbers up and making typos.

It's only to necessary to have a rule for **Direction In** and it's still possible to copy files in both directions.

---

### Post by Morbius1 on 2020-01-21
The key words I picked up in your posts are [highlight]Ubuntu[/highlight], [highlight]desktop[/highlight], and [highlight]nemo-share[/highlight]

Why not just allow samba through your firewall:
```
sudo ufw allow Samba
```
When things like Samba and OpenSSH are installed they set up predefined rules for you in /etc/ufw/applications.d. You just need to apply them with the correct key word - Samba in this case.

---

### Post by ChrisOfBristol on 2020-01-21
> **Morbius1 said:**
> Why not just allow samba through your firewall: ```
sudo ufw allow Samba
```
Haha! I wish you'd seen my OP a day ago, you'd have saved me a whole load of grief...When briefly considering adding a pre-configured rule, I assumed I'd have to allow some Windows program that I didn't know the name of, so didn't want to get tangled up in that. It hadn't occurred to me to allow Samba. I've tried it, worked first time, I'll stick with it as it's less confusing than all the numbers. I assume someone getting to my router from the Internet couldn't be using Samba. 
The 2 rules created using the command:
[ATTACH=CONFIG]284856[/ATTACH]
The 4 rules created using GUFW>Rules>Add>Preconfigured and putting SAMBA on the Application row, then Add. (It's only necessary to have **Direction In** tp be able to copy files in either direction.)
[ATTACH=CONFIG]284855[/ATTACH]
UFW creates a rule for each version of the IP protocol, but GUFW creates two for each. It converts the reference to Samba into numbers (I don't know what they represent) rather than Samba. Both methods work.

---

