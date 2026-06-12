---
title: "dnsmasq problem"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by Wolfpack Fan on 2008-02-14
I am a returning Newbie to Linux (10 years ago I used SUSE while in school.)  I just got Gutsy 7.10 running this weekend and have had problems with the speed of my browsing.  I followed the advise of many and installed and configured dnsmasq.  I do not believe I missed any steps, but now every time I reboot I have to undue the changes in the dhclient.conf the resolv.conf and the dnsmasq.conf files and restart my network.  Then once I get connected I can go through the setup of dnsmasq again and all is well.  Am I missing a simple setup issue?  I could just stop using dnsmasq but without it my browsing is painfully slow.

Thanks,
Chris

---

### Post by kerry_s on 2008-02-14
okay, now that you've ranted, how about some actual info?

why do you need to do all that?
what is it your doing?

here's what i did with my dnsmasq setup after i installed it.

edit /etc/dhcp3/dhclient.conf

you just need to uncomment 1 line(see pic)

reboot

that's all to it.

you can of course fine tune it in dnsmasq.conf, but it's not really needed. i did mine to just work with eth1 and up'ed my cache.(attached)

---

### Post by Wolfpack Fan on 2008-02-14
I apologize if it sounded like I was ranting.  That really was not my intention.  I rarely post anywhere, and I was attempting to give some of my back ground and information about what I was doing.

I think I found out what the problem was.  The DCHP server was enabled on my router. Once I turned that off, I was able to reboot my computer and the internet came up.  

One small problem still.  Browsing was slow, so I looked at the config files the nameserver 127.0.0.1 was not listed in the resolv file. So I added it and my speed came back.

Thanks,
Chris

---

### Post by kerry_s on 2008-02-14
no problem.
remember resolve.conf is rewritten every boot, that's why you need to uncomment that line in dhclient.conf (see pic) and 127.0.0.1 will be added to resolv.conf.

isn't the dhcp server suppose to be on in the router? that gives your computer a access address to the internet, unless your using a static address. dns is what looks up internet address, on some isp's they have slow servers, so caching on the computer with dnsmasq speeds it up, because it does not have to look it up on the next trip.

---

### Post by Wolfpack Fan on 2008-02-14
Thank you very much for your help.  This is a huge learning process for me.  Everything time I mess with something I learn all sorts of unrelated things.  This was one of them.  It was my tweaking of my router that was the cause of all the problems, and it had nothing to do with dnsmasq (I got that setup correctly.) 

Its all good though, and I am having a lot of fun learning.

Thanks again
Chris

---

