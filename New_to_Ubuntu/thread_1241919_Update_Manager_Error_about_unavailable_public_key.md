---
title: "Update Manager Error about unavailable public key"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by andrew222 on 2009-08-16
When I run the Update Manager I get a pop-up GUi box displaying this message:

[B][I]W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: 
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263[/I][/B]

I had no idea that a public key was needed let alone SSL was involved.

Is this a problem with my OS configuration or is it a problem with the server?

---

### Post by mcduck on 2009-08-16
Software repsitories usually use SSL keys for security and to make sure the packages you download are valid and nobody has made any changes to them.

Your situation seems like you have added the Wine repository, but didn't add the signing key for it.

Running the following command should solve that:
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

---

### Post by colau on 2009-08-17
> **andrew222 said:**
> When I run the Update Manager I get a pop-up GUi box displaying this message:

[B][I]W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: 
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263[/I][/B]

I had no idea that a public key was needed let alone SSL was involved.

Is this a problem with my OS configuration or is it a problem with the server?
Hello,
Is your problem solved?

---

### Post by andrew222 on 2009-08-17
Thank you mcduck,

That solved my problem.  

Rgds,

Andrew

---

### Post by HerNameMeansPearl on 2010-01-28
Thanks! I had the same problem and that fixed it!

Meghan

---

