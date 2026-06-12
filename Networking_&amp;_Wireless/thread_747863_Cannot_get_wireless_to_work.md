---
title: "Cannot get wireless to work"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by Okete on 2008-04-07
Downloaded Ubuntu yesterday, ever since, i have been trying to get the wireless to work. I'm not the best with computers, and i have had help from other Linux users i know, everything thats been attempted has ended up not working. I have updated my wireless cards drivers, double checked everything, and in the end, the wireless card stopped detecting servers what-so-ever instead of just failing to connect. I reinstalled Ubuntu fresh and another friend told me some things i could do to try to connect to my routers IP and such, still failed. I'm hoping someone has a solution for this problem, because Ubuntu looks amazing.

If you need any extra information about the wireless card and my internet, say so in replies and i will post them as needed.

---

### Post by riven0 on 2008-04-07
Post the output of this command, so we can see if your wireless card is detected: **lspci**


Then, try this command: **iwconfig**



We can work from there...

---

### Post by Bubba64 on 2008-04-07
There are a lot of posts on this subject so hopefully you know how to search around here is a basic link to a generalized wireless forum
[http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=136](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=136)
The best thing you can do is also list your system specs or search for the terminal commands to get a full readout or hopefully somebody will post them for you. Good Luck well I see riven0 has posted what you need for a system description and detect.

---

### Post by Okete on 2008-04-07
Not sure what i was looking for with the first command, ill write it down in a minute and post it.

But for iwconfig,
lo- no wireless extentions
eth0- no wireless extensions
wmaster0- no wireless extensions
wlan0- IEEE 802.11g

---

### Post by Okete on 2008-04-07
Ram- Nvidia Corporation MCP65 Memory Controller
ISA bridge- Nvidia Corporation MCP65 ISA bridge
Ram- Nvidia Corporation MCP65 Memory Controller
USB Controller- Nvidia Corporation MCP65 USB controller
USB Controller- Nvidia Corporation MCP65 USB controller
Ethernet- Nvidia Corporation MCP65 Ethernet
Audio Device- Nvidia Corporation MCP65 High definition Audio
PCI Bridge- Nvidia Corporation MCP65 PCI Bridge
IDE interface- Nvidia Corporation MCP65 IDE
IDE interface- Nvidia Corporation MCP65 SATA controller
PCI- Nvidia Corporation MCP65 PCI Express bridge
PCI- Nvidia Corporation MCP65 PCI Express bridge
PCI- Nvidia Corporation MCP65 PCI Express bridge
Host Bridge- Advanced Micro Devices [AMD] k8 [Athlon64/optron] hypertransport technology information.
Host Bridge- Advanced Micro Devices [AMD] k8 [Athlon64/optron] Adress Maps
Host Bridge- Advanced Micro Devices [AMD] k8 [Athlon64/optron] DRAM controller
Host Bridge- Advanced Micro Devices [AMD] k8 [Athlon64/optron]Misc control
VGA compatible controller- Nvidia Corporation 672[GeForce 7300 SE]


From the iwconfig

---

### Post by Okete on 2008-04-07
Id also like to note that i can view the connections and there strengths, but when i try to connect, it tries, but it wont, and i have used these connections before when my comp was on a different operating system.

---

### Post by Okete on 2008-04-07
And also, when i tried to install the latest drivers, they were already installed.

---

