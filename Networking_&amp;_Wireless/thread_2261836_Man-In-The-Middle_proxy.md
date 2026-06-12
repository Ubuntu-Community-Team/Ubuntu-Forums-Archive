---
title: "Man-In-The-Middle proxy?"
date: 2015-01-21
forum: Networking &amp; Wireless
---

### Post by ofnuts on 2015-01-21
At work I access Internet via a proxy (BlueCoat, given the name of the proxy machine...).  I have no problem accessing most sites through it, but for one site it doesn't connect and Firefox reports:
```

An error occurred during a connection to XXXXXXX.YYY. The server rejected the handshake because the client downgraded to a lower TLS version than the server supports. (Error code: ssl_error_inappropriate_fallback_alert)

    The page you are trying to view cannot be shown because the authenticity of the received data could not be verified.
    Please contact the website owners to inform them of this problem.

```

Name of site witheld to protect the innocent, but it is a 100% SFW site. Of course no problem accessing this site using a proxy-less network connection.

Is the message above due to the proxy degrading the TLS encryption to a level it can understand, the "client" being the proxy here, because when the client is my Firefox in direct connection it appears to work.

---

### Post by newbie-user on 2015-01-22
Sounds like the proxy needs to be upgraded to support the latest TLS. It probably hasn't had an software upgrade in a while.

---

### Post by ofnuts on 2015-01-23
Ah, OK.

---

