---
title: "I got ubuntu, Please help!!!!!"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by televisible on 2009-03-16
I have installed installed ubuntu 8.1 on my computer
I encountered a lots of problems,
I swear to heaven that google never have been my best friend until the installation of Ubuntu.
(No wonder google support the open source movement so much since people with open source os and program must have boost up the hits of google search.)

Anyway ,after my ugly affair with the world famous web pimp, Mr. google,
some of the problems are fixed and thanks to the all mighty creator of Lazybuntu pack from Taiwan, now my ubuntu can read and write Chinese.

However, the major problems that every new Linux users must encountered, the hardware module installation, Yes, the ultimate killer of Linux. It had been slaughtering numerous Linux newbies. Force them back to the all evil MS® camp. It's nasty trick , Fatal error , module not found on dir/ ... really hurt the newbies ***. And I shared this pain. So I turn to my google again.

Googling and googling still I cannot find what I was looking for.

If you are kind enough, please show me the way to find a solution to fixed my hardware problem. A good tutorial web page of installing hardware module, for TV card, sound card.
or good guide about ubuntu installation. Or you are a Linux hardware Guru who happens to be a kind person who are happy to help. Please kindly instruction what to do.

My hardware and its status are list below :
                                                                                                         
Motherboard:
Asus P5LD2 se with intel chips 945P    * it seems to be working, however get
capability <access denied> remarks

Soundcard on pci:

creative sound blaster audigy value  24.bit advanced HD with chips SB0570 *problem after restart, its volume will be set to maximum.

here is the  "lspci -vvv -nn -xxxx output-" of the sound card

01:01.0 Multimedia audio controller [0401]: Creative Labs SB Audigy LS [1102:0007]
    Subsystem: Creative Labs Device [1102:100a]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (500ns min, 5000ns max)
    Interrupt: pin A routed to IRQ 21
    Region 0: I/O ports at b800
    Capabilities: <access denied>
    Kernel driver in use: CA0106
    Kernel modules: snd-ca0106

VGA dispay card :
Asus Nvidia en7600 GS silent *seems working
04:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7600 GS] [10de:0392] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8231]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at df000000 (32-bit, non-prefetchable) [size=16M]
    Region 1: Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Region 3: Memory at de000000 (64-bit, non-prefetchable) [size=16M]
    Region 5: I/O ports at e800
    [virtual] Expansion ROM at ddfe0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nvidia


I have two TV cards on my computer one is anolog and the other is digital


Analog TV card  on PCI :
shooting V-gear with chip Conexant 10bit * no tuner installed, modprobe get fatal Error
01:00.0 Multimedia video controller [0400]: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (5000ns min, 13750ns max), Cache Line Size: 16 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
    Capabilities: <access denied>
    Kernel driver in use: cx8800
    Kernel modules: cx8800



Digital TV card on PCI-e :
Avermedia averTV Super DMB750, its chips unknown to me.
*Problem modprobe fatal error
I write an email to avermedia, to asked for a linux module, however they are being an *** and point me to the website with vista and xp driver download page  and the worst part is, its xp driver still cannot use hardware decoding with xp even they cliam it can :O Huge mistake to buy such an expensive pci-e card. You should avoid it too.

03:00.0 Multimedia controller [0480]: Philips Semiconductors Device [1131:7160] (rev 03)
    Subsystem: Avermedia Technologies Inc Device [1461:0351]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 16 bytes
    Interrupt: pin A routed to IRQ 11
    Region 0: Memory at dde00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>


I guess this post is getting too long so thank you very much for reading this
I hope I would get a replay for I have tried my best to write this.
Once again thankyou for your time.

---

### Post by kuja on 2009-03-17
I'm thinking I don't have the answer to your question, but without the exact error message I think it'll be difficult for anybody to answer, care to post the exact error message(s) you're getting?

---

### Post by Dynaflow on 2009-03-17
I assume this is one of the higher-end Asus models ... but which one?  Amidst all the information, I can't seem to find a model number.

---

### Post by Sealbhach on 2009-03-17
> **televisible said:**
> 

If you are kind enough, please show me the way to find a solution to fixed my hardware problem.


OK, but what is the problem? What is not working?


.

---

### Post by Temposs on 2009-03-17
> **Sealbhach said:**
> OK, but what is the problem? What is not working?


.

From what I can tell, it's this:

> A good tutorial web page of installing hardware module, for TV card, sound card.

---

### Post by Dynaflow on 2009-03-17
This is what I'm seeing.  Apparent problems are in bold.

> **televisible said:**
> ...
Motherboard:
Asus P5LD2 se with intel chips 945P    * [b]it seems to be working, however get
capability <access denied> remarks[/b]
...

Soundcard on pci:
creative sound blaster audigy value  24.bit advanced HD with chips SB0570 ***problem after restart, its volume will be set to maximum.**
...

shooting V-gear with chip Conexant 10bit * **no tuner installed, modprobe get fatal Error**
...

Digital TV card on PCI-e :
Avermedia averTV Super DMB750, its chips unknown to me.
*[b]Problem modprobe fatal error
I write an email to avermedia, to asked for a linux module, however they are being an *** and point me to the website with vista and xp driver[/b]...

...**this post is getting too long**... 

---

