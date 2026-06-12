---
title: "Wireless - Linksys WMP54G PCI card"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2006-11-16
Hi,

Question for Dapper 6 & Edgy 6.10


Studying the Ubuntu wireless compatibility page, it appears as if Dapper & Edgy should recognize the Linksys WMP54G PCI card right off the get-go.

I use WPA-PSK and would just like to hear from anyone who can confirm that this is a seemless procedure with this PCI card.

I'm assuming I would not have to run the Linksys install CD, as it is Windows-related?

Thanks for your patience!

---

### Post by lonce on 2006-11-16
I use this exact card.  You dont have to install anything.  When you install ubuntu all you do is go to the network manager and configure it.  Worked right away for me.  No issues what so ever.

---

### Post by DapperMe17 on 2006-11-16
Thanks for your input.

 I'm trying SimplyMepis 6 right now as it was mentioned to detect more out-of-the-box hardware. Unfortunately, it's not seeing my PCI card. Looks like a change is in order, I guess. So much for being easier to recognize hardware.

---

### Post by StarSage on 2006-11-16
> **lonce said:**
> I use this exact card.  You dont have to install anything.  When you install ubuntu all you do is go to the network manager and configure it.  Worked right away for me.  No issues what so ever.

How weird.. Kubuntu is recognizing this very card on my system, and I'm able to detect available wireless networks.. but only those that are unsecured and I can't surf once connected. ](*,)

---

### Post by DapperMe17 on 2006-11-17
I've tried V6.10 Ubuntu, Kubuntu & Xubuntu from the LiveCD's & NONE have recognized my Linksys WMP54G card.

I tried the Wireless Configuration Tool in Kubuntu, but it doesn't locate my card.


Is the card supported in Edgy?


Now...

I've noticed that the light on the PCI card(back of tower) isn't lit. I've also noticed that it isn't listed as a PCI device in the settings menu of either three. It appears as if the card has a secure fit in the PCI bus.

Dumb ?...

Because we're talking about Linux, it is my assumption that I don't have to run the accompanying setup CD, as it includes the Windows driver only. Correct me if I'm wrong.

Thanks for any feedback


PS...I am a Ronnie James Dio (Vivian Campbell era) fan as well...gothic picture my fellow metalist!

---

### Post by frogotronic on 2006-11-17
> **StarSage said:**
> How weird.. Kubuntu is recognizing this very card on my system, and I'm able to detect available wireless networks.. but only those that are unsecured and I can't surf once connected. ](*,)

Try installing KEYRING and using that to get onto secured (WEP) networks.

---

### Post by diepruis on 2006-11-17
The problem with this card is that it uses 3 different chipsets, depending on the version. Please post the output of lspci -n and I'll see if I can help you.

---

### Post by jon419 on 2006-11-18
Here is my problem, if anyone can help.

In Ubuntu 6.06, My WMP54G card was detected and worked right off the live CD and into the install.  It uses the rt2500 chipset.

Now, in Ubuntu 6.10, My WMP54G (rt2500 chipset) is NOT detected at all, ever...doesn't work...  I look in the Device Manager and it is listed as WMP54G and all the manufacturer informatin is there, but the card DOESN'T work.  It is not even listed as an option in the Network Tools program....Where did I go wrong?

---

### Post by Aranel on 2006-11-18
> **jon419 said:**
> Here is my problem, if anyone can help.

In Ubuntu 6.06, My WMP54G card was detected and worked right off the live CD and into the install.  It uses the rt2500 chipset.

Now, in Ubuntu 6.10, My WMP54G (rt2500 chipset) is NOT detected at all, ever...doesn't work...  I look in the Device Manager and it is listed as WMP54G and all the manufacturer informatin is there, but the card DOESN'T work.  It is not even listed as an option in the Network Tools program....Where did I go wrong?

Try entering "sudo ifconfig ra0 up" and looking again. My mother's computer uses that card, and it took some hassle for me to get it up and running in Linux (in her case, it wasn't Ubuntu, but I imagine it's more or less the same regardless of the distro...).

---

### Post by diepruis on 2006-11-18
> **jon419 said:**
> Here is my problem, if anyone can help.

In Ubuntu 6.06, My WMP54G card was detected and worked right off the live CD and into the install.  It uses the rt2500 chipset.

Now, in Ubuntu 6.10, My WMP54G (rt2500 chipset) is NOT detected at all, ever...doesn't work...  I look in the Device Manager and it is listed as WMP54G and all the manufacturer informatin is there, but the card DOESN'T work.  It is not even listed as an option in the Network Tools program....Where did I go wrong?

In case Aranel's post doesn't solve your problem, please post the output of
```

lspci -n
lsmod

```

---

### Post by DapperMe17 on 2006-11-19
Does it make a difference if I have WPA enabled in My wireless router....as to the Linksys WMP54G being recognized? Would I have to initially run an unencrypted network off of my router, in order for Kubuntu/Xubuntu to recognize the PCI card?

Yes, I will run that command from a terminal window shortly.

---

### Post by diepruis on 2006-11-19
> **DapperMe17 said:**
> Does it make a difference if I have WPA enabled in My wireless router....as to the Linksys WMP54G being recognized? Would I have to initially run an unencrypted network off of my router, in order for Kubuntu/Xubuntu to recognize the PCI card?

No. You might have problems associating, but the card should be recognised regardless of the settings on the router.

---

### Post by DapperMe17 on 2006-11-19
Thank you.

After referencing the Ubuntu wireless reference guide, I settled on the WMP54G for the easiest recognition out of the box. Unfortunately, the guide doesn't reference more than one chipset.

Bottom line, I should be able to get this card working with some manual configuration?

---

### Post by diepruis on 2006-11-19
> **DapperMe17 said:**
> After referencing the Ubuntu wireless reference guide, I settled on the WMP54G for the easiest recognition out of the box. Unfortunately, the guide doesn't reference more than one chipset.

The guide is wrong. I have exactly the same card and went through exactly the same process as you are going through. If you post the output I asked for, I might be able to point you to the right howto.

---

### Post by DapperMe17 on 2006-11-19
I will run terminal & check lspci -n. 

The PC with the card in question has just been moved to a new location in the house, so I'll have to get it pieced together. For sure, I'll be back with that info Sunday night. 

I've noticed the different versions via NdisWrapper, and have noticed some other chipset drivers. Is this what you had to reference?

---

### Post by diepruis on 2006-11-19
> **DapperMe17 said:**
> I've noticed the different versions via NdisWrapper, and have noticed some other chipset drivers. Is this what you had to reference?

I'm not sure what you mean by "reference". The V4.1 of the card that I have requires firmware to be installed, some others need ndiswrapper. The method you use to get it working depends on the chipset.

---

### Post by DapperMe17 on 2006-11-19
Will get that info to you. Have been searching the forums & have noticed two Ralink & a Broadcom chip install guides. 

I'm working between two locations, so will download some drivers &  those how-to guides directly to a thumb drive, just in case I would need them on the PC.

Will get back to you tonight.

Thanks for your help. This forum is really very impressive & helpful.

---

### Post by DapperMe17 on 2006-11-19
Ok, here's my terminal result for "lspci -n...Linksys WMP54G...Xubuntu Edgy LiveCD

00:00.0 0600: 1106:0691 (rev 42)
00:01.0 0604: 1106:8598
00:07.0 0601: 1106:0596 (rev 11)
00:07.1 0101: 1106:0571 (rev 06)
00:07.2 0c03: 1106:3038 (rev 05)
00:07.3 0600: 1106:3051 (rev 20)
00:0a.0 0200: 1113:1211 (rev 10)
00:0b.0 0401: 127a:4310
00:0b.1 0780: 127a:4311
00:0b.2 0980: 127a:4312
01:00.0 0300: 10de:002c (rev 15)


Running "lshw" from the terminal doesn't show a wireless card.
 
Does this help ID the pci card?

---

### Post by diepruis on 2006-11-20
I used [this](http://kmuto.jp/debian/hcl/index.cgi) page to check your hardware. Go have a look. Your PCI device isn't detected, unless it is one of the "Rockwell" devices. I don't know why this could be, because you said it's fit securely. What are the odds that it got struck by lightning? It might even be a dud. More likely however is that it's one of those Rockwell something devices for which it doesn't seem there are drivers.

---

### Post by DapperMe17 on 2006-11-20
I hope you're not confined to a dark basement, my friend!

Thanks for getting back at me.

I think your right, the card must be kapeeeeeeeeesh. Reason being...although I'm an enthusiastic newbie to Linux, it doesn't take a brain surgeon to realize that the card SHOULD be showing in the PCI device manager, if it's in the slot ok. 

I just switched slots(to that of an active soundcard), and the PCI card still doesn't appear as a PCI device. If the device manager is recognizing all other devices in the PCI slots, then it's painfully obvious:eek: U PC

Too bad, I just bought the darn card on E'bay (100% feedback). It was cheap, so it's really no big deal. I did see that it was a Version 4 card.

I'll find a new one, local this time. If the Wiki for wireless isn't exactly up-to-date, would you have a recommendation for the new one?

Thanks again for your helpfulness. Great forum!

PS...Rockwell is the cruddy, stock HP sound junk...but it works for now.

---

### Post by diepruis on 2006-11-21
Lol! I'm only sent to the basement if I've been a bad boy, so don't worry ;)

Glad to find you so optimistic, many people are much more negative when they start Linux. Sorry, but I can't really help you with a reccomendation. That card works fine **if** you get it working, but you can't run a kernel with  pre-empt or SMP enabled. Not exactly ideal. The guys at [rt2x00.serialmonkey.com](rt2x00.serialmonkey.com) are working on an opensource driver, but it's still in beta for the rt61 chipset (which the Linksys WMP54G 4.1 uses). Several people could reccomend you a chipset, but there's no way of knowing what card uses it, because of the version problem. You'll need to do some more searching and research, but if I come across something, I'll PM you.

Good luck and have fun!

---

### Post by DapperMe17 on 2006-11-22
I picked up a Netgear WG311. Fingers crossed, biting nails! HaHa 

Thanks for all of your valuable information.

---

### Post by bionnaki on 2006-11-23
to install a linksys wmp54g card without ndiswrapper or wpasupplicant, see the link in my signature. works perfectly and very easy to set up.

---

### Post by diepruis on 2006-11-23
> **bionnaki said:**
> to install a linksys wmp54g card without ndiswrapper or wpasupplicant, see the link in my signature. works perfectly and very easy to set up.

Please read the rest of the thread before you comment.

That howto is for rt2500 cards, but the Linksys WMP54G has used 4 different chipsets over its lifetime. For example mine uses rt61. There are also version with non-ralink chipsets.

---

### Post by DapperMe17 on 2006-11-23
Well, I installed the Netgear WG311.

Same issue...hardware not found:( 

The machine is an HP Pavilion 8670C P3, 600mhz. (Pavilion Kestral Bios)

Disk erased & fresh install of Xubuntu 6.06 Dapper.

I'm bewildered here, as the network settings show both my dial-up modem, & my wired ethernet card, but no wireless.

lspci -n show exactly the same as my prior post, which doesn't include the Netgear PCI? 

The bios doesn't show anything unusual, or any wireless-specific settings.  


Is it a possibility that my motherboard doesn't support wireless PCI? It would be hard to believe, but....?

Every other PCI slot is identified as hardware, and in working order.

Another idea...could my router settings influence any of this hardware detection...such as SSID broadcast, WPA encryption, WAN Ping...etc?



What next??

---

### Post by diepruis on 2006-11-23
Firstly: sorry for misidentifying your problem.

I don't know what the problem could be. Have you tried to put the card into different slots?

---

### Post by DapperMe17 on 2006-11-24
Yes, I tried another PCI slot, which was working fine with the sound card. Either the Linksys, or Netgear, are identified' in that slot either.

I'm assuming that Xubuntu should FIRST recgnize the hardware. Therefor, any router settings shouldn't be issue UNTIL the PCI card is actually recognized.   


I really don't want to give up on it here, there has got to be something we're missing. 

Don't notice anything in Bios & don't think it's a necessity to remove the ethernet or dial-up modem prior to adding the wireless card...

I'd hate to go after a USB as the alternative, as it is USB 1.

There's too many know-alls in this forum to give up now! 

Any other ideas?

---

### Post by diepruis on 2006-11-24
I did a quick google search, and it looks like it might be your motherboard drivers, unfortunately I don't have any time to research this now, so you're pretty much on your own. :(

In particular, you should have a look at this device: "VT82C586/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE" and it's kernel module: "via82cxxx".

Good luck!

---

### Post by DapperMe17 on 2006-11-24
Thanks...I'll head to HP's support forum to ask a question. 

The MOB is the HP original...KESTRAL MOB P2B-VT MOB(Made by ASUS for HP)with VIA Apollo 133 chipset & original BIOS.

You could be onto something here.

Should I go to USB wireless adapter instead? 

Thanks for your search efforts!

---

### Post by diepruis on 2006-11-24
No problem.

A USB adapter will solve your problem (if I'm guessing correctly) but it's unneccessary if you can fix your motherboard.

---

### Post by DapperMe17 on 2006-11-24
I'll have to look to the board manufacturer, or post something to HP's forum.

HP only has a bios update (shortly after the original release - no documentation on PCI or wireless in the update), but shows nothing for motherboard drivers.

---

### Post by diepruis on 2006-11-24
> **DapperMe17 said:**
> HP only has a bios update (shortly after the original release - no documentation on PCI or wireless in the update), but shows nothing for motherboard drivers.

Don't forget to look at the actual kernel module as well.

---

### Post by DapperMe17 on 2006-11-24
Nothing found for that motherboard on Google,  or HP.

Pardon me for sounding uneducated, but what is the kernel module?

Kernel is a term I've only heard in Linux, and I still don't know what it is! haha

Any insight on a good USB adapter, that works "fairly" out-of-box?

---

### Post by diepruis on 2006-11-24
> **DapperMe17 said:**
> Nothing found for that motherboard on Google,  or HP.

Pardon me for sounding uneducated, but what is the kernel module?

Kernel is a term I've only heard in Linux, and I still don't know what it is! haha

Any insight on a good USB adapter, that works "fairly" out-of-box?

All operating systems have a kernel. Linux just tells you about it. Linux - that is the kernel - is a monolithic kernel, where windows uses a microkernel. A monolithic kernel incorporates much more functionality into the kernel than a microkernel. For example: in Windows the firewall isn't part of the kernel, while the opposite is true for Linux. Kernel modules are parts of a monolithic kernel that can be added to, or removed from the kernel without recompiling it, or even rebooting. Drivers under Linux are usually kernel modules - that is what you need to check.

I can't really recommend one a usb adapter, but the rt73 based devices seem to work fairly well. Have a look at [this]("http://www.ubuntuforums.org/showthread.php?t=304558") thread.

---

### Post by DapperMe17 on 2006-11-24
When you say to check the kernel module...do you mean I need to check it in Xubuntu? I don't know how to approach something like this yet. 

In reading some other threads...I ended up at passys.nl. Under that first Linksys WMP54G PCI card...it showed drivers from Ralink(RT61), as well as SerialMonkey(RT61)

Would it take either of these, in order to get the card recognized as a hardware device...either in the device manager, or lspci? Other threads, re: no hardware detection, seem to revert to this software to help ID the cards.

If these drivers might help, is there a specific command to run the .tar? Not sure how to manually install software in Linux (...a work in progress).

---

### Post by diepruis on 2006-11-26
Sorry for replying so late. Life has been a bit hectic :)

Those drivers might help ID the card, though I doubt it. If you've found other threads that say they do: then go right ahead. You might've just found a bug where lspci doesn't display a device, but it is detected.

I don't know how to install that specific "tarball" (.tar file). Extract it like so:

```

tar -xvzf the_tarball_s_file_name.tar.gz (for .tar.gz files) or
tar -xvjf the_tarball_s_file_name.tar.bz (for .tar.bz files)

```

Then thouroughly read through the README and INSTALL files extracted from the archive. If you don't understand something in there, ask, or do some research.

---

