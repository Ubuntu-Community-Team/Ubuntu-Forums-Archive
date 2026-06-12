---
title: "Update Mythbuntu via wireless connection to desktop and then internet"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by chipppy on 2009-07-17
Good Morning

**PLEASE HELP ME!!!!!!**

I have a bit of a huge project (for me anyway) that I would like a little help with.

My objective is to be able to update my Mythbuntu HTPC (Mythbuntu 9.04) via some form of remote desktop viewer type thing, over a wireless network connection, from my office PC (Ubuntu 9.04), which has the only Internet connection via a cabled ADSL2+ connection to the www.

I have no idea how to do this.  I have been trying for a couple of days now.  I have tried to follow the various HOW TOs in the support docs and via google searches, with no luck.  I dont think I have been able to get the two PC's to talk via the wireless cards but I am not really sure.

I think what I need to achieve is the following steps.  Please feel free to correct my understanding if it is wrong.

1. Install the wireless networking cards (done)
2. Update the hardware drivers (done)
3. Create a new ad-hoc network on each computer (tried but not sure it worked)
4. Install some sort of remote desktop viewer software
5. Allow Internet sharing on office PC (no idea how to do this)
6. Run update manager on Mythbuntu HTPC (currently a dream)

Basically I was hoping someone out there could point me to a HOW TO: (please read as 'guide for the really dumb guy, with step by step instructions'), for the various steps that I would need.

Considering how much fun I am having at the moment I will try to write a complete step by step HOW TO: at the end of this so that the next newbie can use it.

I have been using Linux for approx 9 months.  I have the basics of *terminal* down pack but the intermediates I still need help with.

**Any and all assistance is greatly appreciated**

Cheers
chipppy

---

### Post by gn2 on 2009-07-17
Why update it at all?
If it's working correctly and not connected to the internet, it's not at risk.

You might find powerline network adapters or a wireless router useful?

---

### Post by Hospadar on 2009-07-17
I agree with the above, especially considering that new features are generally only released on major release cycles (hardy, jaunty, etc), not through the regular updates.

That said, if you do want to update, how will you be connecting these machines?
with a wire coming from a second ethernet card on the desktop to the myth box?

You could set up the desktop as a gateway, if you google around "setting up linux gateway" you'll probably find some stuff.

---

### Post by chipppy on 2009-07-17
Good Morning

I understand the no major need to update, but I also have a few problem with my program guide through the DVB-T and I would like to be able to get the program guide via the Internet so I can record the show that we want to watch (most of the good ones are on really early in the morning.

I will be using wireless due to the fact that it would be very expensive to run CAT5 cables.  

I have installed an ASUS wireless card into both the Mythbuntu and the Ubuntu PC.  
I clicked on System ==> Administration ==> Hardware Drivers and let it do it thing.  I then activated the driver that it recommended nd all seemed to happen without a hitch.
Steps 1 & 2

This is as far as I have worked out so far.  i have tried to setup a new connection but it doesn't appear to have achieved anything
Step 3 is were I am currently stuck


Cheers
chipppy

---

### Post by gn2 on 2009-07-18
> **chipppy said:**
> ~ I will be using wireless due to the fact that it would be very expensive to run CAT5 cables. ~

It's a pity that you have already bought the wireless adapters, because there is a simple alternative to Cat5 which is Powerline or [Homeplug networking]("http://www.homeplug.org/products") adapters.
These are plug-in devices which connect to your domestic electricity sockets, one beside the router and one each beside each device you wish to connect to the network and the data travels along your electrical wiring. 
These devices are literally plug and play and require no drivers.
A pair of them can be bought for under £40 (in the UK)

Next alternative is to buy a wireless router.
This will allow you to connect directly to the internet with the Mythbuntu PC.

The data throughput rate will not be as good for file transfers using wireless, which is why I would suggest powerline adapters if you need to transfer large files between your computers over the network.

As for a useful answer to 3, I'm sorry I haven't a clue.

---

### Post by chipppy on 2009-07-19
Good Morning

Thanks for the ideas.  I shall have a look at these possibilities as I am not having any luck with the wireless setup.

Do you have any hints for item 4 & 5.  The remote desktop application and how to setup internet sharing between the wireless (or whatsever method I end up with) and the main cable broadband?

Cheers
chipppy

---

