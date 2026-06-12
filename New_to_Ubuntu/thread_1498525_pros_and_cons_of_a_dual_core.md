---
title: "pros and cons of a dual core?"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by thomz92 on 2010-05-31
im thinking about switching from a 2.93gHz single core processor to a 2.0gHz dual core processor. how well does ubuntu handle dual cores? will i notice a significant slow-down when running single processes like games? or how does ubuntu use dual cores? will it run compiz better?

---

### Post by Nick_Jinn on 2010-05-31
In my opinion, the only drawback of dual core is the price. For a similar price you can get a single core clocked way higher....however, the rules have changed a bit....they hit a wall on processor clock time and had nowhere else to go with that, so now the power chips are coming down in price and the new race is low power consumption and long battery life.

You shouldnt notice any drawbacks to having a dual core, you just might not always be using its full potential.

When it comes to multimedia tasks, like converting a video from one format to another, multi-core really helps in a very obvious way.

---

### Post by lisati on 2010-05-31
My laptop (which I use for day-to-day stuff and video editing) has a dual core, and my main desktop has a single core. They have similar CPU speeds. I haven't done any serious tests comparing them, but my laptop seems to have an edge when it comes to CPU-intensive stuff such as video editing. Then again, it could be more than the CPU: the laptop also has double the RAM.

---

### Post by thomz92 on 2010-05-31
can single programs use both cores?

---

### Post by nhasian on 2010-05-31
dual core? you should shoot for four cores!  the Intel i7 CPUs have hyperthreading so it will show 8 CPUs in linux :)

depends on the program wether or not it will take advantage of the additional cores.

---

### Post by Shazzam6999 on 2010-06-01
Wow, wow... how can we all be forgetting that one disadvantage is that when you play System Shock 2 you have to switch to one core otherwise it runs poorly?

---

### Post by Ozymandias_117 on 2010-06-01
> **Shazzam6999 said:**
> Wow, wow... how can we all be forgetting that one disadvantage is that when you play System Shock 2 you have to switch to one core otherwise it runs poorly?

Because we don't play System Shock 2 :)

@OP A program can use multiple cores if it's designed to. (Take this with a grain of salt... I may just be naive and am carrying this over from Windows days :P)

---

### Post by shazbut on 2010-06-01
How many years has it been since SS2 was CPU-bound? ;)

In all seriousness, it's pretty hard not to get (at least) a dual core these days unless you're buying second hand.  Even if your main tasks are only single threaded, extra cores will still help take the load off them by processing other background tasks.
Having said that, I rarely see more than one of my three cores fully loaded unless I'm running 3 instances of avidemux at the same time.

---

### Post by Drenriza on 2010-06-01
> **thomz92 said:**
> im thinking about switching from a 2.93gHz single core processor to a 2.0gHz dual core processor. how well does ubuntu handle dual cores? will i notice a significant slow-down when running single processes like games? or how does ubuntu use dual cores? will it run compiz better?

The single core processor is a dead "race".

If you can pick between a single core and a dual core, pick the dual core.

Benefits.
You can run more then 1 program at a time, multitasking.
You will experience greater system performance.
Better architecture.
A dual core is cheaper.

Drawbacks.
None. 
A dual core processor is not more expensive then a single core processor. Its the other way around. Because single core processor aren't produced as much anymore they rise in price.

If you need a new processor, and have the chance to pick the one you want. I would say

Athlon II X4 620 2 MB (AMD Processor in a Box (PIB))

Phenom II X4 925 6 MB (AMD Processor in a Box (PIB))

or

Phenom II X6 1055T 6 MB (AMD Processor in a Box (PIB))

The core i7 from Intel is far overpriced. The Intel 4 core cpu is over double the price of an AMD 4 core cpu.

---

### Post by Nick_Jinn on 2010-06-08
I forgot about one downside....heat. Make sure you have the proper heatsink/cpu cooler for your chip.

---

### Post by Breambutt on 2010-06-08
Do they even sell single cores any more, apart from maybe one Sempron from AMD?

As is already pointed out, multiple cores help the most when running multiple programs at the same time. I'd go for an energy efficient model since you don't seem to be building a hardcore gaming rig, they can cooled passively. More silent, less wear on hardware due to lower heat emission and of course smaller electricity bills, so it'll practically pay itself out in 10 years!

---

### Post by Drenriza on 2010-06-08
unless you overclock or have 0 airflow, the stock colers are quite enough.

---

### Post by Breambutt on 2010-06-08
Naturally, but stock coolers make more noise than colic infants and also break more easily. ;(

---

### Post by Dayofswords on 2010-06-08
> **nhasian said:**
> dual core? you should shoot for four cores!  the Intel i7 CPUs have hyperthreading so it will show 8 CPUs in linux :)

depends on the program wether or not it will take advantage of the additional cores.
i'm getting that [amd 6-core]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103851") soon in about 3 or so days, hyperthreading is helpful, but dont mistake it for real cores

---

### Post by Nick_Jinn on 2010-06-08
I still have a single core in one of my desktops. It has a $300 video card in it and 4gb of RAM, 2.6 ghrz single core Athlon.....and I think it outperforms any of the dual core Atom processors out there. Since its not a laptop I dont worry about the difference in power consumption. The fridge, electric stove, and crappy water heater than our slum lords use all take up enough power to make the difference negligible, and i am already an environmentalist who rides a bike and eats vegetarian so I am not feeling too guilty about it. Atom only makes sense for mobile devices. I think they are sometimes inferior to higher end single cores.


I guess they hit a wall with clock speed so the new race is energy efficiency, but its really only applicable to laptops and net books unless you want to save money on a cooler.


I play some semi new games on the very highest settings with excellent frame rates.


The only time it feels sluggish is when i am converting video from one format to another. My dual core laptop is noticeably faster at a slower clockspeed.



I am looking to buy a cooler for an Athlon 2 dual core for the same system. Anyone have an extra one laying around they dont need? I will pay you for it.

---

### Post by cascade9 on 2010-06-08
> **thomz92 said:**
> im thinking about switching from a 2.93gHz single core processor to a 2.0gHz dual core processor. how well does ubuntu handle dual cores? will i notice a significant slow-down when running single processes like games? or how does ubuntu use dual cores? will it run compiz better?
 
 2.9Ghz vs 2.0Ghz....well, it would help a lot if you actually listed the CPUs. Ghz alone is a bad way to measure perfromance. Assuming that you mean a P4 517 (actually 2.93Ghz, but then again, almost all '2.9Ghz' CPUs are 2.93) vs a Core2Duo E6400 (actually 2.133Ghz) the 'slower' CPU will eat the 'faster' CPU alive, even on single-core gaming. 
 
 This comparison is not the exact CPUs I said above, but it shows what I mean (benchmarking unreal tornament 2004)- 
 
 [http://www.tomshardware.com/charts/cpu-charts-2007/Gaming-Unreal-Tournament-2004,344.html](http://www.tomshardware.com/charts/cpu-charts-2007/Gaming-Unreal-Tournament-2004,344.html)
 
 Core 2 Duo  E6400- 66.16 FPS (E6300, 1.83Ghz- 59.53 FPS)
 Pentium 4 530 (3.0Ghz)- 43.67 FPS (520, 2.8Ghz- 41.43)
 
 If pure Mhz was all that mattered, Intel would never have changed over to the Core2Duos- the fastest (Mhz) Core2Duo is 3333Mhz, the P4s went to 3.8Ghz.

> **Nick_Jinn said:**
> In my opinion, the only drawback of dual core is the price. For a similar price you can get a single core clocked way higher....however, the rules have changed a bit....they hit a wall on processor clock time and had nowhere else to go with that, so now the power chips are coming down in price and the new race is low power consumption and long battery life.

Umm, not anymore. The only single core CPUs you can find new (well, apart from very old stock kept for the upgraders) are Celeron 4XXs (slow as, and normally in the 1.6-2.0Ghz range)  and Semperon 140s (2.7Ghz). Both of which are quite a bit slower (both Mhz and general system perfromance) than the dual/triple/quad/hexa-core CPUs avaible. I dont know about the Celerons, but the semperons are actually an Athlon II dual-core chip with 1 core disabled anyway....

> **Nick_Jinn said:**
> I forgot about one downside....heat. Make sure you have the proper heatsink/cpu cooler for your chip.

For teh very expensive 'top of teh line' chips, heat can be an issue. But for a simple dual-core, its not really. All the Intel Core2Duo chips are 65watts TDP, or less. Apart from the newest Phenom II dual-cores (Phenom II X2 5XX, 80watts TDP) all teh AMD dual-cores are 65watts or less as well. Older CPUs ran to a lot higher TDOPs than 65watts. 

The newer chips are less hot because they use less voltage than the older chips. ;)

---

### Post by Nick_Jinn on 2010-06-08
Upgrading from a single core Athlon to a dual core Athlon made my computer overheat and shutdown. I had to put the old CPU back in to get it to stay on.


So yeah, heat is a factor. It adds to the expense when you have to upgrade the cooler....Unless you are getting a down clocked CPU like an Atom....I would rather keep my power hungry single core, but I am upgrading to a middle of the road Athlon 2. 



I am choosing to do so anyway. I am wondering what cooler I should get.


I still see single cores on the market. Maybe we are not looking in the same places.

---

### Post by cascade9 on 2010-06-08
> **Nick_Jinn said:**
> Upgrading from a single core Athlon to a dual core Athlon made my computer overheat and shutdown. I had to put the old CPU back in to get it to stay on.

If you went from a 4000+ (Socket 939 single core, 62watts TDP) up to a 4800+ (socket 939 dual core, 110watts TDP) and tried to use the heatsink that you got with the 4000+, you could have had issues with heat. Or it could have been something else (overloaded mosfets, etc).  

The socket 939 4800+ was a very early dualcore, the newer versions use less power, and put out a lot less heat. 

> **Nick_Jinn said:**
> So yeah, heat is a factor. It adds to the expense when you have to upgrade the cooler....Unless you are getting a down clocked CPU like an Atom....I would rather keep my power hungry single core, but I am upgrading to a middle of the road Athlon 2. 

Almost all the CPUs come with cooler. Buying a CPU without a cooler might look like you save money, but if you have to buy a new heatsink, then its more expensive. 

I havent had any majors issue with the heatsink and fans you get stock with a CPU from AMD or Intel for single, dual or more cores. Sure, they arent as good as some of the aftermarket heatsinks, but they do the job. 

BTW, the atom isnt really 'downclocked', its designed to be low voltage, low power. 

> **Nick_Jinn said:**
> I am choosing to do so anyway. I am wondering what cooler I should get.

Whats you budget? ;)

> **Nick_Jinn said:**
> I still see single cores on the market. Maybe we are not looking in the same places.

Some places still have them, but not many- newegg just has a Celeron 430 and a Sempron 140. Here, I cant even get a Celeron single core from my suppliers. The single core CPUs are still around, but they are the exception. Almost everything is 2 or more cores these days.

---

### Post by iponeverything on 2010-06-08
I am glad that "they" hit the wall the on clock, as it has forced "them" to find other ways to keep the momentum going with regard to performance.  Advances in architecture, material, fabrication and other areas have allowed moore's law to still hold true in spite of several premature reports of it's demise.

I bought a x200s for my wife with a c2d SU9400 with a TDP of 10w that kills every other system in our house and it runs cool.

---

### Post by Nick_Jinn on 2010-06-08
For MY needs, I wouldnt think of replacing my single core 2.8 ghrz athlon 64 with a 1.6 ghrz dual core Atom, or even a 2.6 ghrz atom would not be ideal. I have not researched every chip, but last I looked it seemed that for my needs the benchmarks for the single core Athlon 64 were better than with the Atom dual core. I dont need a downclocked pentium 3 that runs cooler or quieter. 

The dual core Athlon makes sense for me. Its become a budget chip but I will see some performance gains. I dont need a chip that is quieter or uses less energy. I need power for multimedia and 3d graphics and I am ok with using an extra 60 watts if I need to.

I would like a Phenom or a Core Duo or a Quad core, but I am rather poor these days and I can do everything i need with a faster Athlon 2. I think the chip architecture often has more to do with benchmarks than the number of cores, unless you are running many programs or you are converting large files where you have to read and write intensively at the same time.

There is nothing wrong with getting a CPU without a cooler if you dont need one, like if the chip doesnt run any hotter.





But I am not saying that single core is better or disagreeing that very expensive newer chips are not cooler or that downclocked atoms are not both cooler and affordable, I just dont have money for the higher end phenoms or quads and have no interest in an Atom processor for a desktop....they belong in cheap netbooks and really basic office computers.




Instead of buying a new motherboard and a quad core I decided to buy a dualbook (Entourage edge) and a Wacom pen and touch and use the same old motherboard Ive used for years with the best chip I can get for it, a significant upgrade for $50 + the cooler.....and I underestimated how much hotter it would be.


There is a good chance the OP isnt going for the top of the line dual cores if he is just barely upgrading to one, and I dont personally like the intel Atoms for gaming or video. I get better performance on a hotter AMD with faster clock speed and larger bus with only a single core.



My 14 inch laptop runs a 2ghrz Atlon 64 dual core and it has never let me down performance wise....but an atom notebook actually makes sense, unless you actually want to use it for something more than you were using your old pentium 3 notebooks for (only with more programs and for longer). Even dual core atoms dont have a lot of muscle. Some single cores will outperform them for media and gaming, easily.

---

### Post by Drenriza on 2010-06-08
> **Breambutt said:**
> Naturally, but stock coolers make more noise than colic infants and also break more easily. ;(

I have always used Intel & AMD stock coolers. And i have never heard any of them nor had any problems with heat/breakdown.

I have also overclocked my core 2 duo 400-600mhz over spec with a intel stock coler and still 0 problems. Sure it got hotter but not "dangerous hot" in for acceptable limits.

---

### Post by Breambutt on 2010-06-08
> **iponeverything said:**
> I am glad that "they" hit the wall the on clock, as it has force "them" to find other ways to keep the momentum going with regard to performance.
w0rd.


For the record, refurbished low TDP single cores are great for light tuxboxes. You can build a perfectly usable tux desktop and stuff it in a tiny case or a sock drawer and it barely costs a penny.

I'm still running a 2,5GHz dualcore for multimedia production and it's more than enough (well, the more the merrier), and I'm pretty sure most people don't stress their machines even that much.

> **Drenriza said:**
> I have always used Intel & AMD stock coolers. And i have never heard any of them nor had any problems with heat/breakdown.
I guess you're lucky then. Or I'm unlucky. Actually I know I'm unlucky, but I've never had my stock coolers NOT break and I've always taken extra good care of my computers, sometimes to the point of smacking my pals when they've had the nerve to finger my monitor/keyboard/mouse with greasy hands.

On the other hand GPU coolers are much worse that way.

---

### Post by Nick_Jinn on 2010-06-08
> **iponeverything said:**
> I am glad that "they" hit the wall the on  clock, as it has forced "them" to find other ways to keep the momentum  going with regard to performance.  Advances in architecture, material,  fabrication and other areas have allowed moore's law to still hold true  in spite of several premature reports of it's demise.

I bought a x200s for my wife with a c2d SU9400 with a TDP of 10w that  kills every other system in our house and it runs cool.


lol
You dont believe in "us" and "them"?

Us = the consumers.

Them = Intel, AMD, and maybe a few competitors. 


Its pretty straight forward.




I dont really see the benefit in putting an Atom processor into a desktop. Its not like you are running on battery power, and the amount of energy that goes into actually producing the chip is going to negate any environmental benefits from buying a new chip rather than keeping your old one. 



I am very glad that they are developing these cooler more efficient chips, but put them in your mobile devices. Dont replace a perfectly good work horse in your desktop with one of those economy processors. 


Atoms are for office work. Their capabilities are limited compared to a single core 2.9 ghrz chip of any notable quality.

---

### Post by Breambutt on 2010-06-08
> **Nick_Jinn said:**
> the amount of energy that goes into actually producing the chip is going to negate any environmental benefits from buying a new chip rather than keeping your old one.
This... is something even most hippies seem to forget. That's why I - the über hippie - got an OEM model CPU off of eBay for a server machine, seems to run around 8W on idle loads (undervolted) and the energy efficient AMD chipsets also put these systems on the same level with the Atoms in total consumption while packing a bit more punch as well. Don't know about the newer Atoms though, maybe there's been some development.

---

### Post by Nick_Jinn on 2010-06-08
You could always find some older used CPUs and just downclock them. Reusing what we already have is the better way to go compared to buying the newest and most energy efficient model on the market every 2 years.

For example, you have to own a Prius for 4 to 12 years (depending on driving habits) before you see any environmental benefits over an economy car that you already owned. If you have to have the best prius every 4 years, you are doing more harm that good for the environment.....but at least somebody else can buy your old cars I guess. 


Wasting perfectly good chips that require an incredibly large amount of water to produce in order to buy the latest energy saver is not only going to decrease your performance but its also not going to help the environment.


I think atoms are awesome in that they can power netbooks for office work and internet functions and provide really efficient and cheap computers to poorer countries, while introducing linux to the world......but replacing a single core powerhouse with a wimpy economy dual core may result in overall loss of performance without helping the environment......and its not like you are going to improve the "battery life" of your desktop, unless you plug it in to a battery for some reason.


But yeah, for that generation of architecture, pentium 3 vs early athlon, the 8 watt Athlon is going to pummel the 4watt atom even at a lower clock speed. They were more expensive chips when they were new, but you can do the environment a real favor and recycle rather than trying to help the environment by consuming new products.

---

### Post by cascade9 on 2010-06-08
> **Nick_Jinn said:**
> For MY needs, I wouldnt think of replacing my single core 2.8 ghrz athlon 64 with a 1.6 ghrz dual core Atom, or even a 2.6 ghrz atom would not be ideal. I have not researched every chip, but last I looked it seemed that for my needs the benchmarks for the single core Athlon 64 were better than with the Atom dual core. I dont need a downclocked pentium 3 that runs cooler or quieter. 
  
  Where on earth are you getting the idea that the atom is a 'downclocked p3'? They arent. For one thing, most of them run faster (mhz) than the p3s ever did (1400Mhz max on the P3s, and they are ultra-rare 'server' chips). 
  
  They are slower, clock for clock, than the P3s are as well. 
  
[http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/](http://www.mydigitallife.info/2008/03/08/intel-atom-initial-benchmarking-data-vs-pentium-and-celeron-m-processors-before-official-release/)
  
  (warnign, that test was pre-release, and is on the UMPC 'silverthrone' chips, the dual core netttop CPUs would be faster). 
  
  > **Nick_Jinn said:**
> I would like a Phenom or a Core Duo or a Quad core, but I am rather poor these days and I can do everything i need with a faster Athlon 2. I think the chip architecture often has more to do with benchmarks than the number of cores, unless you are running many programs or you are converting large files where you have to read and write intensively at the same time.
  
  You are awre that with the SB7XX southbridge, you can 'unlock' cores on the Phenom IIs (and the Sempron as well). I'm pretty sure you cant with the Athlon IIs, I *think* they have 2 different lines (1 for the athlon II X2, one for the X4). 
  
  > **Nick_Jinn said:**
> There is nothing wrong with getting a CPU without a cooler if you dont need one, like if the chip doesnt run any hotter.
  
  True. But getting a chip without a cooler, then blaming problems on it being a dual-core isnt really fair ;) 
 
 > **Breambutt said:**
> This... is something even most hippies seem to forget. That's why I - the über hippie - got an OEM model CPU off of eBay for a server machine, seems to run around 8W on idle loads (undervolted) and the energy efficient AMD chipsets also put these systems on the same level with the Atoms in total consumption while packing a bit more punch as well. Don't know about the newer Atoms though, maybe there's been some development.
 
 There has been...less of the stupid northbridges that used more power than the CPU. 

> **Nick_Jinn said:**
> I dont really see the benefit in putting an Atom processor into a desktop. Its not like you are running on battery power, and the amount of energy that goes into actually producing the chip is going to negate any environmental benefits from buying a new chip rather than keeping your old one. 

They can make sense if you are only a 'light' user- if all you do is log is surf the internet, then atoms arent bad. For anyone used to the power of a desktop system and actually uses it, Atoms are kinda.....lame. 

I'd rather have a low power AMD desktop CPU if I was really worried about energy use, but I am not a light user. 

Point on the energy, its one thing that a lot of people forget.

---

### Post by Drenriza on 2010-06-08
> **Breambutt said:**
> 
I guess you're lucky then. Or I'm unlucky. Actually I know I'm unlucky, but I've never had my stock coolers NOT break and I've always taken extra good care of my computers, sometimes to the point of smacking my pals when they've had the nerve to finger my monitor/keyboard/mouse with greasy hands.

On the other hand GPU coolers are much worse that way.

I have abused my hardware mb/gfx/cpu/ram/hdd with heat, overclocking, stress-test to a point where you wont believe it. The biggest problem i have had is that i got BSOD and then i adusted my OC abit and then it was solved. I got my 8800GT passive coled.

And i must say, it just works. No matter what horriable things i have done towards it. smacked a mb that asus says max could run Front side buss of 1500 and smacked it up to 2000, 2200 was the BSOD as i recall. And so on.

---

### Post by robredz on 2010-06-08
I think most games can utilise dual core now, and it certainly helps with multimedia. 
I have been running a dual core AMD 7750 for about 14 months overclocked to 3 Ghz on the stock cooler with no problems.

---

### Post by wmikes on 2010-10-14
LOL.  no cons that i have ever seen!

---

