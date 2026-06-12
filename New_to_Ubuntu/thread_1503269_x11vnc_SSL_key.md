---
title: "x11vnc SSL key ?"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by WitchCraft on 2010-06-06
How do I set a SSL key for x11vnc (server) ?
#1
openssl genrsa -out mycorp.com.key 1024

#2: Create a self-signed certificate, enter:
Code:
openssl req -new -key mycorp.com.key -x509 -out mycorpcom.crt -days 30


But x11vnc doesn't accept the certificate...

I started x11vnc with 
x11nvc -ssl /path/to/mycorp.com.crt

---

### Post by krunge on 2010-06-06
If you run ```
x11vnc -ssl
``` which is the same as 'x11vnc -ssl SAVE', it will create and save the certificate+key for you. It runs openssl commands similar to what you have done manually. Use SAVE_PROMPT if you to be prompted for the various CommonName, etc. fields.

In any event, for the case where you did things manually you just need to combine both the key and the cert into one file, for example:
```

cat mycorp.com.key mycorp.com.crt > ./mycorp.com.pem
x11vnc -ssl ./mycorp.com.pem

```
should work.

---

