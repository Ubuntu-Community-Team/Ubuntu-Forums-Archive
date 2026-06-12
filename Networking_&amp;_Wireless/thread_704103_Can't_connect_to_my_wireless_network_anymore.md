---
title: "Can't connect to my wireless network anymore"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by zirtik on 2008-02-22
Hi,

I have recently done a huge system update and after I rebooted I couldn't connect to my wireless network. I can see the list of the available networks in the network manager so I think it does not have anything to do with my wireless card driver. Strangely, when I try to connect to my home network it says "attempting to join the wireless network" and one of the blue lights turn into green but the other one still remains blue and then after like 45 seconds  it can't connect. I really need to fix this. Any help will be appreciated, thanks.

---

### Post by toa on 2008-02-22
i had some cases where the wireless icon shows its attempting to connect whic its already connected, may its connected already.

You might have some manual configuration to set, such as the key authentication Tkip or other.

What hardware update you made, might also change the settings, depends...

---

### Post by zirtik on 2008-02-22
> **toa said:**
> 
You might have some manual configuration to set, such as the key authentication Tkip or other.

How can I do it? Can you be more specific please?

---

### Post by toa on 2008-02-22
Well you said you made a huge network upgrade, an you didnt change ubuntu settings.

Think about it, each hub,router, piece of hardware has its unique MAC address and IP configured initially, in your case, i dont know the existing wireless network was it secured in having a pass key, which was configured with the new router.

So ubuntu with its existing settings is configured to connect xyz wireless network name (hidden or not) with IP x.x.x.x and pass code x.x.x.x and in addition to that, a fire wall enabled which recognizes ip x.x.x.x

The whole thing is, you have to reconfigure your wireless conection once again... maybe im going far, but it depends on your previuos wireless setting.

---

### Post by zirtik on 2008-02-22
I think there is a misunderstanding here. I did not say I did a huge network update I said I did a system update. Actually, all I did was to install 150 MB of update packages that synaptic suggested me to do. So I guess there should be an easier work around since I did not change any of my network settings, right?

---

### Post by zirtik on 2008-02-22
Any ideas please?

---

