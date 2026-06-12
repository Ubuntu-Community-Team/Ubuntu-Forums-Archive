---
title: "WiFi Indicator Turns To Question Mark - But Still Works?"
date: 2020-04-20
forum: Networking &amp; Wireless
---

### Post by inundated on 2020-04-20
The WiFi indicator up top (panel? what do you call it in Ubuntu? I'm used to Linux Mint) turns into a question mark, but the WiFi connection continues to work.

If you drill down into settings, the network still shows connected without the ?.

Not a huge deal, of course, as the connection still works. I'm just wondering what is going on.

[ATTACH=CONFIG]285565[/ATTACH]

This is in 20.04, though I have no idea if previous versions of Ubuntu had this problem.

---

### Post by QIII on 2020-04-20
Moved to Networking & Wireless.

We're close enough to release to just put this in the general sub-forums.

---

### Post by inundated on 2020-04-20
Thank you for putting it in the right place! I was debating putting it here, but thought I still needed to put it there since the official release isn't until later this week :)

Still, as I assume this bug (if it is one) won't be squashed until after release...good move.

---

### Post by kurt18947 on 2020-04-20
I see that fairly often. If you turn WiFi off then back on it'll probably turn into the symbol we expect for WiFi. I don't know why it comes up with the question mark initially.

---

### Post by inundated on 2020-04-20
> **kurt18947 said:**
> I see that fairly often. If you turn WiFi off then back on it'll probably turn into the symbol we expect for WiFi. I don't know why it comes up with the question mark initially.
It usually STARTS with the right symbol, but eventually changes (all by itself) to the question mark.

As noted, it does not affect the connection at all, and if you dig into WiFi settings, the question mark is not there and there is a checkmark for the used network.

---

### Post by inundated on 2020-04-20
For what it's worth, the question mark thing doesn't seem to happen when I am not logged into my VPN (PIA).

---

### Post by maestrobwh1 on 2020-04-21
This happened in 18.04 for me

---

### Post by kurt18947 on 2020-04-22
> **inundated said:**
> It usually STARTS with the right symbol, but eventually changes (all by itself) to the question mark.

As noted, it does not affect the connection at all, and if you dig into WiFi settings, the question mark is not there and there is a checkmark for the used network.

I see the opposite sequence, question mark when first connecting. Disconnect/reconnect and no more question mark for me. One of the many mysteries of network-manager? And yes, I see this in 18.04 as well as 20.04.

---

### Post by inundated on 2020-04-24
The question mark only stays on if I'm using the VPN (PIA). So that's probably a factor in this, at least in my situation.

---

### Post by super-jugaad on 2020-04-25
> **kurt18947 said:**
> I see the opposite sequence, question mark when first connecting. Disconnect/reconnect and no more question mark for me. One of the many mysteries of network-manager? And yes, I see this in 18.04 as well as 20.04.

I have experienced this sequence as well. I, however, just turn off the module and then it back on {top right hand corner, drop down menu} thereafter the question mark disappears. Mine has been behaving like this since 14.04 and usually took a few long seconds to disappear. But now on 20.04 it disappears far quicker, practically unnoticeable. Used to slow connection down in 14.04 and 16.04, but since 18.04 connection still works, dependant on our superfast connectivity in RSA {snigger...snigger}.

---

