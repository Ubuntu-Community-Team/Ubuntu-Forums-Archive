---
title: "iPod help"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by bobbyv on 2009-04-13
I am new to ubuntu and am having problems try to get iTunes to load on my lap top. I have loaded three of the media players that I found on the HELP button and none of them recognize my iPod touch. Is there anybody out there that can guide me in the right direction? My girlfriend's brother supposedly has it loaded on his lap top, but he is working out of town and can't be reached. Any help would be appreciated.

---

### Post by Wiebelhaus on 2009-04-13
You cannot install Itunes on a Ubuntu Machine and the Native Rhythmbox Music Player works fine for me.

---

### Post by nwadams on 2009-04-13
the ipod touches are a whole bottle of fun. None of the linux native methods will work unless you can jailbreak your touch. I have a second gen touch which is nearly impossible to jailbreak(according to my skill). So What i did is i used virtual box and installed a small windows partition who's sole purpose is for itunes to sync my ipod touch.(you can store all your music on your linux partition and link it to itunes via folder sharing). Works great...for a workaround. 

If you can manage to jailbreak your touch, you can use open ssh and sync it via wireless. (google iphone sync linux or something along those lines and you will get instructions for the iphone which are identical to the itouch (after jailbroken))

---

### Post by TheNosh on 2009-04-13
im not sure if this will help, because it's sort of complex and you need to jailbreak the ipod, but i found this thread: [http://ubuntuforums.org/showthread.php?p=4112903](http://ubuntuforums.org/showthread.php?p=4112903)

good luck

---

### Post by LostMagix on 2009-04-13
There are loads of howtos about using itunes in wine or if you just want to add/remove look into songbird

---

### Post by LostMagix on 2009-04-13
wait, i thought the touch was supported?

did you activate MTP in your media players?

---

### Post by jrothwell97 on 2009-04-13
The iPod Touch is more difficult, as it's treated as a computer networked over USB instead of as a mass storage device (like the 'classic' iPods). The same applies to the iPhone.

This makes it incredibly difficult to do without iTunes, as Apple hasn't released the specification for uploading content to and from the iPhone/iPT. If you're desperate to get it working on Ubuntu, then you *could* jailbreak your iPod, but I'd advise against it (it can cause all sorts of problems, as documented in various places.) My advice is to stick with iTunes for Windows, as-is.

---

### Post by bobbyv on 2009-04-13
WOW, I want to thank all of you for your help. As I mentioned before, I'm new here and these all sound like a good place to start. Thanks again.

---

### Post by nwadams on 2009-04-13
your very welcome, glad we could help :p

Remember. If there is anything you are unsure about...at all. ASK a question. There are no stupid questions...only stupid ppl giving stupid answers :P

---

### Post by jerrynewt on 2009-04-13
How do you activate MTP in the media players??

---

### Post by thesuperjman on 2009-04-13
yea i hope someone smart out there figures out how to work this quickly. 

also, does itunes keep some of the newer albums ive boughten from being imported from my ipod to banshee?

---

### Post by nwadams on 2009-04-13
MTP won't help with the ipod touch. I dont know about nano's or classic's

but hte ipod touch requires a method similar to that of the iphone. 


Nano/classic instructions: for rhythmbox go edit plugins, enable MTP and ipod. then go file scan removable media (after you plug it in). Then it shoudl work as expected.

Iphone/itouch: 
A: jailbreak and use open ssh to sync wirelessly OR
B: virtualbox xp/vista for itunes. 

If i'm completely wrong, someone shoot me:P

---

### Post by thesuperjman on 2009-04-13
what is this mtp? how do i do it in Banshee?

---

### Post by nwadams on 2009-04-13
edit --> preferences -> extentions.

To be honest i've no idea what it is.

---

### Post by thesuperjman on 2009-04-13
strange, it's already turned on. i think the ipod blocks some of the newer songs from getting on my computer.

---

### Post by nwadams on 2009-04-13
may I ask which ipod you have and which firmware you are using?

---

### Post by thesuperjman on 2009-04-13
well my main ipod is an ipod touch 2 gen, but i know i cant use that yet without potentially harming it. so i'm uploading songs from my ipod classic (its was the first ipod video to come out... well not *the first* but you know what i mean) 

and... firmware? idk what kind of firmware is in the ipod

---

### Post by nwadams on 2009-04-13
ok. ya the older ipods work fine. you can use your ipod touch without harming it by using virtual box. You can create a windows partition in virtual box and install itunes to it and manage your music that way. Thats what I do. If you want a pure linux solution without virtual box i believe you are out of luck for the meantime.

---

### Post by thesuperjman on 2009-04-13
o yea, i meant the harm done by jailbreaking. I have WINE, i will look into this tomorrow, thanks.

---

### Post by WhiskyChris on 2009-04-13
> **thesuperjman said:**
> strange, it's already turned on. i think the ipod blocks some of the newer songs from getting on my computer.

If your newer songs were bought from the itunes store then you will have downloaded them as protected content which can't be played outside of itunes/ipod - hence no import to banshee/elsewhere. I've not looked too hard (I only have one affected album) but as far as I saw there wasn't a hack, apart from something nasty like plugging headphone socket into mic and re-recording them...

---

