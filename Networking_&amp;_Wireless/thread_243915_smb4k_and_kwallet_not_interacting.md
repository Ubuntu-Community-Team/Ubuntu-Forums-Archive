---
title: "smb4k and kwallet not interacting"
date: 2006-08-25
forum: Networking &amp; Wireless
---

### Post by fieldbio on 2006-08-25
Hi,

Before I installed Drake everything was working fine, but now I'm having problems with smb4k (now version 0.6.5):

When I open it I can see the usergroup on the left with all of the computers. I try to access my other computer and it gives me two error messages one after the other:

1)Opening the wallet failed! KWallet support will be disabled.
2)An error occurred while trying to get the list of shares: Couldn't connect to server [computer name], the account was disabled.

However, I can mount my other computer's drives manually using smb4k. It gives me the same error #1 but then asks for a password and mounts the drive.

Also, when I attempt to create a wallet using the configuration-authentication tool I get error #1 again.


I think the error is from the kwallet side, because when I first installed smb4k it prompted me to create a wallet, but then crashed and since then it hasn't prompted again.

Using kwalletmanager there are no wallets and it wont let me create one.

I've tried uninstalling/reinstalling both smb4k and kwalletmanager several times (and deleted the files from my home .kde directory) but the same problem keeps occuring.

Thanks

---

