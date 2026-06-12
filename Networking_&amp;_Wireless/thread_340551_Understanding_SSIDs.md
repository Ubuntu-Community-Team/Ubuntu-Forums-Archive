---
title: "Understanding SSIDs"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by happyhacker on 2007-01-17
Need a bit of advice setting up my network.

I have looked at my network and I can see the Ubuntu (6.06) PC from the BT Home hub admin screen (acting as DHCP) ssid is 'BTHub77D' and my ubuntu linux PC (on the other side of a dg834g set up as no DHCP) is set up for ssid 'susey'. My XP Pro PC connected direct to the BT hub is also 'susey' (part of the network before the Hub was introduced).

The XP Pro PC connects through the BT Hub to connect to the DG834g and thence the Ubuntu.

Should these all be the same ssid as I am a little bit wary of changing th BT setup?

Will they work as they are?

---

### Post by lukew on 2007-01-17
> **cantthinkofanickname said:**
> Need a bit of advice setting up my network.

I have looked at my network and I can see the Ubuntu (6.06) PC from the BT Home hub admin screen (acting as DHCP) ssid is 'BTHub77D' and my ubuntu linux PC (on the other side of a dg834g set up as no DHCP) is set up for ssid 'susey'. My XP Pro PC connected direct to the BT hub is also 'susey' (part of the network before the Hub was introduced).

The XP Pro PC connects through the BT Hub to connect to the DG834g and thence the Ubuntu.

Should these all be the same ssid as I am a little bit wary of changing th BT setup?

Will they work as they are?

I am a little confused to the wording of your note; perhaps you could repharse your question. Basically from what i can gather is that you are asking if when connecting to an a wireless network should all clients use the same ssid as the wifi router? That is a definite yes. The ssid is the name of the network; have a different ssid and your client will not even try and connect to your network.

Luke

---

### Post by spd106 on 2007-01-17
As I understand it you have a network with two Access Points, each with their own separate SSID.

Depending on the area you are trying to cover and number of users this is probably overkill. An AP should easily cover 60-100m range with ~30 users, so unless you have a long garden, or some significant dead spots/shielding problems you won't need two APs. Continuing to have two AP close together will cause interference and degrade performance, unless you put them on separate channels.

The only other situation is if you need to have two separate networks for security purposes or ease of management. I this case you won't want to allow communication directly between PCs connected to different APs. For example you and your neighbour both share an Internet connection, but you both want a private network.

If you want to keep both of the APs and have each client connect to the nearest one, then you put them on the same SSID with the same encryption type/keys. Everything else should be automatic.

---

