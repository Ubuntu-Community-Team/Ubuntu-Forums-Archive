---
title: "Network problem..."
date: 2010-12-24
forum: New to Ubuntu
---

### Post by ramoj02 on 2010-12-24
First of all, thanks for viewing this post.

I'm having a very frustrating problem on my Acer Aspire One netbook. I installed Linux Mint on it a few weeks ago and everything were working great until the network kept disconnecting for some reason. I tried resetting my router, resetting it to default and everything and my netbook still keep on disconnecting to my network. My other laptops with Windows don't disconnect so I know it's not my router. So I decided to install Ubuntu on my netbook, and it did the same thing, it keeps on disconnecting from my WiFi network. And since Linux Mint is based on Ubuntu, I thought it might be a driver problem installed by Ubuntu (or Linux Mint) by default. The internet would work fine for about 15 minutes and disconnect and would never connect again, unless I restart the netbook. I'm still using Linux Mint 10, and I tried installing Ubuntu 10.10. I sure hope it's not a hardware problem. :( Any help would be greatly appreciated.

---

### Post by TeoBigusGeekus on 2010-12-24
What is the model of your wireless chipset?
```
lshw | grep net
```

---

