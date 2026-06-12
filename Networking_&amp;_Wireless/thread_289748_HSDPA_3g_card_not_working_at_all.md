---
title: "HSDPA 3g card not working at all"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by dr_dre on 2006-10-31
Hi, i just installed edgy on my compaq nx7010 and besides a few small things here and there it works pretty great. its a completely *stock* install and afterwards i added mplayer\w32codecs and gnomebaker. The only dealbreaker for me is my vodafone pcmia 3g card used to connect to Vodacom South Africa. 

tail -f /var/log/messages gives:

Oct 31 16:54:16 ubuntu-laptop kernel: [17185412.936000] pccard: CardBus card inserted into slot 0
Oct 31 16:54:16 ubuntu-laptop kernel: [17185412.936000] yenta EnE: chaning testregister 0xC9, 04 -> 04

i have looked at some of the other posts but havent found anything that can help. esp since i am a little unsure of exactly what card i have (huawei, nozomi etc). there is nothing printed
on the card so is there any other i can find this out?

i have read [http://www.mybroadband.co.za/vb/showthread.php?t=21726](http://www.mybroadband.co.za/vb/showthread.php?t=21726)

and the following is strange:

/etc/init.d/pcmcia start *doesnt work, i get the following*

/etc/init.d/pcmciautils

which if i try and start i get

*PCMCIA bridge drivers already present in kernel

also none of the /dev/ devices seem to correspond to what my HSDPA card is.

thanks for the help!

---

