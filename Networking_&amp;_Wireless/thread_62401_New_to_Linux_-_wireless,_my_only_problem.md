---
title: "New to Linux - wireless, my only problem"
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by Electrobes on 2005-09-04
So I went out today to buy a new PCI wireless card and got the DWL-G510 (Airplus G). I installed Ubuntu yesterday night and it detected everything that was on there, including my optical wireless thumb mouse. 

After sticking the card into my comp today, it did recognize it.. but for some reason I can't connect to the internet and I am not sure what else to do. Any help would be greatly appreciated, thanks.

---

### Post by viorel on 2005-09-04
did you connection work yesterday? or was there any moment when u had a working connection to the internet with this new card?

If not, u might want to look at your router's settings; are u using mac address filtering?

---

### Post by Electrobes on 2005-09-04
Hi again. Okay I just ran to check on it again, but I was wrong the first time... it did not see my wireless card ever. 

So lemme reiterate what I am using: I am using a D-Link DWL-G510 (wireless), with a Linksys Router (not sure which one). I physically installed the card into the comp hoping it would see it off the bat but it did not happen. I have the cd in the computer now (it refuses to eject it) with the drivers. I do not know how to install the drivers from the cd. What do I need to type into the terminal to make this happen.. maybe it will then recognize the card?

The cd not wanting to eject it telling me that the unmount is busy... any idea why?

Thank you.

---

### Post by Electrobes on 2005-09-05
I still haven't been able to have Ubuntu recognize the wireless card yet. I have the window drivers on the windows cd, just am not sure what to do after that. I finally was able to get the cd to eject. I have the stock new Ubuntu installed on my comp... any ideas what I need to do (in the terminal?) to get the OS to recognize the drivers, and then my card? thanks

---

### Post by VancouverTT on 2005-09-05
I am also a newbie having the same ubuntu problem, only my installation won't recognize a DWL-G520.

I am searching throught the forums (so far without luck), and will keep an eye on this thread in case someone posts a "try this"

---

### Post by Electrobes on 2005-09-05
I have tried a couple of things, but none of them have worked. I wish I had more experience in using the terminal so I could at least try some other things. Argh once I get internet to that box I would have such a more easier time trying to learn all of this... its hard having to run upstairs then back down to get more info.. everytime :p

---

### Post by Electrobes on 2005-09-05
well I tried what was on this page - [https://wiki.ubuntu.com/forum/hardware/ndiswrapper](https://wiki.ubuntu.com/forum/hardware/ndiswrapper) but it said that neta3ab was invalid. I haven't a clue as to what to do now.. since my OS isn't taking the a3ab.inf file as a driver for my wireless card.

---

### Post by Electrobes on 2005-09-05
Bump - I hate bumping but I have nothing else I can try.. do I need to get another wireless card?

---

### Post by drummer on 2005-09-05
[QUOTE=Electrobes]Bump - I hate bumping but I have nothing else I can try.. do I need to get another wireless card?[/QUOTE]
 Try a different version of the driver maybe.
[quote=http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]
Card: D-Link DWL-G510 (Rev B)
    * Chipset: Atheros
    * pciid: 168c:001a
    * Driver: Version 1.0, Provided on CD. Version 2.11 from dlink.com also works.
    * Other: only WEP tested, works fine on 2.6.9 and 2.4.27. The short-named .conf file symlink was pointing to the wrong long-named .conf file - fixed manually. [/quote]not sure what the last sentense means, but could be a problem for you too.

---

### Post by mlomker on 2005-09-05
Cards with native support don't cost any more money--just look through the list and buy one that uses a Prism, ACX100, Atheros, RT2500, or Intel 2200 chipset.

[This list](http://www.linux-wlan.org/docs/wlan_adapters.html.gz) is a little old but gives you an idea.

---

### Post by drummer on 2005-09-05
[QUOTE=mlomker]Cards with native support don't cost any more money--just look through the list and buy one that uses a Prism, ACX100, Atheros, RT2500, or Intel 2200 chipset.

[This list](http://www.linux-wlan.org/docs/wlan_adapters.html.gz) is a little old but gives you an idea.[/QUOTE]
 Ndiswrapper doesn't seem slow to me.
If you replace the card, be careful what you get and that the card has the chipset you expect. I have a Netgear WG311**v2**, which has the ACX111 chip, whereas the WG311 (previous revision) has the Atheros chip. Some vendors don't make it all that clear as to what you're getting.. the 'v2' on mine is in small print near the barcode, and on the chip itself, so not very promenant. BTW, the card I have works fine for me with ndiswrapper and I believe it also works fine without ndiswrapper if you don't use WEP.

---

### Post by mlomker on 2005-09-05
It sounds like there are two versions of that card--the 'B' version has native linux support because it uses an Atheros chipset.

[Read this.](http://www.linuxquestions.org/hcl/showproduct.php?product=2386&sort=8&cat=133&page=1)

---

### Post by Electrobes on 2005-09-05
mlomker - wow thats exactly it. I have been using ndiswrapper the entire time (granted I know nothing of terminal commands.. just kept trying). I tried typing in [ftp://ftp.gnu.org/pub/gnu/sharutils/sharutils-4.3.78.tar.gz](ftp://ftp.gnu.org/pub/gnu/sharutils/sharutils-4.3.78.tar.gz) to the web browser, but it says it can not change directory...

Also do I need to uninstall idnswrapper? I am still trying to understand what it does.. but for now I'll settle with anything as long as I get the internet working... Thanks!

---

### Post by Electrobes on 2005-09-05
Is there a way for me to install the madwifi driver without trying to install [ftp://ftp.gnu.org/pub/gnu/sharutils/sharutils-4.3.78.tar.gz](ftp://ftp.gnu.org/pub/gnu/sharutils/sharutils-4.3.78.tar.gz) (by the way I could not find the one he suggested.. so I dled 4.5.1, but I have no idea how to install it). He said he compiled it using that program, but I don't even know how to do that either. 

Oh should I uninstall ndiswrapper? Or can I keep it?

---

### Post by mlomker on 2005-09-05
You can look for the ndiswrapper line in the /etc/modules file and remove it if it is in there--that's what would cause it to load when you reboot.  Ndiswrapper is a program that allows you to use a Windows network card driver under linux.  It is designed for use with cards that do not have a linux driver.  If you have a card with a linux driver then you're better off using the linux one, of course.

I've never installed madwifi but if you [search the forums](http://www.ubuntuforums.org/showthread.php?t=38972&highlight=madwifi) --  there are a number of posts about it.  It sounds like you do need to download a couple things.

* He said he compiled it using that program, but I don't even know how to do that either. *

You have a lot to learn, then.  Start using Google and the Search feature on this board *a lot* if you plan to continue running linux.  I've been a network admin for ten years and I can't always figure things out...

---

### Post by surbiff on 2005-09-07
hi!
i thougt that, instead of making a new thread i use this one. i think the problem is in the same kategory. (thats what i think) :-p

i have big problems with d-link dwl g650 - H/W..:C3 - F/W..:4.11 
i looked it up and its atheros . 

i have a dwl g520 working. it was no problems at all with that. 

here is what i got so far:
in gnomes (device manager) i can see the card, that it is detected,
in lsmod i see that there is meny modules that are working with wlan and pcmcia
in /var/log/messages  i found that the driver is allready enabled for the card.

i had the card in place when ive started the lapptop, and i tried to rebot a couple of times but it was the same. and then i thought, (what the hl) so i RE-installed the whole thing, i have been running linux now fo 1 year so a little i can do but its not much! :-)  
but after installing, again, it was the same thing. just an eth0 for the cabled card and no eth1/ath0 for the wireless connection.

but in ifconfig or iwconfig i dont get a eth1 or ath0, that doesnt exist or it is hiding somewere :-p ...

i red about madwifi!,  should i need that?  or do i need something else loaded, some module or something like that?

in ubuntus suported hardware list the dwl g650 is in, and it says that it should work out of the box, thats the reason i bought it, (got it today.)


please help me, someone!

---

### Post by mlomker on 2005-09-07
[QUOTE=surbiff]please help me, someone![/QUOTE]

The Atheros driver is called ath_pci.  Try: **dmesg | grep ath_pci** at a command prompt.  If the driver is loaded then you should see some output.  If you don't see anything then try **modprobe ath_pci** to load the driver.  Then try the dmesg, iwconfig, ifconfig to see if you get anything.

---

### Post by surbiff on 2005-09-08
i fixed it!!  :razz: 

damn im glad...

i found a thread here in ubuntuforums: [here it is](http://www.ubuntuforums.org/showthread.php?t=38972) 
if you go down a bit you see a guy that fixed his "dwl G650" card .. thats what i did!

and now it works great! :-)

thanks anyway mlomker!  

may tux be with you all!!!

---

