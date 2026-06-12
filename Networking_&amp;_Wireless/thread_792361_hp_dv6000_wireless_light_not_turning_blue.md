---
title: "hp dv6000 wireless light not turning blue"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by mikykim070 on 2008-05-12
i have a hp dv6000 laptop and i just installed ubuntu v8.04...the newest version.  and now the wireless light won't turn blue.  it's always orange.  can someone help me figure out how to make it turn blue when the wireless is activated.  it really bugs me.

---

### Post by Mr A Mouse on 2008-05-12
Are you getting a wireless connection with an orange light, or is wireless down. (I couldn't get wireless to work at all on my dv6000.)

---

### Post by mikykim070 on 2008-05-12
i am sorry to have provided so little information.  in short though, everything works except the light.  i have full connection.  it's just annoying because i got used to the nice blue lights that match the whole rest of my laptop and i think the big ugly orange... idk :)
i just want to know if there's a cure.

---

### Post by Mr A Mouse on 2008-05-12
> **mikykim070 said:**
> i am sorry to have provided so little information.  in short though, everything works except the light.  i have full connection.  it's just annoying because i got used to the nice blue lights that match the whole rest of my laptop and i think the big ugly orange... idk :)
i just want to know if there's a cure.

OK. Sorry for the confusion on my part. :D That also means I don't have an answer, I fear--I had to go back to Vista for this machine so I could use it at work, but I'll be watching the thread in case I get a chance to go dual-boot later.

---

### Post by Ayuthia on 2008-05-13
Can you post your lspci -nn?  I am guessing that you have an Intel card.  If that is the case, you might just need to install linux-backports-modules-hardy.

---

### Post by mikykim070 on 2008-05-13
well... im not sure exactly what you're talking about right now.  im a really dumby for computers.  how do i find out what my lscpi nn is?

---

### Post by Mr A Mouse on 2008-05-13
- get a terminal (CTRL+ALT+T)
- type 'sudo lscpi -vv >/home/user/my_lspci'
- close the terminal, go to Work tab, click on File Manager and Open /home/user/my_lscpi in the editor, find '01:00.0 Ethernet controller'
- copy  that block of text and copy it into your forum reply.

Sorry--we occasionally forget that we were on a learning curve once, too. :D

---

### Post by Ayuthia on 2008-05-13
> **Mr A Mouse said:**
> - get a terminal (CTRL+ALT+T)
- type 'sudo lscpi -vv >/home/user/my_lspci'
- close the terminal, go to Work tab, click on File Manager and Open /home/user/my_lscpi in the editor, find '01:00.0 Ethernet controller'
- copy  that block of text and copy it into your forum reply.

Sorry--we occasionally forget that we were on a learning curve once, too. :D
Yes, I was going too quickly when I replied.  Sorry about that.

Like, Mr A Mouse said, you need to go to a terminal.  However I am going to make a correction on his post.  It should be lspci instead of lscpi.  You should be looking for something that is either a Network Controller or Ethernet Controller.

---

### Post by Mr A Mouse on 2008-05-13
> **Ayuthia said:**
> However I am going to make a correction on his post.  It should be lspci instead of lscpi.

#-o Thank you, Ayuthia, for your gentle correction. :)

---

### Post by mikykim070 on 2008-05-14
i did that sudo thing in the terminal and it said 'no such file or directory'.  what's works tab?

---

### Post by Aaronb2245 on 2008-05-14
> **mikykim070 said:**
> i am sorry to have provided so little information.  in short though, everything works except the light.  i have full connection.  it's just annoying because i got used to the nice blue lights that match the whole rest of my laptop and i think the big ugly orange... idk :)
i just want to know if there's a cure.

Call Hp I was recently told that if the wireless light goes orange among other things this version may be having mother board problems. This is a common issue (mother board problems) on this version and they will fix out of warranty. GL

---

### Post by mikykim070 on 2008-05-15
even if it's on a different operating system?  im pretty sure but ill double check... i think the light works on vista, just not on ubuntu since the update.

---

### Post by Mr A Mouse on 2008-05-18
Bump.

I can't speak for mikykim, but on my system the wireless light is orange on Hardy and blue on Vista.

---

### Post by mikykim070 on 2008-05-28
ok.  i booted vista and the blue light worked perfectly fine.  it's just ubuntu.  i don't think it's a hardware problem.  on ubuntu, it was working until i updated my system to 8.04.  i still need help.
o, one more thing
my wired connection stopped working.  i tried resetting the connections and stuff.  i had my dad try and help and he's a software engineer.  we couldn't get wired connection to work at all.
i hope that if wired connection works, then the light will work.... i hope.

---

### Post by mariodavidpalacio on 2008-06-02
Mine is a dv2500 t and I had the same problem. Now it's always orange, although I can perfectly connect to the wireless network I have at home. I haven't tried the wired connection but I will have to. That would be a major issue.

Nice to see someone with the same problem and the same concerning about something that is not that important. :D

Best regards

---

### Post by deinonychai on 2008-06-29
Hello folks:

Same problem w/ my HP laptop: dv6000, Atheros WIFI adapter running on 8.04 64-bit, using ndiswrapper (wireless wouldn't work without it).  Results from my lspci check are as follows:

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr+ Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 4 bytes
	Interrupt: pin A routed to IRQ 19
	Region 0: Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
		Address: 00000000  Data: 0000
	Capabilities: [60] Express Legacy Endpoint IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <512ns, L1 <64us
		Device: AtnBtn- AtnInd- PwrInd-
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
		Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
		Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 0
		Link: Latency L0s <512ns, L1 <64us
		Link: ASPM Disabled RCB 128 bytes CommClk+ ExtSynch-
		Link: Speed 2.5Gb/s, Width x1
	Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
		Vector table: BAR=0 offset=00000000
		PBA: BAR=0 offset=00000000

It should also be noted that the wireless switch *works*.  That is to say, when I toggle it off, the wireless cuts out (unlike a few of the other features on my HP laptop, which just don't do a damn thing when I press them... hidden HP remote a notable inclusion...); it's just that the wireless light won't turn blue.

The laptop came installed with Vista.  For the few hours I spent downloading an 8.04 live CD and burning it, the blue light worked for me.  As soon as I was done installing 8.04, it gave up its ghost.

Maybe some of that info will help.  If not, let me know and I'll check into things further.

Thanks

---

### Post by nadeepa on 2008-08-29
Same problem here. Wireless is working fine (after a lengthy search and installing the driver). But light is not turning into blue. Any suggestion?

Thanks

Nadeepa

---

### Post by lowell216 on 2008-08-31
Hi, I don't want to hijack your thread, but how did you get your wireless connection working? ndiswrapper workaround or did you find a better fix? thanks!

---

### Post by deinonychai on 2008-09-03
> **lowell216 said:**
> Hi, I don't want to hijack your thread, but how did you get your wireless connection working? ndiswrapper workaround or did you find a better fix? thanks!

It was an ndiswrapper workaround, yup.  I followed these instructions:

[http://region19.blogspot.com/2008/06/64-bit-wireless-atheros-using-ubuntu.html](http://region19.blogspot.com/2008/06/64-bit-wireless-atheros-using-ubuntu.html)

There were a few solutions posted about, but this is the only one that's worked consistently for me thus far.  Occasionally, I need to sudo ifconfig wlan0 hw ether my card's MAC upon startup (especially for encrypted networks), but that's about it.  Works perfectly otherwise.

Having tried a few solutions, this is the only one that worked for me... running 64-bit Ubuntu w/ Atheros drivers.

---

### Post by maybememe on 2008-12-27
these series of notebooks have a defective gpu/nvidia chip set which over heats and the wireless goes first, then the display. The wireless runs over the gpu I think.

Check hplies.com for uncensored posts, and hps own forums for 1000's of people posting the same issue on windows and linux, no dif as it is a hardware issue.

---

### Post by reltx on 2009-04-16
sudo ifconfig wlan0 up/down (for on and off)

---

