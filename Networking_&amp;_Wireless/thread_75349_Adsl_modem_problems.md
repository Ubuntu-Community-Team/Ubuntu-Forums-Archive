---
title: "Adsl modem problems?"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by Major_Stitch on 2005-10-13
Hi everybody!
This is my first post here!

So can somebody answer these two questions:
1.Is there a way to install and use my Siemens ADSL A-100 USB modem with Ubuntu?

2.If not does Ubuntu support Ericsson HMD 220 ADSL modem, it has an ethernet and an USB interface but can it be used with Ubuntu?

Thank you and hope that somebody could help me!

---

### Post by mips on 2005-10-15
[QUOTE=Major_Stitch]Hi everybody!
This is my first post here!

So can somebody answer these two questions:
1.Is there a way to install and use my Siemens ADSL A-100 USB modem with Ubuntu?

2.If not does Ubuntu support Ericsson HMD 220 ADSL modem, it has an ethernet and an USB interface but can it be used with Ubuntu?

Thank you and hope that somebody could help me![/QUOTE]

You might get the Siemens box to work with PPPoE but ideally you want something that is straight ethernet (router not bridged). Makes live much easier. Maybe you can swop with someone or something like that.

[http://bandalarga.domus.online.pt:8080/temas/siemens_santis.shtml](http://bandalarga.domus.online.pt:8080/temas/siemens_santis.shtml)
[http://www.elitesecurity.org/tema/133210](http://www.elitesecurity.org/tema/133210)
[http://www.linux.hr/modules/phpwiki/index.php/Kako%20podesiti%20Siemens%20A-100-I%20USB%20aDSL%20modem](http://www.linux.hr/modules/phpwiki/index.php/Kako%20podesiti%20Siemens%20A-100-I%20USB%20aDSL%20modem)

[http://ubuntuforums.org/showthread.php?t=72144](http://ubuntuforums.org/showthread.php?t=72144)

---

### Post by Zinckk on 2005-10-15
I've just installed a new ethernet modem to replace my old USB one.  It seems to have improved things - in that I can now ping various URLs, but still can't seem to get internet 'connection' for firefox, etc.

It feels like I'm really close - but don't know what needs changing - can anyone help!?

Cheers

---

### Post by Major_Stitch on 2005-10-22
Well I bought an ethernet modem (Siemens c-100-I) and it's great! :smile:
Everything works and it's great!


[QUOTE=Zinckk]I've just installed a new ethernet modem to replace my old USB one.  It seems to have improved things - in that I can now ping various URLs, but still can't seem to get internet 'connection' for firefox, etc.

It feels like I'm really close - but don't know what needs changing - can anyone help!?

Cheers[/QUOTE]

For Zinckk: did you run 
```
pppoeconf
sudo pon dsl-provider
sudo poff dsl-provider
```

in 'pppoeconf' you set the connection and with the 'pon' and 'poff' you turn on/off the connection.
That worked for me and everything works!

---

