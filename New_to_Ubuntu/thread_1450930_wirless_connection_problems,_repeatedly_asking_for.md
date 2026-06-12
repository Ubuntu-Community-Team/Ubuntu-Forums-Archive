---
title: "wirless connection problems, repeatedly asking for network key, cant connect"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by skyeric on 2010-04-09
Hey,
I installed Ubuntu on an old desktop last night and am having some  problems with my wireless connection. I've searched around a bit and  tried a few solutions but nothing seems to be working so hopefully  someone can help.
I'm using a Netgear WG111v3 wireless USB adapter and am attempting to  connect to a Sky Broadband modem, the connection shows up in the list of  avaliable networks after clicking on the network symbol and after  attempting to connect for a while it then asks for the WPA password. I  enter the password and then this repeats over and over again  continuously asking for the password and me continuously entering it. I  know the password is correct as I'm using it on my laptop and other home  computer right now. I've tried connecting to a hidden wireless network  and inserting the network name and password as some have suggested and  I've also tried adding the details from my router into the connection;  so that I have manually entered the information rather than  automatically finding it, this also hasn't worked.
I should probably add that earlier today I seemingly randomly got  connected and then managed to run some updates but since then it has  disconnected and the same problem is repeating over and over.
Sorry if thats quite a long  explanation but I thought I'd try and make  it as clear as possible,
Any help or suggestions greatly appreciated.

---

### Post by anewguy on 2010-04-09
A couple of quick questions:

- What version of Ubuntu are you running?

- If you set your router as an open network to test, are you able to connect?  This would tell us it is definitely something with WPA, etc..

- And, forgive me but I've messed this in the past, have you selected the correct WPA type and password/passphrase type?

Dave ;)

---

### Post by skyeric on 2010-04-09
hey thanks for the help,
my version of ubuntu is 9.10, how do i set it to an open network? sorry never had any issues with networks before so havent needed to look into it. Yes i've definetly got the right securtiy type, on the laptop im connected to the network on now it says 'WPA Personal' and i've selected 'WPA & WPA2 Personal' as the security type on ubuntu.

---

### Post by anewguy on 2010-04-09
On the router setup page you should be able to select an option that has no WEP, WPA, etc. - this would be an open network at that point.

Also, do you know if the router has MAC filtering?  Perhaps you need to enter the MAC of your PC into the router MAC list.

Dave ;)

---

### Post by skyeric on 2010-04-09
Okay I unsecured my network and then sure enough it connected straight away, I'm now sat in a unsecured little bubble.. panic!
Unsure about this MAC stuff I'm afraid, earlier I was looking at my router setting and found the MAC address of my ADSL port and then inserted that into the wireless setting on Ubuntu, is that related?
thanks so much for this help by the way I have been struggling all day with this

---

### Post by anewguy on 2010-04-09
I would first clear the MAC list, if there is one, on your router - we can set that up after getting the rest to work.

Next, I would set back to WPA/PSK-AES on the router, being sure to note the password you used (remember - everything is case sensitive both on the router and on Linux).

Then, edit the connection in Ubuntu (it will still think there is no key needed from when the network was tested open), and set to WPA/PSK-AES and use the exact password (and case) as you did on the router, and try connecting again.

If that works, you may need to edit the connections on your other PC's that use the same router since you probably changed either the type (WPA/PSK-AES) or the password (unless you were lucky!).

Once you have everything working, then we can go add the MAC addresses to the router for an extra layer of security.

dave ;)

---

### Post by anewguy on 2010-04-10
I just thought of something I thought I'd check on - is it really saying the WPA key is needed, or is it saying the network keyring password is needed?

Dave ;)

---

### Post by spiky001 on 2010-04-10
It could be the network keyring it is asking for try putting the corect password in there

---

### Post by anewguy on 2010-04-10
> **spiky001 said:**
> It could be the network keyring it is asking for try putting the corect password in there

That's why I posted above - it could very well be that.  If so, you want to enter either (a) your normal login password or (b) the first password you entered when it first prompted you.

It's also possible to clear out the keyring password and set it up again.

Again, just let us know as per my above post if it asking for the WPA key specifically (I seem to remember that if that key is incorrect it just tries for a while, then gives up and doesn't connect), or if it is asking for the network keyring password.

Dave ;)

---

### Post by skyeric on 2010-04-10
well after putting the security back onto my network and then restarting my ubuntu computer it connected fine? I've tried this a few times now and although I really don't know how this has worked I'm not complaining, I reused the original password and security type when I put the security back on the router but still, not sure how this has happened.
Do you still think its worth adding the MAC addresses for security? Not really sure how to go about this, I can look at the attatched devices to the network by looking at my routers settings but not sure how to edit..
thanks so much for the help by the way this has been so helpful,
oh and on another note - when i restart my ubuntu computer I have to unplug and plug back in my wireless USB adapter before it starts working, this isn't a major problem and is basically me being lazy but if you have a quick solution it would be greatly appreicated.

---

### Post by anewguy on 2010-04-10
Not sure on the reason you would need to unplug/plugin the adapter on a restart - I'll try to do some searching on that and see if I can find anything that makes any sense to me.

As far as MAC filtering - it depends on how secure you want your wireless network.  With the proper tools, WPA can be cracked quickly as well (not as quick as WEP though).  MAC filtering adds another layer by saying the only devices that can connect to the router have these hardware addresses (not IP addresses).  With the proper packet snooping tools MAC can be cracked and MAC spoofing done to get into your network.

The thing is, all of this takes work, some of it a lot of work, to crack.  Basically you need to look at where you are located and if there is a higher risk of people wanting to get on your wireless network to do bad things.  If you think that risk is high enough, we can add MAC filtering.  If you want, I'd suggest reading the net a little on MAC in general and filtering.  Then see you router's manufacturers web site to see if they offer any instructions.  Usually it's a matter of adding the MAC address of each computer to the list in the router.  This sometimes can be done by having all the devices connected to the router, then using one of them to access the router setup page.  On my particular router you can then add the MAC address of connected devices simply by clicking on them - you don't actually have to find and enter the entire MAC address.

Glad things are working.  My suspicion, and I say this with all respect because I've been there many times, is that even though you thought you were entering things correctly, at some point something was entered incorrectly and was remembered by network manager.  It can get frustrating, so thanks for sticking with things and getting it fixed.

Dave :)

---

### Post by skyeric on 2010-04-10
Okay I'll look up MAC filtering seems like I have nothing to lose by using it really.

Yea thanks that would be great, as I said its not really a major effort for me to bend down and unplug it and plug it back in it just seemed a bit weird to me as to why it was happening.

Thank you SO much for your help you've been so helpful, and yea once it was working I had a look in network connections and their were about 7 or 8 different connections I'd fiddled about with so guess it was getting quite confused there, once again - thanks a lot!

---

