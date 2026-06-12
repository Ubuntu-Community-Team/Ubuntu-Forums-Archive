---
title: "Intel i3 vs i5 and Ubuntu"
date: 2011-08-21
forum: New to Ubuntu
---

### Post by joe4ska on 2011-08-21
Hello everyone,

I'm considering building my own system. I was hoping the Ubuntu community had some insight on i3 vs i5

I don't plan to dual boot the computer. This would be a linux only & future proof for about 5 years.

I'm torn between the i5 2405s & i3 2105 processors

Both offer Intel HD Graphics 3000 and run at 65 Watts

I'm also considering the i5 2500K but I have no interest in over clocking and would purchase an H67 motherboard to take advantage of the on board graphics.

Would there be any future benefits of an i5 processor making it worth the extra $80?

As Wattage goes when Ubuntu is running low cpu intensive actions like basic web surfing would the computer tend to use the same wattage if I were to buy a i5 2405s (65 Watts) vs i5 2500k (95 Watts)? The lower wattage is the only benefit between the 2 i5 models as they cost about the same and the 2500k is faster.

Does Ubuntu or any other linux distro even take advantage of a quad core processor?

Is comparing i3 to i5 even valid?

My goal is to run this with a SATA III SSD & a Standard HD. The most intensive thing I would do regularly is Youtube browsing and ripping DVDs I own to my phone. Eventually I may do some video editing.

I'm a web designer so GIMP and Inkscape would be used regularly.

Heck, if anyone has some AMD suggestions I'll listen but I don't want to  buy a video card so it must have on board graphics that willl work with  Ubuntu out of the box.

I look forward to everyone's feedback as I'm stumped as to the benefits and pitfalls.

Thanks everyone,

---

### Post by pqwoerituytrueiwoq on 2011-08-21
as for AMD go for there APU series they have a nice built in gpu
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103943](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103943)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103942](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103942)

there are dual core version but they are built into the board
sample budget system ($259.31) using a amd apu dual core
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811147131](http://www.newegg.com/Product/Product.aspx?Item=N82E16811147131) (comments say psu has 2 sata plugs)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820134718](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134718)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131732](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131732) (there is a upgraded version with hdmi)
[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.696142](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.696142)
promo codes EMCKBJD28,RWCASEAUG
you may want to add a pci slot cooling fan in it or mod a fan into the case

only thing i have had use all my 4 cores in a sound converter temp did not go over 46 C with 4 cores at 100%

during boot my ssd does not use it full speed it puss <200mbps it can pull 230-240 max

---

### Post by HeadHunter00 on 2011-08-21
> **pqwoerituytrueiwoq said:**
> as for AMD go for there APU series they have a nice built in gpu
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103943](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103943)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103942](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103942)

there are dual core version but they are built into the board
sample budget system ($259.31) using a amd apu dual core
[http://www.newegg.com/Product/Product.aspx?Item=N82E16811147131](http://www.newegg.com/Product/Product.aspx?Item=N82E16811147131) (comments say psu has 2 sata plugs)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820134718](http://www.newegg.com/Product/Product.aspx?Item=N82E16820134718)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131732](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131732)
[http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.696142](http://www.newegg.com/Product/ComboDealDetails.aspx?ItemList=Combo.696142)
promo codes EMCKBJD28,RWCASEAUG
you may want to add a pci slot cooling fan in it or mod a fan into the case

only thing i have had use all my 4 cores in a sound converter temp did not go over 46 C with 4 cores at 100%
wat he said. your needs seem to be leaning more towards gpu power, rather than raw processing power. the new amd llano's have a much better gpu compared to sandy bridge, so that seems like a more suitable choice.

---

### Post by joe4ska on 2011-08-23
Thanks for the suggestion I'll look into AMD's new chip

---

### Post by akand074 on 2011-08-23
In terms of the Intel CPUs. The only main difference between the i3 and the i5 is that the i5 has an extra technology called "Turbo Boost". What that does is it actually clocks up your speed based on usage. Basically, with the i5, it being a quad core and all, you find yourself sometimes only doing one task using only one core. In this case, the other 3 cores are completely wasted. What turbo boost does is take the power out of those 3 cores and super charge your core that is in use (i.e bringing up it's clock speed). This is true for 1 in use, 2 in use, 3 in use or all 4 in use. The amount of boost given differs based on usage. So basically it's just a "smarter" processor that can give you much better performance in comparison to an i3.

That said, comparing the i3-2005 and the i5-2405, I still would say the i5 would perform better for the larger portion of tasks, but that i3 is clocked already at 3.1GHz (which is quite higher than the i5). So I think the added performance boost from the i5 though would exist, it wouldn't be overly significant.

On the other hand, if you compare it to the i5-2500K, then you'll definitely see a pretty huge performance boost. Not to mention you even have it unlocked to bring that performance even higher if required. This one would be worth it if you need/would like the performance boost.

The Intel HD graphics on the sandy bridge chips are actually very very good. They have introduced the turbo boost technology I talked about into the graphics core. So basically the integrated GPU can benefit from it's own turbo boost. Sandy bridge also has a few other improvements one of which is Intel Quick Sync technology which is supposed to make encoding then uploading up to 18x faster.

In terms of Ubuntu supporting the 4 cores. GNU/Linux probably has the best support for multi-threading. You'll definitely get full benefit of the quad core. 

In terms of AMD. AMD has very good cost per performance. (i.e you can get really good performance at a good price, so it's good value). AMD tend to be really good for graphics as well. Though if you're getting a dedicated card anyways, that's irrelevent, and otherwise, like I said, Intel HD graphics is a huge improvement, so I'd deem it comparable to AMD integrated as far as you'll be able to tell unless you game or content create more but at that point you might as well get a dedicated card.

Get what's best for you in terms of performance/value/necessity etc.

---

### Post by oldfred on 2011-08-23
Tom's has a recent comparison and the last page is a chart of comparative performance by chip, so you can compare performance and see what prices are at any time. Article says it is for gaming but I see it as a good comparison.

[http://www.tomshardware.com/reviews/cpu-gaming-performance,3007.html](http://www.tomshardware.com/reviews/cpu-gaming-performance,3007.html)

---

### Post by LowSky on 2011-08-24
5 years is an awful long time for "future proofing".

If thts what you want to do, but the fastest processor you can afford.

If you want a decent cheap PC, buy just enough.

---

### Post by joe4ska on 2011-08-24
Thanks for the advice akand074 & oldfred.

Now that you mention Quad Core support in GNU/Linux I'm likely to splurge for a Quad Core processor in the hopes it will

Power consumption is another concern as I spend a ton of time on my computer and figure saving power in idle tasks is a reasonable goal. This is why I'm interested in the 65W i5 vs 95W i5 

Would the wattage matter on low CPU tasks? Would it be nearly identical? making the power saving i5 2405 nearly non existent.

AMD Llano does look promising so I'll keep checking out that line over the next couple months while i do more research.

In the end I want to build a budget PC that will give me the longest useful lifespan with Ubuntu, LM, Arch etc. so if spending $80 more for an i5 versus the Llano means I get another year out of the machine I'd totally do it.

Thanks for the advice everyone. at the very least I'm sold on a Quad Core now its a matter of AMD vs Intel when I actually hit submit or the order.

---

### Post by joe4ska on 2011-08-24
5 years is a bit much. I do agree, but if buying an i5 over i3 or Llano means i get a extra year or even two out of the computer that $80 would be a good investment.

I'm currently looking to spend between $500-$600 on the Case, PSU, HD, CPU, Motherboard & Ram.

---

### Post by akand074 on 2011-08-24
> **joe4ska said:**
> 5 years is a bit much. I do agree, but if buying an i5 over i3 or Llano means i get a extra year or even two out of the computer that $80 would be a good investment.

I'm currently looking to spend between $500-$600 on the Case, PSU, HD, CPU, Motherboard & Ram.

I'd go for the i5-2500K personally if future proofing is important. Intel chips are generally really good in terms of power usage. They have good support for when their processor/particular cores are in idle.  And like I said before, the Intel HD graphics is fine, if you need more you can always pop in a good dedicated card for 100$ in a year or two if you ever find the need. I don't imagine you will though.

---

### Post by kuvanito on 2011-12-18
I know this post is kind of old but I am in a similar situation where I want to build a new powerful machine for myself.
Counting on my own experiences and the number of times where I have installed Ubuntu to most of my friends I can tell you and advise to any one,please get an Intel based PC.
Yes AMD is cheaper but you will run into some issues,take my word...
I had all sort of problems with AMDs as well as success.
Nvidia and ATI have been troublesome for me too.

BUT I have never ever had a single problem or issue with an Intel based PC and Intel Graphics.It's like one for each other :D 

I am going Intel i7 8GB DDR3 120 SSD with my next toy.

---

### Post by garyhibdon on 2011-12-19
im only putting my 2 cents in in the fact that i currently am running an intel e5300 clocked to 3.4 Ghz. ive not noticed any significant power increase compared to the q9600 i used to run. it still seems to use less power that im aware of, so as far as the 65 watts vs 95 watts, go purely with what you want. intel products are notoriously good, even in gaming situations.

and as one the above poster stated, ive done multiple install of ubuntu on amd and intel based computers, typically w/o any trouble from intel. AMD seems to take a bit more coaxing. 

and im currently catching the worst problems with an invidia card, so if youve another choice on that, go for it.

best of luck

---

### Post by joe4ska on 2011-12-19
I actually ended up building a Intel i5 2500k machine and found that to proivde way more processing power than necessary.

I actually was going to get an AMD chip with onboard graphics but am glad that I went with Intel. I'm sure the LLano line of AMD chips would have been just as sucessful as their graphics are onboard but I have no compliants I feel the i5 was worth the extra 80 bucks or so.

If anyone is curious to my experiences in August 2011 when I built the machine check out
[http://linuxbookpro.tumblr.com/post/9978532353/my-new-linux-build](http://linuxbookpro.tumblr.com/post/9978532353/my-new-linux-build)

or follow me on tumblr at

[http://linuxbookpro.tumblr.com/](http://linuxbookpro.tumblr.com/)

---

### Post by joe4ska on 2011-12-19
> **garyhibdon said:**
> im only putting my 2 cents in in the fact that i currently am running an intel e5300 clocked to 3.4 Ghz. ive not noticed any significant power increase compared to the q9600 i used to run. it still seems to use less power that im aware of, so as far as the 65 watts vs 95 watts, go purely with what you want. intel products are notoriously good, even in gaming situations.

My i5 is pulling roughly 80watts. In retrospect I wish I went with a more efficient power supply When I purchased the parts in store they didn't have the one I had hoped for.

I ended up with a eXtreme Power Plus RS500 Power Supply, it gets the job done and I have no complaints but it's rated at 70% efficency and if I did it again I'd shoot for 80%+

---

