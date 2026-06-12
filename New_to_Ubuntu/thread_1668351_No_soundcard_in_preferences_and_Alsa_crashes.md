---
title: "No soundcard in preferences and Alsa crashes"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by cheapodonuts on 2011-01-16
This is certainly my fault for clicking on buttons and not making a note of what I did. But I was expecting to be able to go back if something didn't work out.
I've been trying to use AMSynth (unsuccessfully) over the last couple of days and have not lost all sound. When I check the sound control properties, there is no hardware visible. And if I try to use Alsamixer, it crashes when I click one 'properties'.


My PC knows the sound card is there, apparently, so what did I do wrong! DOH! :o

cheapo@cheapo-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
cheapo@cheapo-desktop:~$ 

Thanx in advance for any help guys.

Pete.

---

### Post by khelben1979 on 2011-01-16
Have you tried alsamixergui? 

In order for the system to use your sound chips, a proper driver needs to get loaded first (kernel module which can get loaded by the modprobe command). Have you had working sound before using that AMSynth application?

---

### Post by cheapodonuts on 2011-01-16
Thanks for a quick response khelben. :)

I can' find any app that finds my sound card!

My reason for wanting to try this synthesizer is to try and produce a sound exactly the same as my tinnitus, so that I can demonstrate just how horrible it is. When you talk to most people about tinnitus, they are simply not able to comprehend how much it can take over a persons life. It is really awful and very depressing. Tinnitus also makes learning stuff difficult, as it takes my attention, just like having a third task do do at the same time.
 So I'm a bit like Homer Simpson, who forgets most things that he has just been shown how to do! DOH!

Ah, ok. Now I found alsamixergui

Still have a problem as the amSynth won't connect.

I'm not complaining, because I really appreciate the hard work that people have put into all these programs. But I didn't expect it to be so difficult. Haha! :D

---

### Post by khelben1979 on 2011-01-18
Lets start with you making this command: ```
modinfo soundcore
``` and report back to us what happens.

I'm checking the instructions from [here]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel") myself, but it isn't exactly newbie friendly.

---

### Post by cheapodonuts on 2011-01-27
Hi khelben, thanks so much for your input, it truly is appreciated.
 Sorry for the delay. I can't be without sound on my machine. I use it to play background sound to help my tinnitus, so I just said 'hell' to it and re-installed Ubuntu.
I'm going to try AGAIN with AMSynth and won't make any big changes without advice.

I'll be back as soon as i have a problem.

Thanks again. :)

Have a donut.

[IMG]http://i81.photobucket.com/albums/j226/chashugh/donuts-2.jpg[/IMG]

---

### Post by khelben1979 on 2011-01-29
Nice picture! :D

Good luck over there and let us know if you need any more help in this thread. I think I'll take the donut in the left upper corner with the cream in the middle. ;)

*B.t.w. I got tinnitus too, but I'm sure it isn't as bad as yours. Having an ear infection in the last quarter of 2010 I really know how a tinnitus sounds like, don't give up on Ubuntu even though it might be hard at first, it's a great experience to not worry about viruses and trojans you know.*

---

### Post by cheapodonuts on 2011-01-29
Give up on Ubuntu? I have had Ubuntu on my for around 5 years and I love it. The problem is with the VAIO. It now refuses to show any evidence of th desktop apart from the first wallpaper and a cursor. And that's after a second install into another partition today. Neither Ubuntu or Lubuntu will work. I have a disk with Ultimate Boot on it, which should begin with DOS, but the machine just blanks out! 

Very strange. :¬?

Oh yes, the other strange thing is that this VAIO appears to be running without the button cell in the back. That's because I took it out, and accidentally started it when I'd forgotten to put it back! It ran XP, which I have wiped out, then Ubuntu 8.10 very slowly due to 256 meg RAM, then Lubuntu  which I mentioned recently I upgraded, that ran, but while trying to get a bigger screen res I now have a dead lappy. 

I will go to the Lubuntu guys ang ask questions there.

Cheers. Pete.

---

