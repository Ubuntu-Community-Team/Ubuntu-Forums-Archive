---
title: "Am I getting close with my WiFi connect problem"
date: 2005-10-30
forum: Networking &amp; Wireless
---

### Post by MoLeak on 2005-10-30
I installed Ubuntu 5.10 on my laptop again, and it uses a pcmcia Airlink G wifi card. I am not connecting yet but what I do see is in my Network settings, DNS tab, my correct domain under **Searched Domains**, and it has DNS servers listed. That tells me I assume it is seeing the net.  But I still cannot connect with my browser.  I have wlan0 set to active but nothing yet.

Any ideas?

-MoLeak

---

### Post by Dardie on 2005-10-30
MoLeak,

you'll need to provide more information... for starters the output from iwconfig, ifconfig, and netstat -r. Maybe also the contents of /etc/network/interfaces, making sure to **** out your WEP key.

From the way you've phrased your question, sounds like you've already posted in another thread; try to continue a single thread or link to the previous one, otherwise you're making it harder for people who might be able to make useful comment.

Cheers,
Daz

---

### Post by MoLeak on 2005-10-30
[QUOTE=Dardie]MoLeak,

you'll need to provide more information... for starters the output from iwconfig, ifconfig, and netstat -r. Maybe also the contents of /etc/network/interfaces, making sure to **** out your WEP key.

From the way you've phrased your question, sounds like you've already posted in another thread; try to continue a single thread or link to the previous one, otherwise you're making it harder for people who might be able to make useful comment.

Cheers,
Daz[/QUOTE]

Ahhh, that's some CSI forensic level sluthing there Daz!  Good job. ;) 

Anyway, I didn't seem to be getting anywhere with my questions so I thought I'd try a new thread. I am still a noob but I'm not giving up on learning this stuff.  

iwconfig shows no wireless extenstions in either irda0, sit0 and wlan0 shows ieee 802.11b/+ /f+ and a few other things that look pretty common. RX TX stuff.

netstat -r shows nothing under gateway genmast flags mss window, etc.

The things inside interfaces are script grep map wlan0 iface wlan0 inet dhcp yada-yada.

what now?

-MoLeak

---

### Post by Dardie on 2005-10-30
MoLeak,

could you paste the output of those commands (iwconfig, ifconfig, netstat -r, cat /etc/network/interfaces) into a reply here?... maybe there is some clue hidden in the output of those commands.

Cheers,
Daz

---

### Post by MoLeak on 2005-11-03
I wish I could paste it in.  The machine isn't on the net at all.  Which makes it difficult to do.  There isn't a burner on it either.  But I'm still trying.

-MoLeak

---

