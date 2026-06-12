---
title: "Sticky wanted for wireless cards that work out of box"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by dmflad on 2007-02-25
I have a work-supplied Dell D600 with BroadComm card. I got it to work using Ndiswrapper on Dapper Unbuntu and Dapper Xubuntu. Was pain getting to to work but finally card gave in. Then I did upgrade that included kernel and wifi went dead again. Upgraded to Edgy hoping wifi would be easier to achieve but I was wrong.

I found info on various Ubuntu forum pages, they didn't agree with each other, or seemed very old info. I tried surfing laptop sellers who build/support Linux to see if they name wifi cards they use but didn't get very far. 

I no longer want to config distro, Ndiswrapper, drivers, and BroadComm card just so I can sit in comfy chair and work from home.  I am willing to BUY a card for the empty PCcard slot even though its a company laptop IF I can be sure it will work out of the box.

I want one web page with a list of wifi cards that work out of the box under Xubuntu et al and for what version. Maybe there could be links to the wifi card's web page.

I don't want to lose wifi every time I update my OS and then have to stand on my head to get it to work again. 

I continue to believe that gaming and wifi are the two areas were Linux needs to improve before 'the masses' can really get excited about all it can do.

---

### Post by solar george on 2007-02-25
Try looking on the hardware wiki [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

---

### Post by bapoumba on 2007-02-25
This will not be exactly answering your question (sticky thread, I'll check with other staff members), but I use a PCMCIA Asus WL 107G, with a ralink chipset. I's been working out_of_the_box since breezy, both on Ubuntu and Xubuntu. A friend of mine uses KDE, and it's also working okay. WEP encryption is no problem (WPA needs some work, I have not tested it).

edit: thanks for the link, solar george, I was looking for it ;)

---

### Post by Sunflower1970 on 2007-02-25
I bought my PCIMA card based on the above linked list and it doesn't work out of the box. :( I've been struggling for a few days with it. Edgy recognizes the card (and so does Feisty actually, and Dapper) but no matter what I do, I cannot connect. 

If anyone was able to get the D-Link WNA-2330 to work, please let me know what you did. I'm stumped.

---

### Post by solar george on 2007-02-25
> If anyone was able to get the D-Link WNA-2330 to work, please let me know what you did. I'm stumped.

Try opening a new thread.

---

### Post by Sunflower1970 on 2007-02-25
I did. Last night.

---

### Post by dmflad on 2007-03-04
Rebuilt LT last nite. Dell D600, 512k RAM, ASUS WL 107G Wireless Card Bus Adapter. Running Xubuntu 6.10(Edgy) when done.

Installed Xubuntu 6.06 LTS from ISO CD then right way upgraded it to 6.10. Once that was done I rebooted and put in IP addresses for eth0 and ra0, entered essid and network password for ra0. Had put the MAC address for the WL107G card in my wireless router earlier in the day.

The WL107G card just started working. I set it to come up on boot, disconnected eth0 wire and rebooted. All is fine and I am online wirelessly, typing this note, a happy camper once again.

PS. The hardware web page that Solar George pointed to is great if you have a card and want to know if it will work under Ubuntu family. Problem for me was I knew from experience my BroadComm wireless only worked after too much modding and then only if I didn't update kernel. And modding the BroadComm involved lots of conflicting or partially correct instructions. So after months of ups and downs using BroadComm that came with LT I wanted to buy PC wireless card  that worked out of the box.  So I went to the hardware list page for wireless cards and it got real old searching under a manufacturer, reading thru the choice(s), picking one, searching web for availibility and price.  Hence my request for a simple list of wireless cards that just work out of the box and for what member and version of the Ubuntu family.

---

### Post by ftwig on 2007-03-16
I have a similar issue and from experience I know **this question does not have an answe**r;).  

This is because to know if Ubuntu supports a card 'out of the box' you need to know witch chip-set the card uses.  Card makers generally do not make this information easily available and to make things worse they change the chipset without the model number  (and without telling anybody).   So even if you find out that someone has a ChunkyBakon 123x network card which has a  HappyElf xr3 chipset and it works out of the box when you buy yours the chipset has changed and you are, to use a technical term stuffed!

So there are no answers just levels of probability.  **The main thing to find out is how well the card manufacturer suports open source software (i.e. do they publish GPLd drivers)**.  If this is the case you are probably in luck.

Hopefully someone will add info about this to the thread as I really need to get back to work;)

Ben

---

