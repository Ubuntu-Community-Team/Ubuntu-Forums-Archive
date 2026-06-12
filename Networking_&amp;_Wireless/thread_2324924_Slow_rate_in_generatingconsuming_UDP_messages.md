---
title: "Slow rate in generating/consuming UDP messages"
date: 2016-05-17
forum: Networking &amp; Wireless
---

### Post by lasithc on 2016-05-17
I have two simple java programs to generate and receive UDP messages using DatagramSocket .
[B]
Generator[/B]
[COLOR=#2B91AF]String[/COLOR][COLOR=#303336] message [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#7D2727]"MyMessage"[/COLOR][COLOR=#303336];[/COLOR][COLOR=#303336]
[/COLOR][COLOR=#101094]byte[/COLOR][COLOR=#303336][][/COLOR][COLOR=#303336] data [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#303336]([/COLOR][COLOR=#303336]message[/COLOR][COLOR=#303336]).[/COLOR][COLOR=#303336]getBytes[/COLOR][COLOR=#303336]();[/COLOR][COLOR=#303336]
[/COLOR][COLOR=#2B91AF]DatagramPacket[/COLOR][COLOR=#303336] packet [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#101094]new[/COLOR][COLOR=#2B91AF]DatagramPacket[/COLOR][COLOR=#303336]([/COLOR][COLOR=#303336]data[/COLOR][COLOR=#303336],[/COLOR][COLOR=#303336] data[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]length[/COLOR][COLOR=#303336],[/COLOR][COLOR=#303336] host[/COLOR][COLOR=#303336],[/COLOR][COLOR=#303336] port[/COLOR][COLOR=#303336]);[/COLOR][COLOR=#303336]
socket[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]send[/COLOR][COLOR=#303336]([/COLOR][COLOR=#303336]packet[/COLOR][COLOR=#303336]);

[/COLOR]**Receiver**
[COLOR=#2B91AF]DatagramSocket[/COLOR][COLOR=#303336] serverSocket [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#101094]new[/COLOR][COLOR=#2B91AF]DatagramSocket[/COLOR][COLOR=#303336]([/COLOR][COLOR=#303336]port[/COLOR][COLOR=#303336]);[/COLOR][COLOR=#303336]
[/COLOR][COLOR=#2B91AF]DatagramPacket[/COLOR][COLOR=#303336] receiveData [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#101094]new[/COLOR][COLOR=#101094]byte[/COLOR][COLOR=#303336][[/COLOR][COLOR=#7D2727]1024[/COLOR][COLOR=#303336]];[/COLOR][COLOR=#303336]
receivePacket [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#101094]new[/COLOR][COLOR=#2B91AF]DatagramPacket[/COLOR][COLOR=#303336]([/COLOR][COLOR=#303336]receiveData[/COLOR][COLOR=#303336],[/COLOR][COLOR=#303336] receiveData[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]length[/COLOR][COLOR=#303336]);[/COLOR][COLOR=#303336]
serverSocket[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]receive[/COLOR][COLOR=#303336]([/COLOR][COLOR=#303336]receivePacket[/COLOR][COLOR=#303336]);[/COLOR][COLOR=#303336]
[/COLOR][COLOR=#2B91AF]String[/COLOR][COLOR=#303336] message [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#101094]new[/COLOR][COLOR=#2B91AF]String[/COLOR][COLOR=#303336]([/COLOR][COLOR=#303336]receivePacket[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]getData[/COLOR][COLOR=#303336]());

[/COLOR]So generator generate messages and receiver capture them. In windows I can go up to 200,000 messages per second. But in Ubuntu it is 100,000 messages per second (half value from Windows environment).
Not only that it seems if I generate 50,000 per second on Ubuntu then receiver will catch around only 30,000. And if generator generate 100,000 then receiver catch 60,000. Likewise for 200,000 it will catch only 100,000 in the receiver.
I am not sure why this is performing well on windows and not on Ubuntu. We tested on both Ubuntu desktop and server versions.
Could some one help me?
Thanks!

---

