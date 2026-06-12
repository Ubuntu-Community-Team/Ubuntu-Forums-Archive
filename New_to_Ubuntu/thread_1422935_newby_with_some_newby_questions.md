---
title: "newby with some newby questions"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by mileoutrage on 2010-03-06
Hello guys 
i have a few problems i cant to find help on...

on amorak i cant seem to get any playback?? is there some plugin that i can get through the terminal? when i go to play a song ( off itunes in my mounted drive)it will just scan lyrics and not give me any play back at all.


and second, after 3 hours i figured how to enable my brodcom drivers for my wireless, that was alot of fun!!! but the new problem is that i cannot connect to a wired connection at my house but i CAN connect to a wired connection at school =/

im sorry for the lame questions i am really stumped and this is only my 4 day with linux period.

---

### Post by bug67 on 2010-03-06
I believe you need to add the "restricted extras" repositories.  Someone correct me if I'm wrong.  Do a search in Software Center.

---

### Post by Sef on 2010-03-06
> I believe you  need to add the "restricted extras" repositories.  Someone correct me if  I'm wrong.  Do a search in Software Center.

That is correct.  However, universe and multiverse software sources will need to be added.

Applications > Ubuntu Software Center > Edit > Software Sources > tic universe and multiverse > close > Search: Ubuntu restricted > click on ubuntu restricted.   (Note: that will install flash, java and some other restricted applications.  If you just want the music apps, search: gstreamer plugins .)

---

### Post by -kg- on 2010-03-06
> **bug67 said:**
> I believe you need to add the "restricted extras" repositories.  Someone correct me if I'm wrong.  Do a search in Software Center.

Correct.  You will need to install "ubuntu-restricted-extras" from the Ubuntu repositories.  This contains restricted codecs that are not included in a default installation, including the codec for mp3.

There are other even more restricted codecs and drivers available from [the Medibuntu repositories]("http://www.medibuntu.org/"), which is a third party repository.  Instructions on installing this repository are available on a link on that page.

---

### Post by mileoutrage on 2010-03-06
thank you guys im going to try this out right now,
bump for network issue/

---

### Post by cogier on 2010-03-06
I had this issue as well. If all the other advice fails to get a sound try this. Go to System>Administration>Synaptic Package Manager. In the search box enter "libxine1-ffmpeg". Click on the box in the "S" column and select "Mark for Installation" then click on the green "Apply" button on the toolbar.

Once that's all finished you should have sound.

---

### Post by halitech on 2010-03-06
for the networking, is this a new computer that has never connected to the wired connection at home? Or has it connected with a wired connection before? If it has never connected, check the router settings to make sure MAC addresses are not blocked.

---

### Post by mileoutrage on 2010-03-06
cogier, thank you that helped and its working fine!

as for the network problem. im using a Arris modem (for comcast)
and im guessing that when it gets hooked up that it gets the physical address from my desktops NIC, and when i hook it up to my laptop it wont work because its connected to a different mac address. so i tried to change my mac address and nothing has happened 

=/

i did this
sudo gedit /etc/network/interfaces

then

added my hwaddress ether ---------------

then
sudo /etc/init.d/networking restart

nothing.

---

### Post by sandyd on 2010-03-06
are you connected to the modem through a router or directly?
if your directly connected, try connecting w/ a router in between.

---

