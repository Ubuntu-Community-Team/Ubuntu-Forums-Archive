---
title: "Wireless Ubuntu Utopia"
date: 2007-03-04
forum: Networking &amp; Wireless
---

### Post by groeswenphil on 2007-03-04
Hi Group,

Just got Ubuntu up and running......but getting nowhere with my Belkin wireless doohdad.
Reading the posts, it appears that it might be made to work, but I've a feeling that it might be better to just buy another that will work.
So, here's the question....I need a USB Wireless doohdad that will work with Dapper.
Any recommendations?
Phil

---

### Post by gradedcheese on 2007-03-04
This page lists some of them (scroll to the USB section)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

Personally, I would use a PCMCIA (laptop) or PCI (desktop) card instead of a USB adapter, they are more likely to be supported.  However you have a few USB options too, though I don't see Belkin listed.  If you want, run the following in a terminal (Applications->Accessories->Terminal) and post the output here:

```

lsusb

```

If we know what chipset your Belkin card has, it would be a good start.  The other way to get this information is to browse through System->Administration->Device Manager

---

### Post by groeswenphil on 2007-03-05
Thanks for helping. Here's the output.

Bus 002 Device 002: ID 0ea0:2168 Ours Technology, Inc. Transcend JetFlash 2.0 / Astone USB Drive
Bus 002 Device 003: ID 050d:705a Belkin Components
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 04a9:220e Canon, Inc. CanoScan N1240U/LiDE 30
Bus 001 Device 001: ID 0000:0000


I've got a scanner and one of those Flash drive pens fitted at the moment.

Actually, I feel rather proud of myself doing that....my first visit to the terminal and I managed to get the output back to my working XP side of my computer.

Thanks,
Phil

---

### Post by gradedcheese on 2007-03-05
hmm... not enough detail there.  Run it again and verify that Belkin is still bus 002 device 003 and then try:

```

sudo lsusb -s 2:3 -v

```

(or substitute 2:3 for whatever bus:id is relevant).  Paste the useful parts of the output (or just type them) here.  If it's a lot of output, you can have the output saved to a file, which you can then copy to your Windows PC:

```

sudo lsusb -s 2:3 -v > ~/usb_info

```

Any output from the command to the left of '>' will go to the text file (specified on the right), in this case /home/_your_user_name_/usb_info

---

### Post by groeswenphil on 2007-03-06
It's OK..............I've fixed it!!!!!

I looked at the back of my new machine last night and I thought, "That"s a strange little hole....looks like an Ethernet Port. By Golly, it is an Ethernet Port. Why don't I pop down and get some network cable and give it a poke." So I did, and now it works.

That will do nicely thanks. I was getting bad vibes from the wireless network card anyway.

Now that I'm up and running do I get an extra bean on my left hand side forum panel?

All the best,
Phil

---

