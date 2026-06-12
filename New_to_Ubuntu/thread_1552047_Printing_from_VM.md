---
title: "Printing from VM"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by BobJam on 2010-08-13
I want to print from my Windows XP running within a VirtualBox to a printer connected to my Ubuntu “host”.  I can't get it to work, and am just about to throw this thing out the window.

There are two ways to print from a VB guest with a USB printer.

The first is to simply enable the USB port (in the VM) where the printer is connected, install the driver (in the VM), and AFAIK that's it.

But USB support within VB is iffy at best, however I tried it.  It failed, and here are the details.

First of all, as I understand it, only the PUEL version supports USB devices.  I . . . think . . . that's what I have.  I downloaded it from the VB site, not the repository.  I get update notices from Oracle, not Ubuntu.  So I am pretty sure that means I have PUEL instead of Open Source.  Plus I am able to add the USB "filter" in the main VB window:  Settings>USB.  It shows up as "Dell Photo Printer 720 [0100]"

(And yes, I installed and can print to this Dell 720 Printer FROM UBUNTU)

But here's the rub in the VM.  When I start the VM, the 720 USB listing shows up in USB devices but is greyed out.  I can't select it.  (My other USB devices I CAN SELECT, which baffles me).  As you would expect, hovering over the USB icon in the VM window produces "No USB devices attached"

I installed the 720 driver in the WindowsXP VM, but all I get when I try to print is "Communication not available" . . . which makes some sense considering that it's not seeing the USB connection.

So, the USB connection seems hit-or-miss.

The second way to print from my Windows XP running within a VirtualBox to a printer connected to my Ubuntu “host” is just to flat out send the print job through to Ubuntu (via the CUPS function and networking in Windows) and forget doing it via the guest USB connection (which didn't work for me anyway).

So now this fails too.  Here is what I did.

1.  In Ubuntu, I enabled access to my printer by going to System>Administration>Printer and ticking "Publish shared printers connected to this system" in the Server Basic Settings dialogue.

2.  Then I determined the printer URL by going to "http//localhost:631/" in my browser.  That took me to the CUPS admin page, where I navigated to the "manage printers" page, highlighted the 720, and got from the address bar "http//localhost:631/printers/Dell--Photo-Printer-720".

3.  This next step was where I hit the wall.  In my VM, I pasted in to my browser there "http//<my Ubuntu host IP>:631/printers/Dell--Photo-Printer-720", where <my Ubuntu host IP> is the machine IP.  This should have taken me to the CUPS page where I could have gone to the "manage printers" page like above and seen that the WindowsVM could access the printer.  ALL I GOT HERE WAS "SERVER NOT FOUND"

4.  Of course, when I went to config the thing in the Windows "Add Printers" sequence, I hit the same wall with the warning dialog telling me "Windows cannot connect to the printer. Either the printer name was typed incorrectly, or the specified printer has lost its connection to the server".  I retyped several times tediously, but still no go.  I also tried my NAT IP, but got the same message.

I'm not a network kinda' guy and got these procedures from Googling and the virtualbox.org forums, so my sense is that I'm missing something real simple.

There is a workaround I guess.  I have some shared folders in the VM.  I'm guessing maybe if I wanted to print out of the VM, I could "print to file" and store it in a shared folder and then print it to my 720 out of Ubuntu.  But this would seem to work only on text . . . no graphics.

As I'm sure all will notice by now, I'm a novice in this area, and I really don't know what I'm doing.  I'm sure I'm missing something here . . . and as I said, something real basic that will likely result in a "Duhhhhhh . . . " moment for me.

In any case, I'd like to be able to print out of the VM directly, instead of tediously applying a workaround that will only do text anyway.

Help!!!!!  What am I missing?

Ubuntu 9.10, VirtualBox 3.2.8, in VM is WindowsXP HE.

---

### Post by Paqman on 2010-08-13
Is this the full fat version of Virtualbox directly from Oracle, or the open source version from the Ubuntu repos? The latter lacks USB support altogether, among other things.

---

### Post by BobJam on 2010-08-13
@ paqman.

Here's my fifth paragraph in my OP:

> **BobJam said:**
> First of all, as I understand it, only the PUEL  version supports USB devices.  I . . . think . . . that's what I have.  I  downloaded it from the VB site, not the repository.  I get update  notices from Oracle, not Ubuntu.  So I am pretty sure that means I have  PUEL instead of Open Source.  Plus I am able to add the USB "filter" in  the main VB window:  Settings>USB.  It shows up as "Dell Photo  Printer 720 [0100]"

Is there a terminal command that will show "PUEL"?

And, since I can attach my USB sticks (see my OP for that detail too), I would assume it's PUEL (Which is, as you put it "the full fat version).

---

### Post by Paqman on 2010-08-13
Sorry about that, my mistake. Your post was long and I skimread. You have the full version.

---

