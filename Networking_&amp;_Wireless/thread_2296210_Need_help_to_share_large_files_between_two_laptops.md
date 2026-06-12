---
title: "Need help to share large files between two laptops using ethernet patch cable"
date: 2015-09-24
forum: Networking &amp; Wireless
---

### Post by Asiful_Nobel on 2015-09-24
I want to share files between two laptops using ethernet cat6 patch cable, one running windows 8.1 64-bit and the other running Ubuntu 14.04.3 LTS. Although I have googled and found a lot of similar posts about it, I cannot seem to even connect the two laptops on a same network.

I had followed this post's answer to set static ip on both machines after connecting them with ethernet cable: [http://askubuntu.com/questions/59906/how-do-i-connect-my-desktop-and-my-laptop-using-an-ethernet-cable-to-transfer-fi](http://askubuntu.com/questions/59906/how-do-i-connect-my-desktop-and-my-laptop-using-an-ethernet-cable-to-transfer-fi)

And did this on Windows and Ubuntu respectively:
[IMG]http://i.imgur.com/Lt0eUiX.jpg[/IMG][IMG]http://i.imgur.com/ugYwv08.png[/IMG]

Then disconnected and reconnected the ethernet cable, but windows still says that the ethernet network is unidentified public network without network access. Further I cannot ping any of the machines using their ip address.

P.S: I am fairly new to networking and also Linux. So, detailed and helpful informations are more than welcomed.

---

### Post by Bucky Ball on 2015-09-24
Even if you did get this working Windows will not recognise anything on a Linux EXT partition as it has no idea what an EXT partition is and can't read/write to one. Something to keep in mind.

You're best to focus on connecting to the Windows machine from Ubuntu and dropping the files onto one of Windows NTFS partitions, which Ubuntu will read/write to.

PS: Have you had a look [here]("https://duckduckgo.com/?q=connect+windows+ubuntu+ethernet+cable")? There are a few links that will get you further down the track. Just wondering: You don't have a router or is this an obvious question? The two computers aren't on the same local area network (connected to the same device/router/access point) :)

---

### Post by Asiful_Nobel on 2015-09-24
Bucky Ball: I was thinking of sharing a specific folder from windows to ubuntu. I have done this using wifi and cifs-utils, where Windows is the host. With wifi I had started a hostednetwork on windows and shared a folder on that network; then joined the hostednetwork with Ubuntu and mounted the shared-folder. However, now I want to do the same thing with ethernet cable for better file transfer speed. But I do not know how to create a local area network with **ethernet patch cable on windows. **

No, I do not have a router, which is why I am trying to connect the laptops directly. Further the search results that you gave, I have already gone through them and most of them are on how to share internet, **whereas I need to know how to setup a network between two laptops first**. Should I rather post this on a windows forum?

---

### Post by SeijiSensei on 2015-09-24
Try deleting the default gateway entry on the Ubuntu box.  The two machines should be able to communicate directly via Ethernet broadcasts with no gateway.  Otherwise I don't see anything obviously wrong with the setup you have now.

You might be better off in the long run to buy a cheap network switch like [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16833127527) rather than futzing with crossover cables.

If you need some more help, please post the results of the commands "ifconfig" and "route -n" on the Ubuntu box in [noparse]```

```[/noparse] tags.  Also see if you can capture the relevant portion of the command "ipconfig /all" on the Windows box (run cmd.exe to get a shell).  We just need the section that concerns the Ethernet adapter like this:

```

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) Ethernet Connection I217-V
   Physical Address. . . . . . . . . : 38-2C-4A-C5-70-6C
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::19d8:b61a:14fc:a936%11(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.101.1(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :
   DHCPv6 IAID . . . . . . . . . . . : 188230730
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1C-6D-9F-DA-38-2C-4A-C5-70-6C

   DNS Servers . . . . . . . . . . . : 192.168.100.100
   NetBIOS over Tcpip. . . . . . . . : Enabled

```

---

### Post by Asiful_Nobel on 2015-09-24
SeijiSensei: Thanks a lot. It worked just right....:D

---

### Post by Bucky Ball on 2015-09-24
Great news. I was pondering the need for a gateway on the Ubuntu machine myself.

Please see the first link in my signature and enjoy! :)

---

