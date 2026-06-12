---
title: "Belkin F5D7050 Version 2000 - Please help!"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by belkin on 2010-04-20
Hi,

I am an absolute beginner to linux and Ubuntu.  I really need help from someone who knows what they're doing or have been in a similar situation and can help.  I can't get my Belkin USB Wireless G Adapter Model: F5D7050 Version 2000 to work with Ubuntu.  It finds and lists the WI-FI networks in the list, but when I try to connect to my network, it just hangs for a while and displays the message that it is disconnected.  There is nothing wrong with the adapter or my wireless network.  It works perfectly on windows.  I have searched the forums all over the web, but I can't find the driver.  Quite frankly, even if I did find it, I wouldn't know how to install it from the terminal.  If anyone has been able to get their adapter to work, I would really appreciate some help.  I really, really love Ubuntu, but I would hate to have to go back to Windows because of this.  Please help me before the 10.04 LTS comes out.  Thank you!  PS. the version is 2000.

---

### Post by anewguy on 2010-04-20
Obviously you already have some form of a working driver, or you wouldn't be able to see any networks.  So, the questions then become what type of connection is being attempted, whether the driver that is currently running supports that type of connection, etc.:

- does the network you are attempting to connect to have some sort of encryption, like WEP or WPA enabled?  If so, have you gone into network manager and created a new connection with the proper type of encryption and password/passphrase provided?

- does the router which you are attempting to connect to have MAC filtering enabled, and if so, has your computer's MAC address been added to the list?

- version and release of Ubuntu are you running?

Dave ;)

---

### Post by belkin on 2010-04-20
Hey Dave,

Thank you very much for your reply.  As far as the encryption goes, I have a WPA/PSK - TKIP encryption and my router has the MAC address filtering DISABLED.  I haven't setup a connection from the network manager.  I assumed you could just select the network you wanted to connect to from the panel on the desktop and just enter the passphrase there.  Because I believe I tried setting up a network connection from SYSTEM or PREF --> NETWORK CONNECTIONS in version 9.10 karmic koala and it didn't work.  Last night I tried the 10.04 lucid lynx beta 2 and that didn't work either.  Like you said, there must be a working driver or I wouldn't see the networks.  I guess the only thing I can think of then, and correct me if I'm wrong here, is that Ubuntu has trouble connecting to WPA networks.  Or do I need to go into terminal and manipulate the system configuration files with the ifconfig commands or something.  Any feedback would be very much appreciated.  Thanks.

---

### Post by Paddy Landau on 2010-04-20
I have the same Belkin F5D7050 (I don't know about the Version number, though; I don't see it on my adapter) running on a machine with Xubuntu 9.10.

It worked out-the-box without any tweaking, successfully connecting to my router using WPA2 Personal security.

Try it with a Live CD with Xubuntu to see if that works; perhaps there's some difference between Xubuntu and Ubuntu.

Before you installed Ubuntu, did you try it from a Live CD?

I wonder what router you're using? I used to have a D-Link, and the particular model that I had was incompatible with Belkin (bizarrely).

One more thing. You say that when you try to connect, it waits for a while and then fails. Does it not ask you for the TKIP passphrase? You could try (temporarily) disabling security to see whether it connects. Remember to enable security again afterwards.

---

### Post by belkin on 2010-04-20
Hey Paddy Landau,

I did try it using the live CD, but I've never been able to connect.  When I select my network from the list, it does prompt me for my password.  But like I said, then it just hangs for bit, and then says wireless is disconnected.  I know that some other versions of this adapter work right out of the box.  Unfortunately, I guess I went out and bought the exact version that doesn't work.  I really want it up and running before the 10.04 final comes out on the 29th.  I can't think of anything else I might be doing wrong.  Please let me know if you can think of anything else.  Thank you and take care.

---

### Post by Don Mega on 2010-04-20
have you tried going to update manager and installing updates after a reboot with wireless adaptor on?

---

### Post by belkin on 2010-04-20
Yes, I have all the updates installed.  But it still won't connect.  I was able to get online when I installed it inside virtualbox.  But it won't work as a regular install or through live cd.  Any other ideas?  Thanks.

---

### Post by anewguy on 2010-04-20
I don't think it's the driver - you obviously have a working driver when you can see and select your network.  However, perhaps the driver doesn't support the type of encryption you are running.

Paddy Landau mentioned the 1 thing I always have someone try when they are in this situation:

- go to your router's config page and temporarily disable any encryption, no WEP, now WPA, just an "open" network.

- on your Ubuntu machine, go to network manager and check for saved connections for your network.  If there any, delete those.

- now try just clicking on your network and see if it connects.

If this does work, it tells you either the driver doesn't support the encryption you are trying, or as much as you are trying, you haven't selected the correct type in the connection box from Ubuntu and/or you haven't entered the password correctly.  I normally would advise you to go to network manager, select "create new wireless network", and fill in that screen.  Be sure to check "show key" so you can see what you are entering to be sure it matches your router.

Dave ;)

---

### Post by belkin on 2010-04-21
Hey everyone,

Thanks for all your comments.  I will definitely try to connect without any encryption.  For now though I'm just going to wait for the final version and see if it takes care of it itself.  But thank you very much for your help.

---

