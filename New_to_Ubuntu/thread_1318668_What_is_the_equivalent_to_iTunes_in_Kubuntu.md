---
title: "What is the equivalent to iTunes in Kubuntu?"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by mastergunner on 2009-11-07
Just as the title states, what is the itunes equivalent in Kubuntu? This forum has helped me out alot. Thanks for all the forum members help.

---

### Post by Duskao on 2009-11-07
Songbird. Get it at [www.getdeb.net](www.getdeb.net)

---

### Post by mastergunner on 2009-11-07
Thanks but it will not install. I am running Kubuntu 9.10. How do I manually install?

---

### Post by bug67 on 2009-11-07
> **mastergunner said:**
> Thanks but it will not install. I am running Kubuntu 9.10. How do I manually install?

Did you follow the instructions from the above link that read, "Learn how to install applications from this website by clicking here?"

---

### Post by Sourmiloko on 2009-11-07
You could try to go into Synaptic or Add/Remove (idk what it is in k)

And try to add Wine. This will let you install and use windows software on Linux. So now you could just install the regular Itunes. Right click on the Itunes installer and open in Wine.

---

### Post by Marlonsm on 2009-11-07
You can use Amarok, it already comes with Kubuntu.

But there are other alternatives, like SongBird (or anything you can use in normal Ubuntu).

> **Sourmiloko said:**
> You could try to go into Synaptic or Add/Remove (idk what it is in k)

And try to add Wine. This will let you install and use windows software on Linux. So now you could just install the regular Itunes. Right click on the Itunes installer and open in Wine.

I don't think iTunes runs in Wine...

---

### Post by mastergunner on 2009-11-07
> **bug67 said:**
> Did you follow the instructions from the above link that read, "Learn how to install applications from this website by clicking here?"

Yes and nothing happens after properly doing what the instructions said.

---

### Post by LuisGMarine on 2009-11-07
I would highly recommend using songbird.  Before I left Ubuntu a year ago, I promised to come back once they had an application that can stand toe to toe against iTunes.  I deff believe songbird is going to answer my call.

---

### Post by LuisGMarine on 2009-11-07
By the way I dind't really answer your question.  You can download songbird from this link:

[http://www.getsongbird.com/]("http://www.getsongbird.com/")

.. you can follow the instructions in my signature if you need assistance on how to install this.  Let me know if you need any more help =)

---

### Post by Duskao on 2009-11-07
On [www.getdeb.net](www.getdeb.net) when you click the link that says learn how to install software from getdeb, just click on the getdeb in step 1. Then it will download a .deb file which you install like normal. Once that is completed, click on the install now for songbird. 
By doing it this way, when songbird gets updated getdeb will add that to their repos (which you installed with the .deb) and when you update your system it will automatically update songbird or any other software you have installed form getdeb.net. Quite useful if you ask me. You will always have the latest version of the software. Nice if you like the be near the newest stuff. Hope that helps.

---

### Post by Mrandersonjr on 2009-11-07
Try rhythmbox. 
sudo apt-get install rhythmbox

---

### Post by NoaHall on 2009-11-07
Are you using 64 bit or 32 ?

And iTunes won't install in wine.

---

### Post by NickJones on 2009-11-07
> **NoaHall said:**
> And iTunes won't install in wine.

Yes it will.

Get PlayOnLinux from your package manger, install it, fire up PlayOnLinux, select install, type iTunes, click install again, and bam, you are done.

Nick

---

### Post by mastergunner on 2009-11-08
> **Duskao said:**
> On [www.getdeb.net](www.getdeb.net) when you click the link that says learn how to install software from getdeb, just click on the getdeb in step 1. Then it will download a .deb file which you install like normal. Once that is completed, click on the install now for songbird. 
By doing it this way, when songbird gets updated getdeb will add that to their repos (which you installed with the .deb) and when you update your system it will automatically update songbird or any other software you have installed form getdeb.net. Quite useful if you ask me. You will always have the latest version of the software. Nice if you like the be near the newest stuff. Hope that helps.

I have done this and nothing happens. When I click on the install button it opens up a second window but it is blank. Any ideas? I would really like to use songbird. HELP!!!!!

---

### Post by mastergunner on 2009-11-09
Help !!!!!!

---

### Post by seenthelite on 2009-11-09
Songbird is not available for 9.10 yet.

---

### Post by Duskao on 2009-11-12
If you still want songbird your just gonna have to wait a little bit, shouldn't be too long. But if you are really looking for an iTunes alt then Songbird is the way to go. However there are lots of great music player programs on linux so you can have your pic. Here are just a few: 
Songbird (most like iTunes, nearly identical)
Rhythmbox (very nice, lightweight)
Amarok (also nice)
Exaile (my favorite)
Listen
Audacious
Muine
Banshee
Christine Media Player

Plus many others. If you want to try a big media player/entertainment hub, check out xbmc or moovida.

---

### Post by Ant. on 2009-11-12
Songbird and Amarok are the best suggestions in my opinion, I used to use Amarok loads but recently switched to Songbird and I love it.

---

### Post by CaptainMark on 2009-11-12
does songbird have video support yet? that used to be the big thing putting me off.

---

### Post by kio_http on 2009-11-12
By default Amarok is already installed in Kubuntu.

Amarok is my favorite music player

---

### Post by tkawa6 on 2009-11-15
Songbird installs fine on Karmic. You can grab the daily builds here.

[https://launchpad.net/~songbird-daily/+archive/ppa]("https://launchpad.net/~songbird-daily/+archive/ppa")

Or you can add it to your sources.list

type in your terminal:
> sudo nano /etc/apt/sources.list


The paste this to the bottom:
> deb [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu) karmic main 

hit "clrt+x" on your keyboard to save your updated sources.list.

The type the following:
> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5719E347


Then type:
> sudo apt-get update

finally:
> sudo apt-get install songbird

---

### Post by CaptainMark on 2009-11-15
how is the daily builds, i dont want to use debs to use songbird because they dont update, is it stable enough to use daily builds

---

### Post by mastergunner on 2009-11-15
I would like to know this as well.

---

### Post by tkawa6 on 2009-11-16
been using it with karmic for months. works fine. just installed the other day on a fresh install with no problems. make sure you install the gstreamer-plugins-bad for mp3 playback.

---

