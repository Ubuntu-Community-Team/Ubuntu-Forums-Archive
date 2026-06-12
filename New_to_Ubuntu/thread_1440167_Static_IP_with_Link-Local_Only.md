---
title: "Static IP with Link-Local Only"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by Flynsarmy on 2010-03-27
Is it possible to set a static IP with Link-Local Only network method? I have a Win7 machine and a Ubuntu machine connected to the net via Wifi and each other via ethernet with a switch so I can add more machines later. On the Win7 machine i simply set the wifi's metric to be lower than the ethernets - easy. On Ubuntu the only way I could accomplish this was to use Link-Local Only method but that doesn't provide a static IP (IP settings are greyed out). Anyone know how to do this?

---

### Post by ScarySquirrel on 2010-04-01
I think that Link-Local Only just allows you to connect to one other computer, but I could be wrong. I, myself, seek an explanation of how to connect two Ubuntus with a crossover cable.

---

### Post by Iowan on 2010-04-01
> **ScarySquirrel said:**
> I, myself, seek an explanation of how to connect two Ubuntus with a crossover cable. Have you started a thread (or searched the forum)? I'd be happy to pitch in - but not here...

@Flynsarmy:
I'm not familiar with details, but link-local seems to use **avahi** as a pseudo-DHCP network (zero-conf?), so static address may be contrary to design... (Or, I could be completely WRONG!)  Older releases seemed to be easier to mix Network Manager (which only wanted to manage one interface at a time) with */etc/network/interfaces*. Though I haven't given up on NM, removing it completely is frequently recommended.

---

### Post by ScarySquirrel on 2010-04-24
> **Iowan said:**
> Have you started a thread (or searched the forum)? I'd be happy to pitch in - but not here...

Nah. I only start help request threads on these forums out of idle curiousity, really, and I actually want to find out how to do this. 

I've begun to realize that I'm advanced enough that, for the problems I can't fix myself, the community usually responds as follows: 
[IMG]http://icanhascheezburger.files.wordpress.com/2010/04/funny-pictures-cat-does-not-care.jpg[/IMG]

OR responds late enough that it would be simpler to have just spent the time researching or reinstalling. Still, sometimes something good, or amusing, will come up.

---

### Post by BoneKracker on 2010-06-01
> **ScarySquirrel said:**
> OR responds late enough that it would be simpler to have just spent the time researching

You're supposed to do that _before_ you ask.  A good place to start is to search the forums to see if your question has already been answered. ;)

---

### Post by BoneKracker on 2010-06-01
> **njparton said:**
> my interfaces file doesn't contain a eth0 or wlan0 entry so I think it's redundant now???

We need an Ubuntu user's input here.  My take on what I read above is that, at least as of 8.04, the interfaces file was purged (and I assume, is no longer automatically populated), but if you wanted to manually set a metric you could create an entry in the file.  I assume that's why it's still there.  Not every linux system has an "interfaces" file.

Also, I'd check what the metrics say now when you have both wired and wireless interfaces up and running (are they the same, or does the wireless interface have a higher metric?).

Setting routing metrics in Ubuntu must be documented somewhere.  I'd look around.  It's got to be easy to do, because it's a common task.

If all else fails, you could always set it with a one-line script that runs an ifconfig command at the end of your boot-up process.  You could probably also configure something in the wireless software (for example, with WPA Supplicant, you can set up what's called "action scripts" that run on connect or disconnect events).

---

