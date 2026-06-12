---
title: "Is there a way in Ubuntu to tell if my network card is physically broken?"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-12-10
Hello:

All of a sudden my pc can't connect to the internet on the 'wired' connection.

I used my D-Link Wireless USB and I can connect.

Any suggestions?

Thanks,

---

### Post by Hippytaff on 2010-12-10
Does
```

lscpi | grep -i eth

```
return anything, can ubuntu still see the ethernet controller?

---

### Post by Robert.Thompson on 2010-12-10
> **Hippytaff said:**
> Does
```

lscpi | grep -i eth

```
return anything, can ubuntu still see the ethernet controller?

It says command not found.

---

### Post by Hippytaff on 2010-12-10
> **Robert.Thompson said:**
> It says command not found.
 
sorry, typo should be
```

lspci | grep -i eth

```
 
lspci not lscpi *sigh* sorry

---

### Post by Robert.Thompson on 2010-12-10
> **Hippytaff said:**
> sorry, typo should be
```

lspci | grep -i eth

```
 
lspci not lscpi *sigh* sorry


it returned: 00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)

---

### Post by Hippytaff on 2010-12-10
Have you updated/upgrade recently? - check in system -> Administration -> alternative drivers
 
to see if it offers the driver to download.

---

### Post by corncob on 2010-12-10
> **Robert.Thompson said:**
> Hello:

All of a sudden my pc can't connect to the internet on the 'wired' connection.

I used my D-Link Wireless USB and I can connect.

Any suggestions?

Thanks,

I'd check the cable first thing.  Is it snapped into place both on the computer and router?  Do you have another cable to try?

---

### Post by Robert.Thompson on 2010-12-10
> **Hippytaff said:**
> Have you updated/upgrade recently? - check in system -> Administration -> alternative drivers
 
to see if it offers the driver to download.

Nope, no new drivers.

---

### Post by Robert.Thompson on 2010-12-10
> **corncob said:**
> I'd check the cable first thing.  Is it snapped into place both on the computer and router?  Do you have another cable to try?

The cable light flashes at the router but does not flash at the PC - with either of two different cables.

I think my card is cooked.

---

### Post by Hippytaff on 2010-12-10
Did you check that your ethernt cable as per corncob's post.  If so can you post the output of these.
```

lshw -C network

```
```

ifconfig

```

---

### Post by FreeComputerHelp on 2010-12-10
Hello, and your network card is not broken. It may be that you don't have a Ubuntu compatible Ethernet Driver. To connect via Ethernet cable, you need a Ethernet Driver for Ubuntu. 

Please let me know what your Network Card Model is. Then I will find you a driver gladly!  **Remember it's not always a physical problem**

---

### Post by FreeComputerHelp on 2010-12-10
Try connecting to the internet via Ethernet. If you want to use a ***[I]Wireless Network*[/I]**, you have to connect, then go to System > Administration > Hardware Drivers. The connect and download the drivers. The restart and take out the Ethernet wire, and it should say Wireless Networks Available. Then connect to your network! 

Hope this helps!


If you can't connect at all, make sure you press the F2 key on you computer, and then it should connect, or if it does not, please restart the computer, (Or please press Fn+F2)

---

### Post by FreeComputerHelp on 2010-12-10
> **FreeComputerHelp said:**
> Try connecting to the internet via Ethernet. If you want to use a ***[I]Wireless Network*[/I]**, you have to connect, then go to System > Administration > Hardware Drivers. The connect and download the drivers. The restart and take out the Ethernet wire, and it should say Wireless Networks Available. Then connect to your network! 

Hope this helps!


If you can't connect at all, make sure you press the F2 key on you computer, and then it should connect, or if it does not, please restart the computer, (Or please press Fn+F2)

Also, you may want to contact your ISP ( Internet Service Provider ) If you CANT CONNECT AT ALL! EVEN WITH EJECTING THAN INSERTING THE WIRELESS CARD! PLEASE FOLLOW ALL STEPS AND LOOK AROUND TO MAKE SURE IT WORKS!
:KS :KS

---

### Post by Hippytaff on 2010-12-10
> 
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)

Freecomputerhelp - here you go, just in case you didn't notice this a few posts ago :-)

btw - we tried installing drivers ;-)

---

### Post by Robert.Thompson on 2010-12-10
> **Hippytaff said:**
> Did you check that your ethernt cable as per corncob's post.  If so can you post the output of these.
```

lshw -C network

```
```

ifconfig

```

I am sorry but I can't work on this now.

I truly appreciate your help.

I will post on Sunday and pray that you guys are still 'lurking' about in this forum...

---

### Post by Hippytaff on 2010-12-10
> 
Try connecting to the internet via Ethernet. If you want to use a [B][I][I]Wireless Network
[/I][/I][/B]Also, it's the opposite that is going on here. The op can't connect via ethernet but can via usb-wireless :-)

maybe read the thread before suggesting fixes ;-)

---

### Post by Hippytaff on 2010-12-10
> **Robert.Thompson said:**
> I am sorry but I can't work on this now.

I truly appreciate your help.

I will post on Sunday and pray that you guys are still 'lurking' about in this forum...

No worries...looking forward to trying to fix this though..I always lurk here :-)

---

### Post by corncob on 2010-12-11
> **Robert.Thompson said:**
> The cable light flashes at the router but does not flash at the PC - with either of two different cables.

I think my card is cooked.

One thing you could try is reversing the cable -- plug the end where the light goes on into the computer just to check the unlikely event that the light on one end of each cable is burnt out.  Try a different port on the router or plug the computer directly into the modem.  Does the modem have a USB port you could try instead of ethernet?  Actually, I think you're right and I'm beating a dead horse but I don't know what else to say.

---

### Post by Robert.Thompson on 2010-12-13
Hello:

Thank you for all your posts.

The network card was broken/fried/dead.

Also, the power-supply was not working properly!

This Acer pc is just 2 months old!

It will be repaired under warranty but I no longer have any faith in Acer - I feel like they screwed me by selling me a pc that probably should have never left the factory.

Such is life...

Thanks again,

---

### Post by Hippytaff on 2010-12-13
Glad you finally nailed the problem, sorry to hear it was a hardware issue though, at least you get to sort it under warranty :-)

---

