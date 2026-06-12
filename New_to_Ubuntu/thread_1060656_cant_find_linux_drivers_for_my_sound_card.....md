---
title: "cant find linux drivers for my sound card...."
date: 2009-02-05
forum: New to Ubuntu
---

### Post by kingchipo on 2009-02-05
its an older sound card

made by Asonic 

Wave Breaker/opl4

model:a-gold


Found plenty of windows drivers for it but ubuntu drivers... nope... aparently the company is closed down because i cant find a manufacturers site either......


Anyone have any help ??

---

### Post by mpl34 on 2009-02-05
Hey,

I just had a look for any linux drivers and your right i didn't spot any. I'm just a newb too but i know you can install broadcom windows drivers with ndiswrapper so i suggest giving it abit of research may be a possibility.

---

### Post by kingchipo on 2009-02-05
Yea im gona take a wild guess and say there was never a driver rendered for linux i believe the sound card was made around 99?

maybe it was an unpopular one?

Also im REALLY new to linux and am used to a windows style hardware manager.. i didnt notice anything of the sort that i could find to tell me the name of the sound card i had to look manually. is there any type of hardware manager on the newest version of ubuntu?

---

### Post by kingchipo on 2009-02-05
really wish i could get this driver tonight any1 have any ideas were to find it?

---

### Post by kingchipo on 2009-02-05
bump?

---

### Post by handydan918 on 2009-02-05
How do you know you need drivers? 
Please post the output of ```
lspci | grep -i audio
```

---

### Post by qamelian on 2009-02-05
From the look of things [here]("http://www.testmyhardware.com/asonic.html"), it looks like Asonic were mostly C-Media cards. so I would be looking for advice here:> [http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media](http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media)

---

### Post by kingchipo on 2009-02-10
> **handydan918 said:**
> How do you know you need drivers? 
Please post the output of ```
lspci | grep -i audio
```

I get no output for it in the terminal just reups the location

---

### Post by kingchipo on 2009-02-10
Really need to get this sound card working.... if anyone has any ideas please post i got the computer in my hands now and really need help...

---

