---
title: "wireless not found"
date: 2004-12-24
forum: Networking &amp; Wireless
---

### Post by Rule on 2004-12-24
Hi, I have and Averatec 6100 laptop and I cant get the wireless nic working. I looked around for the driver but I couldn't find anything other then the ones for the 3200.

So I looked around and read that I had to extract the windows drivers but I don't know how. I keep getting

"xquizit@lappy:~ $ unzip AF64002.exe -d /home/xquizit/wlan/
Archive:  AF64002.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of AF64002.exe or
        AF64002.exe.zip, and cannot find AF64002.exe.ZIP, period.
"

TIA
Rule

---

### Post by bmartin on 2007-05-15
> **Rule said:**
> Hi, I have and Averatec 6100 laptop and I cant get the wireless nic working. I looked around for the driver but I couldn't find anything other then the ones for the 3200.

So I looked around and read that I had to extract the windows drivers but I don't know how. I keep getting

"xquizit@lappy:~ $ unzip AF64002.exe -d /home/xquizit/wlan/

The drivers you want should be the ones [here]("http://www.averatec.com/customercare/support/downloads/6100_XP_WLAN_2.2.1.0.exe"). I also attached what should be the correct Windows drivers.

Supposing you do need to use Windows drivers to get your wireless working, you'll probably need to use ndiswrapper to get it running. There should be instructions on how to get it and how to use it elsewhere. It's probably as simple as using **sudo aptitude install ndiswrapper**.

---

### Post by bmartin on 2007-05-15
I'm not sure how to check which chipset you have, but if it's this one, it should work out-of-the-box.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek)

---

### Post by MeeMaw on 2007-05-15
> **bmartin said:**
> I'm not sure how to check which chipset you have, ..........

In a terminal, do 
sudo lspci

The chipset should be in the list where you find the wireless card info (where it says Network.... wireless.... it might even say something like RealTec or the AF6400 you posted before) - post it here if you aren't sure.
:)

---

### Post by chili555 on 2007-05-15
My sister, MeeMaw, is wise. Before you dirty your hands, to say nothing of your reputation as a newbie, by delving into the black magic of extracting Windows drivers in Linux, let's take a look at the chipset you have. We may be able to get it going without magic. What do you want to bet it's a Ralink?

---

### Post by MeeMaw on 2007-05-20
> **chili555 said:**
> My sister, MeeMaw, is wise. Before you dirty your hands, to say nothing of your reputation as a newbie, by delving into the black magic of extracting Windows drivers in Linux, let's take a look at the chipset you have. We may be able to get it going without magic. What do you want to bet it's a Ralink?

Thanks, chili!!!!!  (It's always nice to hear I am wise, especially from my own brother!!!!) 

Post it for us and we'll see.

---

### Post by bmartin on 2007-05-20
> **chili555 said:**
> My sister, MeeMaw, is wise. Before you dirty your hands, to say nothing of your reputation as a newbie, by delving into the black magic of extracting Windows drivers in Linux, let's take a look at the chipset you have. We may be able to get it going without magic. What do you want to bet it's a Ralink?
Actually, I used Windows to extract the drivers ;) Honestly, if the WiFi doesn't work when I stick the card in, I don't bother with anything other than ndiswrapper.

---

### Post by MeeMaw on 2007-05-20
> **bmartin said:**
> Actually, I used Windows to extract the drivers ;) Honestly, if the WiFi doesn't work when I stick the card in, I don't bother with anything other than ndiswrapper.

But if you don't find out what chipset you have, how do you know you can't do something easier than ndiswrapper? That seems like the long way around........

---

### Post by bmartin on 2007-05-20
You mean like... plug it in and it works?

---

### Post by chili555 on 2007-05-21
> Honestly, if the WiFi doesn't work when I stick the card in, I don't bother with anything other than ndiswrapperWell, ndiswrapper may be the best approach in many cases and maybe even in this case, but I have seen, and personally answered, many cases where a simple modprobe or a blacklist entry kicked the kernel module to life without the need for ndiswrapper.

I think ndiswrapper has its own set of problems. Do I need the .inf and .sys both? How do I know? Will the XP file work and the 98 not? How do I know? Trial and error? Google? How do I extract these files? Do I have to have a Windows machine running and move them on a USB key? (I have six computers running at my house, *none* run Windows.) I guess I can use cabextract and unshield but what do I use where? And if I see an .exe, how would I know it really can be opened, maybe, with unzip? After I do all this, will it even work? There are plenty of 'ndiswrapper problem' posts on this forum.

This seems like a poor alternative to finding your chipset and seeing if there is an easier way to get running.

I do not believe one size fits all.

---

### Post by MeeMaw on 2007-05-21
Rule;
Have you got yours working yet?
(since you started this thread in the first place.......)
If not, please post your output to "lspci" and we'll see if we can help you as well.
Looking up Averatec 6100,the specs say it uses D-Link hardware....
and just like many other wireless cards, D-Link uses LOTS of different chipsets.

---

