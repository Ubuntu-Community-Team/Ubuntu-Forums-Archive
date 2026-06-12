---
title: "Authenticate 802.1x on wired network"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by Modeverything on 2008-10-23
I have an issue that I cannot figure out.  I have searched Google and the forums and cannot find an answer for this.

At my company, we use 802.1x authentication on a wired network.  Now here is the catch:

**Our systems authenticate to the wired network as supplicants using client certificates.**

There is no username or password to authenticate, all authentication takes place on the computer.  The computer presents it's certificate to the switch, the switch checks with the Microsoft Internet Authentication Service (IAS) RADIUS server and determines whether or not the client is allowed on the network.

I can request a client certificate from our CA via a web page, but I have to submit a request in one of the following Base-64 forms, CMC, PKCS #10, or PKCS #7.  So I need to create an offline request, then copy and paste the Base-64 code of the request into the web browser interface of the CA.

The main issue that I'm having at the moment is I don't know how to create the offline request.  I have looked at openssl, xsupplicant, and wpa_supplicant, and I cannot figure out how to create a file with a Base-64 request to submit to the CA.

Can anyone give me some help on this?



Thanks in advance!

---

### Post by Modeverything on 2008-10-23
Ok, I stumbled across a site that explained how to create the offline request.  I ended up creating two pem files, both encoded Base-64, so the Windows offline CA took the request.

Now the problem is when I try to download the certificate that the CA generated for me, I get an error saying, "This personal certificate can't be installed because you do not own the corresponding private key which was created when the certificate was requested."

I'm thinking maybe I need to download the CA chain from the CA so that my Ubuntu system trusts the CA, but I'm not sure.  I downloaded the certificate chain, but I now have a p7b file which I can't seem to import.  I think I need to convert it into some other format, but I'm not sure what; and when I do get it converted, I'm not sure how to install it.

---

