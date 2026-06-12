---
title: "Connecting to a DSL connection using the network panel"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by NikS on 2011-05-12
Hi,

I have installed KDE on the ubuntu 11.4 system.
In the networking interface on the panel below, it does not list the connection even after creating one.

I can connect to internet by typing pppoeconf in the terminal though, but the networking interface in KDE wont show if I am connected or not!

In unity, it lists the connection and I can connect to it.

How do I make the networking panel work?

---

### Post by NikS on 2011-07-28
May be I should rephrase the question.. How do I connect to Internet in Kubuntu 11.4 without going through terminal?

---

### Post by NikS on 2011-07-31
Alright..
Seems everyone's vanished from the forum.. :p kidding.. I know you guys must be busy..
Anyways, have found a solution that worked for me, just documenting..

While Googling I was navigated to the bug link: [https://bugs.launchpad.net/ubuntu/+source/plasma-widget-networkmanagement/+bug/447241]("https://bugs.launchpad.net/ubuntu/+source/plasma-widget-networkmanagement/+bug/447241")

As per the discussion there, we can use the gnome network manager that is already installed on the ubuntu system (or can install..)

Add "nm-applet" to the autostart as a script. I am not sure what the option '--sm-disable' does, but it caused all the menus from the panel to appear at the top of the screen, as if it was ubuntu's panel at the top.. removing that line fixed the issue, all menus back to their positions... And also of the network manager.. Its working fine, detecting my networks configured from Ubuntu, allowing me to connect and also detecting the connection and showing correct icon. :)

---

### Post by FerroPower on 2011-08-19
I am also unable to connect to my DSL net using the Plasma NetworkManager, I have to use the terminal pppoeconf to connect. 

maybe this bug will take its own sweet time to get fixed. 

New Kubuntu users will get fustrated trying to connect DSL using Plasma Network Manager.

---

