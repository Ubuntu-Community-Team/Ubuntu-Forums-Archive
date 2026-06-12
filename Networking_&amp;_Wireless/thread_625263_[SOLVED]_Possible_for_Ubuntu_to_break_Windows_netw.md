---
title: "[SOLVED] Possible for Ubuntu to break Windows networking?"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by burgerearl on 2007-11-27
I've been trying to get a Windows/Ubuntu dual boot set up (my video issues here: [http://ubuntuforums.org/showthread.php?t=623421](http://ubuntuforums.org/showthread.php?t=623421))

The other day I had network connectivity in Windows (posted on ubuntuforums), in Ubuntu (successfully ran a wget command, I think), and shortly thereafter had no network connectivity at all in Windows.

I'm on a school network with lots of restrictions and have by no means ruled out the myriad of possibilities involving my network or Windows settings.

That said, IIRC, the _only_ thing I did involving the my ethernet connection in between using the internet in windows (to post here) and then booting back into windows to have no network connection was running that wget command.

So my question is: is it "possible" for my Ubunutu installation to affect network connectivity for a Windows installation on a different partition? My only guess would be somehow affecting my motherboard.

Any thoughts?

---

### Post by foolsh on 2007-11-27
It could be two diferent dhcp addresses given to to your mac address one for windows and one for linux try setting your ip address and gateway info exactly the same for both OSes.

---

### Post by burgerearl on 2007-11-27
Hmm, I'm too green to follow all of that. "ipconfig /all" in windows doesn't give me _any_ info in Windows (not even a MAC address). I can see my MAC address with "ifconfig" in Ubuntu.

As for my IP/gateway info, neither OS will give me values for any type of IP or gateway info right now.

Also, I maybe should have clarified that I'm not getting connectivity in Ubuntu either.

---

### Post by burgerearl on 2007-11-28
Turned out to be a corrupted driver (windows/system32/drivers/tcpip.sys was missing). 

I think the only way my Ubuntu installation had any affect was me hard rebooting my computer a few times; I probably corrupted some files.

Solved. Thanks!

---

