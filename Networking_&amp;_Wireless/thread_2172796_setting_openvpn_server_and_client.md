---
title: "setting openvpn server and client"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by rclever on 2013-09-06
GREETINGS all!
I am starting use Linux month ago. Please help me to understand.
there are 2 servers running on ubuntu server 12.04. first connected via openvpn to the second server. Necessary start the openvpn server, the second server in the fall. How is it implemented?
P.S. If I place two config on the first server, it automatically starts both the config file.

Thanks a lot.

---

### Post by SeijiSensei on 2013-09-06
If both machines are configured to start the network at boot, the norm for servers, then install OpenVPN on both machines with a [shared static key]("http://openvpn.net/shared.html").  On the client add the "remote name.of.the.server" directive to the configuration.  When it boots it will try to the connect to the server and establish the connection.  If it cannot do so, it will wait a while and try again.

---

### Post by rclever on 2013-09-06
Thank you, SeijiSensei, for your answer. 
the first, sorry for my English. 
I, apparently, badly laid out the problem. I'll try again: 
there are two iron server running ubuntu (to be specific, server A and server B). Both set openvpn. A server - core, Server B - backup. And as long as the server is running, Server B connects to it as a client openvpn (for exchange of service information), **as soon as Server A drops, Server B has to stop openvpn client side and server-side rear** (respectively with the same settings that were in the server A ).
How to implement the shutdown process openvpn client and the subsequent lifting open vpn server.
Thank you.

---

### Post by SeijiSensei on 2013-09-07
So, if I understand you correctly, you want the client to become the server if the original server goes offline?

You could write a bash script on the client to do this I suspect.  The script would ping the server and, if the ping times out, execute the commands you need to change from client to server.  Something like:

```

while [ "$(ping -c5 server_ip | grep '\ 0% packet loss')" != "" ]
do
     sleep 10
else
     do stuff
done

```

replacing "do stuff" with whatever procedures you want the script to execute if it can no longer connect.

---

### Post by rclever on 2013-09-08
Thank you very much. I'll try do it. And write the result.

---

