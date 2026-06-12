---
title: "Do I need SWAP?"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-01-02
Hello again,
I'm about to install Ubuntu 10.10 on my sister's new laptop. It is 64 bit 2.6Ghz processor with 4 gigs of RAM.

It has a good deal of RAM, so should I still put Swap as a partition or not to worry about it? Also, how much swap (if needed)?

---

### Post by AlphaLexman on 2011-01-02
From the specs you quoted, unless she has a really small harddrive (lessthan 20Gb) by today's standards, and I doubt she does... I recommend a swap partition equal to your RAM = 4Gb.

---

### Post by cheapie on 2011-01-02
Swap is always optional, but highly recommended. Without it, if you run out of RAM, the kernel will panic (a.k.a. crash). If you decide to have swap, I'd recommend 8-12 GB. My computer has 2 GB of RAM and 5 GB of swap.

---

### Post by Bucky Ball on 2011-01-02
Not sure where the others are coming from with their /swap sizes, but generally any more than 2Gb is overkill.

Wise to have a /swap, regardless of the fact you will hardly ever use it. You have 4Gb of RAM. /swap the same size as that is Windows thinking. ;)

cheapie: 8-12Gb??? Please explain!

---

### Post by skyzthelimit230 on 2011-01-02
Thanks guys, I usually skip creating a swap partition on my computer, but as this is my sister's first real intro to open source software I want ti to go smoothly :)

---

### Post by howefield on 2011-01-02
You'll need more swap than Ram if you plan to use the laptops suspend/hibernate features.

---

### Post by HermanAB on 2011-01-02
Howdy,

You need /swap = 2xRAM for suspend to work, which is rather important on a laptop.

---

### Post by heyandy889 on 2011-01-03
found the frequently asked questions about this. first google result for "swap partition."

Community Ubuntu Documentation - Swap FAQ
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

edit: The deal with RAM size relating to swap size and hibernation: when your computer hibernates, the power goes off, meaning that you lose any data stored electrically in RAM?

---

### Post by cariboo on 2011-01-03
When using hibernation, the system writes an image of the system in it's present state to the hard drive, there isn't anything stored in ram. Using suspend the image is written to ram, when the power is disconnected/lost that image in ram is gone.

---

### Post by aysiu on 2011-01-03
> **howefield said:**
> You'll need more swap than Ram if you plan to use the laptops suspend/hibernate features.
Hibernate, yes; suspend, no.

If you hibernate, you need twice the RAM for swap.

If you just suspend to RAM (aka *sleep*), you don't need swap at all, especially with 4 GB of RAM.

---

### Post by NightwishFan on 2011-01-03
2-4gb of swap will work quite fine. You will hardly use it but it will there when needed. I love swap to push useless stuff out and have more ram for cache, especially with VMs. :)

---

### Post by hunter99507 on 2011-01-03
Just out of curiosity does windows use a swap?

---

### Post by Elfy on 2011-01-03
> **hunter99507 said:**
> Just out of curiosity does windows use a swap?pagefile 

To answer the question - if you have the space and I suspect you will have it's better to have the swap and find you don't need it than to not have it and find you do.

---

