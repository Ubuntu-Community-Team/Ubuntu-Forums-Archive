---
title: "Bluetooth Modem Connection (MDA Vario II)"
date: 2007-06-19
forum: Networking &amp; Wireless
---

### Post by Sunni on 2007-06-19
Hello. I've got Ubuntu installed and working well, with a dual boot with Win XP.

However, I cannot get my wireless internet via bluetooth to my mobile phone to work.

I have an MDA Vario II on T-Mobile UK.

I've paired the phone using the bt-applet. I then open up a terminal window, and if I issue the following command:

```
sdptool browse mac-address
```

it just says "Browsing..." but doesn't actually display any details. However, if I enter in:

```
sdptool search DUN
```

it DOES show up the DUN information from the phone.

I also have another phone (through which I cannot use the internet). I paired that, and when I issued the

```
sdptool browse mac-address
```

command, it shows all the details of that particular phone absolutely fine. The command just doesnt work with my MDA Vario II.

Anyway, when I used the sdptool search DUN command on my MDA, it came back saying the rfcomm channel is 4. I entered this, and the phone mac-address into */etc/bluetooth/rfcomm.conf*

I then edited */etc/wvdial.conf* with the relevant details.

If I then issue the

```
wvdial [connection]
``` command, it just doesn't connect. It says connection reset by peer.

It all seems as though it's the phone itself causing the problems since my other phone "browsed" fine with the sdptool browse. However, I have the MDA Vario II working fine in Windows XP as a bluetooth modem, and I've also seen guides on the Internet where they explain using the MDA Vario II, so I'm sure it must work.

Can anyone offer any assistance at all? Is there anything I must do on my phone?

Thanks.

---

### Post by Sunni on 2007-06-20
Bump...

---

