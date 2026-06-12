---
title: "Help me get the PCs be Lanned!"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by dvarsam on 2007-02-17
Hello all!
I am trying to get some PCs see each other in a Local LAN.

**_My target/mission_:**

**1.** First make a successfull [color=blue]WinXP <-> WinXP[/color] LAN.

**2.** Then make a successfull [color=blue]WinXP <-> Ubuntu v6.10[/color] LAN (by using "[color=red]samba[/color]").

The funny part is that I can NOT even make target **1** work...
I have NOT managed to play with Networks before, so I hope you could help me a bit...

Basically I have the following implementation:

1. One WinXP Pro SP2 equipped PC
2. One WinXP Pro SP2 equipped PC
3. A Router that provides Internet Access to them
4. Drivers for the Network Cards are installed correctly
5. Both Windows PCs can access the Internet throught DHCP
6. IF I change IPs to Static, I can't get Internet Access to work on any of them

_Note_:
When I change the Dynamic IPs to Static on [color=blue]Ubuntu OS[/color] PCs, I don't need to tamper the Router's settings (i.e. the Router is still setup as DHCP) & but the IPs of the Ubuntu PCs, are always Static!!!
In [color=blue]WindowsOS [/color], I perform the _same_, without tampering the Router's settings (i.e. the Router is still setup as DHCP) but the WinXP PCs can't access the Internet...
Why is that?
What am I doing wrong?
Do things work differently when using Ubuntu [color=red]vs.[/color] when using Windows?

7. None of the Windows PCs is assigned a Boot Password (I just Boot without being asked to supply a password...).
Is this considered a "requirement" to get Netwoking to work correctly?

8. On PC1, when from the Desktop I open "[color=blue]My Network Places\Entire Network\Microsoft Windows Network\Mshome\[/color]", I can NOT see the PC2 (there is only 1 icon representing PC1)
On PC2, when from the Desktop I open "[color=blue]My Network Places\Entire Network\Microsoft Windows Network\Mshome\[/color]", I can see icons for PC1 & PC2, but when I double click to open up PC1, I get the following message:

```
[color=blue]\\Abc-9785a494c8a[/color] is not accessible. You might not have permissions to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found.
```

There is only one option for the user to selecte, and that is to click on the "OK" button...
I, _myself_, am supposed to be the Administrator...
But I can't give the answer to myself, as I don't know what the answer is... :)

_Questions_:
1. How can I set permissions on PC1 to allow PC2 to enter my PC1?

2. Why PC1 can NOT see PC2 on the Network & how can I fix this?

3. What about the Windows XP Firewall, do I need to activate/open any ports?

Please help, because the next step is to Setup Networking [color=blue]WinXP <-> Ubuntu[/color] using "[color=red]samba[/color]".
I want to setup this type of Networking on a company comprised of 40 PCs.
I want to help them adopt slowly to Ubuntu... but I don't even know how to setup a Network between Windows PCs... :)

Thanks.

P.S.> What seems to be very strange is the following:

1. I created Administrative accounts on both the PCs.
I activated Windows "[color=blue]Remote Desktop[/color]" capabilities & I can connect remotely to both of the PCs (from PC1 to PC2 & from PC2 to PC1)

2. From PC1 when I try to [color=blue]ping[/color] PC2, _all_ packets are sent successfully, however under "My Network Places\Entire Network\Microsoft Windows Network\Mshome" I can NOT see an icon representing PC2...
On PC2, the opposite occurs!!!
i.e. From PC2 when I try to [color=blue]ping[/color] PC1, _all_ packets FAIL to send, however under "My Network Places\Entire Network\Microsoft Windows Network\Mshome" I _can_ see both icons representing PC1 & PC2 on the network...
Why does this happen? :-k

---

### Post by dvarsam on 2007-02-18
Hello again!

I have got some progress going here...

I have managed to make the Network work between 2 WinXP PCs.
I have also managed to setup Static IPs to those PCs...

_But I have the following problem_:

When I set those PCs to [color=blue]Static IP[/color], none of them can access the Internet... 
The can see each other in the Network but can **NOT** surf the Internet!

However, IF I change them to [color=blue]Dynamic IP[/color], they can see each other & surf the Net.

What am I missing here?
Why when the PCs are set to use [color=blue]Static IPs[/color], Internet surf does NOT work, but when the PCs are set to use [color=blue]Dynamic IPs[/color], Internet surf works fine?

Can somebody explain this to me or provide some help?

Is it the Router that needs to be configured...
OR
... the PCs themselves? :-k

Thanks.

P.S.> BTW: When I try to network 2 Ubuntu PCs, they can surf the Internet no matter whether they are set to use [color=blue]Static[/color] or [color=blue]Dynamic IPs[/color].

--------------------------------------------
--------------------------------------------
[color=red]_Update_:[/color]

**I solved my problems - Thanks!**
--------------------------------------------
--------------------------------------------

---

