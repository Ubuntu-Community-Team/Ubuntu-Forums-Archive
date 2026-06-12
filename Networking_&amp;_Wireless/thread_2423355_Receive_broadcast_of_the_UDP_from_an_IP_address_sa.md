---
title: "Receive broadcast of the UDP from an IP address same as oneself"
date: 2019-07-21
forum: Networking &amp; Wireless
---

### Post by antmh on 2019-07-21
[LEFT][COLOR=#242729][FONT=inherit][FONT=Arial][FONT=inherit]I am writing a udp program in C on Ubutu 18.04.
The program can receive successfully if the IP address is different from oneself.
However, when I from the same address as own IP, The program waits forever with the recvfrom function and can not receive the broadcast.
Checked in tcpdump, UDP seems to reach certainly.
I set rp_filter to 0 but the situation does not change.
I could receive using PF_PACKET. Is there any way to receive using AF_INET?
Please advise and thanks for looking.

[LEFT][COLOR=#303336][FONT=inherit] sock [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] socket[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]AF_INET[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit] SOCK_DGRAM[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit] IPPROTO_UDP[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
 addr[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]sin_family [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] AF_INET[/FONT][/COLOR][COLOR=#303336][FONT=inherit];[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
 addr[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]sin_port [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] htons[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]PORT[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
 addr[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]sin_addr[/FONT][/COLOR][COLOR=#303336][FONT=inherit].[/FONT][/COLOR][COLOR=#303336][FONT=inherit]s_addr [/FONT][/COLOR][COLOR=#303336][FONT=inherit]=[/FONT][/COLOR][COLOR=#303336][FONT=inherit] inet_addr[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#2b91af][FONT=inherit]BroadCastAddr[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
 [/FONT][/COLOR][COLOR=#101094][FONT=inherit]if[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]bind[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]sock [/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#101094][FONT=inherit]struct[/FONT][/COLOR][COLOR=#303336][FONT=inherit] sockaddr [/FONT][/COLOR][COLOR=#303336][FONT=inherit]*)&[/FONT][/COLOR][COLOR=#303336][FONT=inherit]addr[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#101094][FONT=inherit]sizeof[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]addr[/FONT][/COLOR][COLOR=#303336][FONT=inherit]))[/FONT][/COLOR][COLOR=#303336][FONT=inherit]<[/FONT][/COLOR][COLOR=#7d2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit])[/FONT][/COLOR][COLOR=#303336][FONT=inherit]{[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
    perror[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#7d2727][FONT=inherit]"bind"[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
 [/FONT][/COLOR][COLOR=#303336][FONT=inherit]}[/FONT][/COLOR][COLOR=#303336][FONT=inherit]
 recv[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit] sock[/FONT][/COLOR][COLOR=#303336][FONT=inherit],[/FONT][/COLOR][COLOR=#303336][FONT=inherit] sRcvBuf[/FONT][/COLOR][COLOR=#303336][FONT=inherit][[/FONT][/COLOR][COLOR=#303336][FONT=inherit]sHead[/FONT][/COLOR][COLOR=#303336][FONT=inherit]],[/FONT][/COLOR][COLOR=#101094][FONT=inherit]sizeof[/FONT][/COLOR][COLOR=#303336][FONT=inherit]([/FONT][/COLOR][COLOR=#303336][FONT=inherit]sRcvBuf[/FONT][/COLOR][COLOR=#303336][FONT=inherit][[/FONT][/COLOR][COLOR=#303336][FONT=inherit]sHead[/FONT][/COLOR][COLOR=#303336][FONT=inherit]]),[/FONT][/COLOR][COLOR=#7d2727][FONT=inherit]0[/FONT][/COLOR][COLOR=#303336][FONT=inherit]);[/FONT][/COLOR][/LEFT]
[/FONT]
[/FONT]
[/FONT][/COLOR][/LEFT]

---

