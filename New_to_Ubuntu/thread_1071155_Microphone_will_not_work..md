---
title: "Microphone will not work."
date: 2009-02-15
forum: New to Ubuntu
---

### Post by G00D_GUY on 2009-02-15
I need help. My mic will not work. I have tried to follow all of the instuctions on how to get it to work, but I am new and think I have followed them correctly. I think the problem is the red image in the GUI alsamixer. Check it out. 

[Screenshot]("http://members.cox.net/mmusacchia1/Screenshot-6.png")

Thanks

---

### Post by halovivek on 2009-02-16
Could you post more about computer configuration.?

i hope you can check this [link]("http://ubuntuforums.org/showthread.php?t=1005416") to get solution.

---

### Post by G00D_GUY on 2009-02-16
That is a hard question, but here it goes.

I have an: Asus A7N8X motherboard
Northbridge Nvidia nforce2 SSP ultra
Southbridge Nvidia nforce2 MCP

The book says: Realtek ALC650 6CH with built in HP Amplifier

I have three jacks on the back of the computer attached directly to the motherboard: red, light green, dark green(i have no idea what this is for).

Basicaly, I have a mic attached to the red jack that I can not get to work. The speakers work great.

I hope this is the info needed. 

Please help me.

---

### Post by halovivek on 2009-02-17
Double click the speaker icon in the desk bar. click the preferences and check for the capture and increase it and do testing.

---

### Post by G00D_GUY on 2009-02-17
Thanks for the reply.

I tried all of the levels, but no luck.:(

---

### Post by halovivek on 2009-02-17
could you please post output from the terminal
lspci

---

### Post by G00D_GUY on 2009-02-17
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)


Hope this helps.

Thanks

---

### Post by mikewu on 2009-02-17
This is what I did to get the microphone working for me.

Go to alsamixer and then enter the full view mode. (Like in your screenshot).

Arrow over to mic and mute it. This prevents the computer from playing the microphone over the speakers. 

Arrow over to anything that says mic Capture or Capture and turn that all the way up.

Quit alsamixer and try the sound recorder.

That's what I did, maybe it will work for you.

Good luck!

---

### Post by G00D_GUY on 2009-02-17
Problem fixed.

Everything works great if I plug the mic into the front of the computer. Although I changed the settings in Alsamixer to Mic 1 and Mic 2 only the front jack works. I should also mention that the crazy thing here is that the front doesn't work in Windows XP. Figure that one out ;) 

Thanks to all.

---

