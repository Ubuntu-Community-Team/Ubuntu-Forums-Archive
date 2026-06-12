---
title: "Video Display Crashed during Update"
date: 2009-10-22
forum: New to Ubuntu
---

### Post by squid68 on 2009-10-22
Hardy updates today crashed my video display. Said during reboot could not find my driver and now left with 640x480 resolution. I did nothing wrong. Please help. I have no idea how to fix this. Please advise. Thanks.

---

### Post by aesis05401 on 2009-10-22
Open a terminal and type:
```

lspci

```

Please post the output here.

---

### Post by squid68 on 2009-10-22
Here it is:

brandon@deep-thought:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
brandon@deep-thought:~$

---

### Post by aesis05401 on 2009-10-22
This doc should help, but I haven't tried it on your hardware: [http://gwos.org/udsf/doku.php/hardware:nvidia](http://gwos.org/udsf/doku.php/hardware:nvidia)

Please post feedback one way or the other.

---

### Post by squid68 on 2009-10-22
Thanks. But this is so confusing. I had to do nothing when I installed Ubuntu. Everything worked right off the bat.  If I do the xorg fail safe and depenency build will that be enough? I don't know what went wrong here.

---

### Post by aesis05401 on 2009-10-22
That is a very good question.  I cannot guarantee that any part of resetting and reinstalling your drivers will correct this issue.  Additionally, I cannot explain why this problem has developed on your machine.  

Resetting and installing the drivers clean is my best suggestion.  Others may have better ideas.

---

### Post by squid68 on 2009-10-22
I was able to purge the driver and rebuild the xorg but could not get the driver installed. It kept saying could not find it in the tty mode.  Not sure why.  At least for now I be back at 1024x768 problem only half solved. Thanks aesis05401 for at least getting me this far!

---

