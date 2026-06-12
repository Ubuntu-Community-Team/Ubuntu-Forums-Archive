---
title: "Can no longer share files Ubuntu to OSX after snow leopard update."
date: 2009-09-09
forum: New to Ubuntu
---

### Post by powel212 on 2009-09-09
I am using System-config-samba to share files out from Ubuntu. 

Before updating to OSX 10.6 I could easily share files back and forth between Ubuntu and OSX but after the upgrade OSX can only see the Ubuntu share but can't access the Share folders.

Anyone else experience this and find a solution.

Any help is a apreciated.

Powel

---

### Post by Clordio on 2009-09-09
One of the biggest things with the latest osx upgrade was the size reduction due to installation. How did they reduce it so much? By extensively altering the way data is stored on the osx system.

In fact, I believe the previous osx has a hard time reading files from the new one as well. It's almost a new filing system entirely. Let me see if I can find the article to better explain it. Uno momento

---

### Post by Clordio on 2009-09-09
Here it is, this is the Ars Technica review on the new OSX and on this page they talk about how the filing has changed with the new installation. It's a rough read but I believe this is the cause for your problems.

[http://arstechnica.com/apple/reviews/2009/08/mac-os-x-10-6.ars/3](http://arstechnica.com/apple/reviews/2009/08/mac-os-x-10-6.ars/3)

You might want to take a look at the whole review when you get a chance (23 pages!) to get a better idea of your new operating system.

Until further notice though, I'm willing to bet this will require some alterations with the linux kernel to be able to identify these files from linux.

---

