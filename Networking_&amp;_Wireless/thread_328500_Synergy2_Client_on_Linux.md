---
title: "Synergy2 Client on Linux"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by mevets on 2006-12-30
I have been trying to network my laptop running ubuntu and a windows machine so that they can share one mouse and keyboard. I have been trying to use Synergy2 ([www.synergy2.sourceforge.net](www.synergy2.sourceforge.net)). This may be  a question for someone a synergy expert but I think it really comes down to simple networking.

I setup and started my Windows server successfully. When I installed the client on Linux I got it through Ubuntu's Synaptic Package Manager and it succeeded in installing. I went into the terminal and typed 'synergy -f 192.168.1.101' which is the right address of the win server. It responded with this: 
 
INFO: synergyc.cpp,716: Synergy client 1.3.1 on Linux 2.6.17-10-386 #2 Tue Dec 5 22:26:18 UTC 2006 i686 
DEBUG: CXWindowsScreen.cpp,840: XOpenDisplay(":0.0") 
DEBUG: CXWindowsScreenSaver.cpp,339: xscreensaver window: 0x00000000 
DEBUG: CXWindowsScreen.cpp,110: screen shape: 0,0 1280x800  
DEBUG: CXWindowsScreen.cpp,111: window is 0x05a00004 
DEBUG: CScreen.cpp,38: opened display 
NOTE: synergyc.cpp,330: started client 
WARNING: synergyc.cpp,265: failed to connect to server: Timed out 
DEBUG: synergyc.cpp,237: retry in 1 seconds 
 
The only problem I can think of is port forwarding. I forwarded 24800, which is the port it wants,  to the server and still did not get any success. Am I on the right track?

---

