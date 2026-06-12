---
title: "advice required"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by tacmend on 2008-12-19
hello, i am a more recent user in ubuntu. i have benn using open source os' for a few years. currently i am running windows. only because of ubuntu hardy harons failure to connect to my 2-wire router so i can use wireless with my u-verse. but i am waiting for the new version to arrive. hopefully it will work. i am trying to get a starting point or a place for a foundation. i am hooked on linux and all unix os'. i have attempted to leran command lines with bash. and i can perform the basics. but i dont know where to go or what to do from there. i would like to know the insides and outs of ubuntu, along with any other os. if there is anyone out there who can help me in any way, i would be very grateful. im short on cash. so if there are any free sources that are more understandable to a teen. it would more fit me. i hope that i can in return help some other who may be in an identical situation. thankyou!

tacmend...

---

### Post by Pjotrovitz on 2008-12-19
Well, welcome to the forums I guess. The best place to learn about linux is to do a bash tutorial (google it) and hang out on these forums. Feel free to ask questiona at any time. Regarding your computer that won't connect, we might be able to help you if you post the make and model of your computer/network card.

---

### Post by tacmend on 2008-12-19
i dont really have a network card.....i think... just an ethernet adapter but my wireless is accessed via usb. its a small 2-wire given to me by the att u-verse tech..

---

### Post by halitech on 2008-12-19
with the usb adapter plugged in, open a terminal and post the output of
```
sudo lsusb
```
and
```
lshw -C network
```
this will tell us if Ubuntu sees the usb adapter. if it does, it will also tell us who made the chipset which will tell us what driver you (hopefully) need to use.

---

### Post by tacmend on 2008-12-19
ok, well as soon as the new disc's arrive i will install ubuntu. but i was reading that  they wanted it to have the ability to recognize wi-fi and enable it automatically. is that true? and has anyone already done it, with u-verse?

---

### Post by halitech on 2008-12-19
hardware detection is getting better but its not perfect yet. It will depend on the hardware. I've never used 2-wire or att so not sure.

---

### Post by tacmend on 2008-12-19
oh and i hand put together my cpu, from various parts that my dad gave me in a box. theyre scrap parts basically. so everything is out of date. and even my bios is ancient. seriously, it clocks my processor at 1.1mhz. when really its a 1.1ghz. it the old origanal pentium. so it is terribley slow. and my motherboard, well....it can only have the old sdram. to 56 pin i think. all i know is they dont exist anywhere any more. i cant find any at least. so im stuck with 256 ram.

---

### Post by tacmend on 2008-12-19
ok. cause i actually took the time to call an att tech and he told me that u-verse was not compatable with ubuntu. but he did not sound like he even knew what it was. i even asked if it was compatible with red hat. or linux. he siad no. so i think he has never heard of either of them. which is fine i guess.

---

### Post by jerome1232 on 2008-12-19
I haven't worked much with the u-verse models but I used to be an employee at 2wire, they are basically just Wireless routers with an adsl modem built in. 

The u-verse is fiber instead of adsl (if i remember correctly) You shouldn't *need* to connect to it via usb, doesn't the 2wire have slots to plug an ethernet cable in? Assuming your network card (the ethernet adapter) is in working order it would be far easier to connect with an ethernet connection than a usb connection as it won't involve drivers and such.

---

### Post by tacmend on 2008-12-19
yes i could connect to it using the ethernet cable, but my computer is in the basement. which is where my mother wants it. which means i cant argue. so i have to use wi-fi. and i only have the 2-wire usb.

---

### Post by halitech on 2008-12-19
not saying you are incorrect but unless you have some serious overclocking going on with major cooling, I doubt you have an original pentium running at 1.1ghz (Pentium 1's only went up to 233, mobile P1's up to 300)

doesn't surprise me that tech support has no clue. Party line for most companies is to deny any knowledge of linux.

---

### Post by jerome1232 on 2008-12-19
okay your using the 2wire wifi card! I thought you were connecting directly to the 2wire router via usb. Yeah follow halitech's advice then :)

edit: And yeah when I worked there we weren't allowed to support linux even IF we knew how to. If it wasn't windows xp or higher or Mac leaporad or higher your were out of luck as far as tech support goes.

---

### Post by tacmend on 2008-12-22
ok cool. well i have relocated my computer. so i am now running on hardy haron. and i have direct internet via ethernet. but i have aroused more questions. first. i have just upgraded my hardy haron via terminal i did sudo apt-get ugrade. but my computer looks the same! the background didnt even change then u updated it in terminal too. so did i mess up? or what? cause it looks the same. is there a difference with installing ibenex or ugrading or? and yeah. i done think my processor is the original i=either. but my bios is a pheonix bios. 6.0 something. and it says my processor is 1.1 mhz. so its really confusingme. and i am worried that that may cause future problems.

---

