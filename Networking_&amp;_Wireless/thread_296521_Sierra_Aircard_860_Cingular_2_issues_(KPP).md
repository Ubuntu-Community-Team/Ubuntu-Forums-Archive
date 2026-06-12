---
title: "Sierra Aircard 860 Cingular 2 issues (KPP)"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by mmarinho on 2006-11-09
I configured my Sierra Aircard 860 Cingular using KPP and I notice two issues.

1) I never have issues connecting but tcp/ip sometimes doesn't work. Can't browse the web, ping. Simply disconnecting/reconnecting solves the issue.


2) The download speed is fine but the upstream speed appears to be capped and doesn't go above that for some odd reason:

Download Speed: 723 kbps (90.4 KB/sec transfer rate)
Upload Speed: 56 kbps (7 KB/sec transfer rate)

At the same exact location my upstream speed under XP exceeds 56 kbps (i've seen it as high as 115 Kbps).

I'm using the latest firmware for the card (new one was just released) and using KPP.


-Manny

---

### Post by mmarinho on 2006-11-15
Never mind the speed, looks like it's an issue with the web site that I'm using and the browser. My speed is fine!

As far as the second issue I'm still having this problem. Sometimes I'll connect and all is fine, other times I have to disconnect, connect again and then it works fine. I never have issues establishing the connection itself though (always get an IP, blah blah). The issue is you can't ping or browse the web. I think this is a KPP/Sierra Aircard generic issue so even if you are using a different card you might have the same problem.

Ideas?

-Manny

---

### Post by flugh on 2006-11-20
I'm curious what type of system you are running this on. I have an HP zd8000 notebook. After getting some drivers from Sierra, and following instructions, starting cardmgr gets me several 'Function not implemented' errors and no love out of the card (sorry to be vague, don't have my notepad w/ info written down handy). Did you have to do anything special to get this working? Right now I am downloading the Edgy install .iso and will do a clean install over the holiday. I'm hoping that the newer software will bring some success.

Any help would be appreciated. Google results are a little thin. And results are either 'me too' or dead-ends so far.

---

### Post by GenX on 2006-11-24
> **flugh said:**
> I'm curious what type of system you are running this on. I have an HP zd8000 notebook. After getting some drivers from Sierra, and following instructions, starting cardmgr gets me several 'Function not implemented' errors and no love out of the card (sorry to be vague, don't have my notepad w/ info written down handy). Did you have to do anything special to get this working? Right now I am downloading the Edgy install .iso and will do a clean install over the holiday. I'm hoping that the newer software will bring some success.

Any help would be appreciated. Google results are a little thin. And results are either 'me too' or dead-ends so far.

I have the ZD8000 as well and have no clue as how to create a connection. I work offshore so my only internet connection is with the Sierra Aircard 860. Right now, sadly enough, I am typing while running XP. If I cannot resolve this issue then I will be forced to quit Linux. That is just not something I want to do.

I have tried running EasyGPRSconnect, but during the install it goes through a checklist of dependencies and stops 1 shy. It is the GTK2-TrayIcon-0.03. It will not let me gp any further than that. I think it is perl. I found this at a site:

 use Gtk2::TrayIcon;
  Gtk2->init;

  my $icon= Gtk2::TrayIcon->new("test");
  my $label= Gtk2::Label->new("test");
  $icon->add($label);
  $icon->show_all;

  Gtk2->main;

What is this KPP thing that is being talked about in the first post of this thread?

---

### Post by flugh on 2006-11-24
kppp is a KDE app that lets you set up dial-up type connections. The main advantage to it in this situation i -think- is that you can easily set an initialization string (I don't see where to do it with the default gnome network connection applet).

I'm in the same boat as you though, still no working solution. But I'm hopeful :-) Considering maybe install wine/bochs/some emulator and trying to run the Cingular software just to see what happens. And I haven't ever tinkered with ndiswrapper, but it was mentioned in one of the few posts Goggle returns when looking for 'ac860 linux' etc.

Hang in there, someone will cure us (or we'll learn enough to cure ourselves :-) )

---

### Post by GenX on 2006-11-29
> **flugh said:**
> kppp is a KDE app that lets you set up dial-up type connections. The main advantage to it in this situation i -think- is that you can easily set an initialization string (I don't see where to do it with the default gnome network connection applet).

I'm in the same boat as you though, still no working solution. But I'm hopeful :-) Considering maybe install wine/bochs/some emulator and trying to run the Cingular software just to see what happens. And I haven't ever tinkered with ndiswrapper, but it was mentioned in one of the few posts Goggle returns when looking for 'ac860 linux' etc.

Hang in there, someone will cure us (or we'll learn enough to cure ourselves :-) )

Well I will keep checking back. I have had to switch to Mandriva so that I can access a local wifi network, but only until I can get the 860 figured out. Please pm me if you have a solution :)

---

### Post by Makyver on 2007-01-04
I'm using kppp and as long as the card initializes fine kppp will connect everytime ... I've never gotten gprsec to work install yes but actually work with this card no ... 
modem initialization string under modems 
at+cgdcont= 1,"IP","ISP.CINGULAR" 
Under Profile
dial *99#
and authentication type PAP/CHAP
then you just need the username and password which you have !!

If you need more I'll take screenshoots of it all for you if need be ...

Just make sure the card isn't flashing orange if it is it will not connect no matter what you do untill you get it to restart correctly ...

---

