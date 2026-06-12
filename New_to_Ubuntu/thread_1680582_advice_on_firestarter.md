---
title: "advice on firestarter"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by kapi on 2011-02-02
Hi

I've installed the firewall ap called firestarter and want to know if when I start it up and close the dialogue box, does it still run in the background? I checked system monitor but couldn't see it.

what does everyone else use?

---

### Post by davidmohammed on 2011-02-02
firestarter isnt a firewall - its just a way to configure the default firewall already in ubuntu which is not "enabled" by default.

firestarter is very old - the recommended firewall editor is gufw

sudo apt-get install gufw

you dont need to have either firestarter or gufw to start on logon/startup - ubuntu will take care of that for you.

---

### Post by 3rdalbum on 2011-02-02
> **davidmohammed said:**
> firestarter isnt a firewall - its just a way to configure the default firewall already in ubuntu which is not "enabled" by default.

firestarter is very old - the recommended firewall editor is gufw

sudo apt-get install gufw

you dont need to have either firestarter or gufw to start on logon/startup - ubuntu will take care of that for you.

+1

The actual firewall is built into the kernel; so programs like Firestarter and gUFW just tell the inbuilt firewall what settings to use.

I'll also add that Ubuntu ships with NO LISTENING SERVICES by default; so you don't really need a firewall anyway (unless you install some network-facing services that you don't want the rest of your network to access).

---

### Post by Frogs Hair on 2011-02-02
I use gufw also , I don't think firestarter has been updated for a very long time.

---

### Post by kapi on 2011-02-03
Thanks for the reply. So unbuntu has an automatic firewall built in then? 

May I ask what you mean by the listening services, I'm interested.

Thanks again





> **3rdalbum said:**
> +1

The actual firewall is built into the kernel; so programs like Firestarter and gUFW just tell the inbuilt firewall what settings to use.

I'll also add that Ubuntu ships with NO LISTENING SERVICES by default; so you don't really need a firewall anyway (unless you install some network-facing services that you don't want the rest of your network to access).

---

### Post by mikewhatever on 2011-02-03
> **kapi said:**
> Thanks for the reply. So unbuntu has an automatic firewall built in then? 

May I ask what you mean by the listening services, I'm interested.

Thanks again

Yes, the firewall is built in, it's called IPtables, and it's not automatic. ;)
No listening services means that no processes listen on ports (same as wait for incoming connection) facing the internet, which means there is nothing to firewall.

---

