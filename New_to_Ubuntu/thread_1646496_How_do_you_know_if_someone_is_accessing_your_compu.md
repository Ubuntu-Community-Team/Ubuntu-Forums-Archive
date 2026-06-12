---
title: "How do you know if someone is accessing your computer?"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by Toronto11 on 2010-12-15
I'm a little concerned about my computer's security and believe it is being accessed and items viewed.  How do I tell if this is happening?  Or if a key-stroke type of programme has been installed?

I have gone to Shields Up and all of my ports are in stealth, but my comp responds to pings.

I have Firestarter firewall up and running.  And ClamTk is up to date.

Is there anyway to prevent someone from getting at my comp and files again if they know my IP address?

Sorry, really junior questions, but all of the other posts I've seen are too far above me or don't directly apply.

Thanks for all the help.  And I don't have anything top secret, just think I have some prying eyes.

---

### Post by CharlesA on 2010-12-15
There are no services listening to external interfaces by default.

The only way for someone to gain access is for you to install something like SSH or VNC (or enable Remote Desktop, which you shouldn't do).

---

### Post by RoflHaxBbq on 2010-12-15
What makes you think that people have hacked you?
I believe you can change your IP sometimes by turning off/unplugging your modem.
And try opening terminal and doing a ```
netstat
```

---

### Post by CharlesA on 2010-12-16
> **RoflHaxBbq said:**
> What makes you think that people have hacked you?
I believe you can change your IP sometimes by turning off/unplugging your modem.
And try opening terminal and doing a ```
netstat
```
**netstat -ln** will give you a list of listening services.

But if your router doesn't have any open ports (everything is set to stealth), you should be fine.

---

### Post by Toronto11 on 2010-12-16
I'm probably just being paranoid, but the IT guy at work is pretty good at what he does and I've heard he's done it before.  And some of the comments he's made, it just made me think, hey, wtf?

---

### Post by CharlesA on 2010-12-16
Sometimes they just want to mess with you.

Also, I'd suggest not using Firestarter, as it's no longer maintained and can cause conflicts with ufw/gufw.

---

### Post by Toronto11 on 2010-12-16
I do get that feeling.

What am I looking for when I type in the netstat command?

---

### Post by CharlesA on 2010-12-16
You'd get something back like this:

```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
[COLOR="Red"]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN[/COLOR]
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:7004            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
[COLOR="Red"]tcp6       0      0 :::22                   :::*                    LISTEN[/COLOR]
tcp6       0      0 ::1:631                 :::*                    LISTEN
tcp6       0      0 :::7004                 :::*                    LISTEN
udp        0      0 0.0.0.0:68              0.0.0.0:*
udp        0      0 192.168.1.32:137        0.0.0.0:*
udp        0      0 0.0.0.0:137             0.0.0.0:*
udp        0      0 192.168.1.32:138        0.0.0.0:*
udp        0      0 0.0.0.0:138             0.0.0.0:*

```

That lists any connections currently listening. The only ones you need to worry about are the ones that are listening at 0.0.0.0 or :::.

The most common ways to connect to a machine remotely are SSH (port 22) and VNC (port 5900).

Note if you are running the desktop version of Ubuntu, you'll see a load of stuff under "Sockets." That is normal.

---

### Post by Toronto11 on 2010-12-16
Thanks for the answers Charles.

So this is normal and I can stop being paranoid?

```
ctive Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN     
tcp6       0      0 :::631                  :::*                    LISTEN     
tcp6       0      0 ::1:25                  :::*                    LISTEN     
udp        0      0 0.0.0.0:46005           0.0.0.0:*                          
udp        0      0 0.0.0.0:68              0.0.0.0:*                          
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:631             0.0.0.0:*              
```

I checked the synaptic package manager and SSH (first on the list) and VNC were not selected, but other random SSH ones were green boxes.

---

### Post by Toronto11 on 2010-12-16
And I guess while I'm here I should ask why Shields Up is saying that I'm failing a port test because my comp is replying to a ping?  How can I permanently disable the ping reply and totally pass the Shields Up test?

---

### Post by CharlesA on 2010-12-16
It looks fine.

The only thing that is running is cups (port 631), which you can uninstall if you don't print from Linux (doesn't harm anything if it's running, but it should be listening on 127.0.0.1:631, not 0.0.0.0:631

Also, do you have a mail server installed? Port 25 is normally used by SMTP.

EDIT: Shields up, tests your router, not your local PC, unless you have the PC hooked directly to the internet.

---

### Post by Toronto11 on 2010-12-16
Thanks Charles.

I do print from Linux, HP printer, so I guess I should leave cups in.

I use Thunderbird so I guess that's the mail server, but again, if it's not a problem then I should probably leave it.

And I don't have a router, just a cable connection to a modem and a modem into my comp.

And I just uninstalled Firestarter as per your advice.  You're on a roll - can you recommend a firewall for me?

Ubuntu is pretty solid, I like it a lot and am glad my system is secure, I just want to pass that damn Shields Up test for some reason.  I just changed a etc/sysconfig file to say all to blocking ICMP requests.  It didn't work.

---

### Post by CharlesA on 2010-12-16
I recommend using ufw (installed by default but not active).

gufw is a good GUI for configuring ufw.

In any case, I think you'll be fine. Since you don't have a router between you and the internet, you'll have to turn on ufw and you'll be good to go. :)

---

### Post by Toronto11 on 2010-12-16
Charles, it's people like you that make Ubuntu easy for people like me and I really do appreciate it.  I'm glad I'm a convert to Unbuntu.

Thanks for all the help.

---

### Post by colin.p on 2010-12-16
Why don't you go to Future Shop/Best Buy and buy a cheap $20 Trendnet router (or the cheapest one they got) and you will forever forget about trying to set your computer up with "windows" security mentality.
Steve Gibson is a nice guy, but has this obsession with being "stealth".
Buy a router and you will be for "all intents and purposes", stealth.

---

### Post by QLee on 2010-12-17
[QUOTE=Toronto11]...

I use Thunderbird so I guess that's the mail server, but again, if it's not a problem then I should probably leave it.
...

..., I just want to pass that damn Shields Up test for some reason....[/QUOTE]

Sorry to jump in here so late but a couple of comments.

Thunderbird is an email client. It wouldn't be listening on port 25, that would be some MTA (Mail Transfer Agent), something like exim or postfix or one of those. Something so your system could send mail and something that you would have installed (not on default install), TBird sends from your ISPs mail server.

You really don't need to worry about responding to pings, these days especially, the black hats are more sophisticated than that, as soon as you use the Internet there are packets leaving with your return IP address on them so they know there is something there even if 
the address doesn't answer a ping.

---

### Post by HermanAB on 2010-12-17
Howdy,

The command who will tell you who is logged in:
$ sudo who

---

### Post by CharlesA on 2010-12-17
> **QLee said:**
> 
Thunderbird is an email client. It wouldn't be listening on port 25, that would be some MTA (Mail Transfer Agent), something like exim or postfix or one of those. Something so your system could send mail and something that you would have installed (not on default install), TBird sends from your ISPs mail server.

Good point.

I'm kinda curious as well, since it looks like something is listening on 127.0.0.1:25, probably an MTA, as you said.

What's even more interesting is that cups is listening on the external interface, and on my machine it's listening on the looback interface.

---

### Post by QLee on 2010-12-18
Well CharlesA, it looks like Toronto11 isn't looking at the forum any longer.

I looked up the ClamTK that was mentioned in the first post and it is a GUI for ClamAV, so postfix is likely installed on the system and that would account for the MTA on port 25. Not that it would give any security to a GNU/Linux system to catch Windows virus. Don't know why Toronto11 doesn't remember installing postfix, maybe it got installed and configured in some automagic way as part of something else.

I agree with you that CUPS should be listening on localhost, since there's no LAN it must be a local printer, but I am not a CUPS expert or even close, never had enough problems with it to learn much.

---

### Post by CharlesA on 2010-12-18
I guess that would make sense if ClamTK installed a MTA. I know smartmontools does the same thing, if an MTA isn't already installed.

As for CUPS, I'm in the same position, as I have never really had problems with it.

---

