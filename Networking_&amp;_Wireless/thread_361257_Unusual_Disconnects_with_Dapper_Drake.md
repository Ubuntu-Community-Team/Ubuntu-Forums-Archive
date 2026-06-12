---
title: "Unusual Disconnects with Dapper Drake"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by ahood on 2007-02-14
Hello,

I am helping a friend that has a computer running Dapper Drake. The friend is very new to computers (never used MSWindows before), but can take direction very well. I helped my friend set up the computer wirelessly using an atheros chipset wireless adapter and wireless motorola cable modem. The friend is using a cable Internet connection.

The friend is experiencing frequent disconnects from the Internet. When the disconnect happen, the system cannot find the mail server (email client) or http server (web browser).

The machine has Network Manager installed and there are blue bars on the bottom taskbar and the signal strength is 70%. 

My friend has firestarter running and when she starts it, it does not display an error message.

My friend will turn off the machine, then restart it the next morning and it will work okay, only to find the connection unavailable in the afternoon.

What are the possible issues to investigate?

The problem does not seem to be with the computer because I conclude that it can successfully connect to the Motorol cable modem wirelessly.

Is it poor service from the cable company?

Could it be Firestarter?

What else could it be?

What are steps to be taken to get a better handle on where the problem appears.

Please note that my friend lives many miles away, so connecting the computer directly to the motorola cable modem isn't an option. It is also not a good solution because connecting it directly can only be done temporarily. Wireless is the way this friend wants to go...

Any help will be greatly appreciated.

DrH

---

### Post by spd106 on 2007-02-15
You can usually tell if the modem has a problem by watching the LEDs. If the cable/internet light is out or flashing it normally means the connection has a problem. They are normally very reliable though, so this is unlikely to be the problem.

From the wireless side, you can check connection by bringing up the web page of the router/gateway/modem. You will have used this to set-up the device initially. If is times out then it's lost connection and the problem is likely to be the wireless link. If it does come up then it will usually have an Internet connection status.

You could always bookmark the web page if you don't want to have to enter [http://192.168](http://192.168) etc

From my experience Atheros cards are pretty reliable, though Dapper has madwifi-old rather than Edgy's madwifi-ng. If I had to point a finger it would be at Network Manager, yes it's easy to use, but I have found it to be rather flaky at times.

---

### Post by ahood on 2007-02-19
Thanks for the input Spd106, very much appreciated. We will upgrade to Edgy or more likely Feisty and hopefully, it will work better.

Al

---

