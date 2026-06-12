---
title: "printer (brother) through router usb port"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by limplenny on 2007-10-29
Hi guys, im sort of stilll a linux newb, and Im running into trouble with my printer which is connected to the usb port of my router (siemens gigaset sx762)
the printer is a Brother hl-5050 and I am running kubuntu gutsy,

some background:
I have my printer connected to my routers USB port. For windows my router's manual said to make a new TCP/IP printer port with "lpr" as the protocol and queue name "lp0". Thats all well and good but didn't quite work, and i think that's because the connection is only in one way, that is to the printer, and not from the printer, so it seemed as if windows print system was waiting for some kind of response, but since the connection is only one-way, it never gets any. I solved this by installing the brother printer driver with the option that it's a lpr printer. 

my problem:
In kubuntu with cups i get a similar problem to what happened in windows. Cups finds the printer at lpd://*ipaddres*/lp0 and can send jobs to it, but the printer wont print for some reason. When i click 'delete all jobs' in cups, all of a sudden it starts printing the job, but sometimes all screwed. So i was wondering if anybody knows a way to solve this?

i hope anyone can help, i read a lot of topics already but can't find anyhting to solve my problem. thanks,
lennard

---

