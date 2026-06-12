---
title: "TURN Server (coturn) on Ubuntu 24.04: Port not listening on 5349 (TLS)"
date: 2024-12-02
forum: Networking &amp; Wireless
---

### Post by shifty-189 on 2024-12-02
I’ve set up a TURN server using coturn on my Ubuntu server, intending it to be reachable on port 5349 (TLS). 
The service starts without any error messages and shows as active, but the server does not appear to be 
listening on port 5349, and external connections fail. Interestingly, port 3478 works perfectly fine.
**Setup:**


[LIST]
[*]**Ubuntu version:** 24.04 LTS
[*]**coturn version:** 4.6.1
[*]**TURN configuration:**
[LIST]
[*]tls-listening-port=5349
[*]use-auth-secret enabled
[*]Certificates correctly configured (Let’s Encrypt)
[*]Internal and external IPs properly defined in the config
[*]Relay ports (49152-65535) specified
[/LIST]

[*]**Firewall:** disabled (ufw is turned off)
[*]**Router setup:** Port 5349 (TCP) is correctly forwarded through NAT.
[/LIST]
**Problem:**


[LIST]
[*]Running sudo netstat -tulnp | grep 5349 returns no output, indicating that the server is not binding to the port.
[*]The TURN server does not appear to be listening on any interface for port 5349.
[*]Logs (sudo journalctl -u coturn) show no errors. Running the TURN server in debug mode also provides no helpful information.
[*]port 3478 works flawlessly, indicating that the basic firewall, NAT, and port forwarding configurations are correct.
[/LIST]
**Tests:**


[LIST]
[*]An OpenSSL connection test (openssl s_client -connect <my_domain_name>:5349) from an external network fails.
[*]Switching to an alternative port (e.g., 8443) produces the same behavior on that specific port.
[*]Certificates are valid and correctly loaded.
[/LIST]
Does anyone have an idea what could be causing this issue? I would greatly appreciate any advice or suggestions.
Thanks in advance for your help!

---

### Post by Irihapeti on 2024-12-02
It may be a certificate and key access issue. What is the location of the TLS certificate and key, and what are their ownership and permissions?

---

### Post by shifty-189 on 2024-12-03
@Irihapeti: Thank you for the suggestion regarding permissions, that was the key! After adjusting the rights for the certificates and directories, 
the TURN server is now working perfectly on port 5349. &#55357;&#56842;

---

