---
title: "Wireless so close, but yet so far."
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by dcast on 2007-11-13
My wireless is almost working... I just installed 7.10, and discovered that my card should be supported with madwifi now, while i was using NDISwrapper in 6.06. The card appears in Network manager, however it says roaming mode is enabled. When this is disabled, it sometimes sees networks, others it will show just one or two, and they will be shown at full signal, wifi-radar seems to do the same. It will not let me connect to my network in the rare times it is shown, although it will say it is connected in Network manager. My card is a D-Link DWA 642, with an Atheros ar5416 chipset. Does anyone have any ideas?

Iwconfig outputs:
wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:822  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I am not sure what the problem is, any help is appreciated. Thanks in advance, Dcast.

---

### Post by SpiritIsReality on 2007-11-14
howdy
could you have a look at these and if they are no help, you can change the time to include more links.
[http://www.google.ca/search?as_q=Atheros+ar5416&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images](http://www.google.ca/search?as_q=Atheros+ar5416&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=m3&as_occt=any&as_dt=i&as_sitesearch=ubuntuforums.org&as_rights=&safe=images)

3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)
trails

---

### Post by dcast on 2007-11-14
Thanks, but they didn't give me too much help. Any other ideas?

---

### Post by SpiritIsReality on 2007-11-14
yep
if you haven't tried this yet, I think it's worth a shot.
I'm sorry about those other links not being much help.
because of your preceding post, i checked to see if I could do a wireless setup and I think the troubleshooting page would help me the most. If you have already tried it, or if you try it and have questions you know the drill, post back.
trails
just about forgot to give you the link, well it's on the wifi docs page.
[http://help.ubuntu.com/community/WifiDocs](http://help.ubuntu.com/community/WifiDocs)
well no it's not, but cruise down that page and see if you can spot your card.
I didn't realize all that was on that page, I guess a guy has to check the size of the slider bar on the right hand of firefox to see how long the things are! Someone ought to put the troubleshooter link on that page don't you think? There is a wifitroubleshooter there.
There you go, that's how I found it. ok give it a shot. all the best. If you have trouble, we can work thru it together., but I'm not much good at wireless. I've only installed two cards and they were a bit of a stretch for me. ndiswrapper. but if you want to try it this way. or just go for the good stuff. YouAreInTheSaddle. giddyup

---

### Post by SpiritIsReality on 2007-11-14
if stchman gets an lspci here, it'll be worth watchin. go to that site and click on thread tools, and click on subscribe to this thread. [http://ubuntuforums.org/showthread.php?t=612496&page=2](http://ubuntuforums.org/showthread.php?t=612496&page=2)

see post #50 here [http://ubuntuforums.org/showthread.php?t=484846&page=5](http://ubuntuforums.org/showthread.php?t=484846&page=5)
trails

---

### Post by dcast on 2007-11-14
Thanks for all of your help SpiritIsReality, I think I have had it up to here *points to neck* with this card, and I am going to go out and buy one that has native support in Ubuntu if I can get a good deal somewhere.

---

### Post by SpiritIsReality on 2007-11-15
> **dcast said:**
> Thanks for all of your help SpiritIsReality, I think I have had it up to here *points to neck* with this card, and I am going to go out and buy one that has native support in Ubuntu if I can get a good deal somewhere.

That's the Spirit!!! You'll go far pardner!!!
I wasn't any help at all.?
could you please post a new thread asking for what you want. ?
hopefully someone will know where there's a good deal.
google.com
price comparisons "the name of the card you think you might want"  (retail OR wholesale) 
might work? sorry I couldn't be more help.
for example this is a search for the card I use in a toshiba laptop old as the hills. toshiba satellite 2140xcds
[http://www.google.ca/search?as_q=computer+parts+wholesale&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=image=](http://www.google.ca/search?as_q=computer+parts+wholesale&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=image=)
[http://www.google.ca/search?hl=en&q=price+comparisons+wpc54gs+%28retail+OR+wholesale%29+&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=price+comparisons+wpc54gs+%28retail+OR+wholesale%29+&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=pricecanada.com&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=pricecanada.com&btnG=Google+Search&meta=)
hell christmas is comin'. what's your address.It'd take me until next month to come up with some scratch. I'd love to help you out with say a sawbuck or two.  "a sawbuck or two" he hears.
[http://www.google.ca/search?hl=en&q=define%3Asawbuck&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=define%3Asawbuck&btnG=Google+Search&meta=)
trails

---

