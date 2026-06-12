---
title: "Help please, im about to kill somthing or somone"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by lukeheald on 2007-08-30
Error connecting to wireless network

The requested wireless network requires security capabilities unsupported by your hardware.


I Get this error when i try to connect to my router.. WANADOO-DD1B


I can connect to one without an encryption and get onto the net.. (kind of) so i presume my wireless adapter is compatible, also when i try turn my Nvidia card on it dosnt let me.. .lol :) 

any help would be appreciated 

regards luke x

---

### Post by echo460 on 2007-08-30
Have you checked here for your nvidia card?

[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

---

### Post by lukeheald on 2007-08-30
Thanks ill try that.. but cant download anything with this connection.. so any help with my net connection would be appreciateddddddddd xx

---

### Post by HermanAB on 2007-08-30
Encryption trouble with WiFi is a common problem.  I am running WiFi at home totally insecurely, since that is the only way that I can make it work reliably.  You'll have to try different encryption modes.  Sometimes WEP works, sometimes WPA works and sometimes nothing works.  When all else fails, apply a few light blows with a big hammer, it won't help with the connectivity but it will make you feel a lot better...

Cheers,

Herman

---

### Post by lukeheald on 2007-08-30
Lol, Yeh a hammer or chainsaw is looking all the more tempting, I dont mind running insecurely how might i go about doing that? 

cheers luke

---

### Post by por100pre1 on 2007-08-30
> **lukeheald said:**
> Lol, Yeh a hammer or chainsaw is looking all the more tempting, I dont mind running insecurely how might i go about doing that? 

cheers luke

Please, try to relax. If you're calm you'll have more chances of to apply any changes as suggested by fellow posters. We understand how difficult it is, but to break your hardware (or hurting somebody) won't do any better.

---

### Post by lukeheald on 2007-08-30
Thanks... that makes me feel better..... didnt get my internet working tho :p

---

### Post by OlympicSoftworks on 2007-08-30
What card are you using?  You have not said wether it is a pcmcia from a notebook or if it is a isa card for a pc,  because of the current limitations with wireless 'driver' availability it is possible your simply cannot do what you want.

As far as running unsecured, that is a setting in your router.  If you find that your card cannot encrypt then at the very least you can tell your router to _not_ broadcast it's presents to make it harder for anyone passing by to be able to use your bandwidth.

But, try to find out what the model/manufacturer of card is that you have.

---

### Post by echo460 on 2007-08-30
hope this helps
[IMG]http://www.stihlusa.com/graphics/chainsaws/MS361CQ.gif[/IMG]
[IMG]http://www.stanleytools.com/catalog_images/web_detail/56-816_web_detail.jpg[/IMG]

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-30
if you uses a prober title for your thread ppl that know about wireless will come and help you 
if you say your going to kill some one the cops come and arrest you, and maybe the FBI its a terrorist threat.

So moral of the story your Title should have been "i need help with wireless problem"
or better yet "I need help with my Nvidia Wireless card and secure network"

---

### Post by lukeheald on 2007-08-30
haha at echo's pictures :) ermm i got my nvidia driver working :) woopie, things wobble now :D 

As for my internet, im not sure what your asking for, but ill take a guess, i have a inventel wireless adapter for wanadoo, i didnt buy it, it came with the router, is there a way to plug my router directly into my pc and make it work that way? its just sitting in the hall, might aswell be in my room. 

cheers luke

---

### Post by lukeheald on 2007-08-30
> **<<joe>> said:**
> if you uses a prober title for your thread ppl that know about wireless will come and help you 
if you say your going to kill some one the cops come and arrest you, and maybe the FBI its a terrorist threat.

So moral of the story your Title should have been "i need help with wireless problem"
or better yet "I need help with my Nvidia Wireless card and secure network"




that helps no1... i mean, its a waste of time.. why do it lol, its about as pointless as my Title.. 


thank you people that have actually attempted to help me

---

### Post by echo460 on 2007-08-30
Are you having wireless problems still? Good to hear your nvidia working. I have the same setup on mine and its fun. :) Hope you get it working soon.

---

### Post by lukeheald on 2007-08-30
Yerh, sat in my cold conservetory, damn those videos on youtube that made me wanna make my desktop look like a cube and fly around :p ahhhhhhhhhhhhh well, im sure ill figure it out soon, its weird and annoying that i can see my connection but not connect to it :( im waiting for my knight :) lukexx

---

### Post by multifaceted on 2007-08-30
I ran into a similar problem when trying to connect to my Linksys wireless router. However, I did not get an error message... it would just simply stop processing. It took some trail and error but, I was able to connect by doing a **manual configuration.** 

Ironically, there is an option in 'configuration' to set it as **"Automatic Configuration"** --in which I selected and input my WEP key. 
*(You can also choose to connect to an unsecured network)*

Every once and a while, I will loose connection but quickly fix it by selecting **'Manual Configuration'** and unckecking "Wireless Connection" ... let it reconfig and then CHECK the box again... wait and let it save the settings once again. It works every time.

That was my work around, hope this helps you man!:)

---

### Post by lukeheald on 2007-08-31
Thanks man, i was actually doing that aswell and i could connect to the internet but only on a unsecured connection not my proper one, if i enter a wep key for the connection i want it says ok and connects to it, it says ihave a signal but Instant messenger and internet wont work, but thanks for your help :) aside the chainsaw and hammer your the most helpful so far :) x

---

### Post by E_K on 2007-10-03
im not too sure where you are up to with this or if you still need help or not but to access the oconfig pages for your router you need to (getting side-tracked slightly do you get a working connection if you use an ethernet cable from your router to the computer?) 

any ways to get to the config pages you need to type 192.168.1.1 into the address bar of internet explorer, if this doesnt work with the wireless connection it means you are not connected to your router, then you must connect the ethernet cable and try again, all going well you should reach the config pages and from there, there is a link to access the config pages, if you have not changed the default username and pass, i suggested that you do before someone access' your network and does before you do, any ways default username is admin and default pass is also admin, then click configuration down he left hand side of the page and then advanced then wireless here you can select what level of security you wish to use, if any. By default i believe it comes WEP or WPA security select none and see if you can then access the network wirelessly.

On the other hand if you can not get a fully working internet connection through your ethernet cable it would lead you to believe that something else is afoot with your internet connection, drop me a PM or an e-mail if you would like some more help

---

