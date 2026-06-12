---
title: "[lubuntu] CA signature digest algorithm too weak"
date: 2018-05-04
forum: Networking &amp; Wireless
---

### Post by joptiopay on 2018-05-04
I just upgraded to Ubuntu 18.x, and suddenly my wifi networking is not working anymore. When I run `wpa_supplicant`, I get the following output:[INDENT][FONT=courier new]
TLS: Certificate verification failed, error 68 (CA signature digest algorithm too weak) depth 0 for '/CN=...'[/FONT][/INDENT]
[INDENT][FONT=courier new]wlp2s0: CTRL-EVENT-EAP-TLS-CERT-ERROR reason=0 depth=0 subject='/CN=...' err='CA signature digest algorithm too weak'[/FONT][/INDENT]
[INDENT][FONT=courier new]SSL: SSL3 alert: write (local SSL3 detected an error):fatal:bad certificate[/FONT][/INDENT]
[INDENT][FONT=courier new]OpenSSL: openssl_handshake - SSL_connect error:1416F086:SSL routines:tls_process_server_certificate:certificate verify failed[/FONT][/INDENT]
[INDENT][FONT=courier new]wlp2s0: CTRL-EVENT-EAP-FAILURE EAP authentication failed[/FONT][/INDENT]
[INDENT][FONT=courier new]wlp2s0: CTRL-EVENT-DISCONNECTED bssid=... reason=0[/FONT][/INDENT]
[INDENT][FONT=courier new]wlp2s0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="My Network" auth_failures=1 duration=10 reason=AUTH_FAILED[/FONT][/INDENT]

Does anyone have an idea what might have changed with the upgrade to cause this to happen?

---

