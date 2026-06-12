---
title: "Unable to connect to the OpenVPN server using PKCS#11 interface"
date: 2023-01-16
forum: Networking &amp; Wireless
---

### Post by adam-kowal on 2023-01-16
Hello!
I want to use keys generated with hardware security module TPM 2.0 for user authentication when connecting to the OpenVPN server.
I am generating key pair and importing signed certificate with use of tpm2-pkcs11 1.8.0 ([https://github.com/tpm2-software/tpm2-pkcs11](https://github.com/tpm2-software/tpm2-pkcs11)) compiled form source.

On Fedora 36 (OpenVPN 2.5.7; OpenSSL 3.0.5) everything works fine, but on Ubuntu 22.10 (OpenVPN 2.6; OpenSSL 3.0.5) on different machine it is not working (same with 22.04 LTS and older version of OpenVPN).
When I try to connect to the VPN server, it asks for the token password (as if it found it) but then these logs appears:
```
2023-01-16 14:20:00: PKCS#11: Cannot get certificate object
2023-01-16 14:20:00: PKCS#11: Cannot get certificate object
2023-01-16 14:20:00: PKCS#11: Unable get evp object
```

The only difference I spot between Ubuntu and Fedora is that syntax of returned pkcs11-id is different.
Under both distributions for ovpn config file I am using pkcs11-ids returned by command **openvpn --show-pkcs11-ids**:
Ubuntu:
```

DN:             C=PL, O=TEST, CN=Test Test
Serial:         034E
Serialized id:  Nuvoton/rls/0000000000000000/test_tpm/30393037363163303139643963616132

```

Fedora:
```

DN:             C=PL, O=TEST, CN=Test Test
Serial:         034D
Serialized id:  pkcs11:model=SLB9670;token=test_tpm;manufacturer=Infineon;serial=0000000000000000;id=22ab4f2e7acf600b

```

Corresponding lines in configuration files:
Ubuntu:
```

pkcs11-id 'Nuvoton/rls/0000000000000000/test_tpm/30393037363163303139643963616132'

```

Fedora:
```
pkcs11-id 'pkcs11:model=SLB9670;token=test_tpm;manufacturer=Infineon;serial=0000000000000000;id=22ab4f2e7acf600b'
```

OpenVPN on Fedora seems to create a valid RFC 7512 ID and using it in ovpn config file works fine. But on Ubuntu I get logs as showed above so I cannot connect to the server.

I am quite sure that key pair was generated properly and the certificate was imported right too, because both Chrome and Firefox can recognize it and I can use this certificate to succesfully perform client SSL auth on both browsers. Also by use of PKCS#11 interface creating (and then verifying) digital signatures with these keys works too.

Any clues? Thank you.

---

