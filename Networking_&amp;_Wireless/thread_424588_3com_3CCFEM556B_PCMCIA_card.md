---
title: "3com 3CCFEM556B PCMCIA card"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by Duron on 2007-04-26
I have Edgy installed on a dual-boot with Win2k on my laptop, and the PCMCIA card (titled) works just fine in Windows. No ISP drivers to install, just plug in and open a browser. In Edgy, the lights won't even come on when I plug it in (or restart the computer with the plug in). The card is listed in the Device Manager under "PCI1225", and I can see it when I type "lspcmcia -v", but still nothing. This is the output from that command:

Socket 0 Device 0: [-- no driver --] (bus ID: 0.0)
Configuration: state: on
Product Name: 3Com Megahertz 3CCFEM556B A 001

I used pppoeconf in a Terminal and it told me that no working ethernet card could be found. I also used modprobe to load the module (3c574_cs, shown on the HardWareSupportComponentsWiredNetworkCards3Com page), which didn't work. modconf doesn't do anything.

There's a thread like this on LinuxQuestions already, but no one's answering it. I tried upgrading to Feisty for the new version of the kernel, but this did not produce anything different. But I noticed as I reinstalled Edgy that this error came up when booting from the Live CD:

firmware_helper[4660]: main: error loading '/lib/firmware/3CCFEM566.cis' for device '/class/firmware/0.0' with driver (unknown)

---

### Post by Ted Nancy on 2007-05-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/fedora/+bug/52510](https://bugs.launchpad.net/fedora/+bug/52510) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm trying to tackle the same problem. If you're better at this than me you might find this discussion useful. Unfrotunately, it was well beyond my understanding:

[https://bugs.launchpad.net/fedora/+bug/52510](https://bugs.launchpad.net/fedora/+bug/52510)

---

