---
title: "[SOLVED] Networked Printer IP Address Problem"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by bilijoe on 2008-07-18
I have an HP 3210xi (I don't think make/model is relevant here), network-ready printer, which has been connected to my network (3 Ubuntu machines, one Window$, and a cable modem), and working fine (using HPLP for the Linux machines) for about a year.:)  Recently, ALL the computers lost their ability to print.:(  Reinstalling the driver on the Window$ machine (I did it first because my son  needed it for schoolwork) allowed that machine to print again, but it would not receive "out of paper" notices, and could not check things like ink levels, from the computer.  I reasoned (not always a good move for me) that the 2-way link between printer and computer was working only one way.  

On the Linux machines, nothing I tried worked.  The HPLP Toolbox said "No Compatible Devices Detected", but showed an Icon, labeled for the 3210, with a small red "x" on it.  When I tried to print from any of the Linux machines, everything appeared normal; all the preparation, and the sending of the print job to the print spooler went as expected, but the job just sat in the queue--forever--and never printed.  I then reasoned (again, often a mistake) that, when Linux sent a print request to the printer, it waited for some kind of "message received" acknowledgment from the printer, whereas the programmer of the Window$ print routine was just too lazy to include that step.  So i concluded (even more risky than reasoning) that the printer hardware had encountered a failure, and had become incapable of 2-way communication (though its self diagnostic routine showed it to be in full duplex mode).  

Being (amongst too many other things) an ex electronics repair tech, I disassembled the Chinese puzzle that HP printers seem to be, and checked the board with the networking circuitry on it.  Found some solder connections I didn't like the look of, and re-soldered about half the board.  With my confidence high, I reassembled, and reconnected the printer, only to have it perform exactly as it had before I did all that work.  Rats! ](*,) 

So I started saving and shopping for another printer.  The 3210 is no longer available, and I couldn't find anything else I liked as much.  Again, rats!  Then last night, while playing around with CD labeling software (I just got a new LightScribe drive), one of them popped up a list of available destinations for the print image, and it showed (along with the LightScribe drive) the 3210, with accompanying summary information.  For some reason, the IP address caught my eye--192.168.1.102.  Wait a minute (I thought to myself), in all the diagnostic stuff I'd had the printer give me, I thought I'd seen .....101. :-k 

I checked System->Administration->Printer, and, sure enough, in the Device URL field was .....102.  So I went to the room the printer is in, and asked it for its network configuration information and, as I had remembered, it showed .....101.  BINGO!  Back to the printer configuration utility, changed the address to .....101, and lo and behold, IT WORKED!  Perfectly!=D>  Did the same to the other two Ubuntu boxes and, by golly, they worked too!  Whew!  I don't have to buy a new printer (yay!).  (I still don't know why bidirectional communication isn't working on the Window$ box, and I don't really give a hoot.  It's only Window$, after all.;-))  

So, after all this unnecessarily lengthy, rambling setup, if anyone is still reading, my question is this; WHAT HAPPENED?  Everything had been working fine for almost a year, so I assume (there I go again) that the network addresses on all the Linux boxes had matched the actual address of the printer, all that time.  And, since all of the computers lost their printer connection at the same time, methinks it must have been the printer's address that changed.  Is that a good assumption?  And, what could have caused it?  And, how can I (or, can I) prevent it from happening in the future? :-s 

The printer and all the computers are connected to a Linksys WRT45G, and there is a cable modem connected to its "Internet" port.  Two of the computers (incl. the Window$ box) are wireless, the printer, and the other two computers are wired connections.  

Since I have it working again, and I know what to look for if something similar happens in the future, I can live without knowing the cause.  But, I am very curious, and always looking to learn more.  So anyone who cane give me their take on what could have caused this condition to occur, I'd much appreciate hearing from you.O:)

---

### Post by bab1 on 2008-07-19
Bill,

I just love long winded guys.  I'm one also.  The short answer is:  the TCP/IP stack got corrupted.  This is a common occurrence on Windows machines.  Most of the time a reboot takes care of the problem.  Yes, I know it is a HP printer.  The truth of the mater is any TCP?IP stack is vulnerable.  Some implementations are more stable than others but none are a physical entity anyway.

What's an TCP/IP stack, you may ask.  Well, you can think of it as a layer cake.  See: [[COLOR="Magenta"]Here[/COLOR]]("http://www.cellsoft.de/telecom/tcpiposi.htm")

We need this stack to interface the physical card with the virtual IP address and thus be able to send packets of information back and forth.  The address is held in memory in the chip on the card.  I wonder if there is a battery on the card or is it CMOS, Like a BIOS chip.  Either way it is an electronic value and that is what went pfffffttt!  :D

---

