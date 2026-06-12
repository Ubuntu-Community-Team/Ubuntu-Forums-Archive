---
title: "Unable to connect to localhost from windows computer into xubuntu 14.04"
date: 2015-10-22
forum: Networking &amp; Wireless
---

### Post by bhart3 on 2015-10-22
Hello!

I am a newby with linux and recently installed xubuntu 14.04 on an old laptop. I would like to create a network on which I can drop all my docs, movies and music from different devices. 
After some research, owncloud was my choice.

I followed the clear guide to install owncloud on ubuntu 14.04 from bsdtutorial.org/ubuntu-linux/owncloud-server.

The only change I made was to configure my router, and not ubuntu, to give me a static IP address.

After installation of owncloud and SSL, I tried to login from another laptop (windows) and typed [https://localhost/owncloud](https://localhost/owncloud). It says it cannot connect to the server. The same for the owncloud client on windows.

Could someone please help me? See attachment for full info on connections.

Thx!

[ATTACH]265092[/ATTACH]

---

### Post by Lars Noodén on 2015-10-22
The convention is that **localhost** stands for the loopback address of the same machine you are on.  For IPv4 that would be 127.0.01, and for IPv6 that would be ::1

The attachment shows some networking information which suggests that the address 192.168.2.10 will reach your machine over the LAN.  If you are using DHCP to get your LAN addresses, then that address might change, but usually the router can be configured to give out the same address to a machine or two.

---

### Post by bhart3 on 2015-10-22
Thank you Lars. On the second windows run laptop I tried to connect with [https://192.168.2.10/owncloud](https://192.168.2.10/owncloud) but failed. Both computers are wired to the same router and I configured the router to always give the ubuntu computer 192.168.2.10 as IP. 
Is this helpful additional information?

---

### Post by Lars Noodén on 2015-10-22
Did you turn on UFW?   If so, you would need to open ports 80 and 443 to let in HTTP and HTTPS.

---

### Post by bhart3 on 2015-10-22
Originally I had not. Now I tried but it gave the same problem. On the windows computer it looks like it can connect through https, because it ask on a owncloud kind of window if I trust 192.168.2.10. After approving this it says unable to connect to server.

---

### Post by Lars Noodén on 2015-10-22
From the Ubuntu machine you said you can connect to [https://localhost/owncloud](https://localhost/owncloud)   What about  [https://192.168.2.10/owncloud](https://192.168.2.10/owncloud) on the Ubuntu machine?  

Is there another non-Windows machine you can check from on the LAN?

---

### Post by bhart3 on 2015-10-22
It does not work either when I try it with [https://192.168.2.10/owncloud](https://192.168.2.10/owncloud) on the ubuntu.

I get the message:

S[B][I]ecure Connection Failed

An error occurred during a connection to localhost. SSL received a record that exceeded the maximum permissible length. (Error code: ssl_error_rx_record_too_long)

    The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.
    Please contact the website owners to inform them of this problem.

[/I][/B]Unfortunately I dont have other non windows machines. exept iphone

---

### Post by Lars Noodén on 2015-10-22
Ok.  That message is enough to see that something is wrong with HTTPS.  Which guide did you follow?

---

### Post by bhart3 on 2015-10-22
bsdtutorial.org/ubuntu-linux/owncloud-server.

What guide can you recommend me? Maybe a possibility is to reconfigure the ssl certificate. Do I need to remove what I installed before?

---

### Post by Lars Noodén on 2015-10-23
The guide looks clear.  There was probably an error in following the steps regarding creating the certificate or pointing the web server at the created certificate.

---

### Post by bhart3 on 2015-10-23
So I will run the guide again. Do I need to remove the files and certificate I already made?

---

