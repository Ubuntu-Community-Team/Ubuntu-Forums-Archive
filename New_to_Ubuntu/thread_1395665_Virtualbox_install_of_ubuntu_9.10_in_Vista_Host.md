---
title: "Virtualbox install of ubuntu 9.10 in Vista Host?"
date: 2010-02-01
forum: New to Ubuntu
---

### Post by nooby on 2010-02-01
I have a frugal install of Ubuntu 9.10 on my vista HP/Compaq that works very well except it doesn't save changes and most likely would crash if I did allow updates? 

Somebody suggested that Vbox would be a safe way to learn to do updates and downloads of new programs to linux ubuntu and to test many different OS together and them not disturbing each other. 

So here I am in Ubuntu 9,10 within a Vbox and now ask. 
[B]
I am in the live cd now. So could I safely ask it to do a full install on the 8GB or something virtual HD and that would allow me to save changes? [/B]


So what I want is to know. If I click install then it only install on the virtual part and not the real Vista then? A kind of sandbox they named it? 

Did I get what tthey wrote?


I take back that Vbox works great. It crashed in streaming video. Maybe that was demanding more memory than I allocated for the vbox set up. I know nothing and only followed their suggestiosn. 


I am a newbie so I feel very unsure about these things. 

and don't tell me to read documents on vbox or ubuntu because I ahve a dyslexia that makes abstract text just blur out into words that I may guess what they mean one by one but totally fail to make a structured meaning of or how to apply them. I see all the words but just get confused. 

I sometimes can follow step for step instructions but that is nto to count on either. took much effort to get the vbox going but hopefully I remember some of the steps tomorrow.

---

### Post by mikewhatever on 2010-02-01
I've never heard a term 'frugal install', can you explain what that is.
A live cd sees you real and not virtual hard disk, so if you install, Ubuntu will go to a real and not virtual partition on a real hdd.
In order to install to a virtual partition, you need to load the installation cd or the iso image in the virtual computer, i.e., virtual box.

> **nooby said:**
> ..............
and don't tell me to read documents on vbox or ubuntu because I ahve a dyslexia that makes abstract text just blur out into words that I may guess what they mean one by one but totally fail to make a structured meaning of or how to apply them. I see all the words but just get confused. 

I sometimes can follow step for step instructions but that is nto to count on either. took much effort to get the vbox going but hopefully I remember some of the steps tomorrow.

In that case, perhaps it's best if someone did it for you. Step by step instructions are a wishful myth, given the number of variables one has to deal with.

---

### Post by J V on 2010-02-01
Your "Frugal install" is more likely a live cd, actually installing it would be a start...

---

### Post by nooby on 2010-02-01
Depends on what you refer to. you mean that I resize the windows partition and then format that one to ext3 or something and then install linux on that partition? 

But that is not my goal. My goal is to keep Vista as it is. 

[B]But can I do an install to the virtual HD that vbox created? 

How can I be sure of that it doesn't change vista? [/B]

Would that make it faster? 

I tried out a remix in Swedish two times now and that one are incredibly slow compared to teh english version so don't know what they did to make it that slow. I have to ask them.

---

### Post by mikewhatever on 2010-02-01
Here is a very good howto you can follow, hope it helps.
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

Here is another: [http://www.wikihow.com/Install-Ubuntu-on-VirtualBox](http://www.wikihow.com/Install-Ubuntu-on-VirtualBox).

Hopefully, they don't qualify as abstract text.

---

### Post by nooby on 2010-02-01
Thanks I take a look at them. I report back maybe in  few days if I managed to make use of them. Thursday maybe? Remind me if  I forget. Just now Iam totally immersed in trying toget frugal to save. I write from frugal install now. Works very well. 

in virtual the firefox crashed on full screen of streaming video from TV statiosn but in frugal it is as fast as on full install and all survives. 

but updating may crash though. So I avoid such.

---

### Post by nooby on 2010-02-01
> **mikewhatever said:**
> I've never heard a term 'frugal install', can you explain what that is.


I try, DSL Damn Small Linux named it Poor Man install IIRC? Knoppix named it cheat codes? I could be wrong but both these could do it that way. 

Slitaz that is based on Slack could even boot the iso as it is. 

That is what Virtualbox does. It open the iso and find thefiles it need to expand. 

But UNetbootin that do frugal install to USB they make use of two files that help them boot. vmlinuz and initrd. kernel and boot intit. 
Then you have other files one need too. In puppy they are in the .sfs format. I guess it is named UnionFS. But I barely get what that is. usually in 2fs or 3fs formatting but squashed to be small. 

> 
In that case, perhaps it's best if someone did it for you. Step by step instructions are a wishful myth, given the number of variables one has to deal with.



Yes it sounds scare to do a lot of partitioning even if it is all virtual. Virtual is just a word what if the Checksum for the hdd changes? Then I lose my windows. :) I guess all the linux supporters would cheer and say. Yeah that is Cold Turkey to you. There stay with it and never go back

---

