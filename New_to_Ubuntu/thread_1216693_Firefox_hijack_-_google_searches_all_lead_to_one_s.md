---
title: "Firefox hijack - google searches all lead to one site"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by shy_guest on 2009-07-18
I installed 9.04 on my Sony laptop a few days ago. It worked fine, but since yesterday I cannot access internet using Firefox because all my searches & bookmarks get hijacked. 

I go to the Firefox homepage OK but when I click on "bookmark", the next page is a French ISP website, Free which asks me for an access code. The web address of the page is my bookmark web address prefixed by [https://wifi.free.fr/?url=](https://wifi.free.fr/?url=)

Similarly, if I use the Firefox homepage to enter a search item for google, the next page is the same also prefixed by [https://wifi.free.fr/?url=www.google.com](https://wifi.free.fr/?url=www.google.com) etc.

I think a parameter must have been changed/updated to add this prefix, but I can't find anywhere in Firefox where such a parameter would be. 

It seems idiotically simple, but I don't have the knowledge to crack it.

Any ideas ?

---

### Post by wojox on 2009-07-18
Are you using free wireless internet?

You could type about:config into the address bar and look through there.

---

### Post by LewRockwell on 2009-07-18
Issues with Firefox...

[http://www.mozilla.org/](http://www.mozilla.org/)

perhaps...

.

---

### Post by Mornedhel on 2009-07-18
Hey shy_guest,

You aren't trying to log in to a FreeWifi wireless instead of your own Freebox's, are you ? FreeWifi redirects you to a portal where you log in, it's expected behavior. Just make sure you're connecting to your own Freebox. If you have never connected to its wireless yet, Ubuntu will try and connect to FreeWifi first since it's unsecured.

(Also a French user, and also using Free as an ISP.)

---

### Post by shy_guest on 2009-07-18
Free is not my service provider which is why I have difficulty where the hijack comes from.

I am using an orange Livebox.

---

### Post by Mornedhel on 2009-07-18
> **shy_guest said:**
> Free is not my service provider which is why I have difficulty where the hijack comes from.

I am using an orange Livebox.

Free doesn't have to be your ISP. Also, it's not a hijack ; what happened is simply that NetworkManager tried to do its job (connect to a network), found out that there were unsecured wireless networks around, and connected to one (FreeWifi). Then when you start Firefox you are automatically redirected to the FreeWifi portal for authentication since it isn't a service you can use without being a Free customer and having activated your own FreeWifi.

You probably just need to left-click on the NetworkManager icon in your notification area, select your own Livebox connection in the drop-down, and from there proceed roughly as you would in Windows.

Once you will have connected to your own network, NetworkManager will remember it and connect to it automatically whenever it's available. Right-clicking the NetworkManager icon and selecting Edit Connections, then Wireless will also allow you to delete the settings for FreeWifi which may be present since you technically connected successfully to it at least once.

---

### Post by shy_guest on 2009-07-18
Thanks very much, mornedhel. 

Simple & I feel a bit less daft now I know that. 

A few seconds before ubuntu had connected to the Livebox automatically with no problems. I guess I must have done something to make it lose its memory.

Anyway that's that frustration out of the way. Forward to the next frustration !

---

