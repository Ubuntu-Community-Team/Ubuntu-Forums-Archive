---
title: "choked torrents"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by nnjond on 2009-04-01
Hi,

Ive just switched isp and it seems my BitTorents are being choked off while i'm using Transmission. Is there an "incrypted" client or something I can use to solve this problem or should I look for a better isp?

Thanks

---

### Post by mkvnmtr on 2009-04-01
I believe Transmission has the option to use random ports. You might have better luck if you enable that option.

---

### Post by llamabr on 2009-04-01
I think the one I use is called deluge.  It has lots of features, including proxy support.  And the one you're looking for, too, probably.

And yes, you should look into an isp that does what you want.

---

### Post by nnjond on 2009-04-01
Thanks for your interest. Ive found the Proxy tab in deluge but i don't understand which options I should take?

---

### Post by ramjet_1953 on 2009-04-01
I'm not sure about the packages previously mentioned, as I have never used them, but [COLOR="Blue"]Azurus[/COLOR] allows you to use encrypted transmission and to change the port used.

When running Azurus, navigate to [COLOR="Blue"]Tools>Options>Connection>Transport Encryption[/COLOR]

This allows you to change the encryption options.

Regards,
Roger :cool:

---

### Post by lovinglinux on 2009-04-02
> **nnjond said:**
> Thanks for your interest. Ive found the Proxy tab in deluge but i don't understand which options I should take?

I don't think is a good idea to use proxy and it won't help with the ISP throttling. It would help if your ISP or local network block the tracker IP, but this is not the case.

First thing you should do is to set Deluge to use a port that is not a common torrent port, because some ISPs throttles any data transfer on the torrent range (6881-6889). You can put a single port value in the "From" and "To" options or a range. Please remember that you need to make sure the router is forwarding the selected port to your machine, so if you use a range and the random port option, then you will probably want to use UPnP, so the router port forwarding can be set automatically by the client. But the easiest way is to select a single port value, untick the random port option and manually forward the selected port on the router. The recommended port range is from 49152 to 65535.

The second thing is to set encryption. Some  ISPs throttles torrent connections based on the packets headers. If you use encryption, then the ISP can no longer determine what type of data is being transfered and thus cannot throttle.

Select "Full" encryption for inbound and outbound options, then "Full Stream" in the level option and tick the "Prefer to encrypt the entire stream".

Some companies use advanced throttling technologies that can't be bypassed by the procedures above. If this is the case, then you might want to change ISP.

---

