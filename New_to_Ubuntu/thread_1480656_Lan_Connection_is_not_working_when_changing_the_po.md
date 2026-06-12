---
title: "Lan Connection is not working when changing the point used!"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by Anas User on 2010-05-11
Hello All,

I am using the LAN connection to connect my UNR 10.04 to the Internet at work. When I remove the cable and go to another point to plug the cable into it, the connection doesn;t work!

It works back when I connect it again at the first point I was using which limits the usage of the LAN connection in my work to one point only and I can't move to any other point!!!

Any solution for that???

Thanks.

---

### Post by Anas User on 2010-05-11
Any help plz?

---

### Post by nhasian on 2010-05-11
you should wait at least 24 hours before bumping your post.  also it is not recommended to connect or disconnect an ethernet cable while the computer is on.

---

### Post by Ozymandias_117 on 2010-05-11
Does your LAN have DHCP? And there isn't any problem with plugging/unplugging an ethernet cable with the computer on...

---

### Post by Kralizec on 2010-05-11
How many ports have you tried? Only the two? If so, there's a possibility that the other port you tried is disabled/broken and I would try a third. Also, you might try plugging a different computer into the port that didn't work for you; this will tell you if it is a problem with your computer or the port. Or possibly an issue with the way IPs are distributed on your network.

---

### Post by alphacrucis2 on 2010-05-11
> **Anas User said:**
> Hello All,

I am using the LAN connection to connect my UNR 10.04 to the Internet at work. When I remove the cable and go to another point to plug the cable into it, the connection doesn;t work!

It works back when I connect it again at the first point I was using which limits the usage of the LAN connection in my work to one point only and I can't move to any other point!!!

Any solution for that???

Thanks.

Is the point that isn't working actually connected to your office switch? The outlet that isn't working may not go anywhere or possibly has a cable fault. Possible issues I can think of:

1. Access point is not connected to a switch.
2. Access point is connected to a switch but the switch port is shut down.
3. Wiring fault on receive or transmit pair or both.
4. Access point is connected to a switch but the switch port is configured for a special vlan (not general office access)


You could try the following command when plugged in to the port that doesn't work:

```
sudo ethtool eth0
```

The last line of output from that will say either:

```
Link detected: yes
```

or 

```
Link detected: no
```

Link detected being yes doesn't necessarily mean it should work as the link may be broken going back to the switch.

Otherwise talk to your office network administrator.

---

### Post by Anas User on 2010-05-11
> **nhasian said:**
> you should wait at least 24 hours before bumping your post.  also it is not recommended to connect or disconnect an ethernet cable while the computer is on.


Sorry for bumping the thread. I didn't know that is not allowed.

Regarding your advice, I will try it.

Thanks

---

### Post by Anas User on 2010-05-11
> **Ozymandias_117 said:**
> Does your LAN have DHCP? And there isn't any problem with plugging/unplugging an ethernet cable with the computer on...

Sorry, what do you mean by DHCP? and how can I check for it?

Regarding the plugging and the unplugging, that only works on the point I installed the cable firstly but if I go to another, it won't and actually, I think I tried it while the computer was on only.

---

### Post by Anas User on 2010-05-11
> **Kralizec said:**
> How many ports have you tried? Only the two? If so, there's a possibility that the other port you tried is disabled/broken and I would try a third. Also, you might try plugging a different computer into the port that didn't work for you; this will tell you if it is a problem with your computer or the port. Or possibly an issue with the way IPs are distributed on your network.

I tried about 4 ports and all are having the same problem. 

I remember that they were working fine when I was using windows xp on my netbook but it started happening when I used ubuntu...

Regarding the IPs issue, how might that affect and is there a solution for it?

---

### Post by Ozymandias_117 on 2010-05-11
> **Anas User said:**
> Sorry, what do you mean by DHCP? and how can I check for it?

Regarding the plugging and the unplugging, that only works on the point I installed the cable firstly but if I go to another, it won't and actually, I think I tried it while the computer was on only.

DHCP means you don't have to manually enter your IP address. One thing I am wondering with what you said, is the other network doesn't have DHCP, which means it won't automatically set your IP address. Is there someone else who runs the network that can tell you if it's DHCP or if there is a specific IP address you need?

---

### Post by Anas User on 2010-05-11
> **alphacrucis2 said:**
> Is the point that isn't working actually connected to your office switch? The outlet that isn't working may not go anywhere or possibly has a cable fault. Possible issues I can think of:

1. Access point is not connected to a switch.
2. Access point is connected to a switch but the switch port is shut down.
3. Wiring fault on receive or transmit pair or both.
4. Access point is connected to a switch but the switch port is configured for a special vlan (not general office access)


You could try the following command when plugged in to the port that doesn't work:

```
sudo ethtool eth0
```The last line of output from that will say either:

```
Link detected: yes
```or 

```
Link detected: no
```Link detected being yes doesn't necessarily mean it should work as the link may be broken going back to the switch.

Otherwise talk to your office network administrator.

Thanks for the detailed reply.

As I said before, those ports were working while I was using windows xp while they are not working when using ubuntu. 

Any idea why that is happening and any solution?

---

### Post by Anas User on 2010-05-11
> **Ozymandias_117 said:**
> DHCP means you don't have to manually enter your IP address. One thing I am wondering with what you said, is the other network doesn't have DHCP, which means it won't automatically set your IP address. Is there someone else who runs the network that can tell you if it's DHCP or if there is a specific IP address you need?


I guess it is having a DHCP as I never entered any manual settings before.

One thing to mention is I remembered that when I was using Windows, using any browser will prompt me to a dialog box to enter my account user & password that I use to access to the company intranet, signature system etc... If it isn't entered, the connection won't work.

Such dialog box is no more showing after using Ubuntu but I still manage to have only one port where I can access the LAN connection and I think that was the first port I used. Moving away to any other port, resulted in no connection.

---

### Post by alphacrucis2 on 2010-05-12
> **Anas User said:**
> I guess it is having a DHCP as I never entered any manual settings before.

One thing to mention is I remembered that when I was using Windows, using any browser will prompt me to a dialog box to enter my account user & password that I use to access to the company intranet, signature system etc... If it isn't entered, the connection won't work.

Such dialog box is no more showing after using Ubuntu but I still manage to have only one port where I can access the LAN connection and I think that was the first port I used. Moving away to any other port, resulted in no connection.

That login is your company proxy server authentication. You really need to talk to your office network administrator.

---

