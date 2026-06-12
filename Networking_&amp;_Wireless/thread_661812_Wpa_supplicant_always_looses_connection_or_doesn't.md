---
title: "Wpa_supplicant always looses connection or doesn't connect at all"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by Marsch123 on 2008-01-08
Hello!
I am a student at Hogeschool Rotterdam and live here in a students appartement where Internet is provided by wired ethernet. However, we need to authenticate ourselves. The university just provides support for Windows and there you just have to install the SecureW2 program and fill in your username and password. It's not so easy with Linux unfortunately. I am using Ubuntu 7.10 with wpasupplicant and I get a Internet connection, but only every fifth or tenth time I start the connection. If it sucessfully connects it only lasts for maybe five minutes until it looses connection again. I used a working configuration that someone else who has the same internet access as I have uses and it works perfectly fine at his place. The configuration is:```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=0

network={
key_mgmt=IEEE8021X
eap=TTLS
identity="xxxxx@hro.nl" #change to your erna login
anonymous_identity ="xxxxx@hro.nl"
password="pass"
phase2="auth=PAP"
}
```


The error Wpasupplicant gives is:
```

OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)

```
After that there are some code lines the authentication is completed successfully, but it doesn't work anyway.
Do you have any idea that could help me?
By the way...I always have to start the Wpasupplicant manually, although it should start automatically. But that's not my major concern, it just has to work stable.
I appreciate any opinion I can get!
Thank you in advance
Marsch

---

### Post by Marsch123 on 2008-01-09
nobody?

---

### Post by rma88 on 2008-01-12
yea i'm having issues setting up wpa_supplicant as well, i get that same error:

OpenSSL: tls_connection_handshake - Failed to read possible Application Data error

-no luck so far, you?

---

### Post by Marsch123 on 2008-01-13
No, unfortunately not. I installed Windows again (Dual boot), but I'm still hoping to find a solution.
Strange that no one has a clue.

---

