---
title: "Linksys/Broadcom 4306 PCMCIA Failure"
date: 2006-12-01
forum: Networking &amp; Wireless
---

### Post by Peter The Plumber on 2006-12-01
Hi Everyone,
  I wanted to drop a note and thank all of you who wrote the excellent how-to's, wiki's, etc outlining the installation of a Broadcom 4306 based wireless card. Thanks to all of you I was able to get it working. Sadly not automatically, I still needed to issue 'dhclient eth1' to get an ip address. I've decided to make a point in my own small way and do away with my existing card and buy a fully supported one from a different manufacturer. All this to get an old machine running for my son! :-k At least I'll know to check next time I buy a new machine!
  I've now got two Thinkpads; a T30 and a T22; running 6.06 and 6.10 respectively. So, alls well that ends well.

Regards,

Peter

---

### Post by wieman01 on 2006-12-01
Hello Peter, 

Do you still need our help? Buying a new card may not be necessary, however, I understand that this is frustrating. Have you tried the solution posted on the other thread? Writing a small script for 'dhclient eth1' is very simple... This is what Chris has suggested:

Open this file (from terminal):
> sudo gedit /etc/rc.local
Then add this line (at the bottom of the file):
> dhclient eth1
Then restart the computer.

If this does not work, I have another solution for you. So don't give up yet. It's not about the old card & saving a few bucks, this is about pride. :-)

---

### Post by Peter The Plumber on 2006-12-02
> **wieman01 said:**
> Hello Peter, 

Do you still need our help? Buying a new card may not be necessary, however, I understand that this is frustrating. Have you tried the solution posted on the other thread? Writing a small script for 'dhclient eth1' is very simple... This is what Chris has suggested:

<snip>

If this does not work, I have another solution for you. So don't give up yet. It's not about the old card & saving a few bucks, this is about pride. :-)

Hi Everyone,
  Thank you very much for following up with me. I'm sure I'll still need help, just not with this issue. I did get the scripts Chris wrote, thank you. I'm sorry I didn't use them, I hope they will be of use to someone else.
  Thank you all for your efforts, but in the end it was my desire to send a small message. Yes; it is about pride; but for me it's about not using a product whose manufacturer makes it difficult to use and all about giving my money to a company who makes it it easy to use their product. While it's not the time of year for me to make such statements; because I am a plumber and things get slow in the fall; I chose to anyway. I'm sure the loss of $60 bucks won't break Linksys and it sure won't make D-Link rich. But it makes life easier for me to set up my old laptop for use by my young son, who is looking forward to using his new toy to fight Pokemon online. I'm looking forward to infecting him with the knowledge that there are options to MS and they aren't painful. Please don't take this excerpt as an insult to your efforts to make things work, it's not meant as such. Thank you again, I look forward to hearing from you.
  For the record, I got a D-Link pcmcia card. Remember, this is an old machine, no mini pci cards here! The m/n is WNA-2330, s/n F30W 162011595, h/w version A1, f/w version 1.0, UPC code 7 90069 28850 0. I selected it using the guide here <https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported>, and no it wasn't my first choice. I do look at Belkin and D-link with a new respect. I don't know if it does indeed contain the Atheros chip as stated on the above page. I do know that all I did was unwrap it and plug it in. That's it. That's how it should be, or so I think ;-). It's reported here <https://help.ubuntu.com/community/WifiDocs/WiFiHowTo> that cards with Orinoko, Prism2 or Atheros chipsets do work out of the box so I'm inclined to think it does. If need be I might be convinced to pry open the case.

Regards,

Peter

---

### Post by wieman01 on 2006-12-02
Thanks for your honest post. I share the same view, if a product does not work out of the box (and I usually apply this to all "commercial" aspects of life), I return it immediately & file a customer complaint. Some companies deal with it professionally, some don't. Linksys is one of the worst as far as customer complaints & technical support is concerned. So again I think you have a point in avoiding their products, however, I personally like their hardware very much.

So generally you always have to put your own time into balance against the money you are willing to spend. If you think your time is more valuable (e.g. because you'd rather spend time with your family, etc.) then you know what to do. I have a similar experience after installing Ubuntu whereby I could not get my wireless keyboard & mouse to work with KDE. I just started behaving very radonmly after a few minutes of usage. So guess what I did? I smashed both keyboard & mouse and got myself a new wired set which I am happy with. Not that I suggest that others should do the same thing, all I am saying is that your point is very valid. If hardware manufacturers can afford to ignore one part of their potential customer base, so be it. Why would I want to support them? There are other vendors out there who do a way better job. 

This post/thread is vastly off-topic but I thought I'd share with you. Hope you have fun with your new device. Let us know if you need any kind of help (which I doubt now). :-)

---

### Post by Peter The Plumber on 2006-12-02
It may be off topic but then it's *my* thread so it's okay, right? I did add tags to reflect that. :mrgreen: I did smash the offending part. I thought afterward I could have done any number of greater things with it, bummer. I do know about doing things as a matter of pride though, in my line of work it's usually antique brass fixtures. 

Best Regards,

Peter

---

