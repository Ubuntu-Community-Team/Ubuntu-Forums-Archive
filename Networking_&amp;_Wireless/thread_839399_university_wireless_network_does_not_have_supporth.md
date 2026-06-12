---
title: "university wireless network does not have support/help info for Linux"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by eternal_sage on 2008-06-24
ok, my wife and i have recently moved our laptops to Linux (Ubuntu 8.04) and are really loving it. however, it appears that our school (East Tennessee State University, in the US, for those interested) does not have support pages for setting up Linux on their wireless networks. i have emailed OIT (our IT department, mostly staffed by Computer Science majors) and gotten the following email:

> I am sorry but there is no configuration available for the Ubuntu OS
currently and I do not see any plan in the near future for ETSU wireless to
become compatible.

now, i don't know if this is something inherently incompatible between Linux and the wireless networks, or if OIT are just a bunch of helpless M$ monkeys who just don't know what they are doing. the whole CS department is funded by M$ (tons of free software for an assurance of only supporting their products) so i wouldn't put this past them.

anyway, long story short, here are the directions for configuring XP to work on their network. [http://www.etsu.edu/oit/wireless/]("http://www.etsu.edu/oit/wireless/") if anyone has any ideas, i'd appriciate it, cause while i know a bit about programming, the net has always been a weak spot in my knowledge, and i'm new to Linux, so i'm not sure where to really get started. thanks!

---

### Post by Sub101 on 2008-06-24
If you click on the network-applet and select connect to other wireless networks you are presented with a drop down menu.

Select WPA Enterprise and you should be able to change the relevant configs. 

Post back if this works.

---

### Post by eternal_sage on 2008-06-24
no luck. however, i think this may be close, as i got something resembling the Windows login dialog for the network. however, i played around with it for about a half hour before giving up and coming home to a do other things.

thank you for your input and help. i'll likely play with these settings some more tomorrow and see if i have any luck.

---

### Post by timcredible on 2008-06-24
they're using 802.1x, and you're going to need that certificate they have for the handhelds.  i've setup wireless networks for windows utilizing 802.1x with certs, but i haen't done it with linux clients.  you'll have to do a search on how to use that cert.   do not try wpa or wep.  you may want to check out this [link]("http://en.wikipedia.org/wiki/Xsupplicant") for a supplicant that may work from the open1x project.

also, if you're paying to go to school there, you should be able to go to the administrative staff (not the IT department) and raise a big ruckus, because you're the customer, and they need to make the network you paid for accessible to you.  but that will take time.

---

### Post by eternal_sage on 2008-06-25
thank you. i shall definitely give this a try when i get a chance! looks like it may solve all our issues. i'll post back if anything comes of this. thanks!

---

### Post by chalewa on 2008-06-25
it took me many hours to get villanova university's wireless working on ubuntu, and that was on breezy i think, i haven't had to use it on hardy at all...

but from what i remember, i had to use xsupplicant via the terminal, and had it point to some hacked certificates and config files with my username and password and stuff. i will see what i can do to find my old config files and stuff.



edit: here is the contents of my old config file
```
#network_list = default, test1, test2
network_list = Villanova

#default_netname = my_defaults
default_netname = Villanova

logfile = /var/log/xsupplicant.log

Villanova {
  allow_types = eap-ttls

  identity = <BEGIN_ID>anonymous<END_ID>

  eap-ttls {
      root_cert = /etc/xsupplicant/Equifax.cer
#      chunk_size = 1398
#      random_file = /dev/urandom
      #cncheck = ns2.villanova.edu
      #cnexact = no
      phase2_type = pap

      pap {
        username = <BEGIN_UNAME><END_UNAME>
        password = <BEGIN_PASS><END_PASS>
      }
  }
}
```

its relatively obvious where your stuff would go, but obviously i can't tell you what the name of your specific certificate would be, or where do even really find it within windows. you might be able to talk to tech support to figure out what the settings for that config file would be. 

remember that most linux kids are willing to help out other users..when i was doing this at my school, there were a couple of IT guys who used linux, and were interested in helping me figure it out, so you might want to poke around in IT and see if there is anyone else in the same boat.

---

### Post by eternal_sage on 2008-06-25
that would be amazing. thank you.

---

### Post by chalewa on 2008-06-25
there may or not be a better way to do all of this now also. xsupplicant still does exist, but there may be gui-fied options for configuring that text file.

---

### Post by Sub101 on 2008-06-25
Have you tried connecting using a LEAP configuration? Just been looking at the tutorials they give and thats how they do it with the MACs.

---

### Post by eternal_sage on 2008-09-05
ok, thanks Sub101, although i didn't see your post before i figured it out myself, this is indeed exactly the solution, at least on Intrepid alpha 4 (my laptop). i won't know if this works with Hardy until i try to get my wife's laptop online on Monday.

---

### Post by knix on 2008-09-05
[http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539")

[http://ubuntuforums.org/showthread.php?t=684495]("http://ubuntuforums.org/showthread.php?t=684495")


might help

---

### Post by eternal_sage on 2008-09-08
LEAP seems to work on Intrepid Alpha...5 i think is what is on my laptop... but it seems that Hardy doesn't seem to like it.

it was so easy on Intrepid, i just selected LEAP, input my user name and password, and BAM... no such luck on my wife's Hardy machine... although its been acting a little odd for the last few days anyway, so it may be unrelated.

---

### Post by johnrhance on 2008-10-30
My name is John, I'm a freshman at ETSU this year. I recently installed Ubuntu 8.10 on my laptop, and I also can't access our wireless connection. I've been leeching off my neighbor's router so far, but that doesn't work in class. I don't have too much Linux experience, and I'm pretty sure I can't get this working. Please update this thread if you do manage to get connected. Thanks.

---

### Post by 080729jk on 2008-10-30
&#20809;&#20142;&#21943;&#27849;&#24037;&#31243;&#65306;&#19968;&#31181;&#26032;&#22411;&#30340;&#21943;&#27849;&#35013;&#32622;&#12290;[**&#21943;&#27849;**](http://www.music-water.com/index.asp)&#28783;&#20809;&#21644;&#21943;&#22836;&#31185;&#23398;&#32467;&#21512;&#65292;&#27700;&#27969;&#36890;&#36807;&#20809;&#28304;&#21453;&#23556;[**&#38899;&#20048;&#21943;&#27849;**](http://www.music-water.com/index.asp)&#65292;&#21943;&#20986;&#30340;&#27700;&#26609;&#36879;&#26126;&#20809;&#28369;&#65292;&#20855;&#26377;&#36739;&#39640;&#30340;&#33402;&#26415;&#21697;&#20301;&#21644;&#35266;&#36175;&#25928;&#26524;[**&#21943;&#27849;&#24037;&#31243;**](http://www.music-water.com/gc.asp?id=64)&#12290;&#22914;&#26524;&#23433;&#35013;&#20010;&#25968;&#22810;&#20110;&#20004;&#20010;&#21487;&#36861;&#36880;&#12289;&#36319;&#36394;&#31561;&#21151;&#33021;&#65292;&#31243;&#24207;&#21487;&#26681;&#25454;&#29992;&#25143;&#38656;&#35201;&#32534;&#21046;&#12290; &#28216;&#20048;&#21943;&#27849;&#25110;&#25103;&#27700;&#21943;&#27849;&#65306;&#21487;&#20379;&#20154;&#28216;&#20048;&#12289;[***&#21943;&#27849;&#20844;&#21496;***](http://www.music-water.com/pqgs.htm)&#29609;&#32781;&#21442;&#19982;&#20854;&#20013;&#30340;&#21943;&#27849;&#12290;&#22914;&#65306;&#25103;&#27700;&#36367;&#27849;&#12289;&#36855;&#23467;&#21943;&#27849;&#12289;[**&#23460;&#20869;&#21943;&#27849;**](http://www.music-water.com/snpq.htm)&#29615;&#22411;&#36339;&#27849;&#12289;&#27700;&#20987;&#29699;&#36187;&#12289;&#36339;&#33310;&#21943;&#27849;&#31561;&#65292;&#24418;&#24335;&#22810;&#31181;&#22810;&#26679;&#65292;&#23089;&#20048;&#24615;&#21644;&#21442;&#19982;&#24615;&#26497;&#24378;&#65292;&#32473;&#20154;&#20197;&#27426;&#24555;&#27969;&#30021;&#30340;&#24863;&#35273;&#65292;&#24102;&#26469;&#32654;&#30340;&#20139;&#21463;

---

### Post by eternal_sage on 2008-10-30
on Intrepid select LEAP when it asks for the type of encryption on the network, input your user name (it used to be a zName, i.e zABC01, but i think it may have been changed recently, i mean whatever you use to log into the campus labs) and password and you should get connected. be advised however, that currently my laptop and my wife's laptop have had a regression in Intrepid in the wireless networking, and neither are able to connect to any wireless network. if you are able to connect to other networks, you should have no problems though.

welcome to ETSU and Intrepid!

---

### Post by johnrhance on 2008-10-30
I actually tried that before I came to this forum for help. It wants a config type file I believe. I'm not on campus until Saturday, but I'll try again when I get back and see what I can do.

---

### Post by eternal_sage on 2008-10-31
my wife and i neither one have had to provide any type of config file, which is odd. another ETSU student who frequents these boards was also having trouble w/ LEAP, so i'm not sure what is up with that.

---

### Post by johnrhance on 2008-11-02
Sorry, I meant a certificate, not a config file. I tried LEAP and it didn't work either.

---

### Post by eternal_sage on 2008-11-02
yea, thats what i meant too.

strange that you are having trouble with it. do you have WPA supplicant installed? we both have it installed (i think it was installed by default, cause i do not remember ever installing it on either computer) and i know that it deals with wi-fi encryption.

---

### Post by johnrhance on 2009-01-21
Just a small update:

I'm now running 9.04 Jaunty Alpha 3. I connected to the ETSU wireless using LEAP. I'm getting a very faint signal in the 5th floor of the communications building, but at least it's working.

---

### Post by Tmoat on 2009-04-01
I am at ETSU as well and recently bought a dell mini with Ubuntu 8.04. I've not been able to get the wireless working either. Any help would be nice.

---

