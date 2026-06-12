---
title: "Shared Internet Conection Linked to a Wireless Router"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by Sir_Clintus on 2008-06-13
I am wondering if its possible and if so How? If with ubuntu you can grab a wireless internet connection then using a shared internet connection wire a router through an ethernet card to another wireless router and broad cast that connection.

Diagram


Wireless ISP ----> Ubuntu ----(wired)----> Belkin Wireless Router

Belkin Wireless Router ----(wireless)----> Wii
Belkin Wireless Router ----(wired)-------> Xbox 360
Belkin Wireless Router ----(wireless)----> Windows PC
Belkin Wireless Router ----(wireless)----> iphone

The reason for this is because at the university I am living at, the internet requires a keycode entered in via using an internet browsers such as IE or Firefox. So gaming systems such as a Xbox 360 or a Wii will not connect through our internet. What we do is using our windows laptops is grab the signal and use an ethernet cord to plug into the xbox360. 

I want to be able to do this wirelessly so I will not have to hook my laptop all the time to my xbox and not have to by a ethernet adapter for my Wii.

***Status***

I created a Desktop Ubuntu computer with spare parts and got it connected to the internet via a wireless card and everything is updated. I have a wireless router on the way.

---

### Post by SpaceTeddy on 2008-06-13
this does not sound too hard... all you need is to enable ip_forward, load a nat rule into the ubuntu machine and (optinionally) create a dhcp-server that will hand out leases to the wifi clients.

Here are a few steps i have written down for [[COLOR="Blue"]internet sharing with ubuntu[/COLOR]]("http://ubuntuforums.org/showthread.php?t=713874"). 

hope it helps :)

---

### Post by Sir_Clintus on 2008-06-13
I was reading through the link you gave me and there is a section that reads "this is only for ethernet" not for wireless. Would this effect me?

---

### Post by SpaceTeddy on 2008-06-13
mhm, must hate written it down wrong... this setup will work on any ubuntu that has at least two network cards - or more. Could you please point out to me where i wrote that so i can correct this for people reading the article in the future. 

thanks:)

---

### Post by Sir_Clintus on 2008-06-13
Sweet Sounds good when I get everything in I will give this all a whirl. and keep you updated. I will try and document everything I do, to post a thread possibly with screenshots.


The location is under the section "Configuring the Network Card" its right after the first set of code you have posted.

---

