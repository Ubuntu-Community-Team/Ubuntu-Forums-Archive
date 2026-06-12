---
title: "Ubuntu - Kubuntu Wireless Blind"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by cooleysreel on 2008-05-02
Hi everyone

Noob incoming

I installed Ubuntu Hardy Heron on this 1st gen macbook using bootcamp dual boot with Leopard a couple of days ago.All went well, wireless worked "straight out of the box". 

 Feeling rather pleased with it all I opted to also install the KDE with Kubuntu desktop to compare. Odd thing is , whenever I run KDE first without having logged into and out of Gnome - No wireless device is found.

So, network settings are set to run in roaming mode and network toolls shows loopback interface, all works fine in gnome. The settings are carried over  ( it seems) when I launch KDE - but if I then hibernate or suspend the KDE the wireless link disappears and I will have to log out of KDE, into Gnome  and back into KDE to wake up the device recognition.

whats going on there ? - any suggestions ?  [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

I am the greenest noob  by a long stretch - any help will be appreciated

thanks.

---

### Post by desktopj on 2008-05-02
> **cooleysreel said:**
> Hi everyone

Noob incoming

I installed Ubuntu Hardy Heron on this 1st gen macbook using bootcamp dual boot with Leopard a couple of days ago.All went well, wireless worked "straight out of the box". 

 Feeling rather pleased with it all I opted to also install the KDE with Kubuntu desktop to compare. Odd thing is , whenever I run KDE first without having logged into and out of Gnome - No wireless device is found.

So, network settings are set to run in roaming mode and network toolls shows loopback interface, all works fine in gnome. The settings are carried over  ( it seems) when I launch KDE - but if I then hibernate or suspend the KDE the wireless link disappears and I will have to log out of KDE, into Gnome  and back into KDE to wake up the device recognition.



Have you setup your wireless in Knetworkmanager? It should be in your tray at the bottom around the right side. On my KDE tray it looks like a little bar graph. I right click it for menu options, including whether Knetworkmanger starts when logging in. 

Jeff

---

### Post by cooleysreel on 2008-05-06
Thanks for picking this up

Hm..

Yes , I ve had a good poke around there. It displays the same as Network manager from gnome when its working. KNetwork manager seems greyed out when theres no wireless connection. When it's seeing my wireless device (after running a gnome session) all the fields are filled in correctly. I cant see an option to have it run at startup though. The only button seems to be the "OK" button. No doubt I'm missing something.

---

### Post by desktopj on 2008-05-07
> **cooleysreel said:**
> Thanks for picking this up

Hm..

Yes , I've had a good poke around there. It displays the same as Network manager from gnome when its working. KNetwork manager seems grayed out when theres no wireless connection. When it's seeing my wireless device (after running a gnome session) all the fields are filled in correctly. I cant see an option to have it run at startup though. The only button seems to be the "OK" button. No doubt I'm missing something.

Oh, just noticed your using a macbook and kde4. Do you have a right mouse button?? 

Also, I've also installed the kde4 and the gnome desktops (menus are a bit overloaded), and really found the kde3 (standard kubuntu)the easiest to setup for wireless. I ran the install for my bcm4306 (bm43 and wl_apsto.o) while in Kubuntu.

You should see a bar graph for wireless, a plug when cat5 is connected and a spinning gear when either is getting an ip address. There should be an options panel to select if you are really accessing knetwork manager.

Even noticed that unlike my XP install (dual boot), Kubuntu disables the wireless connection when I'm connected via ethernet to the same network, and switches seamlessly between each. 

Jeff

---

