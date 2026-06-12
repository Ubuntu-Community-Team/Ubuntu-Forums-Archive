---
title: "TEW-443PI Wireless Problem"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by nils234 on 2007-12-17
Hello,

I'm a total newb when it comes to linux, so I thought: "lets pick out hardware that's uber easy to install". So I did, I bought a TEW-443PI ( whitch has the atheros chipset ). It was said that it works out of the box, no extra installtion required. Well that's not quite true. Put it in. Installed linux. No wirelles. I open network manager, it doesn't give me the option for a wireless network? Only wired and modem. Went on searching the net it said I had to use madwifi drivers. So I download the tar, extract, cd into the folder. The first I had to do according to the manual was typing "make" to compile it. So I did. It starts what it's supposed to do, but when it's "done" I look at the result and it has errors all over the place. cant find this, that doesn't exist etc etc. And I'm pretty damn sure it's the complete archive and it was extracted completely. And yes, I used the sudo thingy :P. Can any1 please help as to why nothing seems to work :( thanks

---

### Post by coolbrook on 2007-12-17
Any luck?  Do you know what hardware version you're using?

What do you see when you type *lspci* in terminal?  What about *lspci -n*

---

