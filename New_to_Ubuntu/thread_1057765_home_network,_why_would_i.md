---
title: "home network, why would i"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by capnthommo on 2009-02-02
hi everybody, (i have got some kind of network up and running i am able to see files on the desktop from the laptop {hooray} and when i have explored things a little more i will come back with a new thread.  its almost certain i will need to refine it cos i dont know how i did it and that worries me.  i need to work with it and see if it works both ways, password issues etc.  thanks again to everybody who helped me so far.
nigel)
i currently run 8.10 on my laptop and win xp in the desktop.  i very seldom use the desktop, it being mainly my wife's who hasn't seen the light yet.
we both access the web through a wireless router/hub.  we both use it mainly for domestic purposes although i run a small construction business and keep simple business records on my laptop (stress on the simple there).

i am just wondering why i would want to set up a home network and why i would not want to.  
is it worth the potential hassle.  
what are the potential benefits.  
what are the potential pitfalls.  
and if i did decide to go ahead what kind of can of worms would i open.
oh yes, and are there any good, clear and simply written (i don't speak tech very well) how tos/guides on the subject.

basically, any thoughts on the subject before i consider entry into the process.

hope you can help, and thanks
cheers
nigel

---

### Post by PriceChild on 2009-02-02
If you're both connecting through the wireless router/hub then you're both connected to your own, home network.

Maybe I'm confused, or you mean something else, could you clarify?

---

### Post by b0b138 on 2009-02-02
Well technically you're already running a home network. You've got more than one computer attached to the same network with the capability to communicate with each other. It's easy to set up and would give you the ability to share files/printers between the two computers.

---

### Post by clive littlewood on 2009-02-02
Hi

Create a new file called shares in your home folder.

Right click on the file and click sharing options.

This will inform you that sharing is not enabled and would you like to enable it. 

Answer yes and "samba shares" will be downloaded and installed.

Any documents that you put in the shared folder will be able to be picked up in the windoze box. and vise versa.

You will need to access networks in windoze and you should see your Ubuntu box. You will be asked for your user name and password to access the folder.

Hope that helps         :D

Clive

---

### Post by capnthommo on 2009-02-02
hi, and thanks for the quick replies PriceChild and b0b138.  what i have at the moment as far as i am aware is two separate machines each using the router/hub to connect with the internet.  but to the best of my knowledge they are not able to communicate with each other - this is where i get confused.
if i go to Network Connections on the windows machine i can see the wireless network connection and 'local area connection' both of which are 'connected'.  but i can't see my laptop anywhere.  I think these are the wireless and cable connection to the router/hub cos when i only had the wireless connected it complained that a network cable was not plugged in.

vice versa, on my laptop i have under 'Places'  'network' which opens a nautilus window showing 'Windows network' but when i click on it i get  'Unable to mount location' Failed to retrieve share list from server.
whatever, i can't seem to locate any actual network which is why i believed i had none - it all seems very complicated to me which is why i sought advice about hwether it was worthwhile.
if i have a network though, i definitely want it working properly so any help anybody can give will be gratefully recieved - but my settings are liable to be a mess cos i just set things up the'simple' way so gods know what state they're in
thanks a million
nigel

---

### Post by tarps87 on 2009-02-02
As a quick test to see they can communicate, on the Ubuntu machine run ifconfig, now look for the ip address (probably 192.168.1. something). Go to the desktop (the xp one, I think it was the desktop), open up a command propt and type
```
ping *ip_address_of_the_other_machine*
```

If you get a response the can communicate.
Hope this helps

---

### Post by billgoldberg on 2009-02-02
> **capnthommo said:**
> hi everybody,
i currently run 8.10 on my laptop and win xp in the desktop.  i very seldom use the desktop, it being mainly my wife's who hasn't seen the light yet.
we both access the web through a wireless router/hub.  we both use it mainly for domestic purposes although i run a small construction business and keep simple business records on my laptop (stress on the simple there).

i am just wondering why i would want to set up a home network and why i would not want to.  
is it worth the potential hassle.  
what are the potential benefits.  
what are the potential pitfalls.  
and if i did decide to go ahead what kind of can of worms would i open.
oh yes, and are there any good, clear and simply written (i don't speak tech very well) how tos/guides on the subject.

basically, any thoughts on the subject before i consider entry into the process.

hope you can help, and thanks
cheers
nigel

I made a very easy to follow guide on sharing your Ubuntu files with XP.

[http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/](http://linuxowns.wordpress.com/2008/10/28/share-ubuntu-folders-with-windows-samba/)

---

Why would you do it? Well it makes sharing files between the computers easy.

---

### Post by egalvan on 2009-02-02
I use a "home network" to keep all my media files (movies, music, pictures, etc) 
and internet downloads, and technical stuff, all in one location.
This means I don't need to have huge drives in each computer in my home to fit this.
(I currently have six running)
Each computer has enough hard drive space to dual-boot XP & one or more *nixes (60-80 on laptops, 160-250 on desktops
An external 160g hard drive is used when I need to take stuff "on the road".

Everything else is accessable from any location in my house.

And it's all CAT5e, with Gigabit switches.
At this time, I do not have wireless.

This is my setup, and some of my reasons.
Your setup, and reasons, may vary.

Cheers!

ErnestG

---

### Post by capnthommo on 2009-02-02
okay thanks tarps87
i got a reply from the 'inet address' so they can communicate.
thanks again
nigel

---

### Post by capnthommo on 2009-02-02
hi again,  firstly egalvan yes i know about the centralisation of files etc, but apart from maybe being useful if i'm consulting with my wife over business advertising (but i can e mail as attachments so not really a problem)and maybe printer sharing (which i can do with a USB cable as things are quite nicely) i so seldom have cause to use the desktop that i wonder if it is worth the effort - but since i seem to have some sort of network anyway then i'm sure enough going to make sure it works right.  i see awful potential for lash ups when grafting two machines together and that's before taking into account the fact that one is linux and one is windows.

and billgoldberg,  thanks to you too, i shall certainly take a good long look at you guide.  and i am sure i will be back on the forums with any probs that occur.  i am really uncertain how this all works so i will probably need all the help i can get.  but faint heart and all that...
cheers
nigel

---

### Post by capnthommo on 2009-02-02
okay thanks everybody so far.
just as i thought, i am completely lost.
the windows pc shows two connections to the router (wireless USB device and cable connection)  the laptop is up and running on wireless but i cant make one speak to the other, not either way.
as i said earlier, i have been able to ping and get a response but other than that???
i suspect somone has run windows network wizard at some stage (there has been more than one administrator on the pc before now) and it thinks it has a windows network set up, but i really don't know.
so can someone take me through it from basics because i think there will be some re-setting up to do, certainly on the windows machine.
very grateful.
i am afraid i can't promise to get back very soon as i have domestic things to do (the perils of being in construction in a. winter and b. slack economy - means i get to do the house work)
thanks for any help and to those who have helped me so far.
nigel
:?

---

### Post by capnthommo on 2009-02-02
hi all
i just closed this as i have just about gotten it running.  please see the edit to the first post in the thread.
cheers
nigel

---

