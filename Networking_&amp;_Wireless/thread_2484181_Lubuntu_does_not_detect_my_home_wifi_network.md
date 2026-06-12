---
title: "Lubuntu does not detect my home wifi network"
date: 2023-02-19
forum: Networking &amp; Wireless
---

### Post by mag-linares on 2023-02-19
I have installed Lubuntu on a Toshiba laptop which I intend to connect to the Wifi via a Hama USB adapter which works fine on another Windows machine.


My problem is that it doesn't detect my home wifi network.


I have read in some pages that I must do a


[FONT=courier new]sudo service network-manager restart[/FONT]


But when I do that I get the error "Failed to restart network-manager.service: Unit network-manager.service not found".


I appreciate any guidance.

---

### Post by guiverc on 2023-02-20
You haven't provided any release details, which let us know details of your software stack, as some things change from release to release.

Your command should have been

```
 sudo service NetworkManager restart

```

ie. case matters, but I can't provide more without release details.  Sometimes the fix is as easy is using a later kernel stack option (*Lubuntu ISO controls your default choice*), however release details are required to know what's available for you

---

### Post by mag-linares on 2023-02-20
Hello.

My apologies for not having provided enough information. I don't have much experience in Linux and I didn't know what data you would need to help me.

I guess a neofetch will do for you.
[FONT=courier new]


     OS: Lubuntu 22.04.1 LTS x86_64 
   Host: SATELLITE PRO C70-B PSCNVE 
  ho` Kernel: 5.15.0-43-generic 
Uptime: 24 mins 
 Packages: 1758 (dpkg), 7 (snap) 
Shell: bash 5.1.16 
Resolution: 1600x900 
DE: LXQt 0.17.1 
h WM: Openbox 
Theme: Arc-Darker [GTK3] 
 Icons: Adwaita [GTK3] 
 Terminal: qterminal 
CPU: Intel i5-4210U (4) @ 2.700G 
   GPU: Intel Haswell-ULT 
     GPU: AMD ATI Radeon R7 M260/M265 
        Memory: 1547MiB / 15914MiB [/FONT]


I use Broadcom 802.11n Network Adapter.

Now (I don't know the reason of change) when I do**[FONT=courier new] sudo service NetworkManager restart[/FONT]** I do not receive any kind of response, neither positive nor negative. Everything just stays the same.

If you need any more information about my system, please tell me.

---

### Post by guiverc on 2023-02-20
> **mag-linares said:**
> Hello.

I use Broadcom 802.11n Network Adapter.

Now (I don't know the reason of change) when I do**[FONT=courier new] sudo service NetworkManager restart[/FONT]** I do not receive any kind of response, neither positive nor negative. Everything just stays the same.


The unix way of executing commands (*back from the 1960s & 1970s*) is to just do it & return awaiting for the next command. Output is only provided if problems were encountered (ie. *warnings or errors*), with the lack of response telling you no issues were encountered.  Computers back then weren't used by *consumers* due to their high cost; so it wasn't till much later than positive feedback was added.  We're using a GNU/Linux system (Lubuntu) that follows the tradition of old (POSIX *standard*), only giving feedback where negative. (*the lack of response told you it worked*).

802.11n is a wireless standard, and relates to radio waves in the air, where your kernel needs to speak electronically with your chipset on the wireless adapter. The brand (broadcom) doesn't always matter (*but can be a huge clue!*), as its the chipset that the Linux kernel interacts with.  We need to explore what your board contains.

Lubuntu is a Ubuntu system, ie. the Lubuntu team alter a *seed* file that causes different packages to be placed on the Ubuntu base product giving us a different desktop & applications; but the base is the same, thus we can use Ubuntu's docs.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

The most useful section in that I find is 3.1 [Device Recognition and Operation]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Devices").

Once you know what chipset is involved, you can usually search online and find all you need to connect, be it
- [https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](https://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
- [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Are you able to follow the 3.1 Device Recognition & Operation guide & work out your chipset?

(*Sorry I'm not good at it as have rarely needed to use it*).

---

### Post by jeremy31 on 2023-02-20
Please see the wireless script link in my signature and post results

---

### Post by mag-linares on 2023-02-21
Many thanks friends. Thanks to your invaluable help I have found where to activate this Broadcom adapter. There was an "Additional Drivers". 

Greetings.

---

