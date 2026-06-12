---
title: "No wireless connection when using a WEP key?"
date: 2006-11-04
forum: Networking &amp; Wireless
---

### Post by tdamocles on 2006-11-04
I'm using a netgear wireless router and set up everything in the configuration using a WEP key but when I enter it in the config in Ubuntu I do not get a connection.  I must disable the protection in the netgear config to get a connection unprotected.  Any ideas what it could be?

---

### Post by banana989 on 2006-11-12
I'm having the same problem. From what I have heard it is a problem with Edgy ( 6.10 ) and wireless ( mine is ipw3945 ).

---

### Post by FrodoB on 2006-11-12
Generate keys at this site:

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

Use Hex keys in the router and in Ubuntu.

After you have them entered in the Networking GUI you can check them by looking in:

/etc/network/interfaces

---

### Post by entropic_existence on 2006-11-16
Hey not sure if this resolves the problem or not but I;m using networkmanager and was also having problems connecting to my WRT54G WEP encrypted network. I also have the intel ipw3945 wireless chipset. My WEP keys are 128 bit hex, and my connections worked excellent under dapper but not in edgy.

Went through these threads and just now, when tinkering, realized that netorkmanager was asking for my passphrase not the key. Didn't think it would work but just decided to put in the passphrase I had used to generate the keys and voila! it worked. I imagine this is because I am using an open system. I have a feeling I should switch that over to shared key. Anyway check and see if this helps!

---

### Post by FrodoB on 2006-11-16
Incidentally, if you are referring to the Authentication Type, open is more secure than shared key.

Open authentication systems should not ask for the key, but you have to use it to communicate.

If you are using ndiswrapper some devices need to use wireless-key1 rather wireless-key in the interfaces file.

---

### Post by banana989 on 2006-11-18
I am having the same problem w/ WEP and ipw3945 ... I thought Ubuntu was supposed to work out of the box but so far I am unimpressed. I am actually trying Ubuntu over Arch for my laptop b/c I thought things were supposed to be easier. I am very comfortable in Linux but have had no success in getting Wireless to work w/ a secured network.

---

### Post by vroomfondel on 2007-01-03
> **banana989 said:**
> ... I thought Ubuntu was supposed to work out of the box but so far I am unimpressed. I am actually trying Ubuntu over Arch for my laptop b/c I thought things were supposed to be easier. I am very comfortable in Linux but have had no success in getting Wireless to work w/ a secured network.

Same here with a USR5410 card. The suggestions to change the router setting amuse me & aren't possible in my case. The router uses SHARED WEP . I know the key but can't change it. If ubuntu can't be made to work with this I'm dumping it.

---

