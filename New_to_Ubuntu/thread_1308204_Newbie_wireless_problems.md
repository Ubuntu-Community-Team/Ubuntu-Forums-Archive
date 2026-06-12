---
title: "Newbie wireless problems"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Stickman123 on 2009-10-31
Hello

This is a repost as I posted this in the Wireless Network area and got no responses in almost a week. I hope to have better results here.

I am very new to Linux and Ubuntu, so please forgive my total lack of knowledge in this area. I am going to try to learn as quickly as I can.

I just installed the Ubuntu (9.04) onto a hard drive as the sole OS (I let it format the disc as the only partition). It installed successfully and looks beautiful, I can't wait to start using it - but at the moment, I can't get online.

My wireless card is a Netgear WG311v2 - I found it on the ['Supported wireless cards' sticky]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear") in this forum, with 2 entries. Apparently I need to use a driver called ACX111 - I looked this up and I just can't understand what this is, if its included in my installation of Ubuntu and how to get my card to use it. And even then, what program will be searching for wireless networks etc?

The standard 'Network Manager' is not even giving me the option to scan for wireless networks. I don't know how to ask Ubuntu what hardware it has detected, so I don't even know if it realises I have a wireless card. I was expecting a Windows-style interface so that as soon as the OS was installed, it would be able to search for local WiFi and away we go.

If anybody could help with very basic-level advice I would hugely appreciate it. I'm happy to learn to run commands etc, but I just need to be told what to run.

Many, many thanks in advance.


P.S. Here are the entries from the sticky that I found:

  **Model** 
    **Chipset** 
    **Driver** 
    **Supports network install?** 
    **Supported in installed system?** 
    **Works "out of the box"** 
    **Comments** 
    **Last Updated** 

 WG311v2 
    Texas Instruments ACX 111 
    ? 
    ? 
    Yes 
    Yes 
    Worked out of the box with Breezy. WEP now works 100%! 
    

    WG311v2 
    Texas Instruments ACX 111 
    acx 
    ? 
    Yes 
    No 
    Did not work with Jaunty. Not compatible with [NetworkManager]("https://help.ubuntu.com/community/NetworkManager"). See [http://acx100.sourceforge.net/wiki/D...on_list/Ubuntu]("http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu") 
    2009-10-14

---

### Post by TheLions on 2009-10-31
you'll need ACX111 driver located here: [http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

also hook here:[http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

---

