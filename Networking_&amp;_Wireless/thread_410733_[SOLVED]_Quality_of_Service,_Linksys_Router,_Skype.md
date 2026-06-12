---
title: "[SOLVED] Quality of Service, Linksys Router, Skype"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by wieman01 on 2007-04-16
Hello, 

After changing my Internet Service Provider a few weeks ago I have had to put up with lower VOIP quality via Skype. Radio streaming or surfing heavily interfers with Skype to such a degree that I cannot do anything on the web without making phone call nearly impossible (disruptions, lags, etc.). 

Now I plan to enable "Quality of Service" (QoS) for my wireless network and in particular for Skype. I have got a Linksys WRT54G router and have played around with the QoS settings but could not get it to work.

Has anyone enabled QoS for Skype on a Linksys router successfully? I would appreciate a bit of advice here.

Thanks!

---

### Post by dmizer on 2007-04-17
it might be equipment.  i have the same provider at home as i do at work.  at home, my skype works fine with moderate browsing.  at work (with a faster connection), it takes ages just to log in, and call quality is junk.

you might try setting your router to allow udp replies in across the skype specific port found like so:
> If you have IIS/Apache or similar software installed that uses ports 80 and/or 443 and you experience conflicts (such as service startup failure or malfunctions) the cause is most likely that your Skype is configured to use the same ports as the applications that experience problems.

There are two possible solutions to this issue:

* In Skype under Tools -> Options -> Connections untick the option "Use ports 80 and 443 for incoming connections". Skype will then use the port specified in the text box (make sure you also have opened that specific port in your router or firewall).

* Configure your http service/IIS/other to use another port for communications
[skype help](http://support.skype.com/index.php?_a=knowledgebase&_j=questiondetails&_i=528)

---

### Post by wieman01 on 2007-04-17
> **dmizer said:**
> it might be equipment.  i have the same provider at home as i do at work.  at home, my skype works fine with moderate browsing.  at work (with a faster connection), it takes ages just to log in, and call quality is junk.

you might try setting your router to allow udp replies in across the skype specific port found like so:

[skype help](http://support.skype.com/index.php?_a=knowledgebase&_j=questiondetails&_i=528)
Excellent, dmizer. I'll check this out tonight. Perhaps that's the issue.

That said, I still thought that QoS would be the solution. Have you played around with it yet?

---

### Post by dmizer on 2007-04-17
unfortunately i inherited this mess of a network from a real amateur.  i was left with nothing, including the router password, so i haven't been able to dig into settings like that yet.

---

### Post by wieman01 on 2007-04-17
Thanks, dmizer! I'll try out your suggestion nonetheless.

Does anyone else have experience concerning QoS and Skype?

---

### Post by dmizer on 2007-04-17
found some fantastic QoS discussion here: [http://www.dslreports.com/forum/remark,17270885](http://www.dslreports.com/forum/remark,17270885)

---

### Post by wieman01 on 2007-04-17
> **dmizer said:**
> found some fantastic QoS discussion here: [http://www.dslreports.com/forum/remark,17270885](http://www.dslreports.com/forum/remark,17270885)
Wow, thanks a ton. I'll read this tonight as well.

---

### Post by wieman01 on 2007-06-04
Just to close this thread and say a few words concerning [DD-WRT]("http://www.dd-wrt.com/dd-wrtv2/index.php"): It's simply terrific.

Before I had the firmware replaced and while I was running Linksys' native firmware that had come with the router, I had serious troubles browsing and Skype'ing while I was using BitTorrent and listening to Internet radio, etc.

After installing DD-WRT all these troubles belong in the past, I can now happily browse the web, do Skype, radio streaming, and BitTorrent all at the same time. No disruption at all.

DD-WRT rocks... that's all I can say. QoS is very easy to configure and just works. I was deeply impressed.

---

