---
title: "HP Compaq Presario; Wireless not working. Wifi Button"
date: 2013-10-10
forum: Networking &amp; Wireless
---

### Post by Devinhdl on 2013-10-10
Hello, I recently installed (didn't test from live CD first) Ubuntu 13.04 on my spare computer, just to mess around with it. Now that it's installed, I can not connect to the internet, wirelessly. At the moment, I am plugging an ethernet cable into my laptop for internet access but would eventually like to use wireless. I am extremely new to linux; I barely know my way around. 

I've done some research on how to fix it and came across some people saying that I need to install the right driver. After spending multiple hours trying to download the right driver and install it and having every result's outcome being a total failure. Now, after all of my failure, I come to these forums to hope to get this problem solved. Thank you for anyone whe helps!

---

### Post by varunendra on 2013-10-11
Welcome to the forums Devinhdl !

Let us first see which wifi card you have and if there is a driver already associated with it. Please open a terminal (Ctrl-Alt-T) and enter these commands (one by one, you may copy-paste) -
```
lspci -nnk | grep -iA2 net
rfkill list all
```
Post back the entire output here in your next post.

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

### Post by Devinhdl on 2013-10-11
Thank you for your reply! This is the output from the terminal:

```
tyler@tyler-Presario-CQ57-Notebook-PC:~$ lspci -nnk | grep -iA2 net
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: r8169
--
07:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
    Kernel driver in use: rt2800pci
tyler@tyler-Presario-CQ57-Notebook-PC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
tyler@tyler-Presario-CQ57-Notebook-PC:~$ 


```

---

### Post by varunendra on 2013-10-11
> **Devinhdl said:**
> ```
07:00.0 Network controller [0280]: Ralink corp. **RT5390** Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
    Kernel driver in use: **rt2800pci**
tyler@tyler-Presario-CQ57-Notebook-PC:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: **[COLOR="#FF0000"]yes[/COLOR]**
    Hard blocked: **[COLOR="#FF0000"]yes[/COLOR]**
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: **[COLOR="#FF0000"]yes[/COLOR]**

```

Please try -
```
sudo rfkill unblock all
```

Then recheck -
```
rfkill list all
```
Is the Hard/Soft block removed? If not, and if your system is **not** a UEFI based setup, try resetting the BIOS to remove the hard block. If it's still there, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by Devinhdl on 2013-10-11
Thank you so much. I reset my BIOS and then turned on my computer and now it works fine. That was the problem I guess. Again, thank you.

---

### Post by varunendra on 2013-10-11
> **Devinhdl said:**
> Thank you so much. I reset my BIOS and then turned on my computer and now it works fine. That was the problem I guess. Again, thank you.

You're welcome! :)

Many wireless cards and/or BIOS have this 'locking feature' which becomes a bug in situations like this. There can be slightly different reasons for them to be triggered, most often a 'lockdown' instruction from a shutting down or hibernating windows os.

But if resetting BIOS worked once, I believe you shouldn't need it again, especially since you don't seem to be dual booting with windows.

If the solution is persistent and you are satisfied, please mark the thread **[SOLVED]** now using the "**Thread Tools**" link above the top post. It helps others by indicating that this thread contains a possible solution to the topic.

---

