---
title: "Wireless WEP D-Link DWL650 working with Ubuntu 6.10"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by Terry851 on 2007-03-31
As a new user to Ubuntu 6.10 (2 days), I thought I'd share my success with wireless networking in hopes that it will help others also struggling with this issue.

Hardware: IBM ThinkPad 600X laptop
D-Link DWL650 wireless pcmcia adapter
LinkSys wireless router setup with 128bit WEP, MAC access control, Shared access, no ESSID broadcasting

Initial Experience:
- Installed PCLinuxOS, Knoppix, Ubuntu, PuppyLinux, Kubuntu; all installed fine, but I could not get the wireless working.  Symptoms: Networking could see eth1, but the light on the D-Link DWL650 would blink, indicating a lack of connection to the wireless access point.  I tried all variations of suggestions (ESSID in uppercase, static ip, dhcp, passphrase in ASCII, passphrase in HEX, etc.)  As the community appeared more robust for Ubuntu than the other distributions, I decided to stick with Ubuntu until I could figure out my wireless issue.
- Reinstalled Ubuntu, and connected via a wired connection (ethernet pcmcia adapter) and applied all updates and installed FireStarter.  Wasted a bit of time playing with GAIN, installing Java and Wine, and playing Mahjongg...
- Decided to test my wireless with another wireless router I had to narrow the issue to a potential hardware problem, or a WEP problem.  With no WEP, my wireless card established a good connection (solid light on the DWL650) with the access point.  Removed the ethernet adapter and rebooted.
- I'll spare you from the 'permutations and combinations' that I tried next, but here's the sequence that worked for me:

note: DWL650 light is blinking at this time
1) System, Administration, Networking: enabled the eth1 connection and specified ESSID (in the Same Mixed Case I used when setting up the wireless router!) and specified DHCP)
2) Applications, Accessories, Terminal:
sudo iwconfig eth1 essid [enter your ESSID here]
sudo iwconfig eth1 key restricted [enter your passphase here]

DWL650 light is solid, but the icon in the taskbar indicates eth1 is disconnected, and I'm not able to access any website or IP address.  [the 'restricted' prefix for the passphrase was needed to enable the connection to my wireless router which was setup for SHARED access vs Open]

3) Applications, Accessories, Terminal: sudo gedit /etc/modprobe.d/blacklist
added to bottom of file:
# disable ipv6; required for DWL650 wireless; 3/31/07 (just my comments)
blacklist ipv6
saved the file and rebooted.

Success! I'm now entering this via wireless access from Ubuntu 6.10 from a ThinkPad 600X!

Hope this helps others!

Thanks to numerous people for responding to others' requests for help on this issue - it was a puzzle putting it together for my particular situation, but it was well worth the time!

Now, off to figure out why my DVD does not play; probably have to load some codecs from somewhere...

---

