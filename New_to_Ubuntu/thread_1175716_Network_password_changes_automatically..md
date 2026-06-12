---
title: "Network password changes automatically."
date: 2009-06-01
forum: New to Ubuntu
---

### Post by Papa-san on 2009-06-01
I use the 'Network Manager' tool for my wireless configuration, and I am currently connected wirelessly, so I know it isn't an issue with drivers or hardware. (Skip the blue text to get right to the tech stuff...)
[COLOR="Blue"]I had my wife willing to eliminate the windows partition of this laptop as long as Ubuntu would work correctly for her. She used it exclusively and was quite happy for several months. That was when it was plugged in and ran continuously for that time.
Once she was no longer able to keep it on all the time, the wireless issue we have here became intolerable in short order, and she switched back to the Vista side. I have managed to convince her to leave Ubuntu installed for a while until I can get this issue corrected, so PLEASE, let's find a solution to this! [/COLOR]
Here goes:
Whenever I boot up into Ubuntu, and occasionally at random times while running it, my wireless doesn't function. I go to 'Network Settings' and invariably find the same problem: My Network password has changed. I have included 2 screenshots that will hopefully give some details.
The first one (Network1.png)is what comes up automatically. The dots in the password box go on for a while past what you can see. There are 64 characters in it. The whole string is shown at the bottom of 'Network2.png', where I have the actual password and the 'default' password compared to each  other.
As you can see, they are quite different. 
What I need is a way to have the proper password saved so that it will allow my wireless to work automatically upon boot-up.
Any assistance would be greatly appreciated!
Thanks!

---

### Post by Hospadar on 2009-06-01
I don't think your passwords are changing per say.
Network Manager always puts a million dots into the text box so as to not give a potential attacker a clue as to the length of the password. (i.e. the number of dots printed when you open the window is not reflectant of the actual password length)

I have a couple questions:
1) If you retype the password, does the connection start working?
2) Do you always have to type the password when you start the machine up (does it connect by itself sometimes?)
3) If not 2, what happens if you restart the machine after the connection has failed, will the password start working again?

Also, when the connection is working, and not working, could you run "ifconfig" in a terminal (for each condition) and post the output here?

Is there anything you can do to make your network connection start working after it has stopped?

---

### Post by Papa-san on 2009-06-01
Thanks,
1 - If I clear the password box and type in the password, the connection works.
2 - I don't have a splash screen where I have to enter my password, if that is what you mean. The system is in a secure place, so it is set to just boot right through automatically. In regards to the wireless, it is supposed to be up and running when the system finishes booting, and optimally, I should not have to enter any passwords. However, it always finishes booting and the icon in the tray says "Not connected" in the balloon when I mouse over it. In answer to your question, it never connects by itself.
3 - It's rare for the wireless connection to fail once I have it running, but it does happen. Usually, all I have to do is open 'Network settings' and clear the long string and enter the correct pw for it to function again. Once or twice, this hasn't worked, so I have had to re-boot. When I do this, it is the same as usual: No connection until I clear and enter the pw.

I'll do the 'ifconfig' things once I get out of the live session it's currently running in.

To make my network connection start working after it has stopped, I usually just need to do the password dance to make it work right again.

---

### Post by Papa-san on 2009-06-01
Upon re-boot, it was not connected, as usual. Here is the output of 'ifconfig' at that time:
```
john@john-1525n:~$ sudo ifconfig
[sudo] password for john: 
eth0      Link encap:Ethernet  HWaddr 00:1d:09:41:fd:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1c:bf:c9:92:1d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126352 (123.3 KB)  TX bytes:126352 (123.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-C9-92-1D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

john@john-1525n:~$
```
Then I did the password dance, and now this is 'ifconfig':```
john@john-1525n:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:41:fd:39  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:1c:bf:c9:92:1d  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fec9:921d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:510960 (498.9 KB)  TX bytes:54042 (52.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2996 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2996 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:126352 (123.3 KB)  TX bytes:126352 (123.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-C9-92-1D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

john@john-1525n:~$ 

```Hopefully this will give some clue as to what is happening here.

---

### Post by neo.patrix on 2009-06-01
Are you using Keyring? It might be possible that during some configuration changes that you have done, wrong password has been saved in keyring...

Hence, every-time password is fetched automatically from keyring during system-startup wrong password turns up. Also, after short disconnection when it tries to reconnect once again wrong password turns up.

---

### Post by freak42 on 2009-06-01
you might also look into replacing network manager with wicd .. it works better for some people..

hth

---

### Post by Papa-san on 2009-06-01
I don't believe I have used keyring unless it is something that is used as a default. 

I tried wicd, and it doesn't work at all. I cannot even get it to connect in the first place.

---

### Post by neo.patrix on 2009-06-01
Actually, when I had re-installed Ubuntu (just 2 months back) on my machine, network-manager automatically detected WiFi. When I had to input my WiFi key for first-time, it had asked me to save it to Key-Ring. After that I never had to type it again. 


You can check if your WiFi password is stored in Key-Ring by 

Applications > Accessories > Password & Encryption Keys. On tab  "Passwords" is there any entry like "Network secret for Auto <your-essid>"? 

One of the possible scenario I could imagine that sometime after you had installed Ubuntu, maybe your WiFi password had been changed, but Key-Ring has not been notified about the change, so it tries to use old WiFi-password.

---

### Post by Papa-san on 2009-06-01
I'll give that a try once I get it back from my wife. She has it running Vista right now, so I need to wait for her to get done. I'll post the results

EDIT: Nope, nothing at all in keyring...

---

