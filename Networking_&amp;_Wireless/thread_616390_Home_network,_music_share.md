---
title: "Home network, music share"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by Anessen on 2007-11-18
Hey there
What I want to do is stream music from a home server using amarok. At the moment, I have the samba share on the server set to mount at startup, but the server doesn't always boot up first (sometimes I leave it off to save electricity, then boot it up later).

I'm thinking I need to get my main computer to automatically mount the Samba share on the remote computer, but I can't see an efficient way of doing that. How do I go about this?

---

### Post by Blutack on 2007-11-18
Sounds like you should really be using DAAP instead.  There is no easy way to do what you are talking about, but with DAAP the server would notify amarok as soon as it was booted.  Use the package mt-daap.  You could also look into wakeup on lan for your server, so you can set it to boot from your main computer.

---

### Post by Anessen on 2007-11-18
OK, to clarify, is there any way to automatically mount a share as it comes online (assuming it is not online when the client system boots)?

---

### Post by njparton on 2007-11-18
Your server PC is running ubuntu and your client windows?

---

### Post by Blutack on 2007-11-18
Nothing springs to mind - only thing I can think of is a bash script something like this

do
{
ping remote.host
}
while(ping fails);

wait 30 (for samba to start
smbmount -whatever

end

and stick it in your init.d

---

