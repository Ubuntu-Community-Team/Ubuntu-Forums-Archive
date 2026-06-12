---
title: "Google Cloud-Ubuntu-Openvpn-No Internet Access"
date: 2020-12-21
forum: Networking &amp; Wireless
---

### Post by k44n on 2020-12-21
Hello. I'm a beginner Linux user. My problem is simply, whenever I disconnect from Openvpn GUI (I use Windows 10), the next time I try to connect is doesn't work. It says " no Internet access ". But like I said on the first connect there is no problem.

So with that short information let me try to explain what I been doing. First I create Ubuntu Vps machine on Google Cloud. Then I connect that Vps machine with Putty because on Google Cloud, the SSH button doesn't work in my browser (Firefox). 

So I connect to Vps with Puppy. First I upgrade, update Ubuntu then I download and install Openvpn. On the settings I pick UDP, port 1194, Google Dns and create a new client name. After all that there is an Openvpn file that just created.

I important this .ovpn file to OpenVPN GUI then I push to connect button and there is no problem, I can access and surf around Internet with that Openvpn file, client. Server works fine. But whenever I disconnect from the OpenVPN GUI, on the next time my I still connect but it says No Internet Access on the Vpn Status and there is no connection at all.

So with that information what may cause this problem? I can upload the config files, logs if there will be need it.

---

