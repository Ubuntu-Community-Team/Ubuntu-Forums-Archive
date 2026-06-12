---
title: "Conceptronic under edgy?"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by TheCutter on 2007-07-10
Hello there,

Just bought a Conceptronic c54ru usb wlan adapter for my girlfriends Toshiba which is running Ubuntu edgy. Would anyone be able to help me configure it? The situation is:
It recognizes the device, I can configure it, but it won't connect. My problem is that I'm a Mac user myself which means A: that I've gotten pretty lazy, things just usually install themselves, and b: since Mac makes me lazy, I've never gotten into the whole Unix science behind it OSX. When I read the info available, there seems to be a lot of coding and terminal work stuff necessary, so my question really is (finally, here it comes: :-) 
Is there a driver that I can just download and install? If so, where can I find it? Otherwise, could anyone please point me to a walkthrough of the setup?

FWIW, my Mac sees the device and gives me the following product id: 0x3c22
Any help would be most appreciated.

Thank you in advance.

---

### Post by sj3fk3 on 2007-07-11
> **TheCutter said:**
> Hello there,
Just bought a Conceptronic c54ru usb wlan adapter for my girlfriends 

Why? I mean why buy Conceptronic... You must not really like that girl huh?

> 
It recognizes the device, I can configure it, but it won't connect. My problem is that I'm a Mac user myself which means A: that I've gotten pretty lazy, things just usually install themselves, and b: since Mac makes me lazy, I've never gotten into the whole Unix science behind it OSX. When I read the info available, there seems to be a lot of coding and terminal work stuff necessary, so my question really is (finally, here it comes: :-) 
Is there a driver that I can just download and install? If so, where can I find it? Otherwise, could anyone please point me to a walkthrough of the setup?

Thank you in advance.

Depending on the version of Ubuntu I would say, use gnome network manager 
'sudo apt-get install network-manager-gnome'

p.s.
I don't really understand the part where you say, that you can configure it, but it won't connect. Do you use WEP (you shouldn't) or WPA? Or no encryption (you really must not like your girlfriend then) at all?

---

### Post by TheCutter on 2007-07-11
> **sj3fk3 said:**
> Why? I mean why buy Conceptronic... You must not really like that girl huh?

Allez Sjefke, ge zijt abuis m'n beste, t'is ne schone! Sorry, couldn't help myself, you ARE Belgian, right? 
It's not easy to find a good product here in the South of Spain. Is there another brand that would be easier to configure?

Anyway:

Depending on the version of Ubuntu I would say, use gnome network manager 
'sudo apt-get install network-manager-gnome'

This is something I have to feed into the Terminal, right? That's what I was afraid of. I'll try :sad:

p.s.
I don't really understand the part where you say, that you can configure it, but it won't connect. Do you use WEP (you shouldn't) or WPA? Or no encryption (you really must not like your girlfriend then) at all?

What I mean is that Ubuntu sees the thing, allows me to set a password (WPA although it only gives me the choice between ascii and hex), then it takes a few moments to get through its process, i can activate the connection, but can't load any pages or do a ping to google.
Enneh, what the thing, I DO like her. :-)

---

### Post by sj3fk3 on 2007-07-12
> **TheCutter said:**
> What I mean is that Ubuntu sees the thing, allows me to set a password (WPA although it only gives me the choice between ascii and hex), then it takes a few moments to get through its process, i can activate the connection, but can't load any pages or do a ping to google.
Enneh, what the thing, I DO like her. :-)

Ah, no I'm not a 'Vlaming' Sjefke is nog my real name, but just a nickname cuzz I'm the chief here (@ office). Anyway, in my humble opinion Conceptronic is really bad sjizzle. Still it should work and it looks like it nearly does. Have you tried 'n open network, just for testing purposes? See if that does work, it sounds like WEP/WPA issue, as far as I know it should be asking for a passphrase in case of WPA and not ascii or hex input (sounds like WEP).

---

