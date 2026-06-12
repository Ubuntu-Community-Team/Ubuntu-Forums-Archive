---
title: "Cant get my internet to work for Ubuntu"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by chinja2 on 2009-07-23
I cannot get my internet to work for Ubuntu version 8.04 now that I have installed the software on my desktop. The internet also doesnt work when I boot from the cd. Can someone help me with this please.
 
Thanks

---

### Post by jrothwell97 on 2009-07-23
Welcome to the Ubuntu Forums!

How are you connecting to the Internet? Is it a wireless connection, or is it connected through a router or modem?

If it's wireless, please try and find out what kind of wireless card (the part of your computer used to connect to the Internet) you have. You can do this by clicking on Applications/Accessories/Terminal, typing the word "lspci" in the window that comes up and pressing enter (it might be labelled *return* on your keyboard).

If you then copy and paste the block of text that puts out into a post here so we can see it, we might be able to find out what's wrong.

---

### Post by Cheesemill on 2009-07-23
How are you trying to connect? Wired or wireless?

Can you post your network adapter details and computer specs, we have nothing to go on at the moment.

---

### Post by mapes12 on 2009-07-23
As the other posts have suggested we need some more info about your configuration. Go to terminal and enter these commands followed by the enter key:

```
sudo lshw
```

```
iwconfig
```

```
ifconfig
```

and post the output back here.

---

