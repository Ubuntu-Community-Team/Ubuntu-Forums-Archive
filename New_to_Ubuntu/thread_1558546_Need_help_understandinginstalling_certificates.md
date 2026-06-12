---
title: "Need help understanding/installing certificates"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by Newbie2910 on 2010-08-22
I have a .Net app that I am running/developing on Mono on Ubunto 10.04.  One of the things it does is read Gmail data.  Now I have read that I need to install the Mozroots certificates, which I did.

I also installed the Gmail certificates, here's the output:
certmgr -ssl smtps://smtp.gmail.com:465Mono Certificate Manager - version 2.6.7.0
Manage X.509 certificates and CRL from stores.
Copyright 2002, 2003 Motus Technologies. Copyright 2004-2008 Novell. BSD licensed.


 X.509 Certificate v3
   Issued from: C=US, O=Equifax, OU=Equifax Secure Certificate Authority
   Issued to:   C=US, O=Google Inc, CN=Google Internet Authority
   Valid from:  6/8/2009 4:43:27 PM
   Valid until: 6/7/2013 3:43:27 PM
   *** WARNING: Certificate signature is INVALID ***
This certificate is already in the CA store.

 X.509 Certificate v3
   Issued from: C=US, O=Google Inc, CN=Google Internet Authority
   Issued to:   C=US, S=California, L=Mountain View, O=Google Inc, CN=smtp.gmail.com
   Valid from:  4/22/2010 4:02:45 PM
   Valid until: 4/22/2011 4:12:45 PM
This certificate is already in the AddressBook store.

No certificate were added to the stores.



This is the error I get using the MonoDevelop debugger:
System.IO.IOException: The authentication or decryption has failed. ---> Mono.Security.Protocol.Tls.TlsException: Invalid certificate received from server. Error code: 0xffffffff80092012
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.validateCertificates (Mono.Security.X509.X509CertificateCollection certificates) [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.Handshake.Client.TlsServerCertificate.ProcessAsTls1 () [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.Handshake.HandshakeMessage.Process () [0x00000] in <filename unknown>:0 
  at (wrapper remoting-invoke-with-check) Mono.Security.Protocol.Tls.Handshake.HandshakeMessage:Process ()
  at Mono.Security.Protocol.Tls.ClientRecordProtocol.ProcessHandshakeMessage (Mono.Security.Protocol.Tls.TlsStream handMsg) [0x00000] in <filename unknown>:0 
  at Mono.Security.Protocol.Tls.RecordProtocol.InternalReceiveRecordCallback (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at Mono.Security.Protocol.Tls.SslStreamBase.AsyncHandshakeCallback (IAsyncResult asyncResult) [0x00000] in <filename unknown>:0 

This seems to indicate the Mono is getting an invalid certificate from Google, is that right (meaning it has nothing to do with the certs I have stored in the machine, it's what Google is sending back)?  If so, any idea how I can get a resolution?

---

