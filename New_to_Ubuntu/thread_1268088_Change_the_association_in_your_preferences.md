---
title: "Change the association in your preferences"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by pirate paul on 2009-09-16
Hi, I am trying to top up my vodafone pay as you go cred. I tried downloading some software which should make a vodafone box come up, which tels me how much cred I have left and allows me to put in a voucher number etc.
When I tried to download the software it said>

/tmp/vodafone-mobile-connect 1.99.17-8 all.deb could not be opened, because the associated helper does not exist. Change the association in your preferences.

What does this mean? I can find preferences but thats about it. I dont know what it means or how to change anything. I am not too good with computers, just learning.

Maybe I dont need to down load anything dunno? 

HOW DO I MAKE THE BOX COME UP ? ANY BRIGHT IDEAS. 

Thanx.

---

### Post by sisco311 on 2009-09-16
go to Edit -> Preferences -> Applications, search for "DEB file" and change the Action to Use gdebi-gtk.

gdebi-gtk is located under /usr/bin.

---

### Post by pirate paul on 2009-09-16
It did not say deb or voda or anything I could connect with the subject.

---

### Post by Mike_IronFist on 2009-09-16
> **pirate paul said:**
> It did not say deb or voda or anything I could connect with the subject.

Right-click the link to the software, and click "save link as" then save it to your desktop.

Once it's on your desktop, you can double-click it from there instead of from the Firefox download window, and it should install no problem.

---

### Post by roger_1960 on 2009-09-16
Hi

Save the file.  Then right click on it and select preferences.  Then select the "open with" tab and select the program you want to open it with.

---

### Post by pirate paul on 2009-09-16
I  forgot what program I opened it with now, what would you recomend.
It now says>

Error: Dependency is not satisfiable: usb-modeswitch

Hmmmmmmmmmmmmmmmmmmmmmmm????????????????????????????????????

---

### Post by sisco311 on 2009-09-16
> **pirate paul said:**
> I  forgot what program I opened it with now, what would you recomend.
It now says>

Error: Dependency is not satisfiable: usb-modeswitch

Hmmmmmmmmmmmmmmmmmmmmmmm????????????????????????????????????

[http://blogs.fsfe.org/drdanz/?p=44]("http://blogs.fsfe.org/drdanz/?p=44")

---

### Post by pirate paul on 2009-09-16
The link is Greek to me I am a bit slow with computers, I tried Googling usb mode switch and downloaded some, but it still says Error: Dependency is not satisfiable: usb mode switch. I am not sure I downloaded the usb switch correctly. I have forgot exactly what I did. I think the only prob now is the usb modeswitch.

Any bright ideas.

                      Thanx.

---

### Post by Mike_IronFist on 2009-09-17
> **pirate paul said:**
> The link is Greek to me I am a bit slow with computers, I tried Googling usb mode switch and downloaded some, but it still says Error: Dependency is not satisfiable: usb mode switch. I am not sure I downloaded the usb switch correctly. I have forgot exactly what I did. I think the only prob now is the usb modeswitch.

Any bright ideas.

                      Thanx.

Try to find a package with the name usb mode in Synaptic Package manager. That might solve your dependency problem.

---

### Post by mc4man on 2009-09-17
don't consider this an endorsement of the suitability of these .deb's or if they'll cause you any issues, ect.
About half way down the page (ubuntu
[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

The install.txt

> VODAFONE MOBILE CONNECT INSTALLATION INSTRUCTIONS.

-------------------------------------------------


* You need a previously working internet connection (e.g: your ethernet one)

* Download from this page these two DEB packages:

     - usb-modeswitch
     - vodafone-mobile-connect

* Install them, e.g: in a terminal command line (substitute the version and architecture here for the ones you have downloaded)

     sudo dpkg -i usb-modeswitch_0.9.4-1_i386.deb
     sudo dpkg -i vodafone-mobile-connect_1.99.17-8_all.deb

* After this step, **you will possibly have unresolved dependencies problems**. To solve them execute:

     sudo apt-get -f install  

* If everything has gone fine you can plug in the modem, and execute the driver with:

     vodafone-mobile-connect-card-driver-for-linux


---

