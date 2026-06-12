---
title: "Please clarify NetWork Question"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by ALinuxLover on 2011-08-24
Hi Everyone...

I am looking for an answer to a "Networking" question, and am not very computer literate. I choose this forum because I have had problems with Viruses and due to the urging of some friends am getting ready to install LINUX and UBUNTU.

That said now to my question.

I have three computers (desktop).  Two of them are connected to the internet and the third one is not and **_will no_t** be connected to the internet.  I have one printer and need it for all three computers.  I have read that I can get a "Switchbox" to allow access to the printer from all three computers and was thinking about getting one when a friend suggested that I Network my computers.  

Is it possible to have only the Printer Networked? 

...and if is networked to all three computers is it be possible that the "not-online" computer could be infected with a virus? 

It is very important to me that my "not-online" computer remain free of any viruses, spyware, malicious ware, hacking etc.  in other words *_I don't want it accessed by the internet in any way shape or form.  _*

My question also applies to having one Monitor, Keyboard and Mouse "Networked", with the same ~safety-for my "not-online"~ computer.

Hope someone can help...

A-L-L

---

### Post by androssofer on 2011-08-24
> **ALinuxLover said:**
> Hi Everyone...

I am looking for an answer to a "Networking" question, and am not very computer literate. I choose this forum because I have had problems with Viruses and due to the urging of some friends am getting ready to install LINUX and UBUNTU.

That said now to my question.

I have three computers (desktop).  Two of them are connected to the internet and the third one is not and **_will no_t** be connected to the internet.  I have one printer and need it for all three computers.  I have read that I can get a "Switchbox" to allow access to the printer from all three computers and was thinking about getting one when a friend suggested that I Network my computers.  

Is it possible to have only the Printer Networked? 

...and if is networked to all three computers is it be possible that the "not-online" computer could be infected with a virus? 

It is very important to me that my "not-online" computer remain free of any viruses, spyware, malicious ware, hacking etc.  in other words *_I don't want it accessed by the internet in any way shape or form.  _*

My question also applies to having one Monitor, Keyboard and Mouse "Networked", with the same ~safety-for my "not-online"~ computer.

Hope someone can help...

A-L-L

em.... seems quite a funky set up u want. and can be done, but not sure about how easy it wud be to do... 

which computers will have ubuntu on them?

if ur non internet 1 has ubuntu, then it will be free of viruses and malware etc (ther are a windows thing, linux doesnt have them) anyway. 

then you could connect the printer into the non-internet computer, set up a printing server on it. get a router and link all the computers to it(non internet included). then restrict all access in and out of the non-internet comp with its firewall, and only allow access to the printer server thts on it. then u'd have pritty air tight security :-)

---

### Post by 3rdalbum on 2011-08-24
The above poster gave a good option that's probably the most correct solution. More appropriate for your needs than what I was going to suggest, which was to set up the third computer to use a static internal IP (rather than it automatically grabbing one from your router), and then just not tell it the modem's IP address, so it can't get on the internet. However this method still allows the other two computers to talk to Computer Three.

If you're in the market for a new printer, you could have a look at the wireless printers, specifically the HP ones. Don't quote me on this, but I think you can have the printer plugged into Computer Three via USB, and have the printer accessible via its own wireless to the network which consists of Computers One and Two. Therefore, Computer Three is not on the network, but it still can use the printer.

I'm not sure 100% if these printers can work wired AND wireless simultaneously, but it should be fairly easy to switch the printer's mode if you needed to do that. At least as easy as using some kind of switcher box, which itself might not be possible.

---

### Post by The Cog on 2011-08-24
I disagree. If whatever that protected computer is doing is important enough to mandate that it must not be connected to the internet, then it should not be connected to the internet even indirectly via other computers. Connecting to the internet via a router/firewall is still connecting to the internet, however much you try to claim that black is white.

For the printer, you can probably find an A/B switch that will switch it between computers. For the keyboard/mouse/screen, look for somethign called a KVM (for Keyboard, Video, Mouse) switch, which is a switch that you connect one keyboard, one VGA screen and one mouse to, and also has two (or more) sets of keyboard/video/mouse connectors to connect to different computers. I quickly found this one on Amazon - not as a recommendation, just an example with pictures: [http://www.amazon.co.uk/D-Link-DKVM-2K-Port-Network-Switches/dp/B00011PC8I/ref=sr_1_6?ie=UTF8&qid=1314213517&sr=8-6](http://www.amazon.co.uk/D-Link-DKVM-2K-Port-Network-Switches/dp/B00011PC8I/ref=sr_1_6?ie=UTF8&qid=1314213517&sr=8-6)

P.S.
If you boot Ubuntu while the screen is connected to the other cmoputer, it will fail to detect the screen capabilities (no surprise), and fall back to a safe very low resolutin like 800x600. So always switch to watch a PC as it boots. There is no problem "disconnecting" the screen after the PC has booted.

---

### Post by ALinuxLover on 2011-08-28
Thanks to everyone for your helpful advice.  I have decided to go with the switchbox, as it seems the safest way to go!  ...and I don't think I could manage to do the other 'stuff'.

---

