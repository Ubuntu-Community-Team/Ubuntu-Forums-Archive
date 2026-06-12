---
title: "WiFi temporary username settings with PEAP/MSCHAPv2 on 14.04"
date: 2014-12-01
forum: Networking &amp; Wireless
---

### Post by nicholi1977 on 2014-12-01
I am setting up a computer for our grad students at my university. I have one standard-user login for all of them to use to make things a bit simpler for them. I am trying to find a way, however, to have the WiFi connection ask for BOTH the username and password when trying to connect to the Univ's wireless system. We connect via WPA2, PEAP, MSCHAPv2, with NO cert required to connect. Getting the connection to ask for the password each time is easy enough, but there is no setting to do the same for the username. I'm running 14.04.


I tried removing the [highlight]identity=[/highlight] string using the touch/nano editing function in terminal, but it removed the connection within the GUI. I could see the connection within terminal, but the GUI would simply create a brand new connection when I would try to connect to the wireless network. 

I also tried to mirror the password settings using nano, and so under the [highlight]802.11 wireless security[/highlight] heading I added [highlight]leap-identity-flags=1[/highlight] and under the [highlight]802.1x[/highlight] heading I added [highlight]identity-flags=1[/highlight] and [highlight]identity-raw-flags=1[/highlight] strings. These were basically variants of the code strings for the password field, and I hoped this would work...but it didn't. It resulted in removing the connection from the GUI just like removing the [highlight]identity=[/highlight] string altogether, although I could still see the original connection using the [highlight]ls[/highlight] command in terminal.

This is what the [highlight]ls[/highlight] command looked like before and after editing the connections via touch/nano in terminal:

```

root@jayadmin-OptiPlex-GX280:/etc/NetworkManager/system-connections# ls
MU WiFi Wired connection 1

root@jayadmin-OptiPlex-GX280:/etc/NetworkManager/system-connections# ls
MU WiFi MU WiFi-d9a0a44b-0d73-4dac-92a6-1158d2d1fdf9 Wired connection 1

root@jayadmin-OptiPlex-GX280:/etc/NetworkManager/system-connections#

```



Any help/options would be greatly appreciated. I REALLY don't want to have to set up EACH of our grad students with usernames to access these computers.

---

