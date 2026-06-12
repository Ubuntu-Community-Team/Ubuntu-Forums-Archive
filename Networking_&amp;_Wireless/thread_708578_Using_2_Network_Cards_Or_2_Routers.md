---
title: "Using 2 Network Cards Or 2 Routers"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by tommohawk on 2008-02-26
These days I only have one reason to boot up my dreaded Windows Partition and that is simply to use my networked printer.

In Windows I can use my inbuilt wireless to connect to the wireless router that gives me my internet access.  I can then use my PCMCIA wireless card to connect to my other router which is connected to my printer.

To date I have not found a way to use both network cards in Linux to connect to two wireless networks at the same time.  

So my first question is....  Is it possible to use both network cards to connect to two wireless networks at the same time.  I can use them both but I have to switch between them with network manager.

The second question is more complicated.....  Ideally I would like to connect both routers together and have one wireless network.  Thing is I cannot really understand how to do this.  I have looked at many forum posts on various sites and still have no idea.

One of my routers is a Netgear DG834G (connected to the Internet) and the other is a Linksys WAG54GS connected to my printer.  They can swap positions if necessary!

Any ideas?

---

### Post by SpaceTeddy on 2008-02-26
network manager prohibits more than one configured network device at the time, but you can configure your second network card manually via the commandline (for testing) and then staticially (somehow - i have never done this for wireless card)

so, while you are connected to the internet with your one wireless card, open up a console and have a look at the comand iwconfig. this will show you the network cards that have wireless extensions in them and let you configure them outside of network manager.

exactly how to configure this i would need to know a little more about your setup... give me the essid's of your two wifi network, and the output of the following commands when connection to the internet.
> iwconfig
ifconfig
route -n

that ought to do it... hopefully

---

### Post by tommohawk on 2008-02-27
Think I have the manual configuration sorted, thanks.

What I really need is someone who knows how to tie the two routers together.

---

### Post by SpaceTeddy on 2008-02-27
mhm, i had a look at the specs of the two router you said you have.
unforteunatly, they are not able to build a wifi bridge (i.e. forward a network between the two) - or the Linksys one is not able to (didn't check the netgear). But since both need that feature, it is pointless search in the manual for the Netgear...

So, unless you run a cable from one to the other, i am afraid i cannot help you with this one :(

sorry....

---

