---
title: "Network Manager! YES! (help please)"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by coldopm on 2008-05-11
[http://ubuntuforums.org/showthread.php?t=766560&highlight=hardy+wireless+broadcom](http://ubuntuforums.org/showthread.php?t=766560&highlight=hardy+wireless+broadcom)

What a great step by step. Thank you. For the first time since Hardy installed my wireless card picks up all the various Networks in my range!

Unfortunately I cannot connect to ANY of the networks in the list. My own (yes I know the password) or any of the unsecure networks in the list either. Are there known issues with the default network manager? Can anyone recommend a working app? Can anyone give me a hand getting connected?

---

### Post by coldopm on 2008-05-11
took me a couple days of browsing forum posts to get my BCM 4310 to even find wireless networks. Now I cannot connect to my own home wireless network. Anyone please help?

---

### Post by LeoSolaris on 2008-05-11
Ok, when ya get to terminal, type in ```
[COLOR=Black]lspci | grep Broadcom\ Corporation[/COLOR]
``` and tell me what you got for your network card, exactly. Cut and paste it.

If you're using BCM4310 (rev 01)then you should not have followed that how-to precisely. The link in the how-to is for other BCM43xx cards rather than the BCM4312 (rev 02). (You mentioned 4310, which needs a different download to get working properly.)
 
 Did you also get the downloads from step 2e in the linked how-to?
 > [COLOR=Red]**For Step 2, You can check your Broadcom wireless version with this command in terminal : [B][COLOR=Red]"_*lspci | grep Broadcom\ Corporation*_"[/COLOR]**,if your wireless device is different from BCM4312 (rev 02), please refer to the following link for this step and you can continue again with step 3 onwards:[/B][/COLOR][COLOR=Red]
[COLOR=Black]Did you make sure to note that additional step?[/COLOR][COLOR=Black](just checking, because it's little things that trip people up.)

This procedure may not work for Hardy, so you may have to install Gutsy, get it working, then try to do a distro upgrade to Hardy and see if it will continue to work.

Leo

P.S. [This How-To]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM43xx_%28all,_ndiswrapper/firmware%29") may work for you, too. You may have to undo all that you did in the first one, but that was tested to work in Gusty. Since it's just an Ndiswrapper, it will probably carry over to Hardy. 
[/COLOR][/COLOR]

---

