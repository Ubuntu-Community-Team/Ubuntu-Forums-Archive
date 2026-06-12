---
title: "Internet connection not working"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by sajiv_k on 2007-08-21
The ISP's Ethernet cable comes to my computer, I don't have any router or other devices installed in my place.

The ISP gives me an IP, Gateway and DNS address which I configure on my computer. 

To get connected they provide me with a dialer where I have to put in my user name and password.

After installing Ubuntu I downloaded their Linux dialer, but I'm not able to get online. 

The ISP guys sent over a technician who told me that he doesn't know anything about Linux.

Someone told me that I need to configure ppoe I did that by typing 

```
sudo pppoeconf
```

At the terminal and following the steps but it didn't work out

Finally I found a workaround , since I have a dual boot system I connected in Windows XP and restarted the computer and booted in Ubuntu.

The net connection works this way. 

But its just a big pain for me every time I have to boot in Windows XP and restart in Ubuntu .

Any idea whats wrong out here??

Attaching the Linux dialer which they have provided. Dunno if it helps

---

### Post by linuxwizard on 2007-08-21
Look over this 
[https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE)

---

### Post by sajiv_k on 2007-08-22
Tried that but it ain't working.

**plog  **

Gives me a CHAP authentication failed error message. 

I'm using the same password and user name in Windows :(

---

### Post by gtdaqua on 2007-08-22
give us some more details - 

the username/pwd for windows need not be the same for internet account. Has your ISP given any details on the method to connect (Authentication method etc)? What exact type of connection is this to the internet?

---

### Post by sajiv_k on 2007-08-22
> the username/pwd for windows need not be the same for internet account. 

I'm not using the Windows login id and  password, the ISP folks have given me their user name and password for authentication.

> 
Has your ISP given any details on the method to connect (Authentication method etc)? What exact type of connection is this to the internet?

Its an Ethernet connection.

The ISP has given IP, Gateway and DNS addresses.

To connect I have to configure these addresses and then use their dialer which prompts me for their user name and password. 

Login and logout is done thru their dialer software.

Their Windows dialer works well, the problem is with their Linux dialer.

I have to run it from the terminal, but it doesn't work and those guys aren't able to hep me out either.

In Windows if I don't logout from their dialer and restart in Ubuntu I can use the Internet connection.

---

