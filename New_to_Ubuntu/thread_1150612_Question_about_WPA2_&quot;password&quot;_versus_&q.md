---
title: "Question about WPA2 &quot;password&quot; versus &quot;passphrase&quot;"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by DenverMike on 2009-05-06
Hello,

I'm attempting to use Network Manager to connect to my home wireless network which uses WPA2 security, but I'm unable to connect.

When I select the network in the list of available networks, I'm prompted for a "WPA & WPA2 Personal" password.  In looking at my router's configuration, it has a WPA2 "passphrase" and not a "password".

Is there a difference?

Anyway, I enter the passphrase and it doesn't connect. 

Then, if I go back to the settings and check the "Show password" checkbox, the value in the password field is a hex value, not my original passphrase.

So the question is, is there some way to convert a passphrase to a password for use in WPA2?

Thanks!

---

### Post by Dngrsone on 2009-05-06
The passphrase is hashed into a larger password, which is a long hexedecimal number.

Plug the hexedecimal word from your router into the your Network Manager's password window and it should work.

---

