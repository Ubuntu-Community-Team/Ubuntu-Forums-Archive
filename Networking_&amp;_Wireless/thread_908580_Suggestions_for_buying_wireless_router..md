---
title: "Suggestions for buying wireless router."
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by KindredCharles on 2008-09-02
Wondering about which router to buy and if it's worth it to mess around with third party firmware. Also if anyone has experience with different ones and would suggest one. Will I get a lot better features if I switch to a third party firmware? 

I'd like something thats 802.11n with wpa2, and the ability to extend an already existing wireless network so it doesn't need to plug directly into ethernet itself.

Not looking for someone to do my shopping for me but if you have suggestions I'd like to hear them.

Thanks for reading.

---

### Post by NadmanET on 2008-09-02
If your willing to pay for it you simply cannot beat Cisco.  Get yourself an ASA 5505 and Aironet 1130AG for your access point.  The 1130AG is a good balance of performance and price.  It has great range however the antennas are built in so no crazy FCC violating, amplified, mega antennas can be used.  Unless you are streaming HD video there really aren't many drivers for 802.11n.  That said, if you do want 802.11n and don't mind paying for it there is the Aironet 1250 that is Draft 2.0 compliant.  That one you *can* put big antennas on to share your connection with your buddy in the next county.  Of the two the 1250 definitely looks way more badass.

In this setup your ASA would be your router.  It would also be a stateful deep packet inspection balls to the walls firewall that can terminate not only IPSEC VPN but SSL VPN tunnels as well.  That's geek for this box rules.  Actually it means that it will protect your network from intruders as well as allow you to remotely connect to your network from anywhere that allows SSL traffic through the firewall (virtually everywhere.)  It has all the features that you will ever need but one of the biggest advantages?  It doesn't crash.  None of this unplugging and counting to 30 crap.  Well, your cable modem might still crash once in a while but that is very rare (for me at least.)  It's just nice to have a network that doesn't go down once a week or once a month.  It just works.  Set it up and you are done.

Finally you can get an UPS and keep surfing from your laptop when the power goes out.  Think of the possibilities...

Here's some links for ya!

[[COLOR="Blue"]ASA5505[/COLOR]]("http://www.cisco.com/en/US/products/ps6120/prod_models_comparison.html") <- This will show just the specs. Go [[COLOR="Blue"]here[/COLOR]]("http://www.cisco.com/en/US/prod/collateral/vpndevc/ps6032/ps6094/ps6120/product_data_sheet0900aecd802930c5.html") for more information, however that is for the whole ASA series.
[[COLOR="Blue"]ASA5505 Video Data Sheet[/COLOR]]("http://www.cisco.com/en/US/prod/collateral/vpndevc/ps6032/ps6094/ps6120/product_data_sheet0900aecd80601ddf.html")
[[COLOR="Blue"]Aironet 1250[/COLOR]]("http://www.cisco.com/en/US/products/ps8382/index.html")
[[COLOR="Blue"]Aironet 1130AG[/COLOR]]("http://www.cisco.com/en/US/products/ps6087/index.html")


Man, Cisco should start paying me.  Good luck!

---

