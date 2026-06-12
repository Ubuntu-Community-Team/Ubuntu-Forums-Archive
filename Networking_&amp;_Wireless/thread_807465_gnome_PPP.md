---
title: "gnome PPP"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by djen9999 on 2008-05-25
My brother is trying to get his modem working but he needs gnome PPP to configure it properly.  The only problem is that he needs an Internet connection to GET gnome PPP.  I'm several thousand miles away so I'm of no help.  He lives in a remote area with little access to groups or individuals to help out.  Is there any way he can use his winmodem in Windows (He's using Wubi) to download gnome PPP and then port it over to Ubuntu?  Any other suggestions will also be helpful.

---

### Post by lswb on 2008-05-25
Hi,

If he has a standard ubuntu installation it should include pppd and a text-mode program called pppconfig. From a terminal he can run

sudo pppconfig

It will prompt him for the information necessary for a ppp dialup connection and create the necessary files. AFAIK it can do everything that gnome-ppp does when it comes to configuring the connection, it just doesn't have the graphicla support like the tray icon & built-in dialer. 

When pppconfig is done, while still in the terminal, type 

ppp connection-name

where connection-name is the name that was given while the pppconfig program was running.

You close the connection by typing the command "poff"

do a man pppd, man pppconfig, and man pppd for more info.

---

### Post by djen9999 on 2008-05-26
Thanks for the info I wanted to get gnome PPP for him because he knows nothing about the terminal.  I think I can talk him through it though.  Once he gets on line, he'll be able to download whatever he needs.  Thanks again.

---

### Post by hillhopper on 2008-06-15
I have Ubuntu 7.04 partially upgraded to 7.10.  After the long download/installation of files, and the subsequent reboot, the PPP dialup config had to reinstalled on a newer version of Linux to run the proprietary modem driver.  Not worried, it ran well before the upgrde.  Ok.  Runs now, but after the driver reinstall, wvdial reinstall, and Gnome PPP reinstall, it connects as always, BUT, leaves an unfinished progress notice on the desktop.  This small window Titled "Connecting..., prints "Authenticating..." above two radio buttons marked Log (left) and circle X Cancel(underscored C).

Before the partial upgrade, this window disappeared and a small double computer flashing traffic icon would be placed between the volume control icon andthe Networking icon next to the clock on the top desktop bar.

No biggie, but a temporary annoyance of unfinished-ness.  (Wish I could write this stuff like some folks.)  Any suggestions/news on this glitch?  Is it typically new, or peculiarly my problem only.  Thanks and Happy Computing!

In the Package manager properties page for Gnome PPP, there is a Dependencies Tab.  Bottom of the file list is one Conflict entry. resolvconf

"Seek and ye shall find."  See:[https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487/]("https://bugs.launchpad.net/ubuntu/+source/gnome-ppp/+bug/121487/")

---

