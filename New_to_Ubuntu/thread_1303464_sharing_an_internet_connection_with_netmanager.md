---
title: "sharing an internet connection with netmanager"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by RichardCL on 2009-10-28
Dear Forum,

I've read through and tried countless tutorials on bridging and firestarter and not been sucessful. What I want to do should be simple.

I want my laptop, which is connected via wireless to a fritzbox router with DHCP to allow a second machine without a wireless adapter to connect to the internet. I'm planning to use my eth0 connection to do this.

Both machines have a fresh install of Karmic.

I assumed that I just set the netmanager IPv4 to "shared to other computers" on both machines and then make the eth0 connections on both machines and the ra0 connection on the host "available to all users".

According to the one tutorial that should be it but firefox on the guest is giving "error loading page", while the same page is display on the host. What am I missing?


Rich

---

### Post by snkiz on 2009-10-28
Set your laptop to share and your desktop to dhcp it should work just fine.

---

### Post by RichardCL on 2009-10-28
No idea what happened but I tried it again and it worked!!!

It would seem that the connection should be made on the host first. Not sure why though.

---

