---
title: "installation via Internet, no cd-drive"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by wmtabada on 2008-12-19
I am new to Edubunto and I have problem installing Java in it. I tried to install it using the following command :

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin

and I was asked to put the Edubunto 7.10 installer CD to the CD drive. The problem is that CD drive was damaged a week ago. Is there a way to install Java or any software  through the Internet without the CD. My computer is connected to the network with Internet via proxy server. Hope somebody could help me on this. Thank you.

---

### Post by halitech on 2008-12-19
probably just need to comment out the cd in your sources.list file.

can you post the output of 
```
cat /etc/apt/sources.list
```

---

### Post by hyper_ch on 2008-12-19
you need to uncomment the cd as source. You can do this in Synaptic.

---

