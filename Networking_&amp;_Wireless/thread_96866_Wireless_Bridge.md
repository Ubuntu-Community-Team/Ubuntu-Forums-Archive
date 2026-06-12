---
title: "Wireless Bridge"
date: 2005-11-29
forum: Networking &amp; Wireless
---

### Post by raghav_p on 2005-11-29
This is for the networking gurus out there.

I have a Ubuntu desktop running with a wireless card. It has another ethernet network card. I want to be able to connect another networking device (printer if u must know) and be able to share it across the network. I saw the commercial offerings for this (ethernet-wireless bridge) but it was too much for my budget.

Can this be done?

------- EDIT -------

Perhaps I should clarify for the printer-sharing. My printer is actually a multi-function with ability to print/scan over the network. I was trying to benefit from that.

---

### Post by jafenske on 2005-11-29
Naperville... I grew up in Naperville.  Sorry, I don't have a answer to your question.

---

### Post by raghav_p on 2005-11-29
[QUOTE=jafenske]Naperville... I grew up in Naperville.  Sorry, I don't have a answer to your question.[/QUOTE]

interesting.. i didn't know anyone else (from) here knew what linux was.everyone seems so l.. microsoft friendly

---

### Post by peanut butter on 2005-11-29
[QUOTE=raghav_p]This is for the networking gurus out there.

I have a Ubuntu desktop running with a wireless card. It has another ethernet network card. I want to be able to connect another networking device (printer if u must know) and be able to share it across the network. I saw the commercial offerings for this (ethernet-wireless bridge) but it was too much for my budget.

Can this be done?[/QUOTE]

to share a printer you just use cups and share it with samba.

sorry i donthav ananswer to your other question

---

### Post by raghav_p on 2005-11-30
bump?

---

### Post by mips on 2005-12-01
Does the printer have an ethernet port ?
What model/brand printer is it ?

---

### Post by raghav_p on 2005-12-01
[QUOTE=mips]Does the printer have an ethernet port ?
What model/brand printer is it ?[/QUOTE]

Yes, the printer has an ethernet port. The model number is: HP Officejet 7130. I checked the HPOJ site and I see its compatible with a "jetdirect capable" printer. I assume the ethernet card would be enough for that. 

I just can't connect the printer to my router because it's too far away :( and I'm planning to put it next to my dad's computer (the one with both the wireless card and ethernet port) so I thought if I could bridge through it, it would be great.

---

### Post by mips on 2005-12-02
That should not be to hard to do, i think.

Is your dad's pc runing Windows or Ubuntu ?

Basically you need to enable internet connection sharing and let your dad's pc act as a gateway. The Printer then gets an IP address from the PC or you configure one statically.

---

### Post by raghav_p on 2005-12-02
[QUOTE=mips]That should not be to hard to do, i think.

Is your dad's pc runing Windows or Ubuntu ?
[/QUOTE}

Ubuntu thankfully :)

I'll try your suggestion this week and let you know how it worked out! Thanks!

---

### Post by mrsudo on 2008-03-05
did it ever work ....?
im trying to do something similiar with an xbox360

---

### Post by mips on 2008-03-05
> **mrsudo said:**
> 
im trying to do something similiar with an xbox360

Similair what?
[http://ubuntuforums.org/showthread.php?t=269235](http://ubuntuforums.org/showthread.php?t=269235)

---

### Post by jeffus_il on 2008-03-05
Do you have a regular printer or a special network server. For a regular printer cups automatically shares it using the ipp protocal, nothing much to do, no cost.

Ignore this, didn't realise this thread was so old, it has cobwebs on it.

---

