---
title: "Wireless not detected"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by compelite on 2010-07-08
Btw I'm typing this from my iPod , lol. I'm having trouble with my Internet connection, I finally got the network manager working (ubuntu studio doesn't include) and the network icon appears at the top right of the screen - but it has a res square with an x symbol. I do not have Ethernet connection but I do have wireless connection - but they are not displayed. Any ideas will be appreciated and I would really like to get started with ubuntu! thanks!

---

### Post by mikewhatever on 2010-07-08
You need to provide some info about the wireless hardware on board, for example, the output of lspci from a terminal window.

---

### Post by compelite on 2010-07-08
Bump, xome on, someone must know - if not then I guess I'll have to find my own way =\

EDIT: spoke too soon, I'll search for net info, brb.

---

### Post by compelite on 2010-07-08
Ok, here is some info I found in terminal, typed innm-applet and here is what I get,btw i'
 a beginner and I hope i did this right and if not would love detailed beginner friendly step by step info as that is he best of help anyone cAn give in beginners section.

** (nm-applet:1548): WARNING ** <WARN> applet_dbus_manager_start_service(): could not aquire the NetworkMqnqgerUserSettings service as it is already taken.

(nm-applet:1548) GLib-G0bject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed

there, took a while but I managed, if there is any other info needed, please let me know as I need to make sure I have the right info, alright hope somone can help.

---

### Post by mikewhatever on 2010-07-08
I've asked for the output of **lspci**, not [s]nm-applet[/s]. Can you provide that?

---

### Post by compelite on 2010-07-08
> **mikewhatever said:**
> I've asked for the output of **lspci**, not [s]nm-applet[/s]. Can you provide that?

How do you find the ispci?

---

### Post by DMzda on 2010-07-08
Type
```
lspci
```
into the terminal.

---

### Post by mikewhatever on 2010-07-08
> **compelite said:**
> How do you find the ispci?

You don't. Just type **lspci** in a terminal window and hit enter.
Don't forget to post the output.

---

### Post by wamses on 2010-07-08
Not sure if this applies to your problem, but I recently started on Ubuntu with a dell inspiron mini and couldn't get connectivity until I turned on bluetooth.
 
Good luck

---

### Post by compelite on 2010-07-08
Alright, a whole list of stuff came up, I'll transfer it via computer, one moment

**Edit: Alright, here is what I got:**
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:03.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX] (rev a2)
06:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
06:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)

---

### Post by compelite on 2010-07-08
I should also mention that I have a Linksys wireless usb network adapter and have found people who are having a similar problem but I still have some fixing to do.

---

