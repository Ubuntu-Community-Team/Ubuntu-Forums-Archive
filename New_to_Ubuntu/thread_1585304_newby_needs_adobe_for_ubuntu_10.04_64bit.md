---
title: "newby needs adobe for ubuntu 10.04 64bit"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by morgan365 on 2010-09-30
i have tried downloading adobe online to no avial it says it is virtual or wrong architecture ive read about synaptic but don't understand how to use it also if someone could point me in the right direction concerning magic jack they are not linux ready but i've read a couple things saying i can use virtual box and use my windows os as a guest and allow it to use the port for magic jack if anyone is already using it this way details would be most appreciated thanks in advance

---

### Post by kDDs on 2010-09-30
What Adobe product are you trying to install?

Flash can be easily installed by going to the Software Centre and installing "ubuntu-restricted-extras"

---

### Post by migs73 on 2010-09-30
So many questions!!!
First, what is the spec of the machine you are using.
Are you using Ubuntu 64bit but trying to dowmload the 32bit adobe (assuming flash)?

---

### Post by Grenage on 2010-09-30
My word.  Text formatting is your friend!

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

See the x64 linux client.

---

### Post by migs73 on 2010-09-30
> **Grenage said:**
> My word.  Text formatting is your friend!
Maybe they are just really excited!!

---

### Post by Grenage on 2010-09-30
> **migs73 said:**
> Maybe they are just really excited!!

Really, really excited. ;)

---

### Post by julio_cortez on 2010-09-30
Wait.. Which Adobe product are you talking about?

If it's Adobe Flash, you should find Flash support in the ubuntu-restricted-extras package.

If it's Adobe Reader, Ubuntu comes with Okular or Evince that are already able to read pdf files, but just in case you need Adobe Reader, [here you are]("http://www.adobe.com/products/acrobat/readstep2_allversions_nojs2.html?option=full&platform=LINUX_.deb&language=English&buttonContinue=") (it looks like the .deb is only x86 at the moment).

If you are talking about the Adobe Creative Suite, I'm afraid you'll either have to rely on alternatives (Gimp and Inkscape) or run it under Wine (I have an old install of Photoshop CS2 and it works flawlessly in wine, don't know about other versions but you can find it out [here]("http://www.winehq.org/")).

Then, I guess you are talking about [these magic jacks]("http://en.wikipedia.org/wiki/MagicJack"), but I can't help you in this case. Never seen one of them :(

---

### Post by migs73 on 2010-09-30
> **Grenage said:**
> Really, really excited. ;)

Really?:)

---

### Post by morgan365 on 2010-09-30
honestly it does not matter to me which adobe i use as long as i can the streaming video i watch on jtv channelsurfing etc could you give me details on how to find and use the software center this is my first day working with linux and i cant find software center i have found a thing called software sources if that where i need to be but i can't figure it out thaks

---

### Post by julio_cortez on 2010-09-30
> **migs73 said:**
> Really?:)
[IMG]http://www.dailyhaggis.com/wp-content/uploads/2009/08/o_rly.jpg[/IMG]

Sorry, couldn't resist :P

---

### Post by migs73 on 2010-09-30
> **morgan365 said:**
> honestly it does not matter to me which adobe i use as long as i can the streaming video i watch on jtv channelsurfing etc could you give me details on how to find and use the software center this is my first day working with linux and i cant find software center i have found a thing called software sources if that where i need to be but i can't figure it out thaksApplications->Ubuntu Software Center, click on it and then type in the keyword for the software you want to use in the search box. Select the sofware you want and click on install. Wait a bit for the install to finish and you're done.

---

### Post by oldos2er on 2010-09-30
The latest 64-bit flash is here: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer_square_p2_64bit_linux_092710.tar.gz)
Extract it to ~/.mozilla/plugins

---

### Post by julio_cortez on 2010-09-30
> **morgan365 said:**
> honestly it does not matter to me which adobe i use as long as i can the streaming video i watch on jtv channelsurfing etc could you give me details on how to find and use the software center this is my first day working with linux and i cant find software center i have found a thing called software sources if that where i need to be but i can't figure it out thaksSo if you talk about videos you are talking about Flash I guess.

For me the easy way will be to open Gnome-terminal and issue this command:
[SIZE=3]**sudo apt-get install ubuntu-restricted-extras**[/SIZE]

Flash support is included in this package, as long as Java and other useful things ([here]("http://packages.ubuntu.com/lucid/ubuntu-restricted-extras") the full list)

---

### Post by migs73 on 2010-09-30
> **julio_cortez said:**
> 

Sorry, couldn't resist :P


Sweet. :P

---

### Post by migs73 on 2010-09-30
> **julio_cortez said:**
> So if you talk about videos you are talking about Flash I guess.

For me the easy way will be to open Gnome-terminal and issue this command:
[SIZE=3]**sudo apt-get install ubuntu-restricted-extras**[/SIZE]

Flash support is included in this package, as long as Java and other useful things ([here]("http://packages.ubuntu.com/lucid/ubuntu-restricted-extras") the full list)

To open a Gnome terminal goto Applications-> Accessories-> Terminal. DO NOT FREAK OUT AT THIS POINT. It may look a bit scary now but it will become a friend. When you type in the code suggested above you will be prompted for your password. Type it in and press enter (Note. Your password, nor any asterisks will appear when you type it in. This is normal) After pressing enter you'll get lots of stuff flashing up on the terminal. Once finished, close the terminal and try out your flash.

---

### Post by morgan365 on 2010-09-30
thank you very much migs73 that works great i'm currently watching scrubs on jtv now i need to figure out the virtual box and how to make magic jack(Yes Its telephone) work with it and no more microsoft thanks agian

---

### Post by migs73 on 2010-09-30
If you use VirtualBox from Oracle, make sure to use the one from the Oracle Website (called the PUEL Version) as the one in the Software centre ( the OSE Version) does not support USB conectivity.
You will still need a valid windows disk to install into the Virtual machine ( so you will still be tethered to MS).
Once you set up the Virtual Machine (takes about 5 mins and is really surprisingly simple), and installed your OS, you will need to install guest additions. The best way to find out what all this means is to read the Vbox manual, it is very useful.

---

