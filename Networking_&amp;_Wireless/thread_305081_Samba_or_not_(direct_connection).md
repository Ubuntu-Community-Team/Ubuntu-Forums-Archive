---
title: "Samba or not? (direct connection)"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by freddiethehawaiian on 2006-11-22
okay so here's my question:

i have two pcs right next to each other.

both have wireless net access, and i want to connect them to share files. do i have to use samba (one is ubuntu the other XP) if i connect them with an ethernet cable? or do i have to go through the router? 

should i just go with samba?
... im reall confuzled.

:-k

---

### Post by dmizer on 2006-11-22
it depends on what you want to do.  but if all you want to do is share files, it's not necessary to do direct connect.

to set it up so xp can see shares on ubuntu, you'll need to set up a samba server on your ubuntu box.  the howto for that is the first link in my sig.

to set it up so ubuntu can see shares on xp, you can try using nautilus, but your best bet is to use something like cifs.  the howto for that is the second link in my sig

---

### Post by freddiethehawaiian on 2006-11-22
well what i want to do is share the root of a drive on my windows box with the linux system.

reason for this is that i want to listen to music and have gAIM running on the linux box and have a game (haha) running on the windows one at the same time.

ive tried to get samba to work for me, but it's not working well... and i tried the links in your sig too. sadky, im missing something.

i know that this is not hard but im just not getting it.](*,)

---

### Post by dmizer on 2006-11-23
why should you want to share the root of a windows drive if all you want to do is share music?  just share the music folder.  it's dangerous to share an entire drive anyway.

what exactly do you not get?  where are you having problems?

---

### Post by freddiethehawaiian on 2006-11-23
well its my archive drive, i have alot of info on there that i want to get to from all of my computers (3 are windows, one linux)

i guess that ima noob, but im not getting how to connect it all...
like samba and cifs, they just haven't clicked yet to me...

plus my network is DHCP and i am not getting how to make that work at all. but i found my old router and so ima try to do it that way, now i need an ethernet cable. :-|

---

### Post by dmizer on 2006-11-24
okay ... i'm more than happy to help you out, but i need more than "they just haven't clicked yet"

what hasn't clicked?  what don't you understand? how can i help you understand?

how are you currently networked?  what kind of internet connection do you have? what kind of equipment do you have currently?  are all your computers able to go online at the same time?

---

### Post by freddiethehawaiian on 2006-11-26
both of the computers in question can access the net at the same time(along with the other two i have).

our internet connection is a cable connection

my laptop(the ubuntu box) has a cisco wireless pc card
the pc(windows) has a linksys wireless pci card
the router that im using is a linsys WRT54G

and as for the network...well at the moment everything just connects to the router and goes out to the net from there. i haven't realy tried to connect the computers this is kinda my first foray into that.

the stuff with samba that isnt clicking is the user stuff. when i set it up should i add a user with the name of my windows system since ill be sharing FROM the windows system TO the linux one? and after that will i need to do something to my router to get this stuff to work? im reading everything i can on this subject but it seems to not go *click* for me.:( 

btw. you're very helpful, sir. im glad that ubuntu has users like you around.

---

