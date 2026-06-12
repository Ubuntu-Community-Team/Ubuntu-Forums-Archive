---
title: "Belkin F5D7001 Wireless Card"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by chill_guy on 2007-11-12
Hi there All,

I know that you guys nearly get asked the same problems and I have tried not to ask about this network card by researching a lot around Ubuntu.

This is what I did:

I have installed Ndiswrapper by Wiki on ubuntu by these commands:
  sudo dpkg -i ndiswrapper-common.deb
  sudo dpkg -i ndiswrapper-utils.deb
  sudo dpkg -i --force-depends ndisgtk.deb

Which all worked and all was successful.

Now I extracted my belkin drivers file on Desktop ./drivers.

So I did ndiswrapper -i bcmwl5.inf which also worked and all successful.

Now I went to ndiswrapper -i and said:
```
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
```

I thought that meant successful but I'm not really sure. But anyway, I went to my Wireless Management and wrote in my SSID and WAP password. It just keeps saying "Connecting to "John's Wireless" and does nothing :(.

I'm I doing something wrong?

Once again I'm sorry to bother you guys when you probly keep answering these sort of questions all the time.

Many Thanks.

Best Regards,
John

---

