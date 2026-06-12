---
title: "Wireless works every other boot"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by ScottinSoCal on 2008-08-02
I just installed Ubuntu - first time user. Novice with Linux, although I have Fedora 9 installed on my home office desktop.

Dell D810 laptop (2.4GHz processor, 80 GB HD, 2 GB RAM)
Intel 2915ABG wireless
Stock install of Ubuntu 8.04 (Hardy Heron)
Dual boot with WinXP Pro
Linksys WRT54G with Sveasoft firmware update
WPA AES encryption enabled

Last night I installed it and the wireless wouldn't connect at all. I deleted the partition this morning and tried again. This morning when I clicked on the Network task bar icon I had the choice of enabling the wireless network - an option I didn't have last night. Excellent, I configured it and it hooked right up. The notebook updated itself (91 updates) and instructed me to restart. No connection, and my option for wireless had changed and was greyed out so I couldn't select it. I rebooted to WinXP to test the connection and linked right up. Found this forum and got some instructions, rebooted back to Ubuntu. Option for wireless still greyed out, but before I made any changes I changed to the 'Home' location. It hooked right up and I've got Internet again.

I've experimented a little bit and this is what I've found:

If I shut down Ubuntu and boot back into Ubuntu, I have no connection. The NIC works, I can see the SSIDs of the networks around me, but I can't connect.

If I shut down Ubuntu, boot into WinXP, then shut down and boot into Ubuntu, I get a connection. So far this has been 100% repeatable.

Might be related, but I'm guessing not - the console light showing my wireless NIC is enabled is off in Ubuntu, whether I have a working connection or not. It works in WinXP.

It's like the Ubuntu shutdown is leaving the NIC in a state where it can't connect. An initialization of WinXP resets it and it works again on the next Ubuntu startup.

Any ideas or suggestions? Because I'm a novice with Linux, I'd prefer to stick with Network Manager if there's a way to get it to work reliably. If not, I'm open to command line fiddling, it just wouldn't be my first choice. I have nothing against command lines, but I like to know what I'm doing when I'm in there.

---

### Post by ScottinSoCal on 2008-08-02
Things move fast here, but bumping seems to be acceptable.

---

### Post by monsag on 2008-08-02
Hello there.

I  had a similar problem before; dual booting my laptop on XP and Hardy, with XP connecting through wireless 100% of the time, and Hardy 100% of the time **AFTER** I use the Manual Configuration **every reboot**, 100% of the time :-)

Then I found a posting to give Wicd a try. It replaced the Network Manager that came with Ubuntu 8.04 installation, and I now I don't have that wireless-pain in the neck problem anymore. And I am **not** dual-booting anymore too :-)

[http://wicd.net/download.php](http://wicd.net/download.php)

The above download link worked for me, I hope it will do the same for you, and for everyone else who have to go through the hassle I went through before I found this solution.

Mon Sagullo

---

