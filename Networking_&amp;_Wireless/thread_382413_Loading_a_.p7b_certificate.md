---
title: "Loading a .p7b certificate?"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by RichZA on 2007-03-12
Hi all,

I have just moved over to linux so forgive me if this is common knowledge.

I need to use a .p7b certificate which I exported from a windows box to connect to a PEAP wireless network. 

I have tried using the gnome network manager with no success. 

How do I load the certificate and get ubuntu to use it to connect to the network?

---

### Post by RichZA on 2007-03-13
Bump.... I really need to sort this out. Anyone have any ideas?

---

### Post by shinkuro on 2007-03-25
Try converting the certificate into a usable format with something like:
  openssl pkcs7 -inform DER -outform PEM -in certname.p7b -out certname.pem -print_certs

Then you can drop the certificate into your repository, usually /etc/ssl/certs.

---

### Post by bouligab on 2007-10-06
I also need to install a ".p7b" certificate.

I tried applicating the instructions, although I'm not sure I did it perfectly well; here is what I wrote in the terminal  (I have openssl installed, the directoy was OK, and the certificate name is "certnew.p7b") :

openssl pkcs7 -inform DER -outform PEM -in certnew.p7b -out certnew.pem -print_certs

I'm not sure I quite understood the instructions, maybe I just did the wrong thing?

anyway, here's what I got:


unable to load PKCS7 project
7796:error:2006F078:BIO routines:BIO_read:uninitialized:bio_lib.c:162:
7796:error:0D06B08E:asn1 encoding routines:ASN1_D2I_READ_BIO:not enough data:a_d2i_fp.c:180:

Is there someone knowing what al this means, and could I possibly resolve the problem?
Thanks!

---

