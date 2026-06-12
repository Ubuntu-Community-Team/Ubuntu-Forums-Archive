---
title: "Can browse networked computers when wired, but not wirelessly"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by rummy3000 on 2007-04-24
First off, my apologies for such an inane first post. 

I just did a clean install of Feisty and everything pretty much worked flawlessly from the start including wireless internet access. I am also able to connect to shared folders on networked Windows computers (via Places/Network) when connected to my router with a wire. However on disconnecting the wire and switching to a wireless connection I can no longer see the network (or the computers) in Nautilus. 

I have seen plenty of documentation regarding Samba, however I am very new to Ubuntu and Linux, and the prospect of setting it up just to do something that Feisty does natively with a wire seems a little daunting. I will be extremely grateful for any advice anyone can offer (especially if you can word it delicately enough for me to understand!).

---

### Post by bnuytten on 2007-04-24
It is not entirely clear if the shared files are on the Windows or Ubuntu machine?

First question: does your wireless connection work. I.e. does it have a (valid) IP address?

---

### Post by rummy3000 on 2007-04-24
Ah, sorry for the lack of info. I am trying to view shared folders on my Windows desktop from my Ubuntu laptop. 

The wireless connection works fine, I can connect to the internet without any problems but I cannot connect to the shared folders on the Windows box. However as soon as I plug in the lan cable this problem disappears. Unfortunately that's not a practical solution.

---

### Post by bnuytten on 2007-04-24
Let's see...  Suppose 192.168.1.1 is the IP address of your windows machine. What is the output of this command? If you need a different username than the one you logged on your Ubuntu box you can try the second line.
```
smbclient -L 192.168.1.1
smbclient -L 192.168.1.1 0 -U username
```

---

### Post by rummy3000 on 2007-04-25
I get 'Timeout' a couple of times followed by connection failed

---

### Post by bnuytten on 2007-04-26
> **rummy3000 said:**
> I get 'Timeout' a couple of times followed by connection failed

Hmmm you should at least be able to get some usefull reply from the Windows machine, like this. There is at least the response message "Access Denied" here because I did not give a correct user and a blank password.
```
smbclient -L 192.168.1.1
Password: 
Anonymous login successful
Domain=[DEII] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 192.168.1.1.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.1.1 failed (Called name not present)
session request to 192 failed (Called name not present)
Anonymous login successful
Domain=[WORKGROUPI] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```

I suggest the following step by step guide. Take on the next step only when the previous one succeeded. I guess it will fail at step 5 or 6. If it fails at 5 there is a problem with your wifi network. If it fails at 6 there maybe a firewall in between or some kind of other restriction.
[LIST=1]
[*]plugin the ethernet cable
[*]ping your windows machine
[*]do the smbclient thing (see above)
[*]remove the cable so you start using wireless
[*]ping your windows machine
[*]do the smbclient thing (see above)
[/LIST]

---

### Post by rummy3000 on 2007-04-26
Thanks again for the reply.

With the cable plugged in I get a solid ping from ubuntu to my windows desktop. I also get an output from the smbclient command that is practically identical to yours. 

> smbclient -L 192.168.0.6
Password: 
Anonymous login successful
Domain=[ALIENSPACE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
cli_rpc_pipe_open: cli_nt_create failed on pipe \srvsvc to machine 192.168.0.6.  Error was NT_STATUS_ACCESS_DENIED
Error returning browse list: NT_STATUS_ACCESS_DENIED
session request to 192.168.0.6 failed (Called name not present)
session request to 192 failed (Called name not present)
Anonymous login successful
Domain=[ALIENSPACE] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------
        DRONE                Rummy's Desktop

        Workgroup            Master
        ---------            -------
        ALIENSPACE           DRONE


However on unplugging the cable the terminal just sits their waiting for the ping to finish. The smbclient command gives this:

>  smbclient -L 192.168.0.6
timeout connecting to 192.168.0.6:445
timeout connecting to 192.168.0.6:139
Error connecting to 192.168.0.6 (Operation already in progress)
Connection to 192.168.0.6 failed

My networking knowledge is awful, so I am not sure what other information might be useful.

---

### Post by bnuytten on 2007-04-26
> **rummy3000 said:**
> However on unplugging the cable the terminal just sits their waiting for the ping to finish.


Ok. Forget about samba for now. The problem here has nothing to do with it. Once you unplugged the cable and go wireless, you should first check if you have an IP address for your wireless interface:
```
ifconfig
```

Say you do not have one. Than you have to go one level lower and check if you are connected to the access point. You will either see "Access Point: Not-Associated" or for instance "Acces Point: AA:BB:CC:DD:EE:FF". The first one means you are not connected.
```
iwconfig
```

If those two tests success, it probably is routing.

---

### Post by peddy on 2008-04-04
> **bnuytten said:**
> Ok. Forget about samba for now. The problem here has nothing to do with it. Once you unplugged the cable and go wireless, you should first check if you have an IP address for your wireless interface:
```
ifconfig
```

Say you do not have one. Than you have to go one level lower and check if you are connected to the access point. You will either see "Access Point: Not-Associated" or for instance "Acces Point: AA:BB:CC:DD:EE:FF". The first one means you are not connected.
```
iwconfig
```

If those two tests success, it probably is routing.

Hi. I am having the same problem. These two tests succeed, however I do not know how to configure routing. Could anyone please help me?

Cheers

---

