---
title: "In search of a remote ( desktop ) manager ?"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by genbuntu on 2008-05-13
Hello Everyone

Having searched through various remote desktop applications I am now confused with the wide variety that is available out there. Hence I'm looking for your opinions and/or experiences , especially on the most desired features like :
a) Ease of use / setup
b) Features
c) Encryption protocol/standards
d) Functionality  etc.

Of-course multi-platform and open-source applications will be a plus but let us leave that optional for now.

My need(s): It arose because I wanted to help a family member overseas (on Windows) with their computer problems occasionally. I have ubuntu / XP dual booted but it'll be nice if I could use only ubuntu on my side.  Also, as with many other people, it is nice to have our home computer accessible from work and vice versa , so I hope everyone can benefit from this thread :) .

Now according to my search on net and the forums I've found the following applications that can be used :

1) **RealVNC**: (free edition ; multi platform ; secure password verification but unsecure session ; some router / firewall configuration to be done)
Site: [http://www.realvnc.com](http://www.realvnc.com)

2) **UltraVNC**: ( free edition ; windows ; full encryption ; I think some configuration is required plus plugins ; open source )
Site: [http://www.uvnc.com](http://www.uvnc.com)

3) **Teamviewer**: ( free for personal use ; windows & mac ; full encryption ; probably no configuration required )
Site: [http://www.teamviewer.com](http://www.teamviewer.com)

4) **TightVNC**: ( free ; windows & unix; secure password but unencrypted session ; router / firewall configuration required ; better for low bandwidth connections ; open source )
Site: [http://www.tightvnc.com](http://www.tightvnc.com)

5) **Java Remote Desktop**: ( free ; cross platform ; authentication & encryption ; newer project ; open source)
Site: [http://jrdesktop.sourceforge.net/](http://jrdesktop.sourceforge.net/)

6) **WallCooler**: ( free edition ; windows only ; authentication & encryption ; little or no configuration )
Site: [http://www.vedivi.com/](http://www.vedivi.com/)

7) **FreeNX**: ( free ; unix-like OS only ; good for low bandwidth connections ; requires router / firewall configuration ; open source)
Site: [http://freenx.berlios.de](http://freenx.berlios.de)

8 ) **Remobo**: (free ; windows only for now ; secure data transfer ; little or no router / firewall configuration ; still in beta stage)
Site: [http://www.remobo.com](http://www.remobo.com)

9) **LogMeIn** , (Hamachi also for remote lan access): ( free edition ; windows & mac ; encrypted traffic ; little or no router / firewall configuration )
Site: [http://www.logmein.com](http://www.logmein.com)

 That sums up most of the products I've found out , which atleast have a free version available for use. 
 I have personally used logmein to connect to a windows pc ( from a windows pc) and found it really easy to use. Have not tried the viewer from Ubuntu though it should work from any browser with java installed.

 So let the thoughts flow ;) . Please share your experiences , recommendations and any other information you'd like to :).

---

### Post by superprash2003 on 2008-05-13
install tightvnc server on the computer you want to connect to.. and in your ubuntu pc go to the terminal and type vncviewer x.x.x.x:0 where x.x.x.x is the ip of the pc which has tightvnc installed

---

