---
title: "How to set an Interface Offline?"
date: 2020-06-03
forum: Networking &amp; Wireless
---

### Post by eric2401 on 2020-06-03
[COLOR=#242729][FONT=Arial]So I'm pretty new to the Linux Ubuntu enviroment and I tried setting up a IP SLA Repsonder from a Programm which was shared on GitHub [https://github.com/cmouse/ip-sla-responder](https://github.com/cmouse/ip-sla-responder)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]So I compiled the programm using Make CC=gcc and asigned an IP-Addresse to the running Responder Programm. As soons as I started the Programm I was receiving data, but the Responder wasn't sening any data back to the Switch. I always got the Error Messang which was saying: Can't establish connection, on the Cisco Switch. So I started reading the threads on the GitHub Link and saw this:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Best if you don't configure any vlans and leave the **interface offline**, so linux or the nic won't eat up your packets. This is best used if you want to support same IP address on multiple VRFs. You can use up to 4096 different VLANs.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Since I'm new to ubuntu I am not entirly sure what thats means while he was saying leave the interfache offline. Do I need to shut it down? Or is this a specific configuration in ubuntu?[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'll attach my Interface configurations...[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Appreciate your Help!


[ATTACH=CONFIG]286086[/ATTACH]

[ATTACH=CONFIG]286087[/ATTACH]

---

### Post by slickymaster on 2020-06-03
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

