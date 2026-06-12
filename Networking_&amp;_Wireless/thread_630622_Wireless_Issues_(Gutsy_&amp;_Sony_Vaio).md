---
title: "Wireless Issues (Gutsy &amp; Sony Vaio)"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by A-dogg on 2007-12-03
I've spent hours searching the forums and still haven't been able to find anything on my issues (looks like a lot of people have unresolved issues).

Internet works perfect if I used wired. Wireless works perfectly if I connect  to my friend's encrypted networks, so obviously the basic ethernet card works with ubuntu 7.10. My card is an Intel PRO/Wireless 2200BG.

My problem is generally when I'm trying to connect to free wifi. 

--How do I stop nm-applet from trying to connect to a signal while it's trying to connect? As of now I have to wait for it to try and fail before it'll let me try another and that could be 10 minutes. 
--How do I exclude various signals so the card never tries them? I may have fixed this by going into "configuration editor" and unsetting the signals that I know are bad. But the big problem here is that it'll start trying to connect to various signals on it's own and I can't stop it from doing that.

I'm planning to try WICD instead of Network Manager (no idea if I should uninstall NM or if they can play nice together), I've heard WICD is much better.

Is there a way to force it (I guess by "it" I mean Network Manager) to refresh the wireless network list? For example, I took my laptop to work today and when I woke it from suspend, it still showed the wireless networks from where I live...

Ugh!

It's a shame because Gutsy rocks aside from this.

---

### Post by chalewa on 2007-12-03
wicd works pretty well...

but no, nm-applet and wicd do not coexist together, upon installing wicd nm-applet will no longer be there.

---

### Post by A-dogg on 2007-12-03
I just installed wicd. seems to be much better so far. granted I'm only using wired internet...

---

