---
title: "Can not connect to other devices on locak network"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by jgpacc on 2010-09-05
I have just installed Ubuntu 10.04 on a Dell laptop.  One of the first things I want to be able to do is to access files mostly media on my Windows server and on a NAS.  I found that I am not able to connect to anything on my network. Can't see any other devices.

I am connected thru a router.  I am able to get to the internet.  I have on my local network a W7 desktop, a W2003 server, W7 media server and a NAS.  I am not able to see any of then in Network from Ubuntu.

I can see my Ubuntu laptop on my router DHCP assignment list and I am able to ping the W7 machines from Ubuntu.  But that is about all.  After playing around for hours I did see Ubuntu show up on my network list in W7.  But I could not do anything with it.  Now it is gone off the list and I don't know how I got it to connect that one time.

Ultimately I would like to use Ubuntu as my media server, I am just learning right now using an old laptop.

---

### Post by gldearman on 2010-09-05
I've had a few bugs with my NAS, too (though less in Ubuntu than in Win7).

So, you cannot see anything in the network.  Can you connect to it anyway, by specifying the host you want to connect to manually?

Try connecting via Places > Connect to Server.  Select service type "Windows share," type the location of the share under "Server", and then click "Connect."  See if you can connect, even without seeing the shares in Network.  Start with the NAS, since you shouldn't have to worry about sharing settings in Windows or firewall settings for the NAS.

With my NAS, I had to use the IP address of the share to connect instead of the share name (so, under "Server," I typed "192.168.1.1/USB_Storage").  Do the devices on your network have fixed IP addresses? And are those addresses in /etc/hosts on you Ubuntu machine?

Also, make sure that your Ubuntu machine has a fixed IP address, and that you have added that address to the trusted zone on the firewalls of your Windows computers.  To use Ubuntu as a server, it would probably help to have that machine in the hosts file on the Windows computers, but I don't happen to know where that file is.

Hope this helps!

---

### Post by sandyd on 2010-09-05
> **gldearman said:**
> I've had a few bugs with my NAS, too (though less in Ubuntu than in Win7).

So, you cannot see anything in the network.  Can you connect to it anyway, by specifying the host you want to connect to manually?

Try connecting via Places > Connect to Server.  Select service type "Windows share," type the location of the share under "Server", and then click "Connect."  See if you can connect, even without seeing the shares in Network.  Start with the NAS, since you shouldn't have to worry about sharing settings in Windows or firewall settings for the NAS.

With my NAS, I had to use the IP address of the share to connect instead of the share name (so, under "Server," I typed "192.168.1.1/USB_Storage").  Do the devices on your network have fixed IP addresses? And are those addresses in /etc/hosts on you Ubuntu machine?

Also, make sure that your Ubuntu machine has a fixed IP address, and that you have added that address to the trusted zone on the firewalls of your Windows computers.  To use Ubuntu as a server, it would probably help to have that machine in the hosts file on the Windows computers, but I don't happen to know where that file is.

Hope this helps!
------------------------------
Ill give you the answer.

but first, please im not here to argue wether winbind is the way to go or not (We already had this in another thread, so im adding this as a warning). If it works for a user, it works, no questions asked.
----------------
There seems to be issues with local network DNS resolution, especially on kermic, so install the winbind program
```

sudo apt-get install winbind
```

---

### Post by jgpacc on 2010-09-05
Using the IP address I was able to connect to my NAS and to W7.  So now I can make some progress.
Thanks.....

---

