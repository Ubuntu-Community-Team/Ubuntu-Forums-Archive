---
title: "ACX111 in Feisty Fawn"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by Cherry Cotton on 2007-03-30
I'm using the Feisty Fawn beta and have that fussy wireless chipset, the "Texas Instruments ACX 111 Wireless Interface." Anyway, yes, it doesn't work. I know that [this here]("http://www.ubuntuforums.org/showthread.php?t=389935&highlight=feisty+acx+111") is a good thread for this subject, but... I'm new to Linux, so it's all Greek to me.

I use WEP encryption with a lengthy hexadecimal key, which I've checked over and over again, and even though I enter it into the settings and _then again_ when I try to connect (it asks me.... twice...), it will not work. I gather that this chipset and its drivers are kinda buggy in Linux, but it sounds like Edgy Eft cleared up most of the problems. Has Feisty Fawn re-awakened the sleeping giant? Please help!

---

### Post by Cherry Cotton on 2007-03-31
Hey, this might help: I just talked to my brother, who's a big Linux expert. (He uses Edgy Eft Ubuntu.) Anyway, he said I ought to ask if there's a way to turn off some of the automated network settings in Feisty Fawn. Since ACX111-based wireless card users seem to be doing fine with Edgy Eft (and most of the ACX111 help materials on the Internet seem to be for Dapper Drake, for that reason), it's probably some of the new stuff in Feisty Fawn that's causing the issues. He told me that, if some of the automated network management features can be turned off--the key element being anything new for Feisty Fawn--he should be able to get my wireless card to see my wireless network the old-fashioned way. (I set up my Linux PC to work as an SSH server through a wired connection, which was fun.)

So, please, yes! Any help with getting my ACX111 card to work with Feisty Fawn, or help in disabling some of the snazzy new networking features in Feisty Fawn, would be super-greatly appreciated! The key is that the automated stuff is conflicting with what my brother was trying to do, which is take control of the wireless network himself. I didn't quite understand it, but okay! And I don't mean to put down the new features in Feisty Fawn--they're what allowed me to install Ubuntu on my Windows box, and I've been having lots of fun with it even offline. The Windows migration tools are superb. So, I recommend the beta--but please, help me with my wireless card! Thanks!

---

### Post by mckechan on 2007-10-17
Did you ever get this to work? I have the same chipset and I can't get it to connect.

---

### Post by rustybronco on 2007-10-17
Linksys wpc54g v2 with an acx-111 chipset worked fine on my laptop with 7.04 in manual mode (no roaming) dhcp and wep (hex code like d35188bbde) it would not work until I selected iv4 and saved it then went back into manual config set to dhcp and saved it again.
Your router is set to wep also isn't it? 
let me know if it helps

[http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1130276681921&pagename=Linksys%2FCommon%2FVisitorWrapper)

---

### Post by mckechan on 2007-10-18
Thanks for a reply. I can't really remember what I did but it's not really a big priority for me right now. I'll post back if I try again another time...

---

