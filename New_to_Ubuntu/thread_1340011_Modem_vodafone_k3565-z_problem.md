---
title: "Modem vodafone k3565-z problem"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by izh34 on 2009-11-28
Hi. I just install Ubuntu 9.10 on my old dekstop computer and now try to connect to the internet. But there is problem when I plug-in my mobile broadband USB. Ubuntu won't detect my modem vodafone k3565-z.

I had followed all the instructions given but to no avail.

[http://www.betavine.net/bvportal/resources/datacards/os/ubuntu](http://www.betavine.net/bvportal/resources/datacards/os/ubuntu)

[http://www.geekology.co.za/blog/2009/05/configuring-vodafone-3g-modem-on-ubuntu-linux-904-jaunty-jackalope/](http://www.geekology.co.za/blog/2009/05/configuring-vodafone-3g-modem-on-ubuntu-linux-904-jaunty-jackalope/)

[http://www.betavine.net/bvportal/forums/index.html?threadId=ff80808122c6188b0122d804ad79382a](http://www.betavine.net/bvportal/forums/index.html?threadId=ff80808122c6188b0122d804ad79382a)

I had download:
[ozerocdoff_0.4-2_i386.deb]("https://forge.betavine.net/frs/download.php/538/ozerocdoff_0.4-2_i386.deb") - success
[usb-modeswitch_0.9.7_i386.deb]("https://forge.betavine.net/frs/download.php/490/usb-modeswitch_0.9.7_i386.deb") - success


[vodafone-mobile-connect_2.15.01-1_all.deb]("https://forge.betavine.net/frs/download.php/565/vodafone-mobile-connect_2.15.01-1_all.deb")  - failed
[vodafone-mobile-connect_svn20090615_all.deb - failed]("https://forge.betavine.net/frs/download.php/542/vodafone-mobile-connect_svn20090615_all.deb")

failed to install as this message appear after I tried to install:

Error: Dependency is not satisfiable: python-gnome2-extras

Can anybody help me, please? I really in confuse now.

---

### Post by alexfish on 2009-11-28
try 

right click on the network manager     should be in   top right panel

select edit connections

in the window click on the Mobile Broadband

click on the  +Add

you should now see a wizard

click forward 


pick your country

in my case its  gb  for the United Kingdom

so pick your country

in the  pane below   pick your  " provider " and the type of plan your on 

Note : if you have forgot the type of plan  your on please try to find out 


click next

next window gives you summary of the details  check that they are correct 

  if incorrect click back  to edit
  if they are correct click apply


in the network connections you should now see the connection

  if you have a pin code activated on the device    click on edit

   enter your pin code  / do not change any other settings for now

   
 also tick the box  Connect Automatically


  click apply and then close


  if nothing happens unplug the stick 

      and plug back in 
     
    you may be ask for a password by the keyring manager / pick something that is easy 
to remember
    
  some times a reboot works after this

---

### Post by izh34 on 2009-11-28
@alexfish thanx 4 the reply.

Now after a bit try n error, Ubuntu seems to detect my modem and the icon to connect to internet seems to be appear. But when I enter firefox, nothing happen. Seems firefox doesn't recognize I have internet connection. Why this happen as I have connect to my modem? Can anyone help me?

---

### Post by AlanR8 on 2009-11-28
That used to happen to me as well. Go to the File Menu and click the item "Work Off Line". FF seemed to need that when I first started using mobile BB

---

### Post by izh34 on 2009-11-28
> **AlanR8 said:**
> That used to happen to me as well. Go to the File Menu and click the item "Work Off Line". FF seemed to need that when I first started using mobile BB

seems not working here.

Now again Ubuntu won't detect my modem. Just a minute it can but not now. Is it unstable for the driver to use on my Ubuntu?

---

### Post by alexfish on 2009-11-28
you now go to the network manager deselect the  auto connect

          go back to the browser and select to work online

   unplug the stick and plug it back in

     wait for the system to settle 

     look at the network manager    if you see the connection click connect

             you may see confusing messages / just wait 

NOTE : assuming there is an led on the device  then normally this will change from flashing 
  to on all the time  / this indicates that the device is connected to your service provider 

close the browser

     when connected try the browser

---

### Post by alexfish on 2009-11-28
for other network problems have a look here / LOOK BEFORE YOU LEAP

RE: pppoe connection via NetworkManager

[http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html](http://www.ubuntugeek.com/how-to-setup-networkmanager-work-with-pppoe-connection-on-ubuntu-9-10-karmic.html)

---

### Post by alexfish on 2009-11-28
here are some screen shots .I have done this  from the live cd ,but  if you have installed ubuntu 9.10  the principal is the same as described . there should be no need to download anything from betavine
   at this stage    . most providers  have accounts that can be accessed through the web

---

### Post by izh34 on 2009-11-28
I can't really say what my problem now is. I plug-in my mobile modem and nothing comes out. Only it storage function and not its connection as modem.

I have install the 2 most important file that are:
[ozerocdoff_0.4-2_i386.deb]("https://forge.betavine.net/frs/download.php/538/ozerocdoff_0.4-2_i386.deb")
[usb-modeswitch_0.9.7_i386.deb]("https://forge.betavine.net/frs/download.php/490/usb-modeswitch_0.9.7_i386.deb")

But fail with
[vodafone-mobile-connect_svn20090615_all.deb]("https://forge.betavine.net/frs/download.php/542/vodafone-mobile-connect_svn20090615_all.deb")

Is this related for making my modem being read as storage rather than modem? Or I just need another method to make my modem works?

---

### Post by alexfish on 2009-11-28
at the moment the best thing I can suggest is 

  go to the synaptic package manager and  uninstall  the ozerocdoff

    and the usb-modeswitch  / you don't need these at present

   go to  the network manager and delete the connection
 

    then reboot the computer  without the usb modem

      wait for the system to settle before putting the modem back in
    

        repeat from the start  of my post /   but do not alter any setting in the web browser
             
          the next post I will make  will show you  how linux will detect the modem

---

### Post by alexfish on 2009-11-28
from the menus /applications click on the terminal

  in the terminal type or copy this code into the terminal

lsusb

look at the screen shot    this should show a list of devices


do you see the same in your terminal

Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

 can you post  a screen shot  of results shown in the terminal

---

### Post by alexfish on 2009-11-28
this is the screen shot

---

### Post by alexfish on 2009-11-29
Having Look at your listing you have downloaded  the wrong version

["www.geekology.co.za/blog/2009/05/configuring-vodafone-3g-modem-on-ubuntu-linux-904-jaunty-jackalope/]("http://www.geekology.co.za/blog/2009/05/configuring-vodafone-3g-modem-on-ubuntu-linux-904-jaunty-jackalope/")"    
NOTE THE VERSION
^^^^^^^^^^^^^

you have Ubuntu 9.10  so the packages may  not work  please if you can uninstall them

---

### Post by alexfish on 2009-12-05
> **AlanR8 said:**
> That used to happen to me as well. Go to the File Menu and click the item "Work Off Line". FF seemed to need that when I first started using mobile BB


**Firefox 3 and PPP connections - fixing Firefox starting in Offline Mode **

 The writers of Firefox 3 have tried to be clever and automatically start Firefoz in the Offline Mode if there is no internet connection present. They have done that in Linux by checking if Network Manager has an open connection which is fine for the Ethernet and Wireless Network connections that are looked after by Network Manager. Unfortunately Network Manager does not know about Point to Point Protocol connections - that is dial up and other mobile connections using the PPP daemon. The result is that if you make a connection using gnome-ppp Firefox swithes into Offline Mode when it starts and it has to be switched back using File -> Work Offline. This is OK for the occasional connection but gets very tedious if you have mobile broadband in use all the time or have a old telephone dial up via a modem. This has been discussed at length and there is now an option to inhibit the feature but only deep in the configuration. The way to access it is by entering **about:config** in the address bar and then enter. This will bring up a warning screen about dragons being present so you have to take care - click Ok and then enter **toolkit.networkmanager.disable** into the filter which will reduce you down to a view of the required option which will be currently set to false. Right click -> **Toggle** - this will change the value to **true** and inhibit the check in network manager. Exit Firefox and when you next use it on a PPP connection it will no longer start up offline. For more details see [The Mozillazine Article toolkit.networkmanager.disable]("http://kb.mozillazine.org/Toolkit.networkmanager.disable")

---

### Post by alexfish on 2009-12-09
Tip

If you have problems The Web Browser Connecting to The Server Try This

    Leave the Browser On  

  " Disconnect  The Mobile Connection "      Then Re Connect  

     Click The Try Again Button  in the Browser

---

### Post by izh34 on 2010-06-01
Thanx all. My problem is now fixed. I installed the usb-modeswitch and [ozerocdoff_0.4-2_i386.deb]("https://forge.betavine.net/frs/download.php/538/ozerocdoff_0.4-2_i386.deb").

Wait for a minute or two, wallah, my bb comes alive.

---

