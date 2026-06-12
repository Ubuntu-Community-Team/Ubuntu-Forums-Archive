---
title: "How to fix this?"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by Ric_NYC on 2009-08-29
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D6A476432590D54C

That happens when I try to update Ubuntu.

---

### Post by NoaHall on 2009-08-29
You need to download and install the key for it. Look on the launchpad website for the key to add. And that's a bad thread title.

---

### Post by Paqman on 2009-08-29
You can get the PPA key off the same page as you got the url originally. In the meantime, don't let it stop you from carrying out updates. You can update from an unsigned PPA if you know it's kosher, it's just giving you a sensible warning.

---

### Post by Ric_NYC on 2009-08-29
Thanks for the replies. I still don't understand how to add the key.
I agree the title is not good.

---

### Post by Ric_NYC on 2009-08-29
When I remove this from the "Software Sources" the Upadte Manager stops showing the error message:


[http://ppa.launchpad.net/ubuntu-webtech/o3d-daily/ubuntu](http://ppa.launchpad.net/ubuntu-webtech/o3d-daily/ubuntu)

It's the o3d plugin from Google.

---

### Post by Ric_NYC on 2009-08-29
I fixed it.

I used this command that I found in the page of the o3d project:


sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2590D54C

---

### Post by juancarlospaco on 2009-08-29
Use DESCRIPTIVE titles, ASAP

---

### Post by Ric_NYC on 2009-08-29
Can anyone fix the title for me?
Something like "Error message when using the Upadate Manager".
Thanks.

---

