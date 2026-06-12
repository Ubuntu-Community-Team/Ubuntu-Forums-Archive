---
title: "A curious wireless networking observation?"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by AndrewS on 2008-01-24
Hi

I just installed a usb wireless adapter in my venerable Thinkpad 770.  Basically it works OK, but I am puzzled by one thing.  Before I can connect I am asked for a nm-tokenring password, and it will only accept an upper-case version of my root password.   My router has 128 bit WEP "security", but using Ubuntu 7.10 I am not asked for the key.  On the odd occasion I use W98SE, I have to give the key.

Can someone explain this to me please?

TIA

Andrew  :confused:

---

### Post by chewearn on 2008-01-25
Previously, when you connect to your wireless network for the first time, you are asked for the WEP key.  Then, you are to supply a password for the keyring manager.  The keyring manager is akin to a vault for your WEP key.  Therefore, when you subsequently connects to the same network, you will be asked to open the vault to retrieve the WEP key.  There is no more asking for the WEP key again.

Usually, one will use the same password for the keyring manager as their login password (so it's easier to remember), but this is not a requirement.  You can actually use any password you want for a particular keyring).  Here is then the probable cause of all uppercase for your keyring password; you must have accidentally hit the capslock that first time when entered your root password for the keyring.

---

### Post by AndrewS on 2008-01-25
Yes, thanks - that'll be the explanation.  Is there any way to change the password on the keyring manager?  I probably had caps lock on when I entered the WEP key (it's a hex string - I don't know if this is case-sensitive or not so I put caps lock on in case).  It's a minor pain having to enter the second password in upper case.

Thanks again.

Andrew

---

### Post by wieman01 on 2008-01-25
> **AstalaVista said:**
> Usually, one will use the same password for the keyring manager as their login password (so it's easier to remember), but this is not a requirement. 
In fact one should not do that for security reasons. Imagine the PC gets stolen, what passwords would a thief try first in order to retrieve all access keys from the vault? The login passwords in all likelihood. Therefore I recommend that you use a separate password for the keyring manager. Otherwise the vault would make no sense at all, would it?!

---

