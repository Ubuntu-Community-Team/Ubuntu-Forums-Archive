---
title: "Weird NetworkManager behavior for broadband network in 16.04"
date: 2016-11-08
forum: Networking &amp; Wireless
---

### Post by pi.no on 2016-11-08
Hi.

I am using a mobile network usb stick (HSPA+ USB Modem 1bbb:022c) since some days. I hoped that support for such hardware is mature enough today, so I blindly just bought an arbitrary one. I think the hardware itself works. I can connect to the Internet and use it. Actually I currently use it for that posting. But, NetworkManager does all kinds of strange things on the way:

- It always asks me for a PIN. Each time. I can check whichever 'Remember that number please' box and whichever 'All users may use this' box I find. Nothing helps. After a reboot, it asks again.
- After I entered it and confirmed, it tells me "Sending unlock key", and something about a timeout a seconds later. I can confirm again and then it works. It seems to me that the timeout comes after an insanely short time.
- Not so short is the waiting time before I see this PIN dialog. It can take a minute or two after login for the system to come up with that PIN dialog. On usb level, the hardware seems okay to me and is detected right after insertion.
- After I entered the PIN, it always asks me for my user password (in the typical 'you arent authorized' system dialog from policykit or whatever that comes from).
- From time to time, the 'connecting' animation never disappears (i think it's also a slightly different one, but the art of icon confusion in networkmanager is a different story). When I now open the menu and click again on the dialup connection - with the hope of trying again from the beginning - some important part of network manager crashes. I haven't checked so far if it is the icon or the service, but in this situation I typically reboot the system in order to get back NetworkManager and to try a second (or third) time.


I can't imagine that mobile network support in 16.04 is that terribly broken. I can connect to the Internet if I actually need it, yes. But this procedure is way too annoying for doing that casually for just checking mails in an idle minute.

Once the connection is up, it is rock stable and fast. So the device does not really seem broken to me.

What could I do wrong? Is there a config file which is worth checking? Log files? Maybe even a known workaround?


Greetings
Josef

---

