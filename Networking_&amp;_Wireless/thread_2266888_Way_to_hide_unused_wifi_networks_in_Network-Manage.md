---
title: "Way to hide unused wifi networks in Network-Manager menu?"
date: 2015-02-26
forum: Networking &amp; Wireless
---

### Post by greg2lapa on 2015-02-26
Anybody know if there is a way to remove (stop displaying) completely unused/unwanted Wifi networks in the Network Manager (NM) menu? When user clicks the network manager indicator  [IMG]http://a.pomf.se/liysmb.png[/IMG]  a dropdown appears and lists wifi networks. Except I only ever connect to a couple networks. And yet I have to wade through a bunch of never-used networks (ones I have never connected to and never will connect to) each time I want to access my networks.

  There is a folder "More networks" in the dropdown. Is there some way to move networks I will never connect to into that folder so that they do not crowd up the NM dropdown?

It seems a bad design to me to force the user to have to do deal with selecting from so many networks when they are all unused. When I click on the Network Manager Indicator  [IMG]http://a.pomf.se/liysmb.png[/IMG]  and select "Edit Connections" and then look under the "Wifi" heading, only a couple networks appear. So why do 5 or more regularly show in the Network Manager dropdown (5 or more I never have connected to)? Is there a way to make networks that do not show under the "Wifi" heading be confined to the "More networks" folder?

Here's a picture with an example of some networks I would like to hide/remove from the dropdown.
[[IMG]http://a.pomf.se/fdqlnn.png[/IMG]]("http://a.pomf.se/fdqlnn.png")

---

### Post by kerry_s on 2015-02-26
those are other networks around you, there suppose to show up.

---

### Post by ian-weisser on 2015-02-26
> **greg2lapa said:**
> It seems a bad design to me to force the user to have to do deal with selecting from so many networks when they are all unused.

You can tell the system to automatically join your favorite networks when they are detected.
It's an option under 'Edit Connections'
The design assumes you use that feature, and select from the menu only when no favorites are in range.

Selecting the same SSIDs over and over would indeed be a poor design if you had to do that.

---

### Post by greg2lapa on 2015-02-26
> **kerry_s said:**
> those are other networks around you, there suppose to show up.

I understand that what I'm reporting is not a "bug." But the idea that they are "supposed to show up" is non-sensical. Why should networks I have never connected to, ones I will never connect to, perpetually display in my menu? It makes no functional sense and only impedes the use of the networks I do use.


> **ian-weisser said:**
> You can tell the system to automatically join your favorite networks when they are detected.
It's an option under 'Edit Connections'
The design assumes you use that feature, and select from the menu only when no favorites are in range.

Selecting the same SSIDs over and over would indeed be a poor design if you had to do that.


Yes, I know I can automatically join networks when they are in range. But there are numerous reasons one might not want to allow this. And even if this is enabled, there still is no reason to be displaying networks that I never connect to. They could just as easily live in the "More networks" folder.

Selecting the same SSIDs over and over is not required (as you describe with the auto-connect setting), but a user regularly selects from a few networks, it is counter-productive to constantly display networks he/she NEVER connects to in the list.

---

### Post by chili555 on 2015-02-26
> But the idea that they are "supposed to show up" is non-sensical.Not at all, actually.

NM tries to be, as do many things in life, all things to all people all the time. In so doing, it is actually not quite all things in every last case. Your particular issue is the first I recall reading in my years and posts on the forums.

One of the hardest things about networking, before NM came along, was going from home to school to coffee shop with a laptop and connecting to several different networks in one day. Can it be done without NM? Sure. Is it easily done by an ordinary non-nerd? Certainly not. NM makes it simple.

Actually, once you've told NM to connect to your network automatically, there is no need to click the NM menu at all. I just now clicked mine to see if it is still there! It is. If you don't want to see the other networks, simply don't click the menu!

Please see my answer to your question at askubuntu.

---

### Post by kerry_s on 2015-02-26
lol
sudo apt-get purge network-manager

there all fixed no more wifi menu. muhaha

---

