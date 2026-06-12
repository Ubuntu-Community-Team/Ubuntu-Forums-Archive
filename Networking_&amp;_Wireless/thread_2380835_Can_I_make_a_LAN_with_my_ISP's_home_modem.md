---
title: "Can I make a LAN with my ISP's home modem?"
date: 2017-12-22
forum: Networking &amp; Wireless
---

### Post by javierdl on 2017-12-22
Hi all,

I have 2 PCs at home, PC-01 is running Win10 and Ubuntu 16.04 (wireless). PC-02 is running Win10 and Linux Mint (Mate) 18.3 (wired).
I was wondering if I could use my ISP's home modem: [Home Hub 3000]("https://www.bell.ca/Bell_Internet/HomeHub3000"), to connect them to each other.

Assuming it is possible, where do I start?

Thanks guys

---

### Post by praseodym on 2017-12-22
Do you want to share folders or directly connect them? For shared folders give the computers fixed IP addresses in that box.

---

### Post by javierdl on 2017-12-22
> "...in that box."

In what box?

---

### Post by QIII on 2017-12-22
Hello!

The modem.

Do you have access to the modem's settings interface?  It is usually accessible from your web browser.

---

### Post by javierdl on 2017-12-22
Yes I do!
I'll go have a look...

---

### Post by javierdl on 2017-12-22
Once inside, I found Advanced Tools & Settings:
1. Networking - DMZ, DDNS, UPnP (Turned ON), DLNA (Turned ON), DHCP, and Port Forwarding.
2. WiFi - WPS, MAC Filtering.
3. Modem - About, DNS, WAN.
4. Tools - Statistics, System Logs, Utilities, Monitoring, Resets, Diagnostics.

What do you think?

---

### Post by javierdl on 2017-12-23
I was able to confirm that both computers can see each other and share files, while in Win10 each. 
Now I need to do the same with Ubuntu 16.04 & Linux Mint 18.3.
What should be the 1st step?

---

### Post by Dennis N on 2017-12-23
> Now I need to do the same with Ubuntu 16.04 & Linux Mint 18.3. What should be the 1st step?
First step: Install openssh-server in Ubuntu and Mint.

---

### Post by javierdl on 2017-12-23
Alright! I got [COLOR=#000000]**openssh-server**  installed in both machines!

I also found this little app in Linux Mint. Am I going to use it now?

[/COLOR][IMG]http://pasteall.org/pic/index.php?id=121268[/IMG][IMG]http://pasteall.org/pic/index.php?id=121268[/IMG][IMG]http://pasteall.org/pic/show.php?id=121268[/IMG]

---

### Post by javierdl on 2017-12-24
I found this [tutorial]("https://www.tecmint.com/install-openssh-server-in-linux/") to configure OpenSSH-Server. I guess I'll take it from here, for now. Should I succeed then I'll just close this thread as Solved. Wish me luck!

---

### Post by javierdl on 2017-12-24
Mmm, never mind!
I can't say that was a helpful tutorial.
I'm still looking...

---

### Post by Dennis N on 2017-12-24
> **javierdl said:**
> I found this [tutorial]("https://www.tecmint.com/install-openssh-server-in-linux/") to configure OpenSSH-Server. I guess I'll take it from here, for now. Should I succeed then I'll just close this thread as Solved. Wish me luck!

What I do is use **gigolo** to help make the actual connection to the other Linux machine. All you need is the ip address of the machine you want to connect to. See image attached. After connection, you can open a file manager window to the remote machine from the gigolo window, and browse around, and copy and paste as you would on a single machine, or even open files. Install gigolo from the ubuntu repository.

Find IP address: run **ifconfig** in the terminal of the remote machine:

```
dmn@Zotac ~ $ ifconfig
enp2s0    Link encap:Ethernet  HWaddr 00:01:2e:58:fe:ee  
          **inet addr:192.168.1.3**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::cc3f:44d1:7ac3:19a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36261782 (36.2 MB)  TX bytes:2529437 (2.5 MB)

```

---

### Post by javierdl on 2017-12-24
Is ther User name anything I want? Otherwise where do I get it from?

---

### Post by Dennis N on 2017-12-25
> **javierdl said:**
> Is ther User name anything I want? Otherwise where do I get it from?

Are you referring to the image in post #12? That user name is the user name of the account I want to log into on the remote computer. After entering it, you then will be prompted for the password on that account. Note: the first time you connect, you will get a warning about unknown host or something like that. Log in anyway and next time you connect to that same user account the warning won't appear.

---

