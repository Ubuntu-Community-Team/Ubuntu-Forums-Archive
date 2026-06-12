---
title: "dual boot ubuntu to save battery"
date: 2011-06-04
forum: New to Ubuntu
---

### Post by Drummingasm on 2011-06-04
I'm going to get my new laptop for college in a few days, and i want to know if i can duel boot into ubuntu.
the computer im buying is ([http://www.newegg.com/Product/Product.aspx?Item=N82E16834215004&Tpk=as5750g](http://www.newegg.com/Product/Product.aspx?Item=N82E16834215004&Tpk=as5750g)) except i will buy 8gb ram instead of the 4gb.

specs: 
proc: i7 2630qm (quad at 2GHz)
GPU: NVIDIA GeForce GT 540M (1 GB)
Memory: 8GB DDR3

I heard some bad things about trying to use ubuntu with an i7 processor, will i have a problem? 
The main reason i want to install linux on my computer is to save my battery. Is it possible to set up the BIOS to only run like 1 core of my 2630qm when i start up linux? Will this be sufficient to run ubuntu? The computer i'm buying says it has 4.5 hours of battery, so i assume ~3-3.5 hours of battery for realsies. Can i expect an increase in battery life by dual booting into ubuntu?

I plan on using ubuntu just for taking notes in class, and windows for hard core computing (science major) + games (teenager). Therefore, all i need from ubuntu is some equivalent of Microsoft word and excel, a browser (i'm going to use chrome), and AIM. (side note, is it possible to download files to a different partition? As in, can i download windows files in my ubuntu partition to my win7 partition?)

Last, how big should my partition be for ubuntu if all the stuff i said above is possible? I will have 8 gb ram, so i won't need page file (or w/e equivalent ubuntu uses, if it does)

I know i'm supposed to post one thread per question, but all my questions are closely related

Also i'm completely new to this forum and linux so please don't hate haha

---

### Post by wolfen69 on 2011-06-04
> **Drummingasm said:**
> 

I heard some bad things about trying to use ubuntu with an i7 processor, will i have a problem? 
It won't be a problem.
> Is it possible to set up the BIOS to only run like 1 core of my 2630qm when i start up linux? 
That depends on the BIOS, not ubuntu.
> Will this be sufficient to run ubuntu? 
Yes.
> Can i expect an increase in battery life by dual booting into ubuntu?
That depends. People have mixed results with battery life.

> side note, is it possible to download files to a different partition? 
Very easy to do.

> Last, how big should my partition be for ubuntu if all the stuff i said above is possible? 
That's a personal choice. I would give it at least 40gb of space, but that's up to you.
> I will have 8 gb ram, so i won't need page file (or w/e equivalent ubuntu uses, if it does)
In linux, it's called swap.

> Also i'm completely new to this forum and linux so please don't hate haha
Welcome aboard!

---

### Post by idoitprone on 2011-06-04
I give you a tip. Try not to avoid kernels 2.6.38+. there is a power regression that hit linux badly. That means you should not use natty which uses the 2.6.38 kernel. If it does not work, then you are forced to use the recent kernel. I hope it get fixed for 2.6.40 kernel release. Since you may have intel HD, you probably do not need the newer kernels. If not and you have sandy bridge, then you may need the newer kernels

Why do you need more ram? 4gb of is all you need. More ram means more power to maintain it. As long as you are not swapping

About your nvidia card... linux do not have a viable alternative for nvidia optimus technology. So linux cannot randomly shut off the nvidia gpu and use the intergrated graphics depending on the load. Either use intel hd intergrated or nvidia full time. Using nvidia card will give you better graphics, but it will affect your battery life

---

### Post by Durden on 2011-06-04
There is an app for Optimus on linux
[http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/](http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/)

still under development but it helps.

---

### Post by idoitprone on 2011-06-04
please note the "viable" in my wording. I hope it does get developed and polished

---

### Post by Durden on 2011-06-04
How is it not viable? It works, seems viable to me. Just doesn't work automatically, that's all.

---

