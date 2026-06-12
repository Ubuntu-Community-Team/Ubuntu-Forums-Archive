---
title: "Networking with Belkin wireless g router"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by rapattack1 on 2008-09-12
Hi I have managed to get this device to share the internet connection(broadband) but how do I access the other computers on the network? I have never done this side of computing and am still pretty much new to Linux. I did notice that there under places>computer>network servers and I clicked onto windows network but do not understand what to do next. Am I on the right path?
Also there is the wireless component of the router and I want get my notebook to talk to it via the wifi pcmcia card I have but so far it is not happening. It was a difficult process even with the wired connection as the isp I have is weird. Nothing is automatic. I have to manually configure all the dns blah blah settings otherwise nothing. I have done this on quite a few machines so I know what i am talking about and had two friends come over when I was at the beginning of my linux time. Just to get connected ordinarily without the network this is the case. I use the notebook at wifi hotspots so I know it is working btw.

---

### Post by superprash2003 on 2008-09-12
to access files on other machines go to places->Computer and under location type smb://x.x.x.x where x.x.x.x is the ip of the other machine.
    To see if ubuntu automatically recognized your card type iwconfig in your terminal and post output here

---

### Post by rapattack1 on 2008-09-15
Hi I am not sure where location is. Is it search? Is what your saying just to access whichever machine but does this also enable me to use the internet via the notebook? 

carolyn@carolyn-laptop:~$ iwconfig 
lo        no wireless extensions. 

wifi0     no wireless extensions. 

ath0      IEEE 802.11g  ESSID:"belkin54g"  Nickname:"" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Maude on 2008-09-15
I just set up a Belkin wireless G adapter in Hardy.
It is only on one CPU now.
For Windows networking, use Synaptic and install SAMBA. This is windows protocal.
I had to read SAMBA tutorials to get the windows setup. 
Use the same DNS name in Ubuntu and Windows machines.
Windows network has to be set up on Ubuntu and Windows. I got the Ubuntu to see windows machines and the windows machines to see Ubuntu.
I hope this helps. I got confused with hetworking machines.
I have gotten airport MACs to go through Ubuntu as a server to network to a printer.
I figure if I want to feel stupid, I try netqorking.
The wifi on the notebook, the driver has to be installed. I used ndiswrapper (install with synaptic) to install windows drivers. You have to find the driver and it installs.
I then went to the network icon on the taskbar and clicked which wireless to use.
I hope I haven't confused you. I tend to do that.
I manage 15 machines, 14 through router, 1 through wireless. 3 MACs, 9 windows, 2 Ubuntu, 1 Xubuntu. This is my excuse for being confused.
Good luck. Ubuntu is easier to figure out than windows.

---

### Post by rapattack1 on 2008-09-15
Um I am not networking with my windows machine. 
I am not sure what you mean about the wireless thing. I am confused now.:lolflag:
You are networking a lot of machines. I hope I can learn something from you as this is my first time in this world. I am getting the machines to share the internet connection but just not what is one the hard drives. I just don't know that much about networking. I have never even used a network. Maybe at an internet cafe but you don't access other machines in those places when your just a user of the cafe.

---

### Post by rapattack1 on 2008-10-04
I still can't get the wifi notebook talking to the Belkin network. Anyone out there can help?:(

---

