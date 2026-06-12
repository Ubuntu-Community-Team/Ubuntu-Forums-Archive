---
title: "Best way to share music between PCs at home"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by keymoo on 2008-12-29
Hi there,

I have an ubuntu server where I want to place my MP3 collection. I want to be able to access the music from any computer in the house, so that my wife and kids can play music on all computers without us all having different music collections on different machines. We have a mixture of Ubuntu, WinXP and Vista client machines.

I was thinking of simply creating a samba share on the ubuntu server and get the other machines to connect to the music through that.

Questions:
1) which directory on the ubuntu server should I place the music?
2) Which samba options should I use?
3) Does this seem a sensible way of doing it?
4) I want to sync music with various iPods on various computers - is this possible with this kind of set up?

Thanks in advance!

---

### Post by Temposs on 2008-12-29
I think an excellent way to do music sharing(at least with Ubuntu) is through DAAP share. I think both Rhythmbox and Amarok have it, so Ubuntu is covered. You can turn it on in rhythmbox by selecting Edit->Plugins->DAAP Share. Then check it, and click the Configure button to set it up. If you set up DAAP sharing on multiple computers, then the other computer's music becomes available at a single click through rhythmbox, and the shared music comes up just as if it were on your computer. It's really quite easy on Ubuntu.

I'm not sure which music players have DAAP share available in Windows, though. You might look around at that.

---

### Post by Dedoimedo on 2008-12-29
Hi there!

Questions:

1) which directory on the ubuntu server should I place the music?
2) Which samba options should I use?
3) Does this seem a sensible way of doing it?
4) I want to sync music with various iPods on various computers - is this possible with this kind of set up?

Answers:

1) anywhere you want, maybe something called data?
2) depends if you have untrusted users at home; you can go with security=user, this requires username and password for an existing user on the machine
3) yes
4) maybe, ipods do not always work well with linux

Dedoimedo

---

### Post by shearn89 on 2008-12-29
> **keymoo said:**
> Hi there,

I have an ubuntu server where I want to place my MP3 collection. I want to be able to access the music from any computer in the house, so that my wife and kids can play music on all computers without us all having different music collections on different machines. We have a mixture of Ubuntu, WinXP and Vista client machines.

I was thinking of simply creating a samba share on the ubuntu server and get the other machines to connect to the music through that.

Thanks in advance!
I was going to do this myself using an ubuntu sever install, have a sort of network media pc connected to a hifi. I came up with:

**1. A samba share in the /home directory** called something like music (/home/music/), which was accessible using a password so everyone could "backup" or just dump music there.
Not sure what settings you need, but the samba wiki and lots of playing around got me to the correct ones.

**2. Use mt-daapd** to serve it up as an itunes share for general playing. Mt-daapd is in the repos, the config file is at /etc/mt-daapd.conf, and well commented.

**3. Use mpd with a web interface** and a connection from the box to my hifi so that i could play music on the system, and control it from a laptop or ipod touch/mobile phone on the local wifi connection. If you go to [this page]("http://mpd.wikia.com/wiki/Clients") they document some of the possible options for this.


Hit me with any questions if you need.

EDIT: oh, not sure about the ipod thing, but I reckon you could mount the samba share as a network drive (easy on windows, my computer -> mount network drive), and then tell itunes to use that as the music directory?

---

