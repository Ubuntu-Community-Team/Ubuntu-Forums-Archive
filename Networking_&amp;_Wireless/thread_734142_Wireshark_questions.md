---
title: "Wireshark questions"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by cowboy1900 on 2008-03-24
(This isn't Ubuntu-specific but I don't know of any Wireshark forums)

I'm playing with Wireshark on my home Wi-Fi.  The network is using 64-bit WEP and I obviously know the WEP key.  Two problems:

1)  When my laptop running Wireshark is connected to the network I can see packets being captured in Wireshark but it seems to only be capturing packets received by the other computer in my network.  It doesn't seem to show any outgoing packets from that computer.  Why would that be?  I have no filters, etc.

2)  When the laptop is not connected to the network I can see packets from my network and others in the area but of cource all the packets are encrypted.  I tried entering the WEP key in preferences but it makes no difference.  I tried both the delimited format and non-delimiited format for the key.  Why doesn't it work?

Thanks in advance.

---

### Post by SpaceTeddy on 2008-03-25
1.) when you enter listening mode on a device with wireshark, this device will unconfigure itself (get assigned the ip 0.0.0.0) and go into promiscious mode (i.e. read ANYTHING that comes in. 
So, in other words, as long as your are listening, you cannot use the network card for any real traffic.

2.) the encryption/decryption is not done in paket level, but rather on driver/hardware ( think just above hardware level - but i am not sure). however - it is done before the pakets are acctually handed to wireshark. Therefore, you will only see the encrypted pakets. As soon as you configure the wireless extension on a card, it will take the key and use it to automaticially decrypt the pakets before they reach wireshark. the card then will also only accept pakets from that network and blend all the others out. 
Since the wireless extension is unrelated to the network configuration, this can acctually work. However, i do not know how to apply keys to pakets after they have passed to wireshark.

i would also like to point out that sniffing pakets from others i something that no one should do. if you sniff yourself, that is fine, but respect the privacy of others...

hope it helps...

---

