---
title: "where to fix my graphics card.. pics of my motherboard attached.."
date: 2009-02-28
forum: New to Ubuntu
---

### Post by luckydeveloper on 2009-02-28
hi,

i am planning to buy a graphics card.. but i am newbie.. dont know where to fix it in my mother board.. i also dont know what type of graphics card i should buy..........

i have attached the pics of my motherboard taken with my mobile camera.. please see to that and help me to buy a new good graphics card...i guess i dont have a agp slot..

Do i have a pci express slot ???

please help

---

### Post by linuxisevolution on 2009-02-28
> **luckydeveloper said:**
> hi,

i am planning to buy a graphics card.. but i am newbie.. dont know where to fix it in my mother board.. i also dont know what type of graphics card i should buy..........

i have attached the pics of my motherboard taken with my mobile camera.. please see to that and help me to buy a new good graphics card...i guess i dont have a agp slot..

please help

You need a pci type card. No pci express. This one isn't bad:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130188](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130188)

---

### Post by linuxisevolution on 2009-02-28
> **luckydeveloper said:**
> hi,

i am planning to buy a graphics card.. but i am newbie.. dont know where to fix it in my mother board.. i also dont know what type of graphics card i should buy..........

i have attached the pics of my motherboard taken with my mobile camera.. please see to that and help me to buy a new good graphics card...i guess i dont have a agp slot..

please help

You put it in the white thingies that look like credit card readers :lolflag:

Seriously, I had a guy from a computer shop tell me that four years ago, and look where I am now :P

---

### Post by luckydeveloper on 2009-02-28
what is the difference between pci and pci express... what about AGP..do i have an AGP slot.. i want atleast 512mb memory card..

---

### Post by luckydeveloper on 2009-02-28
please tell me clearly.. do i have a pci express slot ? coz i have to buy the correct type of card

---

### Post by overdrank on 2009-02-28
> **luckydeveloper said:**
> please tell me clearly.. do i have a pci express slot ? coz i have to buy the correct type of card

Hi and it would appear those are not pcix slots. To make sure get the model of the motherboard and find the manual.

---

### Post by louieb on 2009-02-28
The AGP slot is usually brown and looking from the back its usually to the left of the white pci slots. Looks like you have a card in it now. But can't tell from your picture if its an AGP slot or pci-e. Your best bet is to just google your mother board and find a diagram.  Look around on the mother board you should find a model number you can use for your Googe search.

---

### Post by luckydeveloper on 2009-02-28
how do i find whether i have a pci or pci express slot..?? i cant find any manuals for my intel 865G motherboard...

---

### Post by mc4man on 2009-02-28
Run this (copy and paste into a terminal) and then look in your home folder for hardware.html, should list your motherboard in a section at the beginning 
```

 sudo lshw -html > hardware.html
```

This will tell you what your current display adapter is

```
sudo lshw -C display
```

---

### Post by luckydeveloper on 2009-03-01
in my motherboard.. there is one area marked as AGP 8X ........... but neat that.. there are just holes..(you can see this in the last picture) no brown color slot is there.. 

can we take the motherboard out and fix the AGP slot.. and then fix a AGP graphics card in it..???

---

### Post by louieb on 2009-03-01
Does the attached look like your mother board?
The specs are here [http://www.intel.com/design/motherbd/rh/index.htm](http://www.intel.com/design/motherbd/rh/index.htm)

Wonder what happened to the AGP connector?

---

### Post by diablo75 on 2009-03-01
This will help:

[IMG]http://reference.techpowerup.com/wiki/images/1/10/AGP_PCI_PCIE_PCIEx1_Bus.jpg[/IMG]

---

### Post by bwang on 2009-03-02
[This]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814139038") is a very nice PCI card, and not very expensive either. Or try [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814187041") if you want something cheaper.

---

### Post by linuxisevolution on 2009-03-02
> **luckydeveloper said:**
> what is the difference between pci and pci express... what about AGP..do i have an AGP slot.. i want atleast 512mb memory card..

The amount of memory in the card does not matter most of the time. Most cards for pci or agp will never be able to make use of the whole 512mb anyway. I very fast pci at 256mb is better than 512mb.

---

