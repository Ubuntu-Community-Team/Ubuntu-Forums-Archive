---
title: "Oh dear, all gone after update..."
date: 2011-03-01
forum: New to Ubuntu
---

### Post by trevarez on 2011-03-01
I just used update manager earlier, I simply left all boxes ticked and updated everything without reviewing. The update took around twenty minutes and then the computer needed to be restarted. I let it do that but it never restarted fully, it ended with the following message:

Realtek PCIe FE Family Controller Series v1.12 (07/28/10)
PXE-E61: Media test failure, check cable

PXE-MOF: Exiting PXE ROM

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key_

What's gone wrong? What do I do?

Kai

---

### Post by amjjawad on 2011-03-01
> **trevarez said:**
> I just used update manager earlier, I simply left all boxes ticked and updated everything without reviewing. The update took around twenty minutes and then the computer needed to be restarted. I let it do that but it never restarted fully, it ended with the following message:

Realtek PCIe FE Family Controller Series v1.12 (07/28/10)
PXE-E61: Media test failure, check cable

PXE-MOF: Exiting PXE ROM

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key_

What's gone wrong? What do I do?

Kai

Not quite sure but if I'm reading correctly, your BIOS "maybe" is booting from your LAN.

Double check your BIOS.
Yes, I know you did not touch anything but there is no harm to check!

---

### Post by trevarez on 2011-03-01
> **amjjawad said:**
> your BIOS "maybe" is booting from your LAN.

Double check your BIOS.


Now, I don't understand what you are saying, I have heard of BIOS, don't know what it is though, nor do I know what LAN is (unless you mean local area network), and how do I "check my BIOS"?

Thanks for the quick reply.
Kai

---

### Post by jeremy1138 on 2011-03-01
> **trevarez said:**
> Now, I don't understand what you are saying, I have heard of BIOS, don't know what it is though, nor do I know what LAN is (unless you mean local area network), and how do I "check my BIOS"?

Thanks for the quick reply.
Kai

You should see a prompt to access your computer's BIOS settings very shortly after you press the button to turn your computer on.  I believe on my computer I have to press F2 or F10 to access the BIOS settings but I'm not sure off hand.

You should take a look around in your BIOS settings (while being sure not to accidentally change anything) and see if you can find out the order your computer looks at devices to boot from.  For troubleshooting purposes, just make sure that the disk that Ubuntu is installed on is set to be the first boot device.

---

### Post by trevarez on 2011-03-01
Quite miraculously it mended itself and is working again...

Can I check the system somehow to check if anything is wrong?

Kai

---

### Post by jeremy1138 on 2011-03-01
> **trevarez said:**
> Quite miraculously it mended itself and is working again...

Can I check the system somehow to check if anything is wrong?

Kai

I went back and took a look at the original error message that you posted and I don't think that the boot order was the problem and it doesn't look like it has anything to do with your LAN connection.  It appears, from what I can tell, that there was an error with your hard drive controller that was blocking the computer from accessing the disk.

I suppose it could be a loose hard drive cable or it could mean that the drive controller is going but I'm more inclined to believe that it was just "gremlins" as the IT guy here at work refers to them.

In other words, I wouldn't give it any more thought unless you see it happen again or you notice anything else weird happening.

If you want to pursue it further though, I know there are log files that are kept by the OS and stored on your computer for you to read and diagnose these types of problems.  I'm not sure where the one you need is stored but perhaps someone else can help out more with that?

---

### Post by amjjawad on 2011-03-01
> **trevarez said:**
> Now, I don't understand what you are saying, I have heard of BIOS, don't know what it is though, nor do I know what LAN is (unless you mean local area network), and how do I "check my BIOS"?

Thanks for the quick reply.
Kai

[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

[http://en.wikipedia.org/wiki/Preboot_Execution_Environment](http://en.wikipedia.org/wiki/Preboot_Execution_Environment)

[http://en.wikipedia.org/wiki/Local_area_network](http://en.wikipedia.org/wiki/Local_area_network)

> R[B][I]ealtek PCIe FE Family Controller Series v1.12 (07/28/10)
PXE-E61: Media test failure, check cable

PXE-MOF: Exiting PXE ROM[/I][/B]

I suggest to search the above error message on google and you'll understand at least what was going on.

Always use google before anything else ;)

---

### Post by trevarez on 2011-03-01
Thanks for the suggestions. It's all part of the new learning curve :-)

Kai

---

