---
title: "Wireless on Lenovo Yoga 2"
date: 2014-06-25
forum: Networking &amp; Wireless
---

### Post by amanda on 2014-06-25
I have Ubuntu 14.04 running on a Lenovo Yoga 2, and the internet is super wonky. When I first set the machine up, I was having trouble connecting at all. A friend helped me troubleshoot that (I need to get details) and now I can connect but I get kicked off of connections quickly and often, and my connection is really, really slow. Like speeds of 1Mb/s slow. On a network that works fine for other Ubuntu users. 

Here's a ton of detail about my machine: 

[http://paste.debian.net/106728](http://paste.debian.net/106728)

How do I troubleshoot the incredible slowness? Why do I keep getting kicked off the network?

[COLOR=#000000]I tried running `sudo modprobe -r iwlwifi && sudo modprobe iwlwifi 11n_disable=1` per a suggestion on [/COLOR][http://askubuntu.com/questions/38792...tion-on-lenovo]("http://askubuntu.com/questions/387922/slow-wireless-connection-on-lenovo")[COLOR=#000000] and now I just can't connect at all.[/COLOR]

---

### Post by varunendra on 2014-06-26
First and foremost, if you have admin access to the router/access-point, please change the encryption type to pure **WPA2-PSK with AES (CCMP)**. Currently it is WPA/WPA2 mixed mode with TKIP. This is a common recommendation for all modern hardware regardless of the problem and possible solution (this change itself can be the solution in many cases).

Apart from that, also try changing the channel (also to be done in the router) to 1 or 11. Reboot the router after saving the changes. 

Oh, and if not a problem, please also change the SSID of the access-point to something that contains only alphanumeric characters and hyphen or underscore, no spaces, no other special characters).

If this doesn't help, or if you don't have admin access to the router at all so you can try this, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by mikewhatever on 2014-06-27
Same as this -> [http://ubuntuforums.org/showthread.php?t=2218274](http://ubuntuforums.org/showthread.php?t=2218274). Looks like another card by Itel ...

---

