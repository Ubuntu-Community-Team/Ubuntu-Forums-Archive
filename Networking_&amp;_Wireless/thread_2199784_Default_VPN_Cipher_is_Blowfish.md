---
title: "Default VPN Cipher is Blowfish?"
date: 2014-01-15
forum: Networking &amp; Wireless
---

### Post by NertSkull on 2014-01-15
I have a question or two about VPNs.

1) From everything I can find (which is limited) it appears the 'default' cipher used to encrypt data packets in ubuntu is Blowfish (maybe blowfish-CBC, not sure on that).  Is that correct, is the default Blowfish?

2) Assuming what I've found it is correct (that it is blowfish).  Why?  Just about everything I've read now days suggests using AES (some are even now saying always AES-256).  I know AES is kind of the poster child/celebrity of the field.  But I still am curious why to select blowfish as the default as opposed to the "industry standard" of AES.

3) Should I change my VPN settings to use AES instead of Blowfish?

4) IF I was to change my settings to use AES, does that make me stand out more.  Say I'm connecting to my VPN provider through another country.  And everyone connecting through linux is using Blowfish.  If I am the only 1 of 3 people that is switched it manually to use AES, can others 'see' that I'm using AES, thus making me stand out more?  Or is the type of encryption not known outside of the network?

Thanks

---

### Post by SeijiSensei on 2014-01-17
Blowfish is a very fast cipher [invented by Bruce Schneier]("https://www.schneier.com/paper-blowfish-fse.html") and has stood the test of time.  AES256 is the cipher [approved by the US Federal government]("http://en.wikipedia.org/wiki/Advanced_Encryption_Standard") for all encryption tasks.  I have one OpenVPN tunnel to a healthcare institution where I use AES256 because of the government regulation.  All my other tunnels use Blowfish.  I have yet to see much difference in performance between the two in practice.

I doubt anyone would know looking at the traffic exiting your VPN host how you connected to the host in the first place.

---

### Post by NertSkull on 2014-01-20
If no one can really tell which type of traffic you have (AES vs Blowfish) then I don't really understand all the talk about "brute-forcing" a connection.  Because wouldn't you have to change how you brute-force something based on the encryption type?

So if you can't tell, then that makes all the talk about "X billion-trillion tries before you can brute force AES" kind of meaningless, because it may take that long for AES, but the data may not even be AES encrypted.  So you'd have to it for ALL encryption types at the same time, making it even more complicated to brute-force an encryption scheme.  Does that make sense what I mean? Not sure I explained that well.

My question still kind of stands though, I agree there probably isn't much of a difference.  But still, why Blowfish over AES? Someone, somewhere made that decision, and I would assume they had a good reason.

Plus, I'm less worried about speed as opposed to strength.  So should I switch my VPN default frro Blowfish to AES?

---

