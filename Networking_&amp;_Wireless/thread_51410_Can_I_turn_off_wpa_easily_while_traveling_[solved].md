---
title: "Can I turn off wpa easily while traveling [solved]"
date: 2005-07-23
forum: Networking &amp; Wireless
---

### Post by matthew on 2005-07-23
I use wpa on my home network. When I travel I would like to be able to connect using a public network like at the airport or Starbucks or a hotel. I can confirm the existence of these networks, but I can't seem to connect. I think my wpa_supplicant is running and trying to get an encrypted connection with these open, unsecured, public networks.

Is there an easy way to turn off wpa and then turn it back on easily when I get home?? If so, that will eliminate yet another reason I keep Windows on my hard drive and occasionally boot into it.

---

### Post by luca_linux on 2005-07-27
Yes, just kill the process related to wpa_supplicant. And then run the command mentioned in the HowTo: "sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd".
Anyway, you shouldn't have problems, since wpa_supplicant just works with the networks added to wpa_supplicant.conf

---

### Post by matthew on 2005-07-27
Thank you. Next time I'm out I'll try it out, but it seems so obvious I'm srue I'll have no problem.

---

### Post by matthew on 2005-07-30
> Anyway, you shouldn't have problems, since wpa_supplicant just works with the networks added to wpa_supplicant.conf 
I've been thinking about this. Does this mean I could put more than one network into my wpa_supplicant.conf file and have my computer automatically connect to either when I am in range--for example one network for home and another for work? Something like this:
> network={
       ssid="home"
       proto=WPA
       scan_ssid=1
       key_mgmt=WPA-PSK
       psk="reallygoodpassphrase"
}
network={
       ssid="work"
       proto=WPA
       scan_ssid=1
       key_mgmt=WPA-PSK
       psk="anothergoodpassphrase"
}
That would be awesome! I have no use for it right now, but I bet I could find a use.

Also, did I understand your quote above correctly to mean that my wpa_supplicant.conf should be ignored if the network(s) mentioned are not in range and therefore I should be able to connect to any unsecured network available?

Thanks!!

---

### Post by luca_linux on 2005-07-31
Yes, it's handy, isn't it? :smile:

---

### Post by matthew on 2005-07-31
That is very cool. You know I'll find ways to use this. Thanks for the insight.

---

