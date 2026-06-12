---
title: "Secure Wifi at hotspots through my home internet connection"
date: 2008-08-15
forum: Networking &amp; Wireless
---

### Post by Ceephis on 2008-08-15
Friends,

I am hoping to set up some sort of server using my Ubuntu machine which would enable me to utilize its internet connection as a secure connection so that my wi fi browsing from hotspots is encrypted.


Here is my setup.
I have 4 dedicated IP's through my ISP
I have one PC running Ubuntu Linux
I have many different laptops (running different versions of windows) I want to encrypt the Wi Fi traffic from any hotspot on earth through my home internet connection.

Could any body help with suggestions?

Thanks 

Peter

---

### Post by dannyboy79 on 2008-08-15
setup a SSH server on your home ubuntu machine using public/private keypairs with a passphrase. Use puttygen to convert the ssh private key to a putty key, then use putty to ssh into your home ubuntu ssh server. in putty setup a tunnel for all web traffic to go through the tunnel, it will be encrypted. within firefox, tell it to use a SOCKS5 proxy server being the local ip of 127.0.0.0 with the port that the ssh tunnel is using. there's plenty of guides out there, use goggle.

---

### Post by Ceephis on 2008-08-15
Wow Dannyboy,

you could have explained how to remove someones basil ganglia with a leatherman and I probably would have understood it a bit better.

This of course is not because of your description but because of my super noobieness.

Thank you so much for a road map to my goal I will slowly start walking down it to victory.

Your time and super knowledge are greatly appreciated.

Peter

---

### Post by dannyboy79 on 2008-08-15
you can also use the search tool in the ubuntuforums, this question has been answered plenty of times. try different searchs using different words and you'll find what you're looking for.

---

### Post by snakdoc on 2008-08-15
hey Ceephis i would first get the ssh working then try to add the auth key. also you can install ssh to windows command line instead of using putty. thats up to you doesn't make much difference.

---

