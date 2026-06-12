---
title: "System menu doesn't show &quot;Network&quot;"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by jkkmmck on 2008-11-22
Hi all,

Relative Linux newbie here, trying to get Xubuntu 8.10 up and running on my new MSI Wind netbook -- just got it today. Got the OS installed, but no wireless action at all. Before I start thinking about any hardware specific issues, installing ndiswrapper, etc., I just tried to read the Xubuntu docs -- Chapter 7, Internet -- but I'm stymied as soon as I get to the first instruction|: "Open Applications -> System -> Network." On my default install, [B]there is no panel called Network under the System menu.
[/B]
Any thoughts appreciated. Thanks!

---

### Post by Olivier2371 on 2008-11-22
Have you try to install a more stable version of xubuntu, like 8.04.

What kind of wireless adapter are you using?

---

### Post by jkkmmck on 2008-11-23
Yeah, I could try going down to 8.04, thanks for the suggestion.

The wireless card is, I believe, a Realtek RTL8187SE, although I don't know how to check that on the machine itself.

---

### Post by Olivier2371 on 2008-11-23
To check what adapter you have,

Application->System Tools->Device Manager.

If you don't have Device Manager follow below:

Applications->Add/Remove...

Search for Device Manager, install it.

Then Applications->System Tools->Device Manager

Click in the menu View->Properties

Then look at the picture Below to find your adapter.

[ATTACH]93855[/ATTACH]

---

### Post by jkkmmck on 2008-11-23
thanks for the tip, I was able to download Device Manager and confirm that it's a Realtek RTL8187SE. I found some instructions on <a href="http://forums.msiwind.net/debian/how-have-wireless-ubuntu-models-with-rtl8187se-t4925.html">msiwind.net</a> which should allow me to get the drivers for that card installed.

---

### Post by Olivier2371 on 2008-11-23
your link seems to be the right one.

If you need a driver here is the link.

[http://www.mediafire.com/download.php?pavvaazisj1]("http://www.mediafire.com/download.php?pavvaazisj1")

---

### Post by jkkmmck on 2008-12-01
fyi, my problem with not seeing applications->system->network was that I had to turn it on by choosing the "add/remove..." option. From there I could turn the Network panel on.

more an issue of ubuntu unfamiliarity than anything else i guess!

Now, on to get the driver downloaded.

---

### Post by tonykaz1 on 2008-12-08
I'm having the same problem. I can't get the wireless network configured because there is no "Applications / System / Network" option. I can't just add the device manager because it needs to be downloaded and I have no connection to the internet. This seems to be a catch-22 situation.

Is there any way to get my wireless internet connection to work in Xubuntu 8.1 without downloading a program that requires me to be connected to the internet?

---

### Post by RomanIvanov on 2008-12-08
I use Xubuntu 8.10 and this application named NetworkManager([http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)) and it should be run just after installation - /usr/sbin/NetworkManager


Try to type in terminal: "sudo mn-connection-manager"  (it is like 8.04 manager)

---

### Post by jvanbonn on 2009-01-23
I think I'm at this point...  Where is the Add/Remove option where you turned it on?

---

### Post by lowbot on 2009-02-10
I'm a little confused. I also have this issue. There is no gui entry for NetworkManager in the System menu.

sudo ./NetworkManager in ./usr/sbin doesnt do anything. It just gives me the prompt again.

I guess I can use webmin or just edit the text file that holds the networking info, but Id like to use this tool.  I verified its installed in add/remove too. Its there, but I cant run it. Any ideas?

---

