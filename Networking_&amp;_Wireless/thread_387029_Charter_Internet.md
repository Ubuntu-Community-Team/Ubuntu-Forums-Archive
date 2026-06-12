---
title: "Charter Internet?"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by xptweakerntn on 2007-03-17
I had bellsouth dsl, worked fine with my box. I got charter cable, won't work at all. it works fine on this windows machine. just not at all on my box, i used dapper, but am now trying edgy to see what will happen.

---

### Post by chili555 on 2007-03-18
We would love a bit more information. Wired or wireless? Connected direct to the DSL modem or an intervening router? DHCP or static IP?

What happened when you configured the interface through System -> Administration -> Networking? Any complaints?

---

### Post by ubuntu27 on 2007-03-18
> **xptweakerntn said:**
> I had bellsouth dsl, worked fine with my box. I got charter cable, won't work at all. it works fine on this windows machine. just not at all on my box, i used dapper, but am now trying edgy to see what will happen.

Make sure your modem is cable based, but** avoid** USB modem.

ETHERNET IS RECOMMENDED

My ISP is the same as yours, and their modem (I am leasing it) was trouble free.

---

### Post by lexen on 2007-03-26
I have charter on Edgy, it works, but it is really slow, around a tenth to a twentieth the speed they said it could do.  I just got off the phone with them and we did a speed test that showed that it is working fine when it obviously isn't.  If anyone else is having this problem too, let me know.

---

### Post by ubuntu27 on 2007-03-26
> **lexen said:**
> I have charter on Edgy, it works, but it is really slow, around a tenth to a twentieth the speed they said it could do.  I just got off the phone with them and we did a speed test that showed that it is working fine when it obviously isn't.  If anyone else is having this problem too, let me know.

My Internet speed is slow compared to when I boot Windows.
I don't know why is that. But I know one thing, there are tricks to make it faster.

Try to desable the IP version 6

follow[ this guide]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") for that.

Some people say that if you change your ISP's dns to [OpenDNS]("http://www.opendns.com/"), it would be considerally faster. I have tried this but I haven't noticed any improvements.  You may try it.

[Here is the official guide]("http://www.opendns.com/start/ubuntu.php") for changing your DNS to [OpenDSN]("http://www.opendns.com/"):

---

### Post by stchman on 2007-03-27
> **lexen said:**
> I have charter on Edgy, it works, but it is really slow, around a tenth to a twentieth the speed they said it could do.  I just got off the phone with them and we did a speed test that showed that it is working fine when it obviously isn't.  If anyone else is having this problem too, let me know.

I too have Charter cable modem and the internet is very spotty.  Sometimes the internet is very fast and sometimes it is really slllooowwwww.  I have disabled ipv6 but still really slow.  I have combed these forums for information but no improvment.

Thanks

---

### Post by marx2k on 2007-03-27
I have Charter and have had no problems at all with their 5MB down, 512K up service in Wisconsin.  I was getting BLAZING speeds when I was using my Linksys router with 3rd party firmware, but then that burned the router.

Even with my roommate's crappy Buffalo Airstation router, I seem to be having no real slowdowns.

I have disabled IPV6 but that seemed to give no real performance boost. I also use OpenDNS and that did give a nice boost in lookup speed as some of Charter's DNS servers can be somewhat slow.  I just put OpenDNS' two lookup servers in my router's DNS config and restart my networking and it seems to work fine.

---

