---
title: "[SOLVED] Mobile Broadband and NetworkManager 0.7, Help Needed!"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by Plumtreed on 2008-10-24
I am running NetworkManager 0.7 in Hardy and it works well but I don't know how to set it up for 'mobile broadband'. I usually have to use GnomePPP to get on the net via my Huawei 160G.

Does any one know how to configure NetworkManager so that it works with 'mobile broadband'. It seems to detect it and all those things but I feel I just need to feed Network Manager some additional information.

Just how is it supposed to work???

---

### Post by Crandom on 2008-10-24
Right click on the Network Manager icon in gnome and click "Edit Connections". Click on the "Mobile" tab and then "New Connection". Follow the wizard to set up a new connection.

---

### Post by Plumtreed on 2008-10-24
Thanks Crandom, I did get that far and have responded to the 'wizard' but I really don't know what answers are really essential. In fact, all I filled in were the user and password. 

I am in the UK now, using the 3 network but I am not sure that I always have good 'reception'. Everything seems a bit flaky so that I don't get a constant that I can focus on. 

I think that on one occasion I had a successful 'hit' with my wireless disabled and my mobile broadband came to life! The icon turned to the blue twirlie bit and found the mobile connection. I haven't been able to replicate it.

Can you tell me how you choose to conect to your mobile broadband? When does the 'dongle' go in? Does it always play nice?

---

### Post by Plumtreed on 2008-10-25
I guess I have sorted things out! I now gain access to wired, wireless and 'mobile broadband' through NetworkManager...very neat and tidy. 

There is an awkward step to 'mobile broadband' to find the correct interface because another "drop-down' menu crops up at first but it is not effective. I need to shut it down and try again in order to bring up the right menu. 

If you plan to continue with Hardy, as I do, I suggest you upgrade to NetworkManager 0.7 for Hardy, well worth it!

---

### Post by RMOP on 2008-11-11
Congratulations. I'm still using wvdial for my 3G phone/modem connection with 8.10. I'd like to handle everything through NM, but even after setting up the Mobile Broadband connection, I can find no way to actually *use *the connection from NM.

How did you select the connection for use?

> **Plumtreed said:**
> I guess I have sorted things out! I now gain access to wired, wireless and 'mobile broadband' through NetworkManager...very neat and tidy. 

There is an awkward step to 'mobile broadband' to find the correct interface because another "drop-down' menu crops up at first but it is not effective. I need to shut it down and try again in order to bring up the right menu. 

If you plan to continue with Hardy, as I do, I suggest you upgrade to NetworkManager 0.7 for Hardy, well worth it!

---

### Post by RMOP on 2008-11-11
And I suppose I do, partly. I was thinking that my 3G phone/modem could now be handled from NM, and that was on my mind when I saw Mobile Broadband. But, it's now clear that this is about the (yeah, I know...) Mobile Broadband USB modems.

> **Plumtreed said:**
> I guess I have sorted things out!

---

### Post by lobner on 2008-12-02
> **RMOP said:**
> 
How did you select the connection for use?

To do this you have to select "PC Suite" on your phone, when asked when connecting the USB cable.

If you do this, the new connection will aper :D

---

