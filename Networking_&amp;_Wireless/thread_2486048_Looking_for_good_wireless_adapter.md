---
title: "Looking for good wireless adapter"
date: 2023-04-18
forum: Networking &amp; Wireless
---

### Post by dorasmith24 on 2023-04-18
I am using this product, which I found on a review of Ubuntu wireless adapters: **[B]Panda Wireless® PAU0D AC1200 Wireless AC USB Adapter w/Dual Antennas**[/B]

  [https://www.amazon.com/gp/product/B0B2QD6RPX/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0B2QD6RPX/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)   

We have AT&T "broadband" wireless here, 25 Mbps.   Looks useless on the face of it.   My computer is maybe 40 feet from the modem, 2 rooms away.   Adapter is on top of my loft bed post five or so feet high, with arms perpendicular to a direct line to the modem.   

Speed is right when it works but jitter is allover the place.   On my desktop computer the internet connection disappears frequently - and then comes back - in Windows 10.  In Ubuntu, it disappears and you have to restart the computer, and once it disappears, you have to hard restart the computer because of an infinite loop involving the driver.   

But the thing is, my Roku is not having any of these issues, not even with You Tube.   My phone doesn't seem to have them either.

I'm thinking I may need a different adapter.  But when I research and then look at the recommended ones on Amazon, ALL of them report the same issues, especially, intermittent connection, slow speeds, and, the thing stops working after two weeks!   That seems to be true of both USB adapters, with and without antennas, and wireless cards, even with Intel chips.

What would you all recommend?   In wireless adapters for my desktop, that is.

I also tried an internet upgrade, which is not going well. I had it installed last week, and, after one day, the modem can't even connect.  It's Optimum, formerly Suddenlink, and, customer service was in southeast Asia, and said she can see my modem but can't tell if it has contact with the internet (???!!), and the nearest store is in another city 40 miles away.   It seems most service calls cost the caller $80.  Seems like an uber shoddy operation.   Don't know if that's going to ever work or not.   There are no other options.   Mind, I live in a city/ bedroom community adjacent to Austin.   Specifically, Pflugerville.  They ought to have better internet service here, but the whole place seems to be about being dirt cheap.   Our drinking water comes out of the ground, and tastes as if it comes from the ground during a prolonged drought, and the public library has no real history books on its digital extension service, and said that's what they can afford.  Riding around, I don't know if any upper middle class people even live here.  It seems that until 1960, about 50 families lived here.  People are telling me that nothing that now appears to be old, like an elderly HEB (Texas supermarket chain,usually good quality) with little selection, was here when they were growing up.  

Yours,
Dora Smith

---

### Post by chili555 on 2023-04-18
The best resource for USB wireless is here: [https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

In Linux, many connection/disconnection/reconnection issues can be mitigated with careful setup in the wireless access point, usually a wireless router.

Your wireless may be dropping because of power management; that is, the feature where the card partially powers down to save battery power during periods of inactivity and then, ideally, powers back up seamlessly when activity resumes. Let's disable power saving to see if it helps. From the terminal:

    ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
    
Your wireless may be dropping because the channel to which it was connected has suddenly changed.

Please check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I recommend a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. 

Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like myrouter2.4 and myrouter5.

After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:

    ```
sudo iw reg get
```

If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:

    ```
sudo iw reg set IS
```

Of course, substitute your country code if not Iceland. Set it permanently:

    ```
sudo nano /etc/default/crda
```

Change the last line to read:

    ```
REGDOMAIN=IS
```

Proofread carefully, save and close the text editor.    

Is there any improvement?

---

### Post by mIk3_08 on 2023-04-18
> **dorasmith24 said:**
> I am using this product, which I found on a review of Ubuntu wireless adapters: **[B]Panda Wireless® PAU0D AC1200 Wireless AC USB Adapter w/Dual Antennas**[/B]

  [https://www.amazon.com/gp/product/B0B2QD6RPX/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0B2QD6RPX/ref=ppx_yo_dt_b_search_asin_title?ie=UTF8&psc=1)   

We have AT&T "broadband" wireless here, 25 Mbps.   Looks useless on the face of it.   My computer is maybe 40 feet from the modem, 2 rooms away.   Adapter is on top of my loft bed post five or so feet high, with arms perpendicular to a direct line to the modem.   

Speed is right when it works but jitter is allover the place.   On my desktop computer the internet connection disappears frequently - and then comes back - in Windows 10.  In Ubuntu, it disappears and you have to restart the computer, and once it disappears, you have to hard restart the computer because of an infinite loop involving the driver.   

But the thing is, my Roku is not having any of these issues, not even with You Tube.   My phone doesn't seem to have them either.

I'm thinking I may need a different adapter.  But when I research and then look at the recommended ones on Amazon, ALL of them report the same issues, especially, intermittent connection, slow speeds, and, the thing stops working after two weeks!   That seems to be true of both USB adapters, with and without antennas, and wireless cards, even with Intel chips.

What would you all recommend?   In wireless adapters for my desktop, that is.

I also tried an internet upgrade, which is not going well. I had it installed last week, and, after one day, the modem can't even connect.  It's Optimum, formerly Suddenlink, and, customer service was in southeast Asia, and said she can see my modem but can't tell if it has contact with the internet (???!!), and the nearest store is in another city 40 miles away.   It seems most service calls cost the caller $80.  Seems like an uber shoddy operation.   Don't know if that's going to ever work or not.   There are no other options.   Mind, I live in a city/ bedroom community adjacent to Austin.   Specifically, Pflugerville.  They ought to have better internet service here, but the whole place seems to be about being dirt cheap.   Our drinking water comes out of the ground, and tastes as if it comes from the ground during a prolonged drought, and the public library has no real history books on its digital extension service, and said that's what they can afford.  Riding around, I don't know if any upper middle class people even live here.  It seems that until 1960, about 50 families lived here.  People are telling me that nothing that now appears to be old, like an elderly HEB (Texas supermarket chain,usually good quality) with little selection, was here when they were growing up.  

Yours,
Dora Smith
I have been using this adapter for so long now since I have my Ubuntu 16.04 until now, so far I haven't encounter any error.
[URL="https://www.amazon.com/Alfa-Network-New-Alfa-AWUS036ACH-802-11ac-AC1200-867Mbps-PowerBoost-dualband-WiFi-USB-Adapter/dp/B07Q5NRYBP"]Click Here
[/URL]
This  adapter uses the Realtek RTL8812AU chipset with a wide range USB 3.0 wireless adapter it has a large  external antenna on it.
Dual antennas and 2.4 GHz 300 Mbps/5 GHz 867 Mbps – 802.11ac and a b/g/n compatibility and Long-range WiFi adapter.
To install the required drivers. Just run the command below.

```
apt install realtek-rtl88xxau-dkms
```

---

